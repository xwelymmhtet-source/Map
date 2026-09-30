<!DOCTYPE html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Royal Continent – 3D Map</title>
<style>
:root{--bg:#f4efe4;--fg:#2b2418;--card:#fffaf0;--line:#b9ad94;--muted:#6f6552;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#15130f;--fg:#efe6d2;--card:#26221a;--line:#5b5140;--muted:#a89c82}}
:root[data-theme="dark"]{--bg:#15130f;--fg:#efe6d2;--card:#26221a;--line:#5b5140;--muted:#a89c82}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--fg);font:15px/1.4 Georgia,'Times New Roman',serif}
main{max-width:1250px;margin:0 auto;padding:14px}
h1{margin:0 0 4px;font-size:22px;letter-spacing:.08em}p.s{margin:0 0 10px;color:var(--muted);font-size:13px}
.g{display:grid;grid-template-columns:minmax(0,1fr) 330px;gap:12px}
@media(max-width:860px){.g{grid-template-columns:1fr}}
.card{background:var(--card);border:1px solid var(--line);border-radius:8px;padding:10px;margin-bottom:10px}
#stage{position:relative;height:66vh;min-height:400px;border:1px solid var(--line);border-radius:8px;overflow:hidden;background:#0b1422}
#stage canvas{display:block;width:100%;height:100%;touch-action:none}
#tb{position:absolute;top:8px;left:8px;display:flex;gap:6px;flex-wrap:wrap}
#tb button{width:auto;margin:0;padding:4px 9px;font-size:12px;background:rgba(20,18,14,.75);color:#efe6d2;border-color:#7a6d55}
#tb button.on{background:#b4761f}
#ro{position:absolute;bottom:38px;left:8px;color:#efe6d2;font-size:12px;background:rgba(0,0,0,.55);padding:3px 8px;border-radius:5px;max-width:90%}
#sb{position:absolute;bottom:8px;right:8px;color:#efe6d2;font-size:11px;text-align:center}#sbl{height:6px;border:2px solid #efe6d2;border-top:none;margin:0 auto}
#cp{position:absolute;top:8px;right:8px;width:78px;height:78px;pointer-events:none}
.eb{height:10px;border-radius:5px;margin:6px 0 2px;background:linear-gradient(90deg,#0f2a4a,#2f8a9c,#dcc88e,#557a35,#8d9a55,#8a8570,#f6f4fc)}
#hint{position:absolute;bottom:8px;left:8px;color:#d9ceb4;font-size:12px;background:rgba(0,0,0,.45);padding:3px 8px;border-radius:5px}
label{display:block;font-size:12px;color:var(--muted);margin-top:8px}
select,button{width:100%;padding:6px;font:inherit;background:var(--bg);color:var(--fg);border:1px solid var(--line);border-radius:5px}
button{cursor:pointer;margin-top:8px}
.lg span{display:inline-block;margin-right:10px;font-size:12px}.lg i{display:inline-block;width:11px;height:11px;border-radius:50%;margin-right:4px;vertical-align:-1px;border:1px solid #888}
.rl{font-size:13px;margin:0;padding:0;list-style:none}
.rl li{border-left:4px solid;padding:3px 0 3px 8px;margin:6px 0}
small{display:block;color:var(--muted);font-size:12px}
.sum{font-size:13px;background:var(--bg);border-radius:6px;padding:6px 8px;margin-top:6px}
#dl{max-height:230px;overflow:auto;font-size:13px}
#dl div{padding:4px 2px;border-bottom:1px solid var(--line);cursor:pointer}#dl div:hover{background:var(--bg)}
#err{padding:20px;color:#fff}
</style></head><body><main>
<h1>THE ROYAL CONTINENT</h1>
<p class="s">Fan-made 3D schematic modelled on the continent's layout. Zone names, tiers, silver costs and loot are estimates, not official game values.</p>
<div class="g"><div>
<div id="stage"><div id="tb"><button id="bR">Reset view</button><button id="bT">Top view</button><button id="bL" class="on">Labels</button><button id="bD" class="on">Roads</button><button id="bS">Spin</button><button id="bG" class="on">Grid</button><button id="bC">Contours</button><button id="bK" class="on">Clouds</button><button id="vN" title="View from north">From N</button><button id="vE">From E</button><button id="vS">From S</button><button id="vW">From W</button><button id="vU" title="Look up from underwater">Under</button></div><div id="ro">Move the cursor over the map for coordinates and elevation.</div><div id="hint">Drag: rotate on any side · Right-drag or two fingers: pan · Scroll or pinch: zoom · Click zones to set a route</div><svg id="cp" viewBox="-40 -40 80 80"><g id="cpg"><circle r="36" fill="rgba(20,18,14,.6)" stroke="#d9ceb4"/><path d="M0-27L6 0 0 5-6 0Z" fill="#e5484d"/><path d="M0 27L6 0 0-5-6 0Z" fill="#d9ceb4"/><g fill="#efe6d2" font-size="10" font-family="Georgia" text-anchor="middle"><text y="-29">N</text><text y="34">S</text><text x="30" y="3.5">E</text><text x="-30" y="3.5">W</text></g></g></svg><div id="sb"><div id="sbl"></div><span id="sbt"></span></div></div>
<div class="card lg" style="margin-top:10px"><span><i style="background:#3b82f6"></i>Blue</span><span><i style="background:#eab308"></i>Yellow</span><span><i style="background:#ef4444"></i>Red</span><span><i style="background:#000"></i>Black</span><br><span>🏰 City</span><span>🔺 Solo dungeon</span><span>🔷 Group dungeon</span><span>⭕ Avalon road</span><div class="eb"></div><small style="display:flex;justify-content:space-between"><span>Deep sea</span><span>Sea level</span><span>Lowland</span><span>3,500 m</span></small></div>
</div><div>
<div class="card" id="info" style="min-height:120px">Hover a zone or city.</div>
<div class="card"><b>Route planner</b>
<label>From</label><select id="a"></select><label>To</label><select id="b"></select>
<label>Travel mode</label><select id="mo"><option value="walk">On foot (tolls only)</option><option value="mount" selected>Riding mount</option><option value="cart">Cargo ox (heavy load)</option></select>
<label>Optimise for</label><select id="op"><option value="jumps">Fewest jumps</option><option value="silver">Lowest silver cost</option><option value="safe">Safest path</option></select>
<label>Avoid</label><select id="v"><option value="0">Nothing</option><option value="1">Black zones</option><option value="2">Red and black zones</option></select>
<button id="go">Find route</button><div id="out" style="margin-top:8px"></div></div>
<div class="card"><b>Dungeons</b><label>Filter</label><select id="df"><option value="">All</option><option>Solo</option><option>Group</option><option>Avalon road</option></select><div id="dl" style="margin-top:6px"></div></div>
</div></div></main>
<script src="https://cdn.jsdelivr.net/npm/three@0.128.0/build/three.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js"></script>
<script>
try{(function(){
const C={blue:'#3b82f6',yellow:'#eab308',red:'#ef4444',black:'#111'};
const ORD=['blue','yellow','red','black'];
const RISK={blue:'Safe – no PvP',yellow:'Some PvP risk',red:'High-risk PvP',black:'Extreme-risk, full-loot PvP'};
const TOLL={blue:100,yellow:250,red:600,black:1200};
const MD={walk:{n:'On foot',toll:1,up:0,sec:90},mount:{n:'Riding mount',toll:1,up:120,sec:35},cart:{n:'Cargo ox',toll:1.5,up:220,sec:60}};
const DF={solo:{yellow:600,red:1800,black:4500},group:{red:4000,black:9000}};
const REG=[
{n:'Thetford',z:'Mearepools',c:[345,92],d:[-1,.3],r:'Fiber, Ore',t:'Swamp, mud and ponds',col:0x3f8f8a},
{n:'Fort Sterling',z:'Blyn Brae',c:[478,117],d:[.25,-1],r:'Wood, Ore',t:'Snow-capped mountains and arctic cold',col:0x5d8fd0},
{n:'Lymhurst',z:'Celidon',c:[598,262],d:[1,.3],r:'Wood, Fiber',t:'Lush green forest and hills',col:0x3f9a4a},
{n:'Bridgewatch',z:'Umbrash',c:[385,272],d:[0,1],r:'Hide, Stone',t:'Dry, cracked desert lands',col:0xd9822b},
{n:'Martlock',z:'Gleinmoor',c:[300,187],d:[-.8,.6],r:'Hide, Ore',t:'High hills, mountains, fog and plains',col:0x9a6a3a}];
const TI=[['blue','T2–3'],['yellow','T4–5'],['red','T6'],['black','T7–8']];
const W=['Vale','Reach','Pass','Deep'];
const N={},E=[],ET={};
N.C={id:'C',name:'Caerleon',x:410,y:172,risk:'red',city:1,tier:'Hub',res:'Marketplace, Black Market',bio:'Central plains and trade hub',dun:[],reg:'Center'};
REG.forEach((g,i)=>{
 const L=Math.hypot(...g.d),d=[g.d[0]/L,g.d[1]/L],p=[-d[1],d[0]];
 N['c'+i]={id:'c'+i,name:g.n,x:g.c[0],y:g.c[1],risk:'blue',city:1,tier:'Royal city',res:g.r+' nearby',bio:g.t,dun:[],reg:g.z,ci:i};
 E.push(['C','c'+i,'road']);
 [-1,1].forEach(s=>{let prev='c'+i;
  TI.forEach(([k,t],j)=>{const id=`${i}${k}${s}`,q=22*(j+1),o=s*(6+j*5);
   const dn=[];if(k==='yellow'&&s>0)dn.push('solo');if(k==='red'){dn.push('solo');if(s<0)dn.push('group')}
   if(k==='black'){dn.push('group');if(s<0)dn.push('road')}
   N[id]={id,name:`${g.z} ${W[j]} ${s<0?'I':'II'}`,x:g.c[0]+d[0]*q+p[0]*o,y:g.c[1]+d[1]*q+p[1]*o,risk:k,tier:t,res:g.r,bio:g.t,dun:dn,reg:g.z};
   E.push([prev,id,'']);prev=id;});});
});
const dist2=(a,b)=>Math.hypot(N[a].x-N[b].x,N[a].y-N[b].y);
REG.forEach((g,i)=>{const j=(i+1)%5;
 TI.slice(0,3).forEach(([k])=>{const a=`${i}${k}1`,b=`${j}${k}-1`;if(dist2(a,b)<120)E.push([a,b,''])});
 E.push([`${i}black-1`,`${(i+2)%5}black1`,'avalon']);});
const adj={};Object.keys(N).forEach(k=>adj[k]=[]);
E.forEach(([a,b,t])=>{adj[a].push(b);adj[b].push(a);ET[a+'|'+b]=ET[b+'|'+a]=t});
const fmt=n=>Math.round(n).toLocaleString('en-US')+' silver';
const tm=s=>Math.floor(s/60)+'m '+String(Math.round(s%60)).padStart(2,'0')+'s';
function ecost(a,b,M){const t=ET[a+'|'+b],tl=(N[b].city?50:TOLL[N[b].risk])*M.toll,fee=t==='road'?200:t==='avalon'?1500:0;
 return{toll:tl,up:M.up,fee,total:tl+M.up+fee,sec:M.sec*(t==='avalon'?.3:1)}}
function dungeons(n){const o=[];n.dun.forEach(t=>{
 if(t==='solo')o.push({kind:'Solo',fee:DF.solo[n.risk],m:[1.6,3.2],party:'1 player'});
 if(t==='group')o.push({kind:'Group',fee:DF.group[n.risk],m:[2,4.5],party:n.risk==='black'?'5–20 players':'5 players'});
 if(t==='road')o.push({kind:'Avalon road',fee:1500,m:[1.5,5],party:'1–7 players'})});
 return o.map(d=>({...d,lo:d.fee*d.m[0],hi:d.fee*d.m[1]}))}
const dtxt=n=>{const d=dungeons(n);return d.length?d.map(x=>x.kind).join(', '):'None'};
// ---------- terrain data ----------
const OX=-40,OY=-19,NX=440,NY=244,MW=441,MH=245;
const LAND=[
{k:'swamp',p:[[200,90],[240,65],[300,55],[345,58],[380,85],[365,120],[350,150],[300,170],[250,165],[215,140],[190,120]],l:['MEAREPOOLS',270,110]},
{k:'snow',p:[[345,58],[390,35],[440,22],[500,22],[540,70],[520,110],[510,150],[470,160],[430,150],[395,125],[370,110],[380,85]],l:['BLYN BRAE',445,80]},
{k:'high',p:[[185,190],[215,140],[250,165],[300,170],[350,175],[340,215],[330,255],[290,320],[260,330],[230,280],[200,235]],l:['GLEINMOOR',245,215]},
{k:'desert',p:[[340,215],[345,190],[390,180],[440,190],[470,215],[450,260],[470,300],[440,330],[420,360],[380,375],[350,370],[300,340],[290,320],[330,255]],l:['UMBRASH',400,325]},
{k:'desert',p:[[480,265],[520,262],[545,300],[520,325],[490,315]]},
{k:'desert',p:[[555,285],[590,290],[598,320],[570,330]]},
{k:'desert',p:[[380,378],[410,385],[440,408],[415,412],[385,395]]},
{k:'desert',p:[[540,340],[565,335],[570,370],[550,378]]},
{k:'forest',p:[[470,160],[510,150],[540,165],[600,170],[660,215],[700,300],[705,360],[660,375],[600,330],[540,320],[500,290],[490,240],[470,215]],l:['CELIDON',590,205]},
{k:'snow',p:[[470,25],[500,20],[545,28],[535,48],[490,50]]},
{k:'snow',p:[[118,215],[140,200],[160,235],[150,275],[128,260]]},
{k:'swamp',p:[[110,80],[150,50],[195,42],[180,65],[130,85]]},
{k:'plain',p:[[350,165],[395,125],[430,150],[470,160],[470,215],[440,190],[390,180],[345,190],[350,175]]}];
const inside=(x,y,P)=>{let c=false;for(let i=0,j=P.length-1;i<P.length;j=i++){const[a,b]=P[i],[u,v]=P[j];if((b>y)!=(v>y)&&x<(u-a)*(y-b)/(v-b)+a)c=!c}return c};
const hash=(x,y)=>{const n=Math.sin(x*127.1+y*311.7)*43758.5453;return n-Math.floor(n)};
const vn=(x,y)=>{const xi=Math.floor(x),yi=Math.floor(y),xf=x-xi,yf=y-yi,u=xf*xf*(3-2*xf),v=yf*yf*(3-2*yf),a=hash(xi,yi),b=hash(xi+1,yi),c=hash(xi,yi+1),d=hash(xi+1,yi+1);return a+(b-a)*u+(c-a)*v+(a-b-c+d)*u*v};
const fbm=(x,y)=>{let s=0,a=.5,f=1;for(let i=0;i<4;i++){s+=a*vn(x*f,y*f);f*=2;a*=.5}return s};
const sm=(a,b,x)=>{x=Math.max(0,Math.min(1,(x-a)/(b-a)));return x*x*(3-2*x)};
const mask=new Float32Array(MW*MH),bio=new Int8Array(MW*MH).fill(-1);
for(let b=0;b<MH;b++)for(let a=0;a<MW;a++){const px=OX+2*a,py=OY+2*b;for(let i=0;i<LAND.length;i++)if(inside(px,py,LAND[i].p)){mask[b*MW+a]=1;bio[b*MW+a]=i;break}}
function blur(src,r){const t=new Float32Array(src.length),o=new Float32Array(src.length),n=2*r+1,cl=(v,m)=>Math.max(0,Math.min(m-1,v));
 for(let b=0;b<MH;b++){let s=0;for(let a=-r;a<=r;a++)s+=src[b*MW+cl(a,MW)];for(let a=0;a<MW;a++){t[b*MW+a]=s/n;s+=src[b*MW+cl(a+r+1,MW)]-src[b*MW+cl(a-r,MW)]}}
 for(let a=0;a<MW;a++){let s=0;for(let b=-r;b<=r;b++)s+=t[cl(b,MH)*MW+a];for(let b=0;b<MH;b++){o[b*MW+a]=s/n;s+=t[cl(b+r+1,MH)*MW+a]-t[cl(b-r,MH)*MW+a]}}
 return o}
let F=mask;for(let i=0;i<3;i++)F=blur(F,4);
const cen=LAND.map(L=>[L.p.reduce((s,q)=>s+q[0],0)/L.p.length,L.p.reduce((s,q)=>s+q[1],0)/L.p.length]);
const VN=(NX+1)*(NY+1),H=new Float32Array(VN),BI=new Int8Array(VN),FF=new Float32Array(VN);
for(let j=0;j<=NY;j++)for(let i=0;i<=NX;i++){const k=j*(NX+1)+i,px=OX+2*i,py=OY+2*j,m=k,f=F[m]+(fbm(px/16+7,py/16)-.5)*.34;let bi=bio[m];
 if(bi<0){let md=1e9;cen.forEach((c,q)=>{const d=Math.hypot(c[0]-px,c[1]-py);if(d<md){md=d;bi=q}})}
 BI[k]=bi;FF[k]=f;const L=sm(.2,.5,f),kind=LAND[bi].k;let r;
 if(kind==='snow'){const q=1-Math.abs(2*fbm(px/45+3,py/45)-1);r=4+q*q*q*32+fbm(px/12,py/12)*3}
 else if(kind==='high')r=3+fbm(px/50,py/50)*15+fbm(px/14,py/14)*2;
 else if(kind==='forest')r=3+fbm(px/45,py/45)*11+fbm(px/13,py/13)*1.5;
 else if(kind==='desert')r=2.5+Math.sin(px/9+fbm(px/30,py/30)*6)*1.1+fbm(px/40,py/40)*5+(fbm(px/60+9,py/60)>.6?7:0);
 else if(kind==='swamp')r=1.3+fbm(px/30,py/30)*2.2;
 else r=2.6+fbm(px/35,py/35)*4;
 r+=(fbm(px/5,py/5)-.5)*(kind==='snow'?2.5:.9);
 if(kind==='swamp'&&fbm(px/14+5,py/14)<.46)r=.5;
 const sea=-8*(1-sm(0,.3,f))-.5;H[k]=sea*(1-L)+r*L}
for(let p=0;p<5;p++){const T=H.slice();for(let j=1;j<NY;j++)for(let i=1;i<NX;i++){const k=j*(NX+1)+i;H[k]=(T[k]*4+T[k-1]+T[k+1]+T[k-NX-1]+T[k+NX+1])/8}}
function segD(px,py,a,b){const dx=b[0]-a[0],dy=b[1]-a[1];let t=((px-a[0])*dx+(py-a[1])*dy)/(dx*dx+dy*dy);t=Math.max(0,Math.min(1,t));return Math.hypot(px-a[0]-t*dx,py-a[1]-t*dy)}
const RIV=[[[335,172],[322,200],[305,228],[288,258],[265,288],[240,318],[222,340]],[[520,165],[545,200],[565,235],[598,262],[630,292],[665,332],[700,372]],[[385,272],[392,300],[385,330],[395,360],[402,395]],[[440,62],[462,90],[488,118],[520,150],[556,162]]];
const RD=new Float32Array(VN).fill(99);
RIV.forEach(pl=>{for(let q=0;q<pl.length-1;q++){const a=pl[q],b=pl[q+1],i0=Math.max(0,Math.floor((Math.min(a[0],b[0])-6-OX)/2)),i1=Math.min(NX,Math.ceil((Math.max(a[0],b[0])+6-OX)/2)),j0=Math.max(0,Math.floor((Math.min(a[1],b[1])-6-OY)/2)),j1=Math.min(NY,Math.ceil((Math.max(a[1],b[1])+6-OY)/2));
 for(let j=j0;j<=j1;j++)for(let i=i0;i<=i1;i++){const k=j*(NX+1)+i,d=segD(OX+2*i,OY+2*j,a,b);if(d<RD[k])RD[k]=d}}});
for(let k=0;k<VN;k++)if(RD[k]<4&&H[k]>.6){const w=1-sm(1.4,4,RD[k]);H[k]=H[k]*(1-w)+Math.min(H[k],Math.max(.55,H[k]*.3))*w}
const cities=Object.values(N).filter(n=>n.city);
cities.forEach(c=>{const ci=Math.round((c.x-OX)/2),cj=Math.round((c.y-OY)/2),base=Math.max(2.6,H[cj*(NX+1)+ci]);c.base=base;
 for(let j=0;j<=NY;j++)for(let i=0;i<=NX;i++){const d=Math.hypot(OX+2*i-c.x,OY+2*j-c.y);if(d<22){const w=1-sm(9,22,d),k=j*(NX+1)+i;H[k]=H[k]*(1-w)+base*w}}});
function hAt(px,py){const fx=(px-OX)/2,fy=(py-OY)/2,i=Math.max(0,Math.min(NX-1,Math.floor(fx))),j=Math.max(0,Math.min(NY-1,Math.floor(fy))),u=fx-i,v=fy-j,k=j*(NX+1)+i;
 return H[k]*(1-u)*(1-v)+H[k+1]*u*(1-v)+H[k+NX+1]*(1-u)*v+H[k+NX+2]*u*v}
const P3=n=>new THREE.Vector3(n.x-400,hAt(n.x,n.y),n.y-225);
// ---------- three.js ----------
const stage=document.getElementById('stage'),cpg=document.getElementById('cpg'),sbl=document.getElementById('sbl'),sbt=document.getElementById('sbt');
const renderer=new THREE.WebGLRenderer({antialias:true});renderer.setPixelRatio(Math.min(2,devicePixelRatio));stage.prepend(renderer.domElement);
renderer.shadowMap.enabled=true;renderer.shadowMap.type=THREE.PCFSoftShadowMap;
const cv=renderer.domElement,scene=new THREE.Scene();scene.background=new THREE.Color(0x8aa4bf);scene.fog=new THREE.FogExp2(0x8aa4bf,.00033);
scene.add(new THREE.Mesh(new THREE.SphereGeometry(2600,32,16),new THREE.ShaderMaterial({side:THREE.BackSide,depthWrite:false,fog:false,vertexShader:'varying vec3 p;void main(){p=position;gl_Position=projectionMatrix*modelViewMatrix*vec4(position,1.);}',fragmentShader:'varying vec3 p;void main(){float h=normalize(p).y;vec3 top=vec3(.16,.32,.6),hor=vec3(.66,.77,.88),low=vec3(.04,.09,.17);vec3 c=h>0.?mix(hor,top,pow(h,.55)):mix(hor,low,pow(-h,.4));gl_FragColor=vec4(c,1.);}'})));
const camera=new THREE.PerspectiveCamera(45,1,1,3000);
const controls=new THREE.OrbitControls(camera,cv);controls.enableDamping=true;controls.maxPolarAngle=Math.PI;controls.minDistance=15;controls.maxDistance=1800;controls.screenSpacePanning=true;controls.zoomSpeed=1.2;
const HOME=[new THREE.Vector3(0,330,380),new THREE.Vector3(0,0,10)],TOP=[new THREE.Vector3(0,720,60),new THREE.Vector3(0,0,10)];
camera.position.copy(HOME[0]);controls.target.copy(HOME[1]);
scene.add(new THREE.HemisphereLight(0xcfe2ff,0x4a3b24,.75));
const sun=new THREE.DirectionalLight(0xfff0d0,1);sun.position.set(260,380,200);sun.castShadow=true;sun.shadow.mapSize.set(4096,4096);Object.assign(sun.shadow.camera,{left:-480,right:480,top:320,bottom:-320,near:10,far:1400});sun.shadow.bias=-.0006;sun.shadow.normalBias=.6;scene.add(sun);
const cc=new THREE.Color(),cA=new THREE.Color(),cB=new THREE.Color();
const COL=new Float32Array(VN*3),COL2=new Float32Array(VN*3);
const PAL={snow:['#b9b4d6','#f6f4fc','#7e7aa0'],high:['#5b6b2f','#8d9a55','#8a8570'],forest:['#33552a','#557a35'],desert:['#e4a94f','#f0c273'],swamp:['#66702f','#7f8a3c'],plain:['#6f7f39','#8a9648']};
for(let j=0;j<=NY;j++)for(let i=0;i<=NX;i++){const k=j*(NX+1)+i,px=OX+2*i,py=OY+2*j,h=H[k],f=FF[k],kind=LAND[BI[k]].k,n=fbm(px/7,py/7);
 if(f<.3){cA.set('#0f2a4a');cB.set('#2f8a9c');cc.copy(cA).lerp(cB,sm(-8,0,h))}
 else if(h<1.7&&f<.5&&!(kind==='swamp')){cc.set('#dcc88e').lerp(cA.set('#c9b57a'),n)}
 else{const p=PAL[kind];cA.set(p[0]);cB.set(p[1]);cc.copy(cA).lerp(cB,n);
  if(kind==='snow'){cB.set(p[1]);cc.lerp(cB,sm(9,18,h));if(h<8)cc.lerp(cA.set('#7f9a78'),.35*(1-n))}
  if(kind==='high'&&h>11)cc.lerp(cB.set(p[2]),sm(11,17,h));
  if(kind==='swamp'&&h<.7)cc.set('#3f86c8');
  if(kind==='desert')cc.lerp(cB.set('#b8792c'),h>7?.6:.0)}
 if(RD[k]<2.4&&f>.3&&h>0)cc.lerp(cA.set('#2f6fae'),1-sm(1,2.4,RD[k]));
 if(h>-.9&&h<.5)cc.lerp(cA.set('#e6f4f4'),.5*n);
 const tt=(h/4)%1,dk=(h>1.6&&f>.35&&RD[k]>2.6&&tt<.06)?.7:1;
 COL[k*3]=cc.r;COL[k*3+1]=cc.g;COL[k*3+2]=cc.b;COL2[k*3]=cc.r*dk;COL2[k*3+1]=cc.g*dk;COL2[k*3+2]=cc.b*dk}
const geo=new THREE.PlaneGeometry(880,488,NX,NY);geo.rotateX(-Math.PI/2);
for(let k=0;k<VN;k++)geo.attributes.position.setY(k,H[k]);
geo.setAttribute('color',new THREE.BufferAttribute(COL.slice(),3));geo.computeVertexNormals();
const terrain=new THREE.Mesh(geo,new THREE.MeshStandardMaterial({vertexColors:true,roughness:.95,metalness:0,side:THREE.DoubleSide}));terrain.receiveShadow=true;terrain.castShadow=true;scene.add(terrain);
const wc=document.createElement('canvas');wc.width=wc.height=256;{const x=wc.getContext('2d'),im=x.createImageData(256,256);for(let i=0;i<256;i++)for(let j=0;j<256;j++){const v=(vn(i/12,j/12)*.6+vn(i/5,j/5)*.4)*255,o=(j*256+i)*4;im.data[o]=im.data[o+1]=im.data[o+2]=v;im.data[o+3]=255}x.putImageData(im,0,0)}
const wt=new THREE.CanvasTexture(wc);wt.wrapS=wt.wrapT=THREE.RepeatWrapping;wt.repeat.set(60,40);
const wat=new THREE.Mesh(new THREE.PlaneGeometry(2400,1600),new THREE.MeshStandardMaterial({color:0x2f78b0,transparent:true,opacity:.72,roughness:.12,metalness:.35,bumpMap:wt,bumpScale:.8,side:THREE.DoubleSide}));wat.receiveShadow=true;wat.rotation.x=-Math.PI/2;wat.position.y=.2;scene.add(wat);
const deep=new THREE.Mesh(new THREE.PlaneGeometry(2400,1600),new THREE.MeshBasicMaterial({color:0x0a1830,side:THREE.DoubleSide}));deep.rotation.x=-Math.PI/2;deep.position.y=-9.5;scene.add(deep);
// scatter details
let rs=5;const rnd=()=>(rs=(rs*16807)%2147483647)/2147483647;
const nearCity=(x,y)=>cities.some(c=>Math.hypot(c.x-x,c.y-y)<20);
function scatter(kinds,count,g,mat,sc,cols,minH,maxH,yo){const im=new THREE.InstancedMesh(g,mat,count),d=new THREE.Object3D();let n=0,t=0;
 while(n<count&&t<count*40){t++;const px=OX+rnd()*880,py=OY+rnd()*488,m=Math.round((py-OY)/2)*MW+Math.round((px-OX)/2);
  if(m<0||m>=mask.length||bio[m]<0||!kinds.includes(LAND[bio[m]].k)||F[m]<.8||nearCity(px,py))continue;
  const h=hAt(px,py);if(h<minH||h>maxH)continue;const s=sc[0]+rnd()*(sc[1]-sc[0]);
  d.position.set(px-400,h+yo*s,py-225);d.rotation.y=rnd()*6;d.scale.set(s,s*(.8+rnd()*.6),s);d.updateMatrix();im.setMatrixAt(n,d.matrix);
  im.setColorAt(n,cc.set(cols[Math.floor(rnd()*cols.length)]));n++}
 im.castShadow=true;im.count=n;im.instanceMatrix.needsUpdate=true;if(im.instanceColor)im.instanceColor.needsUpdate=true;scene.add(im)}
const tree=new THREE.ConeGeometry(1.3,4.5,6);tree.translate(0,2.2,0);
const M0=new THREE.MeshStandardMaterial({roughness:.9});
scatter(['forest'],1100,tree,M0,[.8,1.5],['#2a5a2a','#3b7a34','#245224','#4a8a3a'],2,14,0);
scatter(['high','plain'],320,tree,M0,[.7,1.2],['#4a5f2a','#5d7332','#3f5226'],2,11,0);
scatter(['snow'],260,tree,M0,[.7,1.3],['#e8f0ee','#a9c2b0','#d4e0e0'],2,9,0);
const rock=new THREE.DodecahedronGeometry(1.4);
scatter(['desert'],140,rock,M0,[.6,1.8],['#c99552','#b98444','#d9a866'],1.7,20,.3);
scatter(['high'],120,rock,M0,[.6,1.6],['#8a8570','#77735f'],4,25,.3);
const dead=new THREE.CylinderGeometry(.15,.25,3,5);dead.translate(0,1.5,0);
scatter(['swamp'],160,dead,M0,[.7,1.4],['#3a3320','#4a4028'],.9,5,0);
// labels
function label(text,size,color,sx,sy){const c=document.createElement('canvas');c.width=512;c.height=128;const x=c.getContext('2d');x.font=`bold ${size}px Georgia`;x.textAlign='center';x.textBaseline='middle';x.lineWidth=9;x.strokeStyle='rgba(0,0,0,.8)';x.lineJoin='round';x.strokeText(text,256,64);x.fillStyle=color;x.fillText(text,256,64);
 const s=new THREE.Sprite(new THREE.SpriteMaterial({map:new THREE.CanvasTexture(c),transparent:true,depthTest:false}));s.scale.set(sx,sy,1);s.renderOrder=10;return s}
const labelsG=new THREE.Group();scene.add(labelsG);
LAND.forEach(L=>{if(L.l){const s=label(L.l[0],62,'#f3e8c8',110,27.5);s.material.opacity=.85;s.position.set(L.l[1]-400,hAt(L.l[1],L.l[2])+34,L.l[2]-225);labelsG.add(s)}});
// cities
function makeCity(col,dark){const g=new THREE.Group(),stone=new THREE.MeshStandardMaterial({color:0xd2cab6,roughness:.9}),roof=new THREE.MeshStandardMaterial({color:col,roughness:.7}),wood=new THREE.MeshStandardMaterial({color:0xa07c52,roughness:.9});
 const R=6.8;
 for(let i=0;i<12;i++){const a=i/12*Math.PI*2,b=(i+.5)/12*Math.PI*2;
  const w=new THREE.Mesh(new THREE.BoxGeometry(3.7,1.7,.55),stone);w.position.set(Math.cos(b)*R,.85,Math.sin(b)*R);w.rotation.y=-(b+Math.PI/2);g.add(w);
  const t=new THREE.Mesh(new THREE.CylinderGeometry(.75,.85,2.8,8),stone);t.position.set(Math.cos(a)*R,1.4,Math.sin(a)*R);g.add(t);
  const c=new THREE.Mesh(new THREE.ConeGeometry(1.1,1.6,8),roof);c.position.set(Math.cos(a)*R,3.6,Math.sin(a)*R);g.add(c)}
 for(let i=0;i<20;i++){const a=rnd()*6.28,r=1.5+rnd()*4;const h=new THREE.Mesh(new THREE.BoxGeometry(1.3,1+rnd(),1.3),i%3?stone:wood);h.position.set(Math.cos(a)*r,.6,Math.sin(a)*r);g.add(h);
  const rf=new THREE.Mesh(new THREE.ConeGeometry(1.15,.9,4),roof);rf.rotation.y=Math.PI/4;rf.position.set(h.position.x,h.position.y+.9,h.position.z);g.add(rf)}
 const kp=new THREE.Mesh(new THREE.BoxGeometry(2.4,5.5,2.4),stone);kp.position.y=2.75;g.add(kp);
 const kr=new THREE.Mesh(new THREE.ConeGeometry(2,3.2,4),dark?new THREE.MeshStandardMaterial({color:0x220a0a}):roof);kr.rotation.y=Math.PI/4;kr.position.y=7.1;g.add(kr);
 const pole=new THREE.Mesh(new THREE.CylinderGeometry(.06,.06,2.2,4),wood);pole.position.y=9.6;g.add(pole);
 const flag=new THREE.Mesh(new THREE.PlaneGeometry(1.4,.8),new THREE.MeshBasicMaterial({color:col,side:THREE.DoubleSide}));flag.position.set(.7,10.2,0);g.add(flag);
 return g}
const pickables=[],spin=[],mkr={};
Object.values(N).forEach(n=>{const p=P3(n),grp=new THREE.Group();grp.position.copy(p);scene.add(grp);
 if(n.city){const cm=makeCity(n.id==='C'?0x8a1c1c:REG[n.ci].col,n.id==='C');cm.scale.setScalar(1.15);cm.traverse(o=>{if(o.isMesh){o.castShadow=true;o.receiveShadow=true}});grp.add(cm);
  const hit=new THREE.Mesh(new THREE.SphereGeometry(9),new THREE.MeshBasicMaterial({transparent:true,opacity:0,depthWrite:false}));hit.position.y=4;hit.userData.id=n.id;grp.add(hit);pickables.push(hit);
  const s=label(n.name,58,'#ffffff',48,12);s.position.set(p.x,p.y+17,p.z);labelsG.add(s)}
 else{const pole=new THREE.Mesh(new THREE.CylinderGeometry(.25,.25,3.4,6),new THREE.MeshStandardMaterial({color:0x444444}));pole.position.y=1.7;grp.add(pole);
  const sp=new THREE.Mesh(new THREE.SphereGeometry(1.8,16,12),new THREE.MeshStandardMaterial({color:C[n.risk],emissive:C[n.risk],emissiveIntensity:n.risk==='black'?.05:.35,roughness:.4}));sp.position.y=3.6;sp.userData.id=n.id;grp.add(sp);pickables.push(sp);mkr[n.id]=sp;
  const dn=n.dun,off=dn.length>1?[-2,2]:[0];dn.filter(t=>t!=='road').concat(dn.includes('road')?['road']:[]).forEach((t,q)=>{
   let m;if(t==='solo')m=new THREE.Mesh(new THREE.ConeGeometry(1.2,2.8,5),new THREE.MeshStandardMaterial({color:0xffd24a,emissive:0x8a6a00}));
   else if(t==='group')m=new THREE.Mesh(new THREE.OctahedronGeometry(1.6),new THREE.MeshStandardMaterial({color:0xff5a5a,emissive:0x701010}));
   else m=new THREE.Mesh(new THREE.TorusGeometry(1.5,.4,8,16),new THREE.MeshStandardMaterial({color:0xc084fc,emissive:0x5b21b6}));
   m.position.set(dn.length>2?(q-1)*2.6:(off[q]||0),8,0);grp.add(m);spin.push(m)})}
 });
// roads
const roadG=new THREE.Group();scene.add(roadG);
function curve(a,b,y){const A=N[a],B=N[b],pts=[];for(let i=0;i<=12;i++){const t=i/12,x=A.x+(B.x-A.x)*t,z=A.y+(B.y-A.y)*t;pts.push(new THREE.Vector3(x-400,hAt(x,z)+y,z-225))}return new THREE.CatmullRomCurve3(pts)}
E.forEach(([a,b,t])=>{const cu=curve(a,b,.9);
 if(t==='avalon'){const g=new THREE.BufferGeometry().setFromPoints(cu.getPoints(40)),l=new THREE.Line(g,new THREE.LineDashedMaterial({color:0xc084fc,dashSize:2.5,gapSize:1.5}));l.computeLineDistances();roadG.add(l)}
 else roadG.add(new THREE.Mesh(new THREE.TubeGeometry(cu,20,t==='road'?.6:.38,4,false),new THREE.MeshStandardMaterial({color:t==='road'?0xe6d5a5:0xf1e8d0,roughness:.8})))});
// route visuals
const routeG=new THREE.Group();scene.add(routeG);
// grid, clouds, fog
const gridG=new THREE.Group();scene.add(gridG);
const gm=new THREE.LineBasicMaterial({color:0xffffff,transparent:true,opacity:.3});
for(let x=0;x<=800;x+=100){const p=[];for(let y=-15;y<=465;y+=6)p.push(new THREE.Vector3(x-400,Math.max(hAt(x,y),0)+.7,y-225));gridG.add(new THREE.Line(new THREE.BufferGeometry().setFromPoints(p),gm))}
for(let y=0;y<=400;y+=100){const p=[];for(let x=-35;x<=835;x+=6)p.push(new THREE.Vector3(x-400,Math.max(hAt(x,y),0)+.7,y-225));gridG.add(new THREE.Line(new THREE.BufferGeometry().setFromPoints(p),gm))}
'ABCDEFGH'.split('').forEach((c,i)=>{const l=label(c,80,'#ffffff',14,3.5);l.position.set(i*100+50-400,10,-20-225+5);gridG.add(l)});
[50,150,250,350,440].forEach((y,i)=>{const l=label(String(i+1),80,'#ffffff',14,3.5);l.position.set(-38-400+10,10,y-225);gridG.add(l)});
const cl=document.createElement('canvas');cl.width=cl.height=128;{const x=cl.getContext('2d'),g=x.createRadialGradient(64,64,4,64,64,62);g.addColorStop(0,'rgba(255,255,255,.9)');g.addColorStop(1,'rgba(255,255,255,0)');x.fillStyle=g;x.fillRect(0,0,128,128)}
const clT=new THREE.CanvasTexture(cl),cloudsG=new THREE.Group();scene.add(cloudsG);
for(let c=0;c<22;c++){const cx=(rnd()-.5)*1000,cz=(rnd()-.5)*700,cy=120+rnd()*60;for(let q=0;q<4;q++){const s=new THREE.Sprite(new THREE.SpriteMaterial({map:clT,transparent:true,opacity:.5,depthWrite:false,fog:false}));const z=140+rnd()*120;s.scale.set(z,z*.6,1);s.position.set(cx+(rnd()-.5)*90,cy+(rnd()-.5)*10,cz+(rnd()-.5)*50);cloudsG.add(s)}}
for(let t=0,n=0;n<14&&t<400;t++){const b=LAND[2].p,px=200+rnd()*150,py=170+rnd()*160;if(!inside(px,py,b))continue;n++;const s=new THREE.Sprite(new THREE.SpriteMaterial({map:clT,transparent:true,opacity:.4,depthWrite:false}));s.scale.set(70,30,1);s.position.set(px-400,hAt(px,py)+6,py-225);scene.add(s)}
// ---------- UI ----------
const info=document.getElementById('info'),A=document.getElementById('a'),B=document.getElementById('b'),MO=document.getElementById('mo'),OP=document.getElementById('op'),AV=document.getElementById('v'),out=document.getElementById('out');
function show(n){const dd=dungeons(n);
 info.innerHTML=`<b>${n.city&&n.id!=='C'?'🏰 ':n.id==='C'?'🏰 ':''}${n.name}</b>
 <small>${n.reg} · ${n.tier}</small>
 Risk: <b style="color:${n.risk==='black'?'inherit':C[n.risk]}">${n.risk}</b> – ${RISK[n.risk]}<br>Biome: ${n.bio}<br>Resources: ${n.res}<br>
 ${n.city?`Buildings: Marketplace, Bank, Blacksmith, Mage tower, Stables, Guild hall<br>Gate fee: ${fmt(50)} · Caerleon road: ${n.id==='C'?'—':fmt(200+TOLL.red)+' (on foot)'}`:`Entry toll: ${fmt(TOLL[n.risk])} (on foot)`}
 ${dd.length?'<br><b>Dungeons</b>'+dd.map(d=>`<small>${d.kind} · ${d.party}<br>Entry: ${fmt(d.fee)} · Est. loot: ${fmt(d.lo)} – ${fmt(d.hi)}</small>`).join(''):''}`}
Object.values(N).forEach(n=>{const o=`<option value="${n.id}">${n.name}${n.city?'':' ('+n.risk+')'}</option>`;A.insertAdjacentHTML('beforeend',o);B.insertAdjacentHTML('beforeend',o)});
A.value='c1';B.value='c3';
let fly=null;
function flyTo(v,dist){const off=dist?new THREE.Vector3(0,dist*.75,dist*.7):camera.position.clone().sub(controls.target);fly={t:0,from:controls.target.clone(),to:v.clone(),cf:camera.position.clone(),ct:v.clone().add(off)}}
// dungeon list
const DUN=[];Object.values(N).forEach(n=>dungeons(n).forEach(d=>DUN.push({n,...d})));
function dlist(){const f=document.getElementById('df').value,el=document.getElementById('dl');
 el.innerHTML=DUN.filter(d=>!f||d.kind===f).sort((a,b)=>a.fee-b.fee).map(d=>`<div data-id="${d.n.id}"><b>${d.kind}</b> – ${d.n.name} <span style="color:${d.n.risk==='black'?'inherit':C[d.n.risk]}">(${d.n.risk})</span><small>Entry ${fmt(d.fee)} · loot ${fmt(d.lo)} – ${fmt(d.hi)} · ${d.party}</small></div>`).join('')}
dlist();document.getElementById('df').onchange=dlist;
document.getElementById('dl').onclick=e=>{const d=e.target.closest('[data-id]');if(d){const n=N[d.dataset.id];show(n);flyTo(P3(n),70)}};
// picking
const ray=new THREE.Raycaster(),mv=new THREE.Vector2();
function pick(e){const r=cv.getBoundingClientRect();mv.set((e.clientX-r.left)/r.width*2-1,-((e.clientY-r.top)/r.height)*2+1);ray.setFromCamera(mv,camera);const h=ray.intersectObjects(pickables,false)[0];return h?h.object.userData.id:null}
const NAMES={swamp:'Swamp',snow:'Snow mountains',high:'Highland',desert:'Desert',forest:'Forest',plain:'Plains'},ro=document.getElementById('ro');
let lastRO=0;function readout(e){const now=performance.now();if(now-lastRO<60)return;lastRO=now;const r=cv.getBoundingClientRect();mv.set((e.clientX-r.left)/r.width*2-1,-((e.clientY-r.top)/r.height)*2+1);ray.setFromCamera(mv,camera);
 const o=ray.ray.origin,d=ray.ray.direction;let t=0,hit=null;
 for(let q=0;q<1500;q++){t+=q<200?3:8;const x=o.x+d.x*t,y=o.y+d.y*t,z=o.z+d.z*t;if(Math.abs(x)>440||Math.abs(z)>244)continue;if(y<=Math.max(hAt(x+400,z+225),0)){hit=[x,z];break}}
 if(!hit){ro.textContent='Move the cursor over the map for coordinates and elevation.';return}
 const px=hit[0]+400,py=hit[1]+225,h=hAt(px,py),m=Math.round((py-OY)/2)*MW+Math.round((px-OX)/2),b=bio[m]>=0?NAMES[LAND[bio[m]].k]:'Open sea';
 ro.textContent=`Grid ${'ABCDEFGH'[Math.max(0,Math.min(7,Math.floor(px/100)))]}${Math.max(1,Math.min(5,Math.floor(py/100)+1))} · ${(50-py*.045).toFixed(2)}°N ${(px*.05-5).toFixed(2)}°E · ${h<0?'Depth '+Math.round(-h*60)+' m':'Elevation '+Math.round(h*100).toLocaleString()+' m'} · ${b}`}
function setView(az,pol){const t=controls.target.clone(),dd=Math.max(150,camera.position.distanceTo(t)),a=az*Math.PI/180,p=pol*Math.PI/180;fly={t:0,from:t,to:t.clone(),cf:camera.position.clone(),ct:new THREE.Vector3(t.x+dd*Math.sin(p)*Math.sin(a),t.y+dd*Math.cos(p),t.z+dd*Math.sin(p)*Math.cos(a))}}
let hov=null,down=null,pk=0;
cv.addEventListener('pointermove',e=>{if(e.buttons)return;readout(e);const id=pick(e);if(id!==hov){if(hov&&mkr[hov])mkr[hov].scale.setScalar(1);hov=id;cv.style.cursor=id?'pointer':'grab';if(id){show(N[id]);if(mkr[id])mkr[id].scale.setScalar(1.5)}}});
cv.addEventListener('pointerdown',e=>down=[e.clientX,e.clientY]);
cv.addEventListener('pointerup',e=>{if(!down||Math.hypot(e.clientX-down[0],e.clientY-down[1])>5)return;const id=pick(e);if(id){(pk?B:A).value=id;pk^=1;show(N[id]);route()}});
// toolbar
const tg=(id,fn)=>{const b=document.getElementById(id);b.onclick=()=>{fn(b)}};
tg('bR',()=>{flyTo(HOME[1]);fly.ct=HOME[0].clone()});tg('bT',()=>{flyTo(TOP[1]);fly.ct=TOP[0].clone()});
tg('bL',b=>{labelsG.visible=!labelsG.visible;b.classList.toggle('on')});tg('bD',b=>{roadG.visible=!roadG.visible;b.classList.toggle('on')});
tg('bG',b=>{gridG.visible=!gridG.visible;b.classList.toggle('on')});tg('bK',b=>{cloudsG.visible=!cloudsG.visible;b.classList.toggle('on')});
tg('bC',b=>{b.classList.toggle('on');const ca=geo.attributes.color;ca.array.set(b.classList.contains('on')?COL2:COL);ca.needsUpdate=true});
tg('vN',()=>setView(180,60));tg('vE',()=>setView(90,60));tg('vS',()=>setView(0,60));tg('vW',()=>setView(270,60));tg('vU',()=>setView(20,150));
tg('bS',b=>{controls.autoRotate=!controls.autoRotate;controls.autoRotateSpeed=.6;b.classList.toggle('on')});
// route
function route(){
 const s=A.value,t=B.value,v=+AV.value,opt=OP.value,M=MD[MO.value];
 while(routeG.children.length)routeG.remove(routeG.children[0]);
 const ok=id=>id===s||id===t||N[id].city||!(v===2?['red','black'].includes(N[id].risk):v===1&&N[id].risk==='black');
 const w=(a,b)=>opt==='jumps'?1:opt==='silver'?ecost(a,b,M).total:1+ORD.indexOf(N[b].risk)*4;
 const D={[s]:0},prev={[s]:null},done=new Set();
 for(;;){let u=null;for(const k in D)if(!done.has(k)&&(u===null||D[k]<D[u]))u=k;if(u===null||u===t)break;done.add(u);
  adj[u].forEach(x=>{if(!ok(x))return;const nd=D[u]+w(u,x);if(!(x in D)||nd<D[x]){D[x]=nd;prev[x]=u}})}
 if(!(t in prev)){out.textContent='No route found with those restrictions.';return}
 const path=[];for(let u=t;u!==null;u=prev[u])path.unshift(u);
 let tot=0,tolls=0,ups=0,fees=0,sec=0;const rows=[];
 path.forEach((p,i)=>{let c=null;if(i){c=ecost(path[i-1],p,M);tot+=c.total;tolls+=c.toll;ups+=c.up;fees+=c.fee;sec+=c.sec}rows.push({p,c,cum:tot})});
 // 3D route
 const pts=[];path.forEach((p,i)=>{if(i){curve(path[i-1],p,1.6).getPoints(12).forEach(q=>pts.push(q))}});
 routeG.add(new THREE.Mesh(new THREE.TubeGeometry(new THREE.CatmullRomCurve3(pts),Math.max(20,pts.length*2),.9,6,false),new THREE.MeshStandardMaterial({color:0xfb923c,emissive:0xc2410c,emissiveIntensity:.9})));
 path.forEach((p,i)=>{const q=P3(N[p]),s2=label(String(i+1),96,'#ffb066',14,3.5);s2.position.set(q.x,q.y+(N[p].city?22:13),q.z);routeG.add(s2)});
 const mid=pts[Math.floor(pts.length/2)];flyTo(new THREE.Vector3(mid.x,0,mid.z));
 const top=path.reduce((m,p)=>Math.max(m,ORD.indexOf(N[p].risk)),0),regs=[...new Set(path.map(p=>N[p].reg))],
  res=[...new Set(path.flatMap(p=>N[p].res.split(', ').filter(r=>!/nearby|Market/.test(r))))],
  dz=path.filter(p=>N[p].dun.length),av=path.some((p,i)=>i&&ET[path[i-1]+'|'+p]==='avalon');
 out.innerHTML=`<div class="sum"><b>${path.length-1} jumps · ${fmt(tot)} · ${tm(sec)}</b> (${M.n})<br>${N[s].name} → ${N[t].name}<br>
 Breakdown: tolls ${fmt(tolls)}, mount/cargo upkeep ${fmt(ups)}, road & portal fees ${fmt(fees)}<br>
 Regions: ${regs.join(' → ')}<br>Highest risk: <b style="color:${top?C[ORD[top]]:'inherit'}">${ORD[top]}</b> – ${RISK[ORD[top]]}<br>
 Resources on the way: ${res.join(', ')||'none'}<br>Dungeon zones on route: ${dz.length}${av?'<br>Uses an Avalon road portal':''}</div><ol class="rl">`+
 rows.map(({p,c,cum},i)=>{const n=N[p],dd=dungeons(n);return `<li style="border-color:${n.risk==='black'?'#888':C[n.risk]}"><b>${i+1}. ${n.name}</b>
 <small>${n.reg} · ${n.risk} · ${n.tier}<br>${n.bio}<br>Resources: ${n.res}${c?`<br>This jump: ${fmt(c.total)} (toll ${fmt(c.toll)}${c.fee?', fee '+fmt(c.fee):''}) · running total ${fmt(cum)}`:'<br>Start of route'}
 ${dd.length?'<br>Dungeons: '+dd.map(d=>`${d.kind} (entry ${fmt(d.fee)}, loot ~${fmt(d.lo)}–${fmt(d.hi)})`).join('; '):''}
 ${i&&i<path.length-1&&ORD.indexOf(n.risk)>=2?'<br>⚠ '+RISK[n.risk]:''}</small></li>`}).join('')+'</ol>';
}
document.getElementById('go').onclick=route;[AV,MO,OP,A,B].forEach(e=>e.onchange=route);
// loop
function resize(){const w=stage.clientWidth,h=stage.clientHeight;renderer.setSize(w,h,false);camera.aspect=w/h;camera.updateProjectionMatrix()}
new ResizeObserver(resize).observe(stage);resize();
(function loop(){requestAnimationFrame(loop);
 if(fly){fly.t=Math.min(1,fly.t+.03);const e=fly.t*fly.t*(3-2*fly.t);controls.target.lerpVectors(fly.from,fly.to,e);camera.position.lerpVectors(fly.cf,fly.ct,e);if(fly.t>=1)fly=null}
 spin.forEach(m=>m.rotation.y+=.025);
 wt.offset.x+=.0003;wt.offset.y+=.0002;cloudsG.children.forEach(s=>{s.position.x+=.04;if(s.position.x>650)s.position.x=-650});
 controls.update();
 cpg.setAttribute('transform','rotate('+(controls.getAzimuthalAngle()*180/Math.PI)+')');
 const dist=camera.position.distanceTo(controls.target),ppu=stage.clientHeight/2/(Math.tan(camera.fov*Math.PI/360)*dist),km=[1,2,5,10,20,50,100,200,500].find(k=>k*2*ppu>=60)||500;
 sbl.style.width=km*2*ppu+'px';sbt.textContent=km+' km (approx.)';
 renderer.render(scene,camera)})();
route();
})()}catch(e){document.getElementById('stage').innerHTML='<div id="err">3D view could not start (WebGL is required): '+e.message+'</div>'}
</script></body></html>
