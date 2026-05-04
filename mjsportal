import { useState } from “react”;

/* ── PALETTE ── */
const MJS_NAVY = “#1E2D6B”;
const MJS_DARK = “#141D45”;
const FIZZ_PURPLE = “#6B21A8”;
const FIZZ_GREEN = “#A3E635”;
const GOLD = “#F5C518”;
const BG = “#0f0f0f”;
const CARD = “#1a1a1a”;
const CARD2 = “#222222”;

/* ── GLOBAL STYLES ── */
const G = `
@import url(‘https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@700;900&family=DM+Sans:wght@300;400;500;600&display=swap’);
*{box-sizing:border-box;margin:0;padding:0;}
body,#root{min-height:100vh;font-family:‘DM Sans’,sans-serif;background:${BG};}
.app{min-height:100vh;background:${BG};color:#fff;}

/* NAV */
.nav{background:#000;border-bottom:2px solid ${MJS_NAVY};padding:12px 18px;display:flex;align-items:center;gap:12px;position:sticky;top:0;z-index:100;}
.mjs-logo{display:flex;flex-direction:column;align-items:flex-start;}
.mjs-letters{font-family:‘Barlow Condensed’,sans-serif;font-size:28px;font-weight:900;color:#fff;letter-spacing:2px;line-height:1;}
.mjs-bar{background:${MJS_NAVY};color:#fff;font-size:8px;letter-spacing:4px;padding:2px 8px;margin-top:1px;font-weight:600;}
.nav-tag{margin-left:auto;font-size:9px;color:#555;text-align:right;line-height:1.6;letter-spacing:1px;}

/* HERO */
.hero{background:#000;padding:28px 18px 22px;border-bottom:1px solid #222;}
.hero-label{font-size:10px;color:${GOLD};letter-spacing:3px;text-transform:uppercase;margin-bottom:8px;}
.hero-title{font-family:‘Barlow Condensed’,sans-serif;font-size:38px;font-weight:900;line-height:0.95;text-transform:uppercase;margin-bottom:10px;}
.hero-title span{color:${GOLD};}
.hero-sub{font-size:12px;color:#888;line-height:1.6;max-width:320px;}

/* PORTAL CARDS */
.portal-section{padding:20px 18px;}
.section-label{font-size:10px;color:#555;letter-spacing:3px;text-transform:uppercase;margin-bottom:16px;}
.portal-cards{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:24px;}
.pcard{border-radius:10px;padding:20px 14px;cursor:pointer;border:1px solid #333;transition:all .25s;position:relative;overflow:hidden;}
.pcard:hover{transform:translateY(-2px);}
.pcard.employer{background:linear-gradient(145deg,#0d1a0d,#111);}
.pcard.employer:hover{border-color:#16a34a;box-shadow:0 6px 20px rgba(22,163,74,.2);}
.pcard.employee{background:linear-gradient(145deg,#0a0d1f,#111);}
.pcard.employee:hover{border-color:${MJS_NAVY};box-shadow:0 6px 20px rgba(30,45,107,.3);}
.pcard-icon{font-size:26px;margin-bottom:8px;}
.pcard-num{font-size:9px;color:#444;letter-spacing:2px;margin-bottom:4px;}
.pcard h3{font-family:‘Barlow Condensed’,sans-serif;font-size:18px;font-weight:700;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px;}
.pcard.employer h3{color:#4ade80;}
.pcard.employee h3{color:${GOLD};}
.pcard p{font-size:10px;color:#666;line-height:1.5;}

/* CONTACT BAR */
.contact-bar{background:#111;border:1px solid #222;border-radius:10px;padding:14px 16px;margin:0 18px 20px;}
.contact-bar-row{display:flex;align-items:center;gap:8px;font-size:11px;color:#888;margin-bottom:4px;}
.contact-bar-row:last-child{margin-bottom:0;}
.contact-bar-row span{color:#ddd;}
.contact-dot{width:6px;height:6px;background:${GOLD};border-radius:50%;flex-shrink:0;}

/* PAGE */
.page{padding:18px;animation:fu .35s ease;}
@keyframes fu{from{opacity:0;transform:translateY(14px);}to{opacity:1;transform:translateY(0);}}
.back{display:flex;align-items:center;gap:6px;color:${GOLD};font-size:11px;cursor:pointer;margin-bottom:16px;background:none;border:none;padding:0;letter-spacing:1px;}
.prog-wrap{margin-bottom:16px;}
.prog-bar{background:#1f1f1f;border-radius:99px;height:3px;overflow:hidden;margin-bottom:5px;}
.prog-fill{height:100%;background:linear-gradient(90deg,${MJS_NAVY},${GOLD});border-radius:99px;transition:width .4s ease;}
.prog-label{font-size:9px;color:#444;letter-spacing:2px;text-transform:uppercase;}
.page-title{font-family:‘Barlow Condensed’,sans-serif;font-size:26px;font-weight:900;text-transform:uppercase;letter-spacing:1px;color:#fff;margin-bottom:3px;}
.page-title span{color:${GOLD};}
.page-sub{font-size:11px;color:#666;margin-bottom:18px;line-height:1.5;}
.divider{height:1px;background:linear-gradient(90deg,transparent,#2a2a2a,transparent);margin:16px 0;}
.sec-title{font-size:9px;color:#555;letter-spacing:3px;text-transform:uppercase;margin-bottom:10px;padding-bottom:6px;border-bottom:1px solid #1f1f1f;}

/* FORM */
.fg{margin-bottom:14px;}
.fl{display:block;font-size:10px;color:#666;letter-spacing:.5px;text-transform:uppercase;margin-bottom:5px;}
.fi,.fs,.ft{width:100%;background:#1a1a1a;border:1px solid #2a2a2a;border-radius:8px;padding:11px 13px;color:#fff;font-family:‘DM Sans’,sans-serif;font-size:13px;outline:none;transition:border-color .2s;-webkit-appearance:none;}
.fi:focus,.fs:focus,.ft:focus{border-color:${MJS_NAVY};}
.fs option{background:#111;color:#fff;}
.ft{resize:vertical;min-height:70px;}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:10px;}

/* PLANS */
.plan-cards{display:flex;flex-direction:column;gap:10px;margin-bottom:14px;}
.plan-card{border-radius:10px;padding:16px;border:2px solid #2a2a2a;cursor:pointer;transition:all .2s;position:relative;}
.plan-card.selected.fizz{border-color:${FIZZ_PURPLE};background:rgba(107,33,168,.1);}
.plan-card.selected.std{border-color:${GOLD};background:rgba(245,197,24,.07);}
.plan-card:hover{border-color:#444;}
.plan-badge{position:absolute;top:10px;right:10px;font-size:9px;font-weight:700;padding:2px 8px;border-radius:20px;letter-spacing:1px;}
.plan-badge.popular{background:${GOLD};color:#000;}
.plan-price{font-family:‘Barlow Condensed’,sans-serif;font-size:28px;font-weight:900;color:#fff;margin-bottom:2px;}
.plan-price span{font-size:13px;color:#666;font-family:‘DM Sans’,sans-serif;font-weight:400;}
.plan-name{font-size:11px;color:${GOLD};letter-spacing:2px;text-transform:uppercase;margin-bottom:8px;}
.plan-features{display:flex;flex-direction:column;gap:4px;}
.plan-feat{font-size:11px;color:#aaa;display:flex;align-items:center;gap:6px;}
.plan-feat::before{content:’’;width:4px;height:4px;background:${GOLD};border-radius:50%;flex-shrink:0;}

/* UPLOAD */
.upload-box{border:2px dashed #2a2a2a;border-radius:10px;padding:18px;text-align:center;cursor:pointer;transition:all .2s;background:rgba(255,255,255,.02);}
.upload-box:hover,.upload-box.done{border-color:${MJS_NAVY};}
.upload-box input{display:none;}
.upload-box .ui{font-size:24px;margin-bottom:4px;}
.upload-box h4{font-size:11px;color:${GOLD};margin-bottom:2px;}
.upload-box p{font-size:10px;color:#555;}

/* SKILLS */
.skill-tags{display:flex;flex-wrap:wrap;gap:6px;margin-top:6px;}
.stag{padding:5px 11px;border-radius:20px;font-size:11px;cursor:pointer;border:1px solid #2a2a2a;background:transparent;color:#666;transition:all .2s;}
.stag.on{background:${MJS_NAVY};color:#fff;border-color:${MJS_NAVY};}

/* MARGA */
.marga-banner{background:linear-gradient(135deg,#1a0000,#2d0000);border:1px solid #7f1d1d;border-radius:10px;padding:14px;margin-bottom:16px;}
.marga-banner h3{font-family:‘Barlow Condensed’,sans-serif;font-size:16px;letter-spacing:1px;color:#fca5a5;margin-bottom:4px;text-transform:uppercase;}
.marga-banner p{font-size:11px;color:#fecaca;line-height:1.5;}
.video-card{background:#111;border:1px solid #2a2a2a;border-radius:10px;overflow:hidden;margin-bottom:14px;}
.video-thumb{background:linear-gradient(135deg,#1a0000,#2a0a0a);height:160px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:8px;cursor:pointer;transition:background .2s;}
.video-thumb:hover{background:linear-gradient(135deg,#2d0000,#3d1010);}
.play-btn{width:50px;height:50px;background:${GOLD};border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:18px;}
.video-thumb h4{font-family:‘Barlow Condensed’,sans-serif;font-size:14px;color:#fca5a5;letter-spacing:1px;text-transform:uppercase;}
.video-thumb p{font-size:10px;color:#666;}
.video-body{padding:12px;}
.vpoint{display:flex;gap:8px;align-items:flex-start;font-size:11px;color:#aaa;padding:8px 10px;background:rgba(255,255,255,.02);border-radius:6px;margin-bottom:6px;border-left:3px solid;}
.vpoint.red{border-color:#ef4444;}
.vpoint.gold{border-color:${GOLD};}
.vpoint.green{border-color:#4ade80;}
.vpoint.blue{border-color:#60a5fa;}

/* AGREEMENT */
.agr-box{background:#0a0a0a;border:1px solid #2a2a2a;border-radius:10px;padding:14px;max-height:340px;overflow-y:auto;margin-bottom:12px;}
.agr-box h4{font-family:‘Barlow Condensed’,sans-serif;font-size:14px;color:${GOLD};letter-spacing:2px;text-transform:uppercase;margin-bottom:10px;}
.agr-clause{margin-bottom:12px;}
.agr-clause h5{font-size:11px;color:#aaa;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px;}
.agr-clause p{font-size:11px;color:#666;line-height:1.6;}
.agr-sign{background:#111;border:1px solid #2a2a2a;border-radius:10px;padding:12px;margin-bottom:12px;}
.agr-sign label{display:block;font-size:10px;color:#555;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px;}

/* CHECKBOX */
.cb-row{display:flex;align-items:flex-start;gap:8px;padding:10px;background:rgba(245,197,24,.04);border:1px solid rgba(245,197,24,.15);border-radius:8px;cursor:pointer;margin-bottom:10px;}
.cb-row input{margin-top:2px;accent-color:${GOLD};}
.cb-row span{font-size:11px;color:#aaa;line-height:1.5;}

/* FIZZ LOGO */
.fizz-badge{display:inline-flex;align-items:center;gap:6px;background:${FIZZ_PURPLE};border-radius:8px;padding:4px 10px;margin-bottom:10px;}
.fizz-badge span{font-family:‘Barlow Condensed’,sans-serif;font-size:16px;font-weight:900;color:#fff;letter-spacing:1px;}
.fizz-dot{width:8px;height:8px;background:${FIZZ_GREEN};border-radius:50%;}

/* CAREER CARDS */
.career-cards{display:flex;flex-direction:column;gap:10px;margin-bottom:16px;}
.career-card{background:${CARD};border:1px solid #2a2a2a;border-radius:10px;padding:14px;display:flex;align-items:center;justify-content:space-between;gap:10px;}
.cc-left h4{font-family:‘Barlow Condensed’,sans-serif;font-size:16px;font-weight:700;text-transform:uppercase;letter-spacing:.5px;color:#fff;margin-bottom:2px;}
.cc-left p{font-size:10px;color:#666;}
.cc-badge{font-size:9px;padding:3px 8px;border-radius:20px;letter-spacing:1px;font-weight:700;white-space:nowrap;}
.cc-badge.open{background:rgba(74,222,128,.1);color:#4ade80;border:1px solid #4ade80;}
.cc-badge.fizz{background:${FIZZ_PURPLE};color:#fff;}

/* BTNS */
.btn{width:100%;padding:14px;border:none;border-radius:10px;font-family:‘DM Sans’,sans-serif;font-size:14px;font-weight:700;cursor:pointer;letter-spacing:.5px;transition:all .2s;margin-top:6px;}
.btn-primary{background:${GOLD};color:#000;}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 5px 18px rgba(245,197,24,.3);}
.btn-primary:disabled{opacity:.35;cursor:not-allowed;transform:none;}
.btn-secondary{background:transparent;color:${GOLD};border:1px solid ${GOLD};}
.btn-secondary:hover{background:rgba(245,197,24,.08);}
.btn-navy{background:${MJS_NAVY};color:#fff;}
.btn-navy:hover{background:${MJS_DARK};}
.btn-fizz{background:${FIZZ_PURPLE};color:#fff;}

/* ALERT */
.alert{border-radius:8px;padding:10px 12px;font-size:11px;line-height:1.5;margin-bottom:12px;}
.alert.red{background:rgba(239,68,68,.08);border:1px solid rgba(239,68,68,.25);color:#fca5a5;}
.alert.gold{background:rgba(245,197,24,.06);border:1px solid rgba(245,197,24,.2);color:#fde68a;}

/* SUCCESS */
.success{padding:30px 18px;min-height:calc(100vh - 64px);display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;animation:fu .4s ease;}
.success-icon{width:70px;height:70px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:32px;margin:0 auto 18px;box-shadow:0 0 30px rgba(74,222,128,.2);background:linear-gradient(135deg,#064e3b,#065f46);}
.success h2{font-family:‘Barlow Condensed’,sans-serif;font-size:28px;font-weight:900;text-transform:uppercase;letter-spacing:1px;color:#fff;margin-bottom:6px;}
.success h2 span{color:${GOLD};}
.success p{font-size:12px;color:#666;line-height:1.6;margin-bottom:4px;}
.ref-box{background:#111;border:1px solid #2a2a2a;border-radius:10px;padding:14px 20px;margin:18px 0;width:100%;}
.ref-box p{font-size:9px;color:#555;letter-spacing:2px;text-transform:uppercase;margin-bottom:4px;}
.ref-box h3{font-family:‘Barlow Condensed’,sans-serif;font-size:22px;color:${GOLD};letter-spacing:3px;}
.footer-strip{background:#000;border-top:1px solid #1a1a1a;padding:10px 18px;display:flex;align-items:center;justify-content:space-between;}
.footer-strip span{font-size:9px;color:#333;letter-spacing:1px;}
`;

