<template>
 <div  id="GDAudioDividendProductCtrl1">
    <Headerbtns :title = page_title>
        <div slot="left" class="back">
            <i class="fa fa-angle-left" @click="back()"></i>
        </div>
    </Headerbtns>
    <div class="manage-contents">
      <!-- 条码区 -->
      <div class="img1" style="display:flex;justify-content:space-between;">
          <div>
              <img src="../../../../static/img/policy/2011401.jpg"  style="width:130px;height:60px;">
          </div>
          <div>
            <img src="../../../../static/img/policy/logo.png"  style="width:130px;height:50px;">
          </div>
      </div>
      <div>
          <h1>录音录像客户问答内容确认书</h1>
          <h1>{{queType}}</h1>
      </div>
      <!-- 内容区 -->
      <div class="content">
          <p>您好，为维护您的权益，请您对投保录音录像客户问答内容进行确认。对话已作录音录像，请确保您的回答是您自己真实表示。</p>
          <p><b>问题1 ：</b>您的姓名是<input type="text" style="border-bottom: 1px solid black;width:35%;text-align:center;" readonly  v-model="dividendTypeBook.appntName">，
              身份证是<input type="text" readonly style="border-bottom: 1px solid black;width:60%;text-align:center;" v-model="dividendTypeBook.appntIDNo">,
              投保单号是<input type="text" readonly style="border-bottom: 1px solid black;text-align:center;" v-model="dividendTypeBook.prtNo">?</p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题2：</b></p>
          <p>（适用于趸交产品）您是否清楚您购买的是<input type="text" style="border-bottom: 1px solid black;width:50%;text-align:center;" readonly  v-model="dividendTypeBook.comName">保险有限公司
              <span style="border-bottom:1px solid #000">{{dividendTypeBook.riskName}}</span>产品，此产品是趸交产品，保险期是<input type="text" style="border-bottom: 1px solid black;width:30%;text-align:center;" readonly v-model="dividendTypeBook.insuYears">____年？</p>
          <p>（适用于期交产品）您是否清楚您购买的是<input type="text" style="border-bottom: 1px solid black;width:50%;text-align:center;" readonly v-model="dividendTypeBook.comName">保险有限公司<span style="border-bottom:1px solid #000">{{dividendTypeBook.riskName}}</span>
              产品，此产品是期交产品，交费期是<input type="text" style="border-bottom: 1px solid black;width:30%;text-align:center;"  v-model="dividendTypeBook.payYears">年，
              每年（期）交费<input type="text" style="border-bottom: 1px solid black;width:30%;text-align:center;" v-model="dividendTypeBook.prem">元，
              保险期是<input type="text" style="border-bottom: 1px solid black;width:30%;text-align:center;"  v-model="dividendTypeBook.insuYear">年？</p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题3：</b>您是否已对投保单填写内容逐项进行了核对，确认投保单上的填写内容是自己的真实意愿表示？</p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题4：</b>投保单上的风险提示语是否是您本人亲自填写的，内容是：本人已阅读保险条款、产品说明书和投保提示书，了解本产品的特点和保单利益的不确定性？</p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题5：</b>投保单、投保提示书等资料上的投保人和被保险人的签名，是否是由您（和被保险人）本人亲自签署的？</p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题6：</b>您是否知道自己享有保险合同中约定的15个自然日的犹豫期，且犹豫期内可以有无条件全额退保的权利？</p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题7：</b>您是否已经知悉了宣传材料上的利益演示是基于公司精算假设，保单的红利分配是不确定的，红利可能有，也可能为零？</p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题8：</b>您是否清楚犹豫期后退保可能会产生损失，您退保收到的金额可能少于已交保费？
          </p>
          <p>
              回答: 是的。
          </p>
          <p><b>问题9：</b>您保单的销售人员是否是<input type="text" readonly style="border-bottom: 1px solid black;width:30%;text-align:center;" v-model="dividendTypeBook.agentName">，
              工号是<input type="text" readonly style="border-bottom: 1px solid black;width:40%;text-align:center;" v-model="dividendTypeBook.agentCode">？</p>
          <p>
              回答: 是的。
          </p>
          <div class="inp">
              <p class="inp_p">&nbsp;&nbsp;&nbsp;&nbsp;投&nbsp;&nbsp;&nbsp;保&nbsp;&nbsp;&nbsp;人&nbsp;&nbsp;:
                  <img :src="sign" alt="" style="border-bottom:1px solid #000;width:30px;height:30px;">
              </p>
              <p class="inp_p" v-model="dividendTypeBook.appSignDate">&nbsp;&nbsp;&nbsp;日&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;期&nbsp;&nbsp;&nbsp;:
              </p>
              <p class="inp_p">&nbsp;&nbsp;&nbsp;&nbsp;银行销售人员:
                  <img :src="signImgsAgent" alt="" style="border-bottom:1px solid #000;width:30px;height:30px;">
              </p>
              <p class="inp_p"  v-model="dividendTypeBook.bankAgentSignDate">&nbsp;&nbsp;&nbsp;日&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;期&nbsp;&nbsp;&nbsp;:
              </p>
          </div>
        </div>
        <div style="margin:5% 0 0 0;line-height: 20px;">
            <input type="checkbox" v-model="isAgree">&nbsp;&nbsp;本人{{dividendTypeBook.appntName}}已认真阅读投保特别提示，且全面知晓理解相关内容，并予以确认。
        </div>
    </div>
    <alert ref="alert"></alert>
    <Footerbtns :is_show=false 
        total_premium="10000.00">
        <button class="btnFoote" slot="center" @click="jumpToBack()" :disabled="!isAgree">
            下一步
        </button>
    </Footerbtns>
