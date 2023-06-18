<template>
    <div id="DynamicResume">
      <h1>{{ metaData.basics.name }}</h1>
      <hr />
      <p><em>{{ metaData.basics.label}}</em></p>
      <p><a href="{{ metaData.basics.email}}">{{ metaData.basics.email}}</a></p>
    <br />
    
    <h2>Work History</h2>
    
    <div class="grid-wrapper">
        <div class="work-grid" v-for="workItem in metaData.work" :key="workItem.name">
          <div class="workStartDate floatleft">Start: {{ workItem.startDate}}</div>
          <div class="workEndDate">Ended: {{ workItem.endDate}}</div>
          <div class="workName">{{ workItem.name}}</div>
          <div class="workPosition">{{ workItem.position}}</div>
          <div class="workUrl"><a href="{{ workItem.url}}">{{ workItem.url}}</a></div> 
          <div class="workSummary">{{ workItem.summary}}<br />
          <h5>Highlights:</h5>
            <ul>
              <li v-for="highlight in workItem.highlights" :key="highlight">{{ highlight}}</li>
            </ul>
          </div>
          <br /><br />
    </div>
    
    <h2>Volunteering</h2>
    <div class="grid-wrapper">
        <div class="work-grid" v-for="workItem in metaData.volunteer" :key="workItem.organization">
          <div class="workStartDate floatleft">Start: {{ workItem.startDate}}</div>
          <div class="workEndDate">Ended: {{ workItem.endDate}}</div>
          <div class="workName">{{ workItem.organization}}</div>
          <div class="workPosition">{{ workItem.position}}</div>
          <div class="workUrl"><a href="{{ workItem.url}}">{{ workItem.url}}</a></div> 
          <div class="workSummary">{{ workItem.summary}}<br />
          <h5>Highlights:</h5>
            <ul>
              <li v-for="highlight in workItem.highlights" :key="highlight">{{ highlight}}</li>
            </ul>
          </div>
          <br /><br />
    </div>
    </div>
    
    <h2>Education</h2>
    <div class="grid-wrapper">
        <div class="work-grid" v-for="workItem in metaData.education" :key="workItem.institution">
          <div class="workStartDate floatleft">Start: {{ workItem.startDate}}</div>
          <div class="workEndDate">Ended: {{ workItem.endDate}}</div>
          <div class="workName">{{ workItem.institution}}</div>
          <div class="workPosition">Study Type: {{ workItem.studyType }}<br />
            Score: {{ workItem.score}}</div>
          <div class="workUrl"><a href="{{ workItem.url}}">{{ workItem.url}}</a></div> 
          <div class="workSummary">{{ workItem.summary}}<br />
          <h5>Courses:</h5>
            <ul>
              <li v-for="course in workItem.courses" :key="course">{{ course}}</li>
            </ul>
          </div>
          <br /><br />
    </div>
    </div>
    <h2>Awards</h2>
    <div class="grid-wrapper">
        <div class="work-grid" v-for="award in metaData.awards" :key="award.title">
          <div class="workName">{{ award.title}}</div>
          <div class="workPosition">date: {{ award.date }}<br /></div>
          <div class="workUrl">Awarder: {{ award.awarder}}</div> 
          <div class="workSummary">{{ award.summary}}<br />
          </div>
          <br /><br />
    </div>
    </div>
    
    <h2>Certificates</h2>
    <div class="grid-wrapper">
        <div class="work-grid" v-for="certificate in metaData.certificates" :key="certificate.name">
          <div class="workName">{{ certificate.name}}</div>
          <div class="workPosition">date: {{ certificate.date }}<br /></div>
          <div class="workUrl">Issuer: {{ certificate.issuer}}</div> 
          <div class="workSummary"><a href="{{ certificate.url}}">{{ certificate.url}}</a><br />
          </div>
          <br /><br />
    </div>
    </div>
    
    <h2>Publications</h2>
    <div class="grid-wrapper">
        <div class="work-grid" v-for="publication in metaData.publications" :key="publication.name">
          <div class="workName">{{ publication.name}}</div>
          <div class="workPosition">date: {{ publication.releaseDate }}<br /></div>
          <div class="workUrl">Publisher: {{ publication.publisher}}</div> 
          <div class="workSummary"><a href="{{ publication.url}}">{{ publication.url}}</a><br />
          {{ publication.summary }}
          </div>
          <br /><br />
    </div>
    </div>
    
    </div>
    </div>
    </template>
    
    <script>
    export default {
      name: 'DynamicResume',
      props: ['metaData'],
      created() {
        console.log("Exported Module");
      }
    }
    </script>
    
    <style>
    .floatleft {
        float: left;
    }
    .grid-wrapper {
      display: grid; 
      justify-content: center;  
    }
    .work-grid {
       display: grid;
       grid-template-rows: 1fr 1fr 1fr;
       grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
       gap: 0px;
       height: 100%;
       width: 960px;
       align-content: stretch;
    }
    .workName {
      align-content: left;
      border-bottom: 1px solid #47A3D8;
      grid-row-start: 1;
      grid-column-start: 1;
      grid-row-end: 2;
      grid-column-end: 4;
      font-size: 1.2em;
      text-align: left;
    }
    .workStartDate {
      border-bottom: 1px solid #47A3D8;
      font-style: italic;
      grid-row-start: 1;
      grid-column-start: 4;
      grid-row-end: 2;
      grid-column-end: 5; 
    }
    .workEndDate {
      border-bottom: 1px solid #47A3D8;
      font-style: italic;
      grid-row-start: 1;
      grid-column-start: 5;
      grid-row-end: 2;
      grid-column-end: 6;
    }
    .workPosition{
      font-style: italic;
      grid-row-start: 2;
      grid-column-start: 1;
      grid-row-end: 3;
      grid-column-end: 6;
      text-align: left;
    }
    .workUrl {
      grid-row-start: 3;
      grid-column-start: 1;
      text-align: left;
      grid-row-end: 4;
      grid-column-end: 6;   
    }
    .workSummary {
      grid-row-start: 4;
      grid-column-start: 1;
      grid-row-end: 5;
      grid-column-end: 6;
      text-align: left;
    }
    </style>