const SKILLS = [“Plumber”,“Electrician”,“AC Mechanic”,“Carpenter”,“Painter”,“Welder”,“Mason”,“Driver”,“Delivery Agent”,“Hotel Staff”,“Housekeeping”,“Cook”,“Security Guard”,“Cleaner”,“Helper”,“Waiter”,“Pantry Boy”,“Other”];
const STATES = [“Andhra Pradesh”,“Assam”,“Bihar”,“Chhattisgarh”,“Gujarat”,“Jharkhand”,“Karnataka”,“Madhya Pradesh”,“Maharashtra”,“Odisha”,“Punjab”,“Rajasthan”,“Uttar Pradesh”,“Uttarakhand”,“West Bengal”,“Delhi/NCR”,“Other”];
const DISTRICTS_KL = [“Kasargod”,“Kannur”,“Wayanad”,“Kozhikode”,“Malappuram”,“Palakkad”,“Thrissur”,“Ernakulam”,“Idukki”,“Kottayam”,“Alappuzha”,“Pathanamthitta”,“Kollam”,“Thiruvananthapuram”];

function genRef(prefix) {
return prefix + “-” + Math.random().toString(36).substring(2,7).toUpperCase();
}

const CAREERS = [
{ id:1, title:“Delivery Agent”, sub:“Fizz Delivery — Payyannur / Trikaripur”, badge:“fizz”, type:“fizz” },
{ id:2, title:“Plumber”, sub:“MJS OneCall — Skilled Trade”, badge:“open”, type:“onecall” },
{ id:3, title:“Electrician”, sub:“MJS OneCall — Skilled Trade”, badge:“open”, type:“onecall” },
{ id:4, title:“AC Mechanic”, sub:“MJS OneCall — Skilled Trade”, badge:“open”, type:“onecall” },
{ id:5, title:“Housekeeping Staff”, sub:“MJS Group — Hotel & Home Services”, badge:“open”, type:“general” },
{ id:6, title:“Hotel Helper / Waiter”, sub:“MJS Group — Hospitality”, badge:“open”, type:“general” },
{ id:7, title:“House Cleaning Staff”, sub:“MJS OneCall”, badge:“open”, type:“onecall” },
];

