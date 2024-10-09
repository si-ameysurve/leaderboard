<template>
  <div>
    <div class="waf-body">
                                <div class="table standings-table">
                                  <div class="table-head">
                                    <div class="table-row">
                                      <div class="table-data matches-position"><p class="text">#</p></div>
                                      <div class="table-data matches-team"><p class="text">Clubs</p></div>
                                      <div class="table-data matches-play"><p class="text">Played</p></div>
                                      <div class="table-data matches-won"><p class="text">Won</p></div>
                                      <div class="table-data matches-draw"><p class="text">Draw</p></div>
                                      <div class="table-data matches-lost"><p class="text">Lost</p></div>
                                      <div class="table-data matches-goal-for"><p class="text">GF</p></div>
                                      <div class="table-data matches-goal-against"><p class="text">GA</p></div>
                                      <div class="table-data matches-goal-difference"><p class="text">GD</p></div>
                                      <div class="table-data points"><p class="text">Points</p></div>
                                      <div class="table-data form-guide"><p class="text">Form</p></div>
                                    </div>
                                  </div>
                                  
                                  <div v-for="(x,index) in qwerty2" :key="x.team_id" class="table-body">
                                    <div id="row-0" class="table-row">
                                      <div class="waf-accordion-head">
                                        <div class="table-row table-row-head">
                                          <div  class="table-data matches-position">
                                            <div class="table-data-wrap">
                                              <p class="position">{{ index + 1 }}</p>
                                              <p class="position-indicator"></p>
                                            </div>
                                          </div>
                                          
                                          <div  class="table-data matches-team">
                                            
                                            <div class="table-data-wrap">
                                              <div class="team-name">
                                                <p class="name full-name">{{x.team_name}}</p>
                                                <p class="name short-name">{{x.short_name}}</p>
                                                
                                              </div>
                                            </div>
                                            
                                            
                                            
                                          </div>
                                          <div  class="table-data matches-play">
                                            
                                            
                                            
                                            <p class="count">{{ x.played }}</p>
                                            
                                          </div>
                                          <div  class="table-data matches-won">
                                            
                                            
                                            <p class="count">{{ x.wins }}</p>
                                            
                                          </div>
                                          <div  class="table-data matches-draw">
                                            
                                            
                                            
                                            <p class="count">{{ x.draws }}</p>
                                            
                                          </div>
                                          <div  class="table-data matches-lost">
                                            
                                            
                                            
                                            <p class="count">{{ x.lost }}</p>
                                            
                                          </div>
                                          <div  class="table-data matches-goal-for">
                                            <p class="count">{{ x.gf }}</p>
                                          </div>
                                          <div  class="table-data matches-goal-against">
                                            <p class="count">{{ x.ga }}</p>
                                          </div>
                                          <div  class="table-data matches-goal-difference"> 
                                            <p class="count">{{Number(x.gf) - Number(x.ga)}}</p>
                                          </div>
                                          <div  class="table-data points">
                                            <p class="count">{{ x.points }}</p>
                                            
                                          </div>
                                          
                                          
                                              <div  class="table-data form-guide">
                                                <div v-for="(y,index) in arr[index]" :key="index" > 
                                                  <ol v-for="(z,index1) in y" :key="index1"  class="form-guide-listing">
                                                      <li class="form-guide-item" 
                                                      :class="{
                                                        'win' : z ==='W',
                                                        'lost' : z === 'L',                                                                                                                                                                                    
                                                        'draw' : z ==='D',
                                                        'no-match' : z === '-'
                                                      }">
                                                          <p  class="text">{{ z }}</p>
                                                      </li> 
                                                  </ol>
                                                </div                         >
                                              </div>
                                              
                                              </div>  
                                        </div>
                                        </div>
                                        
                                      <div
                                        id="standingsRow-0"
                                        role=""
                                        aria-labelledby="standingsAccordion0"
                                        class="waf-accordion-panel"
                                        hidden="true"
                                        >  
                                      </div>
                                    </div>
                                    </div>
                                  </div>      
                                </div>
                                </template>



<script>
  import qwerty from '../standings/data/standings.json'
  const qwerty2 = qwerty.standings.groups[0].teams.team;
  console.log(qwerty2);
  // console.log( "zxc " + qwerty.standings.groups[0].teams.team[0].home_wins);
  // console.log( "zxc " + qwerty.standings.groups[0].teams.team[0].match_result.match[0].result);
  // console.log(qwerty.standings.groups[0].teams.team[0]);
  // console.log(arr)

export default {
  data(){
    return{
      qwerty2 : qwerty2,
      qwerty : qwerty,
      arr : []

    }
  },
  created(){
    this.formData()
  },
  methods:{

    formData(){
      let arr = []
      console.log("inside")
      qwerty.standings.groups[0].teams.team.forEach(x => {
        const arr2 = new Array(5).fill("-")
        console.log("inside x ");
        let index = 0;
        x.match_result.match.forEach(z => {
            arr2[index++] = z.result;
          }) 
          this.arr.push(arr2)
          console.log(arr2)

    }
  )
    
    console.log(arr)
  },
  

}
}
</script>