</div>
</template>
<script>
  import Headerbtns from '../../common/Header.vue'
  import Footerbtns from '../../policy/common/Footer.vue'
  import alert from '../common/alert.vue'
  import premList from '../../../../static/dict/prem_sunlife.json'


  export default{
    name: 'audioAndVideoDividendTypeProductBook',
    components:{Headerbtns,Footerbtns,alert},
		props: {
		},
		data() {
			return {
                page_title: '录音录像客户问答内容确认书',
                queType:"(分红型产品)",//问卷类型
                current_total_premium: '10000.00',
                isAgree:false,
                isShare:this.$route.params.share,
                saveName:"2011401_01",
                channel:this.$route.params.channel,
                sign:JSON.parse(this.$route.params.signImgs),
                signImgsAgent:JSON.parse(this.$route.params.signImgsAgent),
                dividendTypeBook:{
                    appntName:this.$route.params.applicant,//投保人姓名
                    appntIDNo:"",//身份证号
                    prtNo:"" ,//投保单号
                    prem:"",//每期保费
                    agentCode:"",//销售人员编码
                    comName:"光大永明人寿", //保险公司
                    riskName:"",//产品名称
                    insuYears:"",//保险年期
                    insuYear:"",//保险年期
                    payYears:"",//缴费年期
                    agentName:"",//销售人员姓名
                    agentCode:"",//销售工号
                    appSignDate:"",//投保人签字日期
                    bankAgentSignDate:"",//销售人员签字日期
                    wn:{
                        guaranteeRate:"",//保证利率
                        initialFee:"",//初始扣费
                        mngFee:"",//保单管理费
                        feeYear:"",//部分领取扣费年限
                        fee1:"",//部分领取扣费1
                        fee2:"",//部分领取扣费2
                        fee3:"",//部分领取扣费3
                        fee4:"",//部分领取扣费4
                        wannengRiskName:"",//万能产品名称
                        freeARTimes:"",//免费部分领取次数
                        aRFee:"",//部分领取手续费
                        shouxuarfee:"",//部分领取手续费
                    },
                    tl:{
                      initialFee:"",//初始扣费
                      mngFee:"",//资产管理费
                      otherFee:"",//补充扣费内容
                      toulianRiskName:"",//投连产品名称
                    },
                }   
			}
		},
        watch:{
            'isAgree': {
                handler(val) {
                    if(val){
                        $(".btnFoote").attr({'disabled':false})
                        $(".btnFoote").css({'opacity':1})
                    }else{
                        $(".btnFoote").css({'opacity':0.5})
                        $(".btnFoote").attr({'disabled':true})
                    }
                },
                deep: true
            },
        },
        beforeMount(){
            $(".btnFoote").css({'opacity':0.5})
            // 判断再次进入单证缓冲有数据且赋值,
            let documentInfo = utils.cache.get("documentInfo")
            if(documentInfo!=null && documentInfo!=undefined && documentInfo.length>0){
                for(var i=0;i<documentInfo.length;i++){
                    if(documentInfo[i].name == this.saveName){
                        this.dividendTypeBook = documentInfo[i].content
                    }
                }
            }else{
                
            }
        },
        mounted(){
            $(".btnFoote").css({'opacity':0.5})
            let policyResult=this.$route.params.policyResult
            console.log("获取投保书信息",policyResult)
            //投保人身份证号
            this.dividendTypeBook.appntIDNo=policyResult.custInfo.appnt.idNo
            //投保单号
            this.dividendTypeBook.prtNo=policyResult.applyCode
            let products=policyResult.productInfo.products.product
            console.log("产品",products)
            for(var i=0; i<products.length;i++){
                //产品名称
                this.dividendTypeBook.riskName += products[i].prodName
                if(products[i].isMaster=="1"){
                    if(products[i].payIntv ="single"){
                        //保险年期 
                        this.dividendTypeBook.insuYears=this.getPrem(products[i].insureYear)
                        this.dividendTypeBook.payYears=""
                        this.dividendTypeBook.prem=""
                        this.dividendTypeBook.insuYear=""
                    }else{
                        this.dividendTypeBook.insuYears=""
                        //缴费年期
                        this.dividendTypeBook.payYears=this.getPay(products[i].payYear)
                        this.dividendTypeBook.prem=products[i].prem
                        this.dividendTypeBook.insuYear=this.getPrem(products[i].insureYear)
                    }
                }
            }
            //销售人员姓名
            this.dividendTypeBook.agentName=policyResult.agentInfo.name
            //销售人员工号
            this.dividendTypeBook.agentCode=policyResult.agentInfo.agentcode
        },
		methods: {
            jumpToBack(){
                if(!this.isShare){
                    if(this.channel == "13" || this.channel == "02"){
                        this.$router.push({
                            path: '/policy/ElectronicsYinBaoPolicyPage.vue',
                            name: 'ElectronicsYinBaoPolicyPage',
                            params: {
                                planId:this.$route.params.planId,
                                applyCode:this.$route.params.applyCode,
                                sendInfo:{
                                    name:"2011401_01",
                                    isRed:"0", 
                                    content:this.dividendTypeBook,
                                }
                            }
                        })
                    }else{
                        this.$router.push({
                            path: '/policy/ElectronicsPolicyPage.vue',
                            name: 'electronics_policy_page',
                            params: {
                                planId:this.$route.params.planId,
                                applyCode:this.$route.params.applyCode,
                                sendInfo:{
                                   name:"2011401_01",
                                   isRed:"0",  
                                   content:this.dividendTypeBook,
                                }
                                
                            }
                        })
                    }
                }else{
                    if(this.channel == "13" || this.channel == "02"){
                        this.$router.push({
                            path: '/policy/ElectronicsYinBaoPolicySharePage.vue',
                            name: 'electronics_yinbao_policy_share_page',
                            params: {
                                planId:this.$route.params.planId,
                                applyCode:this.$route.params.applyCode,
                                index:this.$route.params.index,
                                result:"-1",
                                resultmsg:this.$route.params.resultmsg,
                                sendInfo:{
                                    name:"2011401_01",
                                    isRed:"0", 
                                    content:this.dividendTypeBook,
                                }
                            }
                        })
                    }else{
                        this.$router.push({
                            path: '/policy/ElectronicsPolicySharePage.vue',
                            name: 'electronics_policy_share_page',
                            params: {
                                planId:this.$route.params.planId,
                                applyCode:this.$route.params.applyCode,
                                index:this.$route.params.index,
                                result:"-1",
                                resultmsg:this.$route.params.resultmsg,
                                sendInfo:{
                                   name:"2011401_01",
                                   isRed:"0",  
                                   content:this.dividendTypeBook,
                                }
                                
                            }
                        })
                    }
                }
               
            },
            //按钮返回
            back(){
                if(!this.isShare){
                    if(this.channel == "13" || this.channel == "02"){
                        this.$router.push({
                            path: '/policy/ElectronicsYinBaoPolicyPage.vue',
                            name: 'ElectronicsYinBaoPolicyPage',
                            params: {
                                planId:this.$route.params.planId,
                                applyCode:this.$route.params.applyCode,
                                sendInfo:{
                                    name:"2011401_01",
                                    isRed:"1", 
                                    content:this.dividendTypeBook,
                                }
                            }
                        })
                    }else{
                         this.$router.push({
                             path: '/policy/ElectronicsPolicyPage.vue',
                             name: 'electronics_policy_page',
                             params: {
                                 planId:this.$route.params.planId,
                                 applyCode:this.$route.params.applyCode,
                                 sendInfo:{
                                    name:"2011401_01",
                                    isRed:"1",  
                                    content:this.dividendTypeBook,
                                 }
                                 
                             }
                         })
                    }
                }else{
                    if(this.channel == "13" || this.channel == "02"){
                        this.$router.push({
                            path: '/policy/ElectronicsYinBaoPolicySharePage.vue',
                            name: 'electronics_yinbao_policy_share_page',
                            params: {
                                planId:this.$route.params.planId,
                                applyCode:this.$route.params.applyCode,
                                index:this.$route.params.index,
                                result:"-1",
                                resultmsg:this.$route.params.resultmsg,
                                sendInfo:{
                                    name:"2011401_01",
                                    isRed:"1", 
                                    content:this.dividendTypeBook,
                                }
                            }
                        })
                    }else{
                        this.$router.push({
                            path: '/policy/ElectronicsPolicySharePage.vue',
                            name: 'electronics_policy_share_page',
                            params: {
                                planId:this.$route.params.planId,
                                applyCode:this.$route.params.applyCode,
                                index:this.$route.params.index,
                                result:"-1",
                                resultmsg:this.$route.params.resultmsg,
                                sendInfo:{
                                    name:"2011401_01",
                                    isRed:"1",  
                                    content:this.dividendTypeBook,
                                }    
                            }
                        })
                    }
                }
            },
            //获取保险期
           getPrem(code){
              if(code != undefined && code != ""){
                if (premList != undefined && premList !="") {
                 for (var i = 0; i < premList.declare.parameter.insure.item.length; i++) {
                      if(premList.declare.parameter.insure.item[i].code == code){
                        return premList.declare.parameter.insure.item[i].show
                      }
                  }
                }
              }
            },
            //获取交费期
            getPay(code){
               if(code != undefined && code != ""){
                 if (premList != undefined && premList !="") {
                  for (var i = 0; i < premList.declare.parameter.pay.item.length; i++) {
                       if(premList.declare.parameter.pay.item[i].code == code){
                         return premList.declare.parameter.pay.item[i].show
                       }
                   }
                 }
               }
             },
        },
       //提示框
       showMsg:function(msg){
           if(msg!=undefined && msg!=""){
                this.$refs.alert.showMOdal(msg)
           }
       },
  }
</script>
<style lang="scss" scoped type="text/css">
.back{
    display: block;
    height: 100%;width: 100%;
    position: relative;
    img{
        position: absolute;
        top: 50%;left: 50%;
        margin-top: -10px;
        margin-left: -20px;
    }
}
.fa{
    color: #03345C;
}
.fa-angle-left{
    display: inline-block;
    width: 100%;height: 100%;
    line-height: 48px;
    text-align: center;
    font-size: 30px;
}
.manage-contents{
    position: absolute;
    padding: 0 5%;
    left: 0;right: 0;top: 48px;bottom: 50px;
    overflow-y: auto;
    overflow-x: hidden;
    background: #FFF;
    margin-top: 7%; 
}
.clear{
    content:"";
    clear:both;
    display:block
}   
h1{
    text-align: center;
    font-weight:bold;
    margin:10px 0 ;
}
.btnFoote{
    border:0;
    color:#fff;
    width:100%;
    height: 50px;
    background:#FEB101;
    height:50px
}
.content>p{
    text-indent:2em;
    line-height: 25px;
}
.inp_p{
    /*text-align: center;*/
    margin:10px auto;
}
</style>