export default function App() {
const [screen, setScreen] = useState(“home”);
const [empPath, setEmpPath] = useState(null); // “fizz” | “staff”
const [candidatePath, setCandidatePath] = useState(null); // “kerala” | “guest”
const [step, setStep] = useState(1);
const [selectedPlan, setSelectedPlan] = useState(null);
const [skills, setSkills] = useState([]);
const [uploads, setUploads] = useState({ cv: null, aadhaar: null, pcc: null });
const [videoWatched, setVideoWatched] = useState(false);
const [agreeChecked, setAgreeChecked] = useState(false);
const [signName, setSignName] = useState(””);
const [refNo] = useState({ employer: genRef(“MJS-EMP”), candidate: genRef(“MJS-CND”) });
const [selectedJob, setSelectedJob] = useState(null);

const [eForm, setEForm] = useState({ bizName:””, bizType:””, contactName:””, phone:””, email:””, location:””, district:””, deliveryArea:””, notes:””, staffType:””, qty:””, salary:”” });
const [cForm, setCForm] = useState({ fullName:””, dob:””, gender:””, phone:””, email:””, state:””, district:””, address:””, experience:””, currentRole:””, salary:””, emgName:””, emgPhone:”” });

const ue = (k,v) => setEForm(f=>({…f,[k]:v}));
const uc = (k,v) => setCForm(f=>({…f,[k]:v}));
const toggleSkill = s => setSkills(p => p.includes(s)?p.filter(x=>x!==s):[…p,s]);
const handleUpload = (k,e) => { if(e.target.files[0]) setUploads(u=>({…u,[k]:e.target.files[0].name})); };

const goHome = () => { setScreen(“home”); setStep(1); setEmpPath(null); setCandidatePath(null); setSkills([]); setUploads({cv:null,aadhaar:null,pcc:null}); setVideoWatched(false); setAgreeChecked(false); setSignName(””); setSelectedPlan(null); setSelectedJob(null); };

/* ── NAV ── */
const Nav = () => (
<div className="nav">
<div className=“mjs-logo” onClick={goHome} style={{cursor:“pointer”}}>
<div className="mjs-letters">MJS</div>
<div className="mjs-bar">GROUP</div>
</div>
<div className="nav-tag">mjgroups.co.in<br/>+91 730 654 5404</div>
</div>
);

/* ── HOME ── */
if (screen === “home”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="hero">
<div className="hero-label">— MJS Career & Partner Zone</div>
<div className="hero-title">Built for<br/><span>Payyannur.</span></div>
<div className="hero-sub">Register as an employer, become a vendor partner, or find your next career opportunity across MJS Group ventures.</div>
</div>
<div className="portal-section">
<div className="section-label">— Select your path</div>
<div className="portal-cards">
<div className=“pcard employer” onClick={()=>setScreen(“employer-choose”)}>
<div className="pcard-icon">🏢</div>
<div className="pcard-num">01</div>
<h3>Employer / Vendor</h3>
<p>Partner with us, get delivery service or request staff</p>
</div>
<div className=“pcard employee” onClick={()=>setScreen(“candidate-choose”)}>
<div className="pcard-icon">👷</div>
<div className="pcard-num">02</div>
<h3>Job Seeker</h3>
<p>Find your next opportunity across MJS ventures</p>
</div>
</div>

```
      <div className="section-label">— Our ventures</div>
      {[
        {num:"#01", name:"MJS ONECALL", tag:"HOME SERVICES", col:"#F5C518"},
        {num:"#02", name:"FIZZ DELIVERY", tag:"HYPERLOCAL DELIVERY", col:"#9333ea"},
        {num:"#03", name:"PROPILOT DRIVERS", tag:"DRIVER SERVICE", col:"#22c55e"},
        {num:"#04", name:"MJS E-SERVICE", tag:"ELECTRONICS", col:"#f97316"},
      ].map(v=>(
        <div key={v.num} style={{display:"flex",alignItems:"center",gap:12,padding:"10px 0",borderBottom:"1px solid #1a1a1a"}}>
          <div style={{fontSize:9,color:"#333",width:24}}>{v.num}</div>
          <div style={{flex:1}}>
            <div style={{fontFamily:"'Barlow Condensed',sans-serif",fontSize:14,fontWeight:700,color:"#fff",letterSpacing:1}}>{v.name}</div>
            <div style={{fontSize:9,color:"#555",letterSpacing:2}}>{v.tag}</div>
          </div>
          <div style={{width:6,height:6,borderRadius:"50%",background:v.col}}/>
        </div>
      ))}
    </div>
    <div className="contact-bar">
      <div className="contact-bar-row"><span className="contact-dot"/><span>+91 730 654 5404 / +91 994 784 5404</span></div>
      <div className="contact-bar-row"><span className="contact-dot"/><span>Vellap, Trikaripur · Payyannur, Kerala 671310</span></div>
      <div className="contact-bar-row"><span className="contact-dot"/><span>Mon – Sat · 8:00 AM – 8:00 PM</span></div>
    </div>
    <div className="footer-strip">
      <span>MJS GROUP © 2025</span>
      <span>PAYYANNUR · TRIKARIPUR · KANNUR</span>
    </div>
  </div>
</>
```

);

/* ── EMPLOYER CHOOSE ── */
if (screen === “employer-choose”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="page">
<button className="back" onClick={goHome}>← BACK</button>
<div className="page-title">EMPLOYER <span>ZONE</span></div>
<div className="page-sub">Choose a service to register or enquire</div>
<div className="divider"/>
<div style={{display:“flex”,flexDirection:“column”,gap:12,marginBottom:20}}>
<div style={{background:CARD,border:`1px solid ${FIZZ_PURPLE}`,borderRadius:12,padding:18,cursor:“pointer”}} onClick={()=>{setEmpPath(“fizz”);setScreen(“employer-fizz”);setStep(1);}}>
<div className="fizz-badge"><div className="fizz-dot"/><span>FIZZ</span></div>
<div style={{fontFamily:”‘Barlow Condensed’,sans-serif”,fontSize:20,fontWeight:900,color:”#fff”,textTransform:“uppercase”,letterSpacing:1,marginBottom:4}}>Delivery + Digital Package</div>
<div style={{fontSize:11,color:”#888”,marginBottom:12,lineHeight:1.5}}>Subscribe to our delivery service with social media content creation. Two plans available.</div>
<div style={{display:“flex”,gap:8}}>
<div style={{flex:1,background:“rgba(107,33,168,.15)”,border:`1px solid ${FIZZ_PURPLE}`,borderRadius:8,padding:“8px 10px”}}>
<div style={{fontSize:9,color:”#a78bfa”,letterSpacing:2,marginBottom:2}}>BASIC</div>
<div style={{fontFamily:”‘Barlow Condensed’,sans-serif”,fontSize:18,color:”#fff”}}>₹15,999<span style={{fontSize:10,color:”#666”}}>/mo</span></div>
</div>
<div style={{flex:1,background:“rgba(245,197,24,.07)”,border:`1px solid ${GOLD}`,borderRadius:8,padding:“8px 10px”}}>
<div style={{fontSize:9,color:GOLD,letterSpacing:2,marginBottom:2}}>STANDARD</div>
<div style={{fontFamily:”‘Barlow Condensed’,sans-serif”,fontSize:18,color:”#fff”}}>₹24,999<span style={{fontSize:10,color:”#666”}}>/mo</span></div>
</div>
</div>
</div>
<div style={{background:CARD,border:“1px solid #2a2a2a”,borderRadius:12,padding:18,cursor:“pointer”}} onClick={()=>{setEmpPath(“staff”);setScreen(“employer-staff”);setStep(1);}}>
<div style={{fontSize:20,marginBottom:6}}>🏨</div>
<div style={{fontFamily:”‘Barlow Condensed’,sans-serif”,fontSize:20,fontWeight:900,color:”#fff”,textTransform:“uppercase”,letterSpacing:1,marginBottom:4}}>Staff Supply Enquiry</div>
<div style={{fontSize:11,color:”#888”,lineHeight:1.5}}>Request trained hotel staff, cleaners, housekeeping and more — all verified through MARGA protocol.</div>
<div style={{marginTop:10,display:“inline-block”,background:“rgba(245,197,24,.1)”,border:`1px solid ${GOLD}`,borderRadius:20,padding:“3px 10px”,fontSize:9,color:GOLD,letterSpacing:2}}>REGISTER INTEREST</div>
</div>
</div>
</div>
</div>
</>
);

/* ── EMPLOYER FIZZ ── */
const fizzSteps = 3;
if (screen === “employer-fizz”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="page">
<button className=“back” onClick={()=>setScreen(“employer-choose”)}>← BACK</button>
<div className="prog-wrap">
<div className="prog-bar"><div className=“prog-fill” style={{width:`${(step/fizzSteps)*100}%`}}/></div>
<div className="prog-label">Step {step} of {fizzSteps}</div>
</div>
<div className="fizz-badge"><div className="fizz-dot"/><span>FIZZ</span></div>
<div className="page-title">VENDOR <span>REGISTRATION</span></div>
<div className="page-sub">Fizz Delivery & Digital Marketing Partnership</div>
<div className="divider"/>

```
      {step===1 && <>
        <div className="sec-title">Business Details</div>
        <div className="fg"><label className="fl">Business / Restaurant Name *</label><input className="fi" placeholder="e.g. Spice Corner Restaurant" value={eForm.bizName} onChange={e=>ue("bizName",e.target.value)}/></div>
        <div className="fg"><label className="fl">Business Type *</label>
          <select className="fs" value={eForm.bizType} onChange={e=>ue("bizType",e.target.value)}>
            <option value="">Select type</option>
            {["Restaurant","Hotel","Bakery","Grocery Store","Pharmacy","Supermarket","Cafe","Cloud Kitchen","Retail Shop","Other"].map(x=><option key={x}>{x}</option>)}
          </select>
        </div>
        <div className="fg"><label className="fl">Contact Person Name *</label><input className="fi" placeholder="Owner / Manager name" value={eForm.contactName} onChange={e=>ue("contactName",e.target.value)}/></div>
        <div className="row2">
          <div className="fg"><label className="fl">Phone / WhatsApp *</label><input className="fi" type="tel" placeholder="+91" value={eForm.phone} onChange={e=>ue("phone",e.target.value)}/></div>
          <div className="fg"><label className="fl">Email</label><input className="fi" type="email" placeholder="email@domain.com" value={eForm.email} onChange={e=>ue("email",e.target.value)}/></div>
        </div>
        <div className="fg"><label className="fl">Business Location / Address *</label><input className="fi" placeholder="Shop address" value={eForm.location} onChange={e=>ue("location",e.target.value)}/></div>
        <div className="fg"><label className="fl">Area / Delivery Zone *</label>
          <select className="fs" value={eForm.deliveryArea} onChange={e=>ue("deliveryArea",e.target.value)}>
            <option value="">Select area</option>
            {["Vellap","Trikaripur","Payyannur","Padannakkad","Valiyaparamba","Other"].map(x=><option key={x}>{x}</option>)}
          </select>
        </div>
        <button className="btn btn-primary" disabled={!eForm.bizName||!eForm.bizType||!eForm.contactName||!eForm.phone||!eForm.deliveryArea} onClick={()=>setStep(2)}>Continue →</button>
      </>}

      {step===2 && <>
        <div className="sec-title">Choose Your Plan</div>
        <div className="plan-cards">
          <div className={`plan-card fizz ${selectedPlan==="basic"?"selected":""}`} onClick={()=>setSelectedPlan("basic")} style={{border:`2px solid ${selectedPlan==="basic"?FIZZ_PURPLE:"#2a2a2a"}`}}>
            <div className="plan-name">Basic Plan</div>
            <div className="plan-price">₹15,999 <span>/month</span></div>
            <div className="divider" style={{margin:"8px 0"}}/>
            <div className="plan-features">
              <div className="plan-feat">20 deliveries per day</div>
              <div className="plan-feat">5–6 social media posts per month</div>
              <div className="plan-feat">Service area: Payyannur / Trikaripur</div>
              <div className="plan-feat">Operations: 3:00 PM – 10:30 PM daily</div>
              <div className="plan-feat">Replacement delivery support</div>
            </div>
          </div>
          <div className={`plan-card std ${selectedPlan==="standard"?"selected":""}`} onClick={()=>setSelectedPlan("standard")} style={{border:`2px solid ${selectedPlan==="standard"?GOLD:"#2a2a2a"}`}}>
            <div className="plan-badge popular">POPULAR</div>
            <div className="plan-name" style={{color:GOLD}}>Standard Plan</div>
            <div className="plan-price">₹24,999 <span>/month</span></div>
            <div className="divider" style={{margin:"8px 0"}}/>
            <div className="plan-features">
              <div className="plan-feat">50 deliveries per day</div>
              <div className="plan-feat">8–10 social media posts per month</div>
              <div className="plan-feat">Service area: Payyannur / Trikaripur</div>
              <div className="plan-feat">Operations: 3:00 PM – 10:30 PM daily</div>
              <div className="plan-feat">Priority support & replacement</div>
            </div>
          </div>
        </div>
        <div className="alert gold">💡 Extra deliveries beyond your plan limit are charged additionally per delivery. Unused deliveries do not roll over.</div>
        <div className="fg"><label className="fl">Additional Notes</label><textarea className="ft" placeholder="Any special requirements or questions..." value={eForm.notes} onChange={e=>ue("notes",e.target.value)}/></div>
        <button className="btn btn-primary" disabled={!selectedPlan} onClick={()=>setStep(3)}>Review Agreement →</button>
        <button className="btn btn-secondary" onClick={()=>setStep(1)}>← Back</button>
      </>}

      {step===3 && <>
        <div className="sec-title">Service Agreement</div>
        <div className="alert red">📋 Please read the full agreement before signing. This is a legally binding document.</div>
        <div className="agr-box">
          <h4>Fizz Delivery — Service Agreement</h4>
          <div className="agr-clause">
            <h5>1. Package & Service</h5>
            <p>The Vendor has selected the <strong style={{color:GOLD}}>{selectedPlan==="basic"?"Basic Plan (₹15,999/month)":"Standard Plan (₹24,999/month)"}</strong>. This includes {selectedPlan==="basic"?"20 deliveries/day + 5–6 social media posts":"50 deliveries/day + 8–10 social media posts"} per month. Service is provided by Fizz Enterprise, a venture under MJS Group.</p>
          </div>
          <div className="agr-clause">
            <h5>2. Delivery Terms</h5>
            <p>Operating hours: 3:00 PM – 10:30 PM daily. Orders placed after 10:00 PM are not guaranteed for same-day delivery. Maximum deliveries are as per plan. Unused deliveries do not roll over. Extra deliveries beyond plan are billed at additional per-delivery rate fixed by Fizz. Service area: Vellap, Trikaripur, Payyannur, Padannakkad, Valiyaparamba only.</p>
          </div>
          <div className="agr-clause">
            <h5>3. Digital Marketing</h5>
            <p>Content materials (logo, product images, descriptions) must be provided at least 3 days before posting. Delays in providing materials are the Vendor's responsibility. Maximum 2 revisions per design are permitted.</p>
          </div>
          <div className="agr-clause">
            <h5>4. Payment Terms</h5>
            <p>Monthly fee is payable in advance on the 1st of each month. A delay of more than 3 days gives Fizz Enterprise the right to suspend services without prior notice. All fees paid are non-refundable.</p>
          </div>
          <div className="agr-clause">
            <h5>5. Packaging Responsibility</h5>
            <p>Vendor is fully responsible for safe and proper packaging of all products. Fizz Enterprise bears no liability for damage caused by inadequate packaging.</p>
          </div>
          <div className="agr-clause">
            <h5>6. Liability & Force Majeure</h5>
            <p>Fizz Enterprise is not liable for delivery delays caused by traffic, accidents, rain, hartals, or natural disasters. Customer complaints regarding food quality, quantity, or taste are entirely the Vendor's responsibility.</p>
          </div>
          <div className="agr-clause">
            <h5>7. Termination</h5>
            <p>Fizz Enterprise may terminate this agreement immediately if any terms are violated. Vendor must provide 30 days written notice to terminate. Advance payments are non-refundable upon termination.</p>
          </div>
          <div className="agr-clause">
            <h5>8. Jurisdiction</h5>
            <p>All legal disputes arising from this agreement fall under the jurisdiction of courts in Kasargod District, Kerala.</p>
          </div>
        </div>
        <div className="agr-sign">
          <label className="fl">Your Full Name (Digital Signature) *</label>
          <input className="fi" placeholder="Type your full legal name" value={signName} onChange={e=>setSignName(e.target.value)}/>
        </div>
        <div className="cb-row" onClick={()=>setAgreeChecked(v=>!v)}>
          <input type="checkbox" checked={agreeChecked} onChange={()=>{}}/>
          <span>I have read and understood the complete Fizz Delivery Service Agreement. I agree to all terms, conditions, and legal obligations stated above on behalf of <strong>{eForm.bizName||"my business"}</strong>.</span>
        </div>
        <button className="btn btn-fizz" disabled={!agreeChecked||!signName} onClick={()=>setScreen("success-employer")}>✅ Sign & Submit Registration</button>
        <button className="btn btn-secondary" onClick={()=>setStep(2)}>← Back</button>
      </>}
    </div>
  </div>
</>
```

);

/* ── EMPLOYER STAFF ── */
if (screen === “employer-staff”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="page">
<button className=“back” onClick={()=>setScreen(“employer-choose”)}>← BACK</button>
<div className="page-title">STAFF <span>REQUEST</span></div>
<div className="page-sub">Tell us your requirement — we’ll get back to you with a quote</div>
<div className="divider"/>
<div className="alert gold">🔒 All staff supplied are MARGA-certified — background verified, drug-awareness trained, and Kerala culture oriented.</div>
<div className="fg"><label className="fl">Business / Hotel Name *</label><input className=“fi” placeholder=“Your business name” value={eForm.bizName} onChange={e=>ue(“bizName”,e.target.value)}/></div>
<div className="fg"><label className="fl">Business Type *</label>
<select className=“fs” value={eForm.bizType} onChange={e=>ue(“bizType”,e.target.value)}>
<option value="">Select</option>
{[“Hotel”,“Restaurant”,“Resort”,“Hospital”,“Office”,“Apartment Complex”,“Construction Site”,“Other”].map(x=><option key={x}>{x}</option>)}
</select>
</div>
<div className="fg"><label className="fl">Contact Person & Phone *</label><input className=“fi” placeholder=“Name — +91 XXXXXXXXXX” value={eForm.contactName} onChange={e=>ue(“contactName”,e.target.value)}/></div>
<div className="fg"><label className="fl">Staff Type Required *</label>
<select className=“fs” value={eForm.staffType} onChange={e=>ue(“staffType”,e.target.value)}>
<option value="">Select staff category</option>
{[“Hotel Housekeeping”,“Kitchen / Cook Staff”,“Cleaning Staff”,“Security Guards”,“Plumbers”,“Electricians”,“AC Mechanics”,“Waiters / F&B Staff”,“Drivers”,“Mixed Requirement”].map(x=><option key={x}>{x}</option>)}
</select>
</div>
<div className="row2">
<div className="fg"><label className="fl">No. of Staff Needed</label><input className=“fi” type=“number” placeholder=“e.g. 5” value={eForm.qty} onChange={e=>ue(“qty”,e.target.value)}/></div>
<div className="fg"><label className="fl">Budget / Salary Range</label>
<select className=“fs” value={eForm.salary} onChange={e=>ue(“salary”,e.target.value)}>
<option value="">Select</option>
{[“₹10k–13k”,“₹13k–15k”,“₹15k–20k”,“₹20k–30k”,“₹30k+”,“Open to discussion”].map(x=><option key={x}>{x}</option>)}
</select>
</div>
</div>
<div className="fg"><label className="fl">Location / District</label>
<select className=“fs” value={eForm.district} onChange={e=>ue(“district”,e.target.value)}>
<option value="">Select district</option>
{DISTRICTS_KL.map(x=><option key={x}>{x}</option>)}
</select>
</div>
<div className="fg"><label className="fl">Additional Notes</label><textarea className=“ft” placeholder=“When needed, special requirements, etc.” value={eForm.notes} onChange={e=>ue(“notes”,e.target.value)}/></div>
<button className=“btn btn-primary” disabled={!eForm.bizName||!eForm.bizType||!eForm.contactName||!eForm.staffType} onClick={()=>setScreen(“success-employer”)}>Submit Enquiry →</button>
</div>
</div>
</>
);

/* ── CANDIDATE CHOOSE ── */
if (screen === “candidate-choose”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="page">
<button className="back" onClick={goHome}>← BACK</button>
<div className="page-title">MJS <span>CAREERS</span></div>
<div className="page-sub">Current openings across all MJS Group ventures</div>
<div className="divider"/>
<div className="sec-title">— Open Positions</div>
<div className="career-cards">
{CAREERS.map(j=>(
<div key={j.id} className=“career-card” onClick={()=>{setSelectedJob(j);setScreen(“candidate-zone”);}}>
<div className="cc-left">
<h4>{j.title}</h4>
<p>{j.sub}</p>
</div>
<div className={`cc-badge ${j.badge}`}>{j.badge===“fizz”?“FIZZ”:“OPEN”}</div>
</div>
))}
</div>
<div className="alert gold">📋 All positions require document verification. Non-Keralite candidates must complete MARGA orientation before deployment.</div>
</div>
</div>
</>
);

/* ── CANDIDATE ZONE SELECT ── */
if (screen === “candidate-zone”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="page">
<button className=“back” onClick={()=>setScreen(“candidate-choose”)}>← BACK</button>
<div className="page-title">APPLY — <span>{selectedJob?.title}</span></div>
<div className="page-sub">Select your worker category</div>
<div className="divider"/>
<div style={{display:“flex”,flexDirection:“column”,gap:12,marginBottom:20}}>
<div style={{background:CARD,border:“1px solid #16a34a”,borderRadius:12,padding:18,cursor:“pointer”}} onClick={()=>{setCandidatePath(“kerala”);setScreen(“candidate-form”);setStep(1);}}>
<div style={{fontSize:24,marginBottom:6}}>🌴</div>
<div style={{fontFamily:”‘Barlow Condensed’,sans-serif”,fontSize:18,fontWeight:900,color:”#4ade80”,textTransform:“uppercase”,letterSpacing:1,marginBottom:4}}>Kerala Worker</div>
<div style={{fontSize:11,color:”#666”,lineHeight:1.5}}>For candidates from Kerala. Upload documents and apply directly.</div>
</div>
<div style={{background:CARD,border:`1px solid ${GOLD}`,borderRadius:12,padding:18,cursor:“pointer”}} onClick={()=>{setCandidatePath(“guest”);setScreen(“candidate-form”);setStep(1);}}>
<div style={{fontSize:24,marginBottom:6}}>🇮🇳</div>
<div style={{fontFamily:”‘Barlow Condensed’,sans-serif”,fontSize:18,fontWeight:900,color:GOLD,textTransform:“uppercase”,letterSpacing:1,marginBottom:4}}>Guest Worker</div>
<div style={{fontSize:11,color:”#666”,lineHeight:1.5}}>For non-Keralite candidates. Includes MARGA orientation, anti-drug awareness & police verification.</div>
<div style={{marginTop:8,display:“inline-block”,background:“rgba(239,68,68,.1)”,border:“1px solid #ef4444”,borderRadius:20,padding:“2px 10px”,fontSize:9,color:”#fca5a5”,letterSpacing:2}}>MARGA REQUIRED</div>
</div>
</div>
</div>
</div>
</>
);

/* ── CANDIDATE FORM ── */
const totalSteps = candidatePath === “guest” ? 4 : 3;
if (screen === “candidate-form”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="page">
<button className=“back” onClick={()=>step===1?setScreen(“candidate-zone”):setStep(s=>s-1)}>← BACK</button>
<div className="prog-wrap">
<div className="prog-bar"><div className=“prog-fill” style={{width:`${(step/totalSteps)*100}%`}}/></div>
<div className="prog-label">Step {step} of {totalSteps} — {selectedJob?.title}</div>
</div>
<div className="divider"/>

```
      {step===1 && <>
        <div className="page-title">PERSONAL <span>DETAILS</span></div>
        <div className="page-sub">{candidatePath==="guest"?"Guest Worker — MARGA Registration":"Kerala Worker Registration"}</div>
        {candidatePath==="guest" && <div className="marga-banner"><h3>🚫 MARGA — Zero Drug Tolerance</h3><p>All guest workers must complete MARGA awareness before deployment. Drug use leads to immediate removal and legal action.</p></div>}
        <div className="fg"><label className="fl">Full Name *</label><input className="fi" placeholder="Your full name" value={cForm.fullName} onChange={e=>uc("fullName",e.target.value)}/></div>
        <div className="row2">
          <div className="fg"><label className="fl">Date of Birth *</label><input className="fi" type="date" value={cForm.dob} onChange={e=>uc("dob",e.target.value)}/></div>
          <div className="fg"><label className="fl">Gender *</label>
            <select className="fs" value={cForm.gender} onChange={e=>uc("gender",e.target.value)}>
              <option value="">Select</option><option>Male</option><option>Female</option><option>Other</option>
            </select>
          </div>
        </div>
        <div className="fg"><label className="fl">Phone / WhatsApp *</label><input className="fi" type="tel" placeholder="+91 XXXXXXXXXX" value={cForm.phone} onChange={e=>uc("phone",e.target.value)}/></div>
        <div className="fg"><label className="fl">Email</label><input className="fi" type="email" placeholder="optional" value={cForm.email} onChange={e=>uc("email",e.target.value)}/></div>
        {candidatePath==="guest" && <>
          <div className="sec-title">Home State</div>
          <div className="row2">
            <div className="fg"><label className="fl">State *</label>
              <select className="fs" value={cForm.state} onChange={e=>uc("state",e.target.value)}>
                <option value="">Select state</option>{STATES.map(s=><option key={s}>{s}</option>)}
              </select>
            </div>
            <div className="fg"><label className="fl">District / City *</label><input className="fi" placeholder="Home district" value={cForm.district} onChange={e=>uc("district",e.target.value)}/></div>
          </div>
        </>}
        <div className="fg"><label className="fl">Current Address</label><textarea className="ft" placeholder="Address in Kerala or hometown" value={cForm.address} onChange={e=>uc("address",e.target.value)}/></div>
        <div className="row2">
          <div className="fg"><label className="fl">Emergency Contact Name</label><input className="fi" placeholder="Name" value={cForm.emgName} onChange={e=>uc("emgName",e.target.value)}/></div>
          <div className="fg"><label className="fl">Emergency Phone</label><input className="fi" type="tel" placeholder="+91" value={cForm.emgPhone} onChange={e=>uc("emgPhone",e.target.value)}/></div>
        </div>
        <button className="btn btn-primary" disabled={!cForm.fullName||!cForm.phone||(candidatePath==="guest"&&!cForm.state)} onClick={()=>setStep(2)}>Continue →</button>
      </>}

      {step===2 && <>
        <div className="page-title">SKILLS & <span>EXPERIENCE</span></div>
        <div className="page-sub">Tell us about your work background</div>
        <div className="fg">
          <label className="fl">Select Skills / Profession *</label>
          <div className="skill-tags">{SKILLS.map(s=><button key={s} className={`stag ${skills.includes(s)?"on":""}`} onClick={()=>toggleSkill(s)}>{s}</button>)}</div>
        </div>
        <div className="fg"><label className="fl">Years of Experience</label>
          <select className="fs" value={cForm.experience} onChange={e=>uc("experience",e.target.value)}>
            <option value="">Select</option>{["Fresher (0 years)","Less than 1 year","1–2 years","3–5 years","5–10 years","10+ years"].map(x=><option key={x}>{x}</option>)}
          </select>
        </div>
        <div className="fg"><label className="fl">Current / Previous Job Role</label><input className="fi" placeholder="e.g. Plumber at ABC Builders" value={cForm.currentRole} onChange={e=>uc("currentRole",e.target.value)}/></div>
        <div className="fg"><label className="fl">Expected Monthly Salary (₹)</label>
          <select className="fs" value={cForm.salary} onChange={e=>uc("salary",e.target.value)}>
            <option value="">Select range</option>{["₹10,000–₹13,000","₹13,000–₹15,000","₹15,000–₹20,000","₹20,000–₹30,000","₹30,000–₹40,000","₹40,000+"].map(x=><option key={x}>{x}</option>)}
          </select>
        </div>
        <button className="btn btn-primary" disabled={skills.length===0} onClick={()=>setStep(3)}>Continue →</button>
      </>}

      {step===3 && <>
        <div className="page-title">DOCUMENT <span>UPLOAD</span></div>
        <div className="page-sub">Upload for verification</div>
        {candidatePath==="guest" && <div className="alert red">🔒 Police Clearance Certificate is mandatory for all Guest Workers under MARGA protocol.</div>}
        <div className="fg">
          <label className="fl">CV / Resume (optional)</label>
          <label className={`upload-box ${uploads.cv?"done":""}`}>
            <input type="file" accept=".pdf,.doc,.docx" onChange={e=>handleUpload("cv",e)}/>
            <div className="ui">{uploads.cv?"✅":"📄"}</div>
            <h4>{uploads.cv||"Upload CV"}</h4>
            <p>{uploads.cv?"File selected":"PDF or DOC — Max 5MB"}</p>
          </label>
        </div>
        <div className="fg">
          <label className="fl">Aadhaar Card *</label>
          <label className={`upload-box ${uploads.aadhaar?"done":""}`}>
            <input type="file" accept="image/*,.pdf" onChange={e=>handleUpload("aadhaar",e)}/>
            <div className="ui">{uploads.aadhaar?"✅":"🪪"}</div>
            <h4>{uploads.aadhaar||"Upload Aadhaar"}</h4>
            <p>{uploads.aadhaar?"File selected":"Front & back — JPG, PNG or PDF"}</p>
          </label>
        </div>
        {candidatePath==="guest" && <div className="fg">
          <label className="fl">Police Clearance Certificate (PCC) *</label>
          <label className={`upload-box ${uploads.pcc?"done":""}`}>
            <input type="file" accept="image/*,.pdf" onChange={e=>handleUpload("pcc",e)}/>
            <div className="ui">{uploads.pcc?"✅":"👮"}</div>
            <h4>{uploads.pcc||"Upload PCC"}</h4>
            <p>{uploads.pcc?"File selected":"From home state police — PDF preferred"}</p>
          </label>
        </div>}
        <button className="btn btn-primary" disabled={!uploads.aadhaar||(candidatePath==="guest"&&!uploads.pcc)} onClick={()=>candidatePath==="guest"?setStep(4):setScreen("success-candidate")}>
          {candidatePath==="guest"?"Continue to MARGA Awareness →":"Submit Application"}
        </button>
      </>}

      {step===4 && candidatePath==="guest" && <>
        <div className="page-title">MARGA <span>AWARENESS</span></div>
        <div className="page-sub">Mandatory — Watch before final submission</div>
        <div className="marga-banner"><h3>🚫 Drug Free Kerala Initiative</h3><p>MARGA is MJS Group's commitment to a safer Kerala workplace. Every guest worker must watch and acknowledge this awareness programme.</p></div>
        <div className="video-card">
          <div className="video-thumb" onClick={()=>setVideoWatched(true)}>
            <div className="play-btn">▶</div>
            <h4>MARGA Awareness Video</h4>
            <p>Anti-Drug & Worker Conduct — 12 mins</p>
          </div>
          <div className="video-body">
            <div className="vpoint red"><span>🚫</span><span><strong>Anti-Drug Policy</strong> — Zero tolerance. Drug use = immediate removal + legal action under Kerala law.</span></div>
            <div className="vpoint gold"><span>📋</span><span><strong>Discipline & Conduct</strong> — Workplace behaviour, dress code, and professional standards in Kerala.</span></div>
            <div className="vpoint green"><span>⚖️</span><span><strong>Your Rights</strong> — Labour laws, minimum wage, Athidhi Portal registration, and grievance process.</span></div>
            <div className="vpoint blue"><span>🌴</span><span><strong>Kerala Culture</strong> — Local customs, public behaviour, and community respect.</span></div>
          </div>
        </div>
        <div className="cb-row" onClick={()=>setVideoWatched(v=>!v)}>
          <input type="checkbox" checked={videoWatched} onChange={()=>{}}/>
          <span>I confirm I have watched the MARGA Awareness Video and agree to the zero drug tolerance policy, discipline rules, and Kerala labour laws. I understand violation results in immediate termination.</span>
        </div>
        <button className="btn btn-primary" disabled={!videoWatched} onClick={()=>setScreen("success-candidate")}>✅ Accept & Submit Application</button>
      </>}
    </div>
  </div>
</>
```

);

/* ── SUCCESS EMPLOYER ── */
if (screen === “success-employer”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="success">
<div className="success-icon">✅</div>
<h2>Registration <span>Complete!</span></h2>
<p>Your {empPath===“fizz”?“Fizz vendor registration”:“staff enquiry”} has been submitted.</p>
<p>Our team will contact you within <strong style={{color:GOLD}}>24–48 hours.</strong></p>
<div className="ref-box">
<p>Reference Number</p>
<h3>{refNo.employer}</h3>
</div>
<p style={{fontSize:10,color:”#555”,marginBottom:4}}>Confirmation sent to</p>
<p style={{fontSize:11,color:GOLD,marginBottom:6}}>mjsgroup.mail@gmail.com</p>
{empPath===“fizz” && selectedPlan && (
<div style={{background:“rgba(107,33,168,.1)”,border:`1px solid ${FIZZ_PURPLE}`,borderRadius:10,padding:12,marginBottom:16,width:“100%”}}>
<p style={{fontSize:10,color:”#a78bfa”,letterSpacing:2,textTransform:“uppercase”,marginBottom:4}}>Selected Plan</p>
<p style={{fontSize:16,fontFamily:”‘Barlow Condensed’,sans-serif”,fontWeight:900,color:”#fff”}}>{selectedPlan===“basic”?“BASIC — ₹15,999/month”:“STANDARD — ₹24,999/month”}</p>
</div>
)}
<p style={{fontSize:10,color:”#555”,marginBottom:6}}>Questions? Call us:</p>
<p style={{fontSize:13,color:”#ddd”,marginBottom:20}}>+91 730 654 5404 / +91 994 784 5404</p>
<button className="btn btn-primary" onClick={goHome}>← Back to Home</button>
</div>
<div className="footer-strip"><span>MJS GROUP © 2025</span><span>PAYYANNUR · KERALA</span></div>
</div>
</>
);

/* ── SUCCESS CANDIDATE ── */
if (screen === “success-candidate”) return (
<>
<style>{G}</style>
<div className="app">
<Nav/>
<div className="success">
<div className="success-icon">✅</div>
<h2>Application <span>Received!</span></h2>
<p>Applied for: <strong style={{color:GOLD}}>{selectedJob?.title}</strong></p>
<p>Our HR team will review and contact you within <strong style={{color:GOLD}}>2–3 working days.</strong></p>
<div className="ref-box">
<p>Application Reference</p>
<h3>{refNo.candidate}</h3>
</div>
{candidatePath===“guest” && (
<div style={{background:“rgba(239,68,68,.08)”,border:“1px solid rgba(239,68,68,.25)”,borderRadius:10,padding:12,marginBottom:16,width:“100%”}}>
<p style={{fontSize:11,color:”#fca5a5”,lineHeight:1.6,textAlign:“left”}}>🚫 <strong>MARGA Reminder:</strong> You have accepted the Zero Drug Tolerance policy. Any violation means immediate removal and legal action. Stay disciplined. Build a better future.</p>
</div>
)}
<p style={{fontSize:10,color:”#555”,marginBottom:4}}>Details sent to</p>
<p style={{fontSize:11,color:GOLD,marginBottom:20}}>tojess.rr@gmail.com</p>
<button className=“btn btn-primary” onClick={()=>setScreen(“candidate-choose”)}>View More Jobs</button>
<button className="btn btn-secondary" onClick={goHome}>← Back to Home</button>
</div>
<div className="footer-strip"><span>MJS GROUP © 2025</span><span>PAYYANNUR · KERALA</span></div>
</div>
</>
);

return null;
}