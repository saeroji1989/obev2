<!DOCTYPE html>
<html lang="id"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<title>SIMOBE – Monitoring Capaian OBE</title>
<link rel="manifest" href="data:application/json,%7B%22name%22%3A%22SIMOBE%22%2C%22short_name%22%3A%22SIMOBE%22%2C%22start_url%22%3A%22.%22%2C%22display%22%3A%22standalone%22%2C%22background_color%22%3A%22%23ffffff%22%2C%22theme_color%22%3A%22%231d4ed8%22%7D">
<style>
:root{--bg:#f6f8fc;--cd:rgba(255,255,255,.72);--tx:#0f172a;--mu:#64748b;--pr:#1d4ed8;--bd:rgba(148,163,184,.35);--ok:#16a34a;--wa:#d97706;--er:#dc2626;--in:#fff;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media(prefers-color-scheme:dark){:root:not([data-theme=light]){--bg:#0b1220;--cd:rgba(30,41,59,.7);--tx:#e2e8f0;--mu:#94a3b8;--pr:#60a5fa;--bd:rgba(148,163,184,.25);--in:#0f172a}}
:root[data-theme=dark]{--bg:#0b1220;--cd:rgba(30,41,59,.7);--tx:#e2e8f0;--mu:#94a3b8;--pr:#60a5fa;--bd:rgba(148,163,184,.25);--in:#0f172a}
*{box-sizing:border-box}html,body{height:100%;margin:0}html{scroll-padding-top:env(safe-area-inset-top,0px)}[hidden]{display:none!important}
body{font:14px/1.5 system-ui,'Inter',sans-serif;background:var(--bg);color:var(--tx)}
#app{position:fixed;inset:0;z-index:99999;overflow:auto;background:radial-gradient(circle at 10% 0,rgba(29,78,216,.14),transparent 40%),radial-gradient(circle at 90% 100%,rgba(14,165,233,.14),transparent 40%),var(--bg)}
.card{background:var(--cd);backdrop-filter:blur(14px);-webkit-backdrop-filter:blur(14px);border:1px solid var(--bd);border-radius:16px;padding:16px;margin-bottom:14px;box-shadow:0 6px 24px rgba(15,23,42,.06)}
#sb{position:fixed;left:0;top:0;bottom:0;width:220px;padding:18px 12px;overflow:auto;border-right:1px solid var(--bd);background:var(--cd);backdrop-filter:blur(14px);-webkit-backdrop-filter:blur(14px)}
#sb h1{font-size:19px;color:var(--pr);margin:0 8px 2px}
.nv{display:flex;gap:8px;align-items:center;padding:8px 10px;border-radius:10px;color:var(--tx);cursor:pointer;border:0;background:none;width:100%;font:inherit;text-align:left}
.nv.on{background:var(--pr);color:#fff}
#mn{margin-left:220px;padding:22px;max-width:1200px}#bn{display:none}
@media(max-width:800px){#sb{display:none}#mn{margin-left:0;padding:14px 12px 96px}
#bn{display:flex;position:fixed;left:10px;right:10px;bottom:calc(10px + env(safe-area-inset-bottom,0px));gap:4px;overflow-x:auto;padding:6px;border-radius:20px;background:var(--cd);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);border:1px solid var(--bd);box-shadow:0 8px 30px rgba(0,0,0,.18)}
#bn .nv{flex:0 0 auto;width:auto;flex-direction:column;font-size:10px;padding:6px 10px;gap:0}}
table{border-collapse:collapse;width:100%;font-size:13px}th,td{padding:8px 10px;border-bottom:1px solid var(--bd);text-align:left;white-space:nowrap}.ov{overflow-x:auto}
input,select,textarea{width:100%;padding:9px 11px;border:1px solid var(--bd);border-radius:10px;background:var(--in);color:var(--tx);font:inherit;margin:4px 0 8px}
.sc{width:78px;margin:0;padding:5px}label{font-size:12px;color:var(--mu)}
.b,.g{border:0;border-radius:10px;padding:8px 14px;font:inherit;cursor:pointer}.b{background:var(--pr);color:#fff}.g{background:transparent;border:1px solid var(--bd);color:var(--tx);margin-right:4px}.g.d{color:var(--er)}.b:disabled{opacity:.5}
.hd{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;margin-bottom:12px}h2,h3{margin:0 0 8px}.hd h2{margin:0}.ac{display:flex;gap:8px;flex-wrap:wrap;align-items:center}.ac select{width:auto;margin:0}
.st{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px;margin-bottom:14px}.st .card{margin:0}.g2{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:14px}
.r{display:grid;grid-template-columns:minmax(90px,1.3fr) 2fr 44px 76px;gap:8px;align-items:center;margin:7px 0;font-size:13px}.pb{height:8px;background:var(--bd);border-radius:9px;overflow:hidden}.pb i{display:block;height:100%}
.tg{padding:2px 8px;border-radius:99px;font-size:11px;text-align:center;color:#fff}.tg.ok{background:var(--ok)}.tg.wa{background:var(--wa)}.tg.er{background:var(--er)}.tg.mu{background:var(--mu)}b.ok{color:var(--ok)}b.er{color:var(--er)}
#mod{position:fixed;inset:0;background:rgba(15,23,42,.45);display:none;align-items:center;justify-content:center;z-index:100000;padding:14px}.mc{width:100%;max-width:460px;max-height:90%;overflow:auto;background:var(--bg)}
#toast{position:fixed;left:50%;top:20px;transform:translateX(-50%);background:var(--tx);color:var(--bg);padding:8px 16px;border-radius:99px;opacity:0;transition:.3s;z-index:100001;pointer-events:none}
#login{padding:14px}.lg{max-width:380px;margin:12vh auto 0}.lg h1{margin:0;color:var(--pr)}.mu{color:var(--mu)}.tabs{display:flex;gap:6px;margin:14px 0}.tabs button{flex:1;padding:8px;border:1px solid var(--bd);background:none;border-radius:10px;color:var(--tx);cursor:pointer}.tabs .on{background:var(--pr);color:#fff}
@media print{#sb,#bn,.ac{display:none!important}#mn{margin:0}}
</style></head>
<body>
<div id="app"><div id="login"></div><div id="shell" hidden><aside id="sb"></aside><main id="mn"></main><nav id="bn"></nav></div><div id="mod"></div><div id="toast"></div></div>
<script type="module">
// KONFIGURASI APLIKASI
const IS_PREVIEW = true; // Set false JIKA SUDAH TERHUBUNG KE FIREBASE
// PASTE FIREBASE CONFIG ANDA DI SINI
const firebaseConfig = {
  apiKey: "API_KEY_ANDA",
  authDomain: "PROJECT_ID.firebaseapp.com",
  projectId: "PROJECT_ID",
  storageBucket: "PROJECT_ID.appspot.com",
  messagingSenderId: "SENDER_ID",
  appId: "APP_ID"
};

const $=id=>document.getElementById(id);
const COLS=['settings','pl','cpl','plCpl','mk','cpmk','cpmkCpl','sub','ases','dosen','mhs','kelas','nilai','evaluasi'];
const D={};COLS.forEach(c=>D[c]=[]);
let fb=null,S=null,cur='dash',selK='',lapA='',role='admin',PEND=[],COMMIT=null;

// ===== PWA: Service Worker via Blob =====
try{if('serviceWorker' in navigator){const sw=URL.createObjectURL(new Blob([`self.addEventListener('install',e=>self.skipWaiting());self.addEventListener('activate',e=>e.waitUntil(clients.claim()));self.addEventListener('fetch',e=>{if(e.request.method!=='GET')return;e.respondWith(fetch(e.request).catch(()=>caches.match(e.request)))})`],{type:'text/javascript'}));navigator.serviceWorker.register(sw).catch(()=>{})}}catch(e){}

// ===== Lapisan Data =====
async function initFb(){const b='https://www.gstatic.com/firebasejs/10.12.2/';const [a,f,au]=await Promise.all([import(b+'firebase-app.js'),import(b+'firebase-firestore.js'),import(b+'firebase-auth.js')]);const app=a.initializeApp(firebaseConfig);fb={db:f.getFirestore(app),auth:au.getAuth(app),f,au}}
async function dbLoad(){if(IS_PREVIEW)return;for(const c of COLS){const s=await fb.f.getDocs(fb.f.collection(fb.db,c));D[c]=s.docs.map(d=>({id:d.id,...d.data()}))}}
async function dbSave(c,o){if(!o.id)o.id=c+Date.now().toString(36)+Math.random().toString(36).slice(2,6);const i=D[c].findIndex(x=>x.id==o.id);i<0?D[c].push(o):D[c][i]=o;if(!IS_PREVIEW){const {id,...r}=o;await fb.f.setDoc(fb.f.doc(fb.db,c,id),r)}return o}
async function dbDel(c,id){D[c]=D[c].filter(x=>x.id!=id);if(!IS_PREVIEW)await fb.f.deleteDoc(fb.f.doc(fb.db,c,id))}
const H=async s=>[...new Uint8Array(await crypto.subtle.digest('SHA-256',new TextEncoder().encode(s)))].map(x=>x.toString(16).padStart(2,'0')).join('');

// ===== Auto Setup Database (data dummy awal) =====
async function autoSetupDatabase(){
 if(D.settings.length)return;
 const Q=[],add=(c,o)=>Q.push(dbSave(c,o)),hp=await H('123456'),nm=['Algoritma dan Pemrograman','Basis Data','Rekayasa Perangkat Lunak'];
 ['Profesional TI|Merancang dan membangun sistem informasi','Peneliti dan Analis Data|Melakukan kajian ilmiah dan analisis data','Technopreneur|Menciptakan usaha berbasis teknologi'].forEach((t,i)=>{const[n,d]=t.split('|');add('pl',{id:'pl'+i,kode:'PL'+(i+1),nama:n,desk:d})});
 ['Sikap|Menjunjung etika profesi dan tanggung jawab','Pengetahuan|Menguasai konsep dasar komputasi dan data','Keterampilan Umum|Bekerja sama dan berkomunikasi dalam tim','Keterampilan Khusus|Membangun perangkat lunak berbasis basis data'].forEach((t,i)=>{const[k,d]=t.split('|');add('cpl',{id:'cpl'+i,kode:'CPL'+(i+1),kat:k,desk:d})});
 [[0,0],[0,1],[1,1],[1,3],[2,2],[2,3]].forEach(([a,b],i)=>add('plCpl',{id:'pc'+i,pl:'pl'+a,cpl:'cpl'+b,bobot:50}));
 let n=0;
 nm.forEach((k,m)=>{add('mk',{id:'mk'+m,kode:'IF10'+(m+1),nama:k,sks:3,smt:m+2});
  for(let c=0;c<2;c++){const ci='cm'+m+c;add('cpmk',{id:ci,kode:`CPMK${m+1}.${c+1}`,mk:'mk'+m,desk:`Mampu menerapkan materi ${c?'lanjutan':'dasar'} ${k}`});add('cpmkCpl',{id:'cc'+m+c,cpmk:ci,cpl:'cpl'+((m*2+c)%4),bobot:100});
   for(let s=0;s<2;s++){const si='sb'+m+c+s,sk=`S${m+1}.${c+1}.${s+1}`;add('sub',{id:si,kode:sk,cpmk:ci,desk:`Capaian ${s?'praktik':'konsep'} ${k}`,bobot:s?40:60});
    ['Tugas','Kuis'].forEach((j,q)=>{const ai='as'+m+c+s+q;add('ases',{id:ai,nama:j+' '+sk,jenis:j,sub:si,bobot:q?40:60});for(let i=0;i<10;i++)add('nilai',{id:'n_m'+i+'_'+ai,mhs:'m'+i,ases:ai,skor:55+(i*37+m*13+c*7+s*11+q*5+n)%41});n++})}}
  add('kelas',{id:'kl'+m,mk:'mk'+m,dosen:'d'+m,tahun:'2025/2026 Ganjil',peserta:[...Array(10)].map((_,i)=>'2023'+String(i+1).padStart(3,'0')).join(',')})});
 ['Ahmad Fauzi','Siti Aisyah','Budi Santoso','Dewi Lestari','Rizky Pratama','Nadia Putri','Fajar Nugroho','Intan Permata','Dimas Saputra','Rani Wulandari'].forEach((x,i)=>add('mhs',{id:'m'+i,nim:'2023'+String(i+1).padStart(3,'0'),nama:x,angkatan:2023+i%2,pw:hp,aktif:true}));
 ['Dr. Hendra Wijaya, M.Kom','Prof. Sari Utami, Ph.D','Dr. Agus Prasetyo, M.T'].forEach((x,i)=>add('dosen',{id:'d'+i,nidn:'0411000'+(i+1),nama:x,pw:hp,aktif:true}));
 await Promise.all(Q);
 await dbSave('settings',{id:'app',prodi:'S1 Teknologi Informasi',univ:'Universitas Contoh',tahun:'2025/2026',tercapai:70,cukup:56});
}

// ===== Mesin Perhitungan Capaian =====
const wa=a=>{let s=0,w=0;a.forEach(([v,b])=>{if(v!=null){s+=v*b;w+=b}});return w?s/w:null};
const avg=a=>{a=a.filter(v=>v!=null);return a.length?a.reduce((x,y)=>x+y,0)/a.length:null};
const NV=(m,a)=>{const n=D.nilai.find(x=>x.mhs==m&&x.ases==a);return n?+n.skor:null};
const cSub=(m,id)=>wa(D.ases.filter(a=>a.sub==id).map(a=>[NV(m,a.id),+a.bobot]));
const cCpmk=(m,id)=>wa(D.sub.filter(s=>s.cpmk==id).map(s=>[cSub(m,s.id),+s.bobot]));
const cCpl=(m,id)=>wa(D.cpmkCpl.filter(x=>x.cpl==id).map(x=>[cCpmk(m,x.cpmk),+x.bobot]));
const cPl=(m,id)=>wa(D.plCpl.filter(x=>x.pl==id).map(x=>[cCpl(m,x.cpl),+x.bobot]));
const CALC={sub:cSub,cpmk:cCpmk,cpl:cCpl,pl:cPl};
const V=(lv,ids,id)=>avg(ids.map(m=>CALC[lv](m,id)));
const f=v=>v==null?'–':v.toFixed(1);
const st=v=>{const s=D.settings[0];return v==null?['–','mu']:v>=+s.tercapai?['Tercapai','ok']:v>=+s.cukup?['Cukup','wa']:['Belum','er']};
const tag=v=>`<span class="tg ${st(v)[1]}">${f(v)}</span>`;
const bar=(l,v)=>`<div class=r><span>${l}</span><div class=pb><i style="width:${v||0}%;background:var(--${st(v)[1]})"></i></div><b>${f(v)}</b><span class="tg ${st(v)[1]}">${st(v)[0]}</span></div>`;
const capaian=(lv,ids)=>`<div class=card>${D[lv].map(o=>bar(o.kode+' '+(o.nama||(o.desk||'').slice(0,34)),V(lv,ids,o.id))).join('')}</div>`;
function radar(it){const n=it.length,c=110,R=82,p=(i,r)=>[c+r*Math.sin(2*Math.PI*i/n),c-r*Math.cos(2*Math.PI*i/n)];
 const g=[25,50,75,100].map(k=>`<polygon points="${it.map((_,i)=>p(i,R*k/100)).join(' ')}" fill="none" stroke="var(--bd)"/>`).join('');
 return `<svg viewBox="0 0 220 220" style="max-width:300px;width:100%">${g}<polygon points="${it.map((x,i)=>p(i,R*(x[1]||0)/100)).join(' ')}" fill="var(--pr)" fill-opacity=".25" stroke="var(--pr)" stroke-width="2"/>${it.map((x,i)=>{const[a,b]=p(i,R+14);return `<text x="${a}" y="${b}" font-size="9" text-anchor="middle" fill="var(--mu)">${x[0]}</text>`}).join('')}</svg>`}

// ===== Skema CRUD Generik =====
const SC={
 pl:{t:'Profil Lulusan',f:[['kode','Kode'],['nama','Nama'],['desk','Deskripsi','ta']]},
 cpl:{t:'Capaian Pembelajaran Lulusan (CPL)',f:[['kode','Kode'],['desk','Deskripsi','ta'],['kat','Kategori','sel:Sikap,Pengetahuan,Keterampilan Umum,Keterampilan Khusus']]},
 plCpl:{t:'Matriks PL ↔ CPL',f:[['pl','Profil Lulusan','ref:pl'],['cpl','CPL','ref:cpl'],['bobot','Bobot (%)','num']]},
 mk:{t:'Mata Kuliah',f:[['kode','Kode'],['nama','Nama'],['sks','SKS','num'],['smt','Semester','num']]},
 cpmk:{t:'CPMK',f:[['kode','Kode'],['mk','Mata Kuliah','ref:mk'],['desk','Deskripsi','ta']]},
 sub:{t:'Sub-CPMK',f:[['kode','Kode'],['cpmk','CPMK','ref:cpmk'],['desk','Deskripsi','ta'],['bobot','Bobot terhadap CPMK (%)','num']]},
 cpmkCpl:{t:'Matriks CPMK ↔ CPL',f:[['cpmk','CPMK','ref:cpmk'],['cpl','CPL','ref:cpl'],['bobot','Bobot (%)','num']]},
 ases:{t:'Komponen Asesmen',f:[['nama','Nama Komponen'],['jenis','Jenis','sel:Tugas,Kuis,UTS,UAS,Proyek,Praktikum'],['sub','Sub-CPMK','ref:sub'],['bobot','Bobot terhadap Sub-CPMK (%)','num']]},
 kelas:{t:'Kelas & Pengampu',f:[['mk','Mata Kuliah','ref:mk'],['dosen','Dosen Pengampu','ref:dosen'],['tahun','Tahun Akademik'],['peserta','Peserta (NIM dipisah koma)','ta']]},
 dosen:{t:'Data Dosen',f:[['nidn','NIDN'],['nama','Nama'],['pwd','Password (kosongkan jika tidak diubah)','pw']]},
 mhs:{t:'Data Mahasiswa',f:[['nim','NIM'],['nama','Nama'],['angkatan','Angkatan','num'],['pwd','Password (kosongkan jika tidak diubah)','pw']]},
 evaluasi:{t:'Evaluasi & Tindak Lanjut',f:[['tipe','Tipe','sel:CPMK,CPL'],['ref','Kode CPMK/CPL'],['catatan','Catatan Evaluasi','ta'],['tindak','Tindak Lanjut','ta']]}
};
const lab=(c,id)=>{const o=D[c].find(x=>x.id==id);return o?[o.kode||o.nidn,o.nama||(o.desk||'').slice(0,28)].filter(Boolean).join(' – '):'?'};
const cell=(fd,o)=>{const t=fd[2]||'',v=o[fd[0]];return t.startsWith('ref:')?lab(t.slice(4),v):t=='ta'?(v||'').slice(0,60):v??''};
const inp=(k,t='',v='')=>{
 if(t=='ta')return `<textarea id="f_${k}">${v}</textarea>`;
 if(t.startsWith('sel:'))return `<select id="f_${k}">${t.slice(4).split(',').map(x=>`<option ${x==v?'selected':''}>${x}</option>`).join('')}</select>`;
 if(t.startsWith('ref:')){const c=t.slice(4);return `<select id="f_${k}">${D[c].map(o=>`<option value="${o.id}" ${o.id==v?'selected':''}>${lab(c,o.id)}</option>`).join('')}</select>`}
 return `<input id="f_${k}" type="${t=='num'?'number':t=='pw'?'password':'text'}" value="${v}">`};
const CSVT={mhs:['nim,nama,angkatan,password','2024001,Budi Santoso,2024,123456'],dosen:['nidn,nama,password','0411999,Dr. Contoh Dosen,123456']};
const impBtn=c=>CSVT[c]?`<button class=g onclick="tpl('${c}')">Unduh Template CSV</button><button class=g onclick="impMaster('${c}')">Impor CSV</button>`:'';
function table(c){const s=SC[c],cols=s.f.filter(x=>x[2]!='pw');
 return `<div class=hd><h2>${s.t}</h2><div class=ac>${impBtn(c)}<button class=b onclick="edit('${c}')">+ Tambah</button></div></div><div class="card ov"><table><tr>${cols.map(x=>`<th>${x[1]}</th>`).join('')}<th></th></tr>${D[c].map(o=>`<tr>${cols.map(x=>`<td>${cell(x,o)}</td>`).join('')}<td><button class=g onclick="edit('${c}','${o.id}')">Ubah</button><button class="g d" onclick="del('${c}','${o.id}')">Hapus</button></td></tr>`).join('')}</table></div>`}
function modal(h){const m=$('mod');m.innerHTML='<div class="card mc">'+h+'</div>';m.style.display='flex'}
const closeM=()=>$('mod').style.display='none';
const toast=t=>{const e=$('toast');e.textContent=t;e.style.opacity=1;setTimeout(()=>e.style.opacity=0,2200)};
function edit(c,id){const s=SC[c],o=id?D[c].find(x=>x.id==id):{};modal(`<h3>${s.t}</h3>`+s.f.map(([k,l,t])=>`<label>${l}</label>${inp(k,t,o[k])}`).join('')+`<div class=ac><button class=g onclick="closeM()">Batal</button><button class=b onclick="saveF('${c}','${id||''}')">Simpan</button></div>`)}
async function saveF(c,id){const o=id?{...D[c].find(x=>x.id==id)}:{};
 for(const [k,,t] of SC[c].f){const v=$('f_'+k).value;if(t=='pw'){if(v)o.pw=await H(v)}else o[k]=t=='num'?+v:v}
 if(c=='mhs'||c=='dosen'){if(!o.pw)o.pw=await H('123456');o.aktif=true}
 await dbSave(c,o);closeM();toast('Data tersimpan');render()}
function del(c,id){modal(`<h3>Hapus data?</h3><p>Data yang dihapus tidak dapat dikembalikan.</p><div class=ac><button class=g onclick="closeM()">Batal</button><button class=b onclick="delOk('${c}','${id}')">Hapus</button></div>`)}
async function delOk(c,id){await dbDel(c,id);closeM();render()}

// ===== CSV: Template, Parse, Pratinjau, Impor =====
function dl(name,text){const a=document.createElement('a');a.href=URL.createObjectURL(new Blob(['\ufeff'+text],{type:'text/csv'}));a.download=name;a.click()}
function parse(t){t=t.replace(/^\ufeff/,'');const d=t.split('\n')[0].includes(';')?';':',';return t.split(/\r?\n/).filter(x=>x.trim()).map(r=>r.split(d).map(x=>x.trim().replace(/^"|"$/g,'')))}
function pickCsv(cb){const i=document.createElement('input');i.type='file';i.accept='.csv,text/csv';i.onchange=async()=>{if(i.files[0])cb(parse(await i.files[0].text()))};i.click()}
const tpl=c=>dl(`template_${c}.csv`,CSVT[c].join('\n'));
function showPrev(title,ok,er,commit){PEND=ok;COMMIT=commit;modal(`<h3>Pratinjau Impor ${title}</h3><p><b class=ok>${ok.length} baris valid</b> · <b class=er>${er.length} error</b></p>${er.slice(0,8).map(e=>`<div class="tg er" style="text-align:left;margin:3px 0">${e}</div>`).join('')}<br><div class=ac><button class=g onclick="closeM()">Batal</button><button class=b ${ok.length?'':'disabled'} onclick="commitP()">Simpan ${ok.length} data</button></div>`)}
async function commitP(){await COMMIT(PEND);closeM();toast('Impor selesai');render()}
function impMaster(c){pickCsv(async rows=>{const [h,...b]=rows,key=c=='mhs'?'nim':'nidn',ok=[],er=[];
 for(const [i,r] of b.entries()){const o=Object.fromEntries(h.map((x,j)=>[x.toLowerCase(),r[j]]));
  if(!o[key]||!o.nama){er.push(`Baris ${i+2}: ${key}/nama kosong`);continue}
  const ex=D[c].find(x=>x[key]==o[key]);
  ok.push({...(ex||{}),[key]:o[key],nama:o.nama,...(c=='mhs'?{angkatan:+o.angkatan||new Date().getFullYear()}:{}),pw:await H(o.password||'123456'),aktif:true})}
 showPrev(c=='mhs'?'Mahasiswa':'Dosen',ok,er,async a=>{for(const o of a)await dbSave(c,o)})})}

// ===== Dosen: kelas & nilai =====
const mine=()=>D.kelas.filter(k=>k.dosen==S.id);
const curK=()=>{const m=mine();return m.find(k=>k.id==selK)||m[0]};
const pes=k=>{const n=(k.peserta||'').split(/[,;\s]+/);return D.mhs.filter(m=>n.includes(m.nim))};
const asesOf=mk=>D.ases.filter(a=>{const s=D.sub.find(x=>x.id==a.sub),c=s&&D.cpmk.find(x=>x.id==s.cpmk);return c&&c.mk==mk});
const kSel=()=>`<select onchange="setK(this.value)">${mine().map(k=>`<option value="${k.id}" ${k==curK()?'selected':''}>${lab('mk',k.mk)} (${k.tahun})</option>`).join('')}</select>`;
const setK=v=>{selK=v;render()};
async function saveNilai(){const Q=[];document.querySelectorAll('.sc').forEach(i=>{if(i.value==='')return;Q.push(dbSave('nilai',{id:'n_'+i.dataset.m+'_'+i.dataset.a,mhs:i.dataset.m,ases:i.dataset.a,skor:Math.min(100,Math.max(0,+i.value))}))});await Promise.all(Q);toast(Q.length+' nilai tersimpan')}
function tplNilai(){const k=curK(),A=asesOf(k.mk);dl('template_nilai_'+lab('mk',k.mk).split(' ')[0]+'.csv',['nim','nama',...A.map(a=>a.nama)].join(',')+'\n'+pes(k).map(m=>[m.nim,m.nama,...A.map(()=>'')].join(',')).join('\n'))}
function impNilai(){const k=curK(),A=asesOf(k.mk),P=pes(k);pickCsv(rows=>{const [h,...b]=rows,ok=[],er=[];
 const col=A.map(a=>[a,h.findIndex(x=>x.toLowerCase()==a.nama.toLowerCase())]).filter(x=>x[1]>=0);
 b.forEach((r,i)=>{const m=P.find(x=>x.nim==r[0]);if(!m)return er.push(`Baris ${i+2}: NIM ${r[0]} tidak terdaftar di kelas`);
  col.forEach(([a,j])=>{if(r[j]===''||r[j]==null)return;const v=+r[j];if(isNaN(v)||v<0||v>100)return er.push(`Baris ${i+2}: skor ${a.nama} tidak valid (0–100)`);ok.push({id:'n_'+m.id+'_'+a.id,mhs:m.id,ases:a.id,skor:v})})});
 showPrev('Nilai',ok,er,async a=>{await Promise.all(a.map(o=>dbSave('nilai',o)))})})}
const kls=()=>`<div class="card ov"><table><tr><th>Mata Kuliah</th><th>Tahun</th><th>Peserta</th><th>Rata CPMK</th><th></th></tr>${mine().map(k=>{const P=pes(k);return `<tr><td>${lab('mk',k.mk)}</td><td>${k.tahun}</td><td>${P.length}</td><td>${tag(avg(D.cpmk.filter(c=>c.mk==k.mk).map(c=>V('cpmk',P.map(x=>x.id),c.id))))}</td><td><button class=g onclick="setK('${k.id}');go('nilai')">Input Nilai</button><button class=g onclick="setK('${k.id}');go('anal')">Analisis</button></td></tr>`}).join('')}</table></div>`;
const none='<div class=card>Belum ada kelas yang diampu.</div>';

// ===== Laporan =====
const setLapA=v=>{lapA=v;render()};
function lapData(){const ms=D.mhs.filter(m=>!lapA||m.angkatan==lapA),ids=ms.map(m=>m.id);
 return [['NIM','Nama','Angkatan',...D.cpl.map(c=>c.kode),...D.pl.map(p=>p.kode)],...ms.map(m=>[m.nim,m.nama,m.angkatan,...D.cpl.map(c=>f(cCpl(m.id,c.id))),...D.pl.map(p=>f(cPl(m.id,p.id)))]),['','Rata-rata','',...D.cpl.map(c=>f(V('cpl',ids,c.id))),...D.pl.map(p=>f(V('pl',ids,p.id)))]]}
const expLap=()=>dl('laporan_capaian.csv',lapData().map(r=>r.map(x=>`"${x}"`).join(',')).join('\n'));

// ===== Pengaturan & Password =====
async function saveSet(){const s={...D.settings[0]};['prodi','univ','tahun','tercapai','cukup'].forEach(k=>{const v=$('s_'+k).value;s[k]=['tercapai','cukup'].includes(k)?+v:v});await dbSave('settings',s);toast('Pengaturan tersimpan');render()}
async function chPw(){const v=$('np').value;if(v.length<6)return toast('Minimal 6 karakter');
 try{if(S.role=='admin'){if(!IS_PREVIEW)await fb.au.updatePassword(fb.auth.currentUser,v)}else{const c=S.role=='dosen'?'dosen':'mhs',o={...D[c].find(x=>x.id==S.id)};o.pw=await H(v);await dbSave(c,o)}toast('Password diperbarui')}catch(e){toast('Gagal. Login ulang lalu coba lagi')}}
const pwBox=`<div class=card><b>Ganti Password</b><input id=np type=password placeholder="Password baru (min. 6 karakter)"><button class=b onclick="chPw()">Ubah Password</button></div>`;
const prof=()=>`<h2>Profil</h2><div class=card><b>${S.nama}</b><br><span class=mu>Peran: ${S.role=='mhs'?'Mahasiswa':S.role=='dosen'?'Dosen':'Admin'}</span></div>`+pwBox;

// ===== Halaman =====
const ME=()=>[S.id];
const EX={evaluasi:()=>{const ids=D.mhs.map(m=>m.id),T=+D.settings[0].tercapai,l=[...D.cpl.map(c=>['cpl',c]),...D.cpmk.map(c=>['cpmk',c])].map(([t,c])=>[t,c,V(t,ids,c.id)]).filter(x=>x[2]!=null&&x[2]<T);return `<h3>Perlu Tindak Lanjut (di bawah ${T})</h3><div class=card>${l.length?l.map(([t,c,v])=>bar(t.toUpperCase()+' '+c.kode,v)).join(''):'Semua CPL dan CPMK mencapai ambang.'}</div>`}};
const PG={
admin:{
 dash:()=>{const ids=D.mhs.map(m=>m.id),T=+D.settings[0].tercapai,ok=D.cpl.filter(c=>V('cpl',ids,c.id)>=T).length,ang=[...new Set(D.mhs.map(m=>m.angkatan))].sort();
  const w=[...D.cpmk.filter(c=>D.sub.filter(s=>s.cpmk==c.id).reduce((a,s)=>a+ +s.bobot,0)!=100).map(c=>'Bobot Sub-CPMK pada '+c.kode+' belum 100%'),...D.sub.filter(s=>{const x=D.ases.filter(a=>a.sub==s.id);return x.length&&x.reduce((a,y)=>a+ +y.bobot,0)!=100}).map(s=>'Bobot asesmen pada '+s.kode+' belum 100%')];
  return `<div class=hd><h2>Dashboard Prodi</h2><span class=mu>${D.settings[0].prodi} · ${D.settings[0].tahun}</span></div><div class=st>${[['Mahasiswa',D.mhs.length],['Dosen',D.dosen.length],['Mata Kuliah',D.mk.length],['CPL Tercapai',ok+'/'+D.cpl.length]].map(([a,b])=>`<div class=card><small class=mu>${a}</small><h2>${b}</h2></div>`).join('')}</div>`+(w.length?`<div class=card style="border-color:var(--wa)"><b>⚠ Validasi bobot</b><br>${w.join('<br>')}</div>`:'')+`<div class=g2><div><h3>Profil Lulusan</h3>${capaian('pl',ids)}</div><div><h3>CPL</h3>${capaian('cpl',ids)}</div></div><h3>Rata-rata CPL per Angkatan</h3><div class=card>${ang.map(a=>bar('Angkatan '+a,avg(D.cpl.map(c=>V('cpl',D.mhs.filter(m=>m.angkatan==a).map(m=>m.id),c.id))))).join('')}</div>`},
 lap:()=>{const ang=[...new Set(D.mhs.map(m=>m.angkatan))].sort();return `<div class=hd><h2>Laporan Ketercapaian</h2><div class=ac><select onchange="setLapA(this.value)"><option value="">Semua angkatan</option>${ang.map(a=>`<option ${a==lapA?'selected':''}>${a}</option>`).join('')}</select><button class=g onclick="expLap()">Ekspor CSV</button><button class=b onclick="print()">Cetak / PDF</button></div></div><div class="card ov"><table>${lapData().map((r,i)=>'<tr>'+r.map(x=>i?`<td>${x}</td>`:`<th>${x}</th>`).join('')+'</tr>').join('')}</table></div>`},
 set:()=>{const s=D.settings[0];return `<h2>Pengaturan</h2><div class=card>${[['prodi','Program Studi'],['univ','Perguruan Tinggi'],['tahun','Tahun Akademik'],['tercapai','Ambang Tercapai (≥)'],['cukup','Ambang Cukup (≥)']].map(([k,l])=>`<label>${l}</label><input id="s_${k}" value="${s[k]}">`).join('')}<button class=b onclick="saveSet()">Simpan</button></div>`+pwBox}
},
dosen:{
 dash:()=>{const m=mine();return `<h2>Dashboard Dosen</h2><div class=st><div class=card><small class=mu>Kelas diampu</small><h2>${m.length}</h2></div><div class=card><small class=mu>Total mahasiswa</small><h2>${m.reduce((a,k)=>a+pes(k).length,0)}</h2></div></div>`+kls()},
 kls:()=>`<h2>Kelas Saya</h2>`+kls(),
 nilai:()=>{const k=curK();if(!k)return none;const A=asesOf(k.mk),P=pes(k);return `<div class=hd><h2>Input Nilai</h2><div class=ac>${kSel()}<button class=g onclick="tplNilai()">Unduh Template CSV</button><button class=g onclick="impNilai()">Impor CSV</button><button class=b onclick="saveNilai()">Simpan</button></div></div><div class="card ov"><table><tr><th>NIM</th><th>Nama</th>${A.map(a=>`<th>${a.nama}</th>`).join('')}</tr>${P.map(m=>`<tr><td>${m.nim}</td><td>${m.nama}</td>${A.map(a=>`<td><input class=sc type=number min=0 max=100 data-m="${m.id}" data-a="${a.id}" value="${NV(m.id,a.id)??''}"></td>`).join('')}</tr>`).join('')}</table></div>`},
 anal:()=>{const k=curK();if(!k)return none;const P=pes(k),ids=P.map(m=>m.id),C=D.cpmk.filter(c=>c.mk==k.mk);return `<div class=hd><h2>Analisis Ketercapaian Kelas</h2>${kSel()}</div><div class=g2><div class=card><h3>CPMK</h3>${C.map(c=>bar(c.kode,V('cpmk',ids,c.id))).join('')}</div><div class=card><h3>Sub-CPMK</h3>${C.flatMap(c=>D.sub.filter(s=>s.cpmk==c.id)).map(s=>bar(s.kode,V('sub',ids,s.id))).join('')}</div></div><div class="card ov"><table><tr><th>Mahasiswa</th>${C.map(c=>`<th>${c.kode}</th>`).join('')}</tr>${P.map(m=>`<tr><td>${m.nama}</td>${C.map(c=>`<td>${tag(cCpmk(m.id,c.id))}</td>`).join('')}</tr>`).join('')}</table></div>`},
 prof
},
mhs:{
 dash:()=>`<h2>Dashboard Capaian</h2><div class=g2><div class="card" style="text-align:center"><h3>Radar CPL</h3>${radar(D.cpl.map(c=>[c.kode,V('cpl',ME(),c.id)]))}</div><div><h3>Profil Lulusan</h3>${capaian('pl',ME())}</div></div>`,
 mcpl:()=>`<h2>Capaian CPL</h2>`+capaian('cpl',ME()),
 mcpmk:()=>`<h2>Capaian CPMK dan Sub-CPMK</h2>`+D.mk.map(k=>`<h3>${k.kode} – ${k.nama}</h3><div class=card>${D.cpmk.filter(c=>c.mk==k.id).map(c=>bar(c.kode,V('cpmk',ME(),c.id))+D.sub.filter(s=>s.cpmk==c.id).map(s=>bar('↳ '+s.kode,V('sub',ME(),s.id))).join('')).join('')}</div>`).join(''),
 mpl:()=>`<h2>Capaian Profil Lulusan</h2>`+capaian('pl',ME()),
 prof
}};
const NAV={
 admin:[['dash','Dashboard','📊'],['pl','Profil Lulusan','🎓'],['cpl','CPL','🎯'],['plCpl','PL↔CPL','🔗'],['mk','Mata Kuliah','📚'],['cpmk','CPMK','📝'],['sub','Sub-CPMK','🧩'],['cpmkCpl','CPMK↔CPL','🔗'],['ases','Asesmen','✅'],['kelas','Kelas','🏫'],['dosen','Dosen','👨‍🏫'],['mhs','Mahasiswa','👥'],['lap','Laporan','📄'],['evaluasi','Evaluasi','🔍'],['set','Pengaturan','⚙️']],
 dosen:[['dash','Dashboard','📊'],['kls','Kelas Saya','🏫'],['nilai','Input Nilai','✏️'],['anal','Analisis','📈'],['prof','Profil','👤']],
 mhs:[['dash','Dashboard','📊'],['mcpl','CPL','🎯'],['mcpmk','CPMK & Sub','🧩'],['mpl','Profil Lulusan','🎓'],['prof','Profil','👤']]};
const go=k=>{cur=k;render()};
function render(){
 const it=NAV[S.role].map(([k,l,i])=>`<button class="nv ${k==cur?'on':''}" onclick="go('${k}')"><span>${i}</span><span>${l}</span></button>`).join(''),out=`<button class=nv onclick="logout()"><span>⎋</span><span>Keluar</span></button>`;
 $('sb').innerHTML=`<h1>SIMOBE</h1><p class=mu style="margin:0 8px 12px;font-size:12px">${S.nama}</p>`+it+out;$('bn').innerHTML=it+out;
 $('mn').innerHTML=S.role=='admin'&&SC[cur]?table(cur)+(EX[cur]?EX[cur]():''):PG[S.role][cur]();
 $('app').scrollTop=0}

// ===== Login Hybrid =====
async function login(r,u,p){
 if(r=='admin'){if(IS_PREVIEW){if(u=='admin@prodi.ac.id'&&p=='admin123')return {role:'admin',nama:'Administrator'};throw 0}
  const x=await fb.au.signInWithEmailAndPassword(fb.auth,u,p);return {role:'admin',nama:x.user.email}}
 const c=r=='dosen'?'dosen':'mhs',k=r=='dosen'?'nidn':'nim',x=D[c].find(o=>o[k]==u&&o.aktif!==false);
 if(x&&x.pw==await H(p))return {role:r,id:x.id,nama:x.nama};throw 0}
function loginUI(){$('login').innerHTML=`<div class="card lg"><h1>SIMOBE</h1><p class=mu>Monitoring Capaian Profil Lulusan, CPL, CPMK dan Sub-CPMK</p><div class=tabs>${[['admin','Admin'],['dosen','Dosen'],['mhs','Mahasiswa']].map(([k,l])=>`<button class="${k==role?'on':''}" onclick="setRole('${k}')">${l}</button>`).join('')}</div><input id=lu placeholder="${role=='admin'?'Email':role=='dosen'?'NIDN':'NIM'}" autocomplete="username"><input id=lp type=password placeholder="Password" autocomplete="current-password" onkeydown="if(event.key=='Enter')doLogin()"><div id=le class="mu" style="color:var(--er);min-height:20px"></div><button id=lb class=b style="width:100%" onclick="doLogin()">Masuk</button></div>`}
const setRole=r=>{role=r;loginUI()};
async function doLogin(){const b=$('lb');b.disabled=true;try{if(!D.settings.length)throw 1;S=await login(role,$('lu').value.trim(),$('lp').value);cur='dash';$('login').hidden=true;$('shell').hidden=false;render()}catch(e){$('le').textContent='Login gagal. Periksa kembali data Anda.'}b.disabled=false}
async function logout(){try{if(!IS_PREVIEW&&S.role=='admin')await fb.au.signOut(fb.auth)}catch(e){}S=null;$('shell').hidden=true;$('login').hidden=false;loginUI()}

Object.assign(window,{go,edit,del,delOk,closeM,saveF,commitP,setRole,doLogin,logout,setK,setLapA,expLap,saveSet,chPw,saveNilai,tplNilai,impNilai,impMaster,tpl});
(async()=>{loginUI();try{if(!IS_PREVIEW)await initFb();await dbLoad();await autoSetupDatabase()}catch(e){$('le').textContent='Gagal menyiapkan database: '+e.message}})();
</script>
</body></html>
