<script setup>
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

// --- DATA LAYANAN ---
const services = [
  { 
    num: '01', title: 'Website Bisnis', tag: 'Company Profile', color: 'blue',
    items: ['Company profile', 'Landing page promosi', 'Website portofolio', 'Website layanan profesional'] 
  },
  { 
    num: '02', title: 'Sistem Informasi', tag: 'Manajemen Data', color: 'green',
    items: ['Dashboard admin', 'Sistem manajemen pelanggan (CRM)', 'Sistem inventaris dan stok', 'Sistem manajemen karyawan', 'Sistem registrasi dan keanggotaan', 'Sistem laporan dan analitik'] 
  },
  { 
    num: '03', title: 'E-commerce & Transaksi', tag: 'Penjualan Online', color: 'orange',
    items: ['Toko online', 'Katalog produk', 'Sistem pemesanan dan reservasi', 'Sistem kasir dan transaksi', 'Manajemen pesanan dan pembayaran'] 
  },
  { 
    num: '04', title: 'Aplikasi Interaktif', tag: 'Realtime & Chat', color: 'purple',
    items: ['Aplikasi chat realtime', 'Notifikasi realtime', 'Platform komunitas dan media sosial', 'Aplikasi kolaborasi dan manajemen proyek', 'Sistem tiket bantuan pelanggan'] 
  },
  { 
    num: '05', title: 'Backend & Integrasi', tag: 'API & Server', color: 'cyan',
    items: ['REST API', 'Backend aplikasi web', 'Integrasi layanan pihak ketiga', 'Sistem autentikasi dan hak akses', 'Backend berbasis microservices'] 
  },
  { 
    num: '06', title: 'Aplikasi Kustom', tag: 'Solusi Khusus', color: 'rose',
    items: ['Sistem operasional bisnis', 'Aplikasi SaaS berbasis langganan', 'Sistem manajemen dokumen', 'Aplikasi berbasis database', 'Sistem otomatisasi alur kerja'] 
  },
]

// --- DATA ALUR KERJA ---
const workflowSteps = [
  { num: '01', title: 'Konsultasi Kebutuhan', desc: 'Diskusi tentang ide, tujuan bisnis, fitur, anggaran, dan target penyelesaian.', icon: '💬' },
  { num: '02', title: 'Perencanaan & Penawaran', desc: 'Menentukan ruang lingkup pekerjaan, estimasi biaya, jadwal, dan hasil yang akan diberikan.', icon: '📝' },
  { num: '03', title: 'Pengembangan Aplikasi', desc: 'Membangun tampilan, backend, database, dan fitur sesuai kesepakatan.', icon: '' },
  { num: '04', title: 'Pengujian & Revisi', desc: 'Memeriksa fungsi aplikasi dan melakukan revisi sesuai kebutuhan dan kesepakatan.', icon: '✅' },
  { num: '05', title: 'Deployment & Serah Terima', desc: 'Memasang aplikasi ke hosting/server, menyerahkan hasil proyek, dan memberikan panduan penggunaan.', icon: '' },
]

// --- DATA PEMBAYARAN ---
const paymentSteps = [
  { num: '1', title: 'DP Sebelum Pengerjaan', desc: 'Sebagai tanda jadi setelah kesepakatan proyek.', percent: '± 30%', progress: 'w-[30%]' },
  { num: '2', title: 'Pembayaran Bertahap (Saat Progres)', desc: 'Dibayarkan sesuai tahapan pengembangan yang disepakati.', percent: '± 40%', progress: 'w-[70%]' },
  { num: '3', title: 'Pelunasan Sebelum Serah Terima', desc: 'Setelah hasil diuji dan disetujui sebelum proyek selesai.', percent: '± 30%', progress: 'w-full' },
]

// --- DATA INFRASTRUKTUR ---
const infraCategories = [
  {
    title: 'Shared Hosting',
    desc: 'Cocok untuk website company profile, landing page, blog, dan aplikasi PHP/Laravel yang sesuai dengan spesifikasi hosting.',
    color: 'blue',
    providers: [
      { name: 'Hostinger', url: 'www.hostinger.co.id' },
      { name: 'Niagahoster', url: 'www.niagahoster.co.id' },
      { name: 'Qwords', url: 'www.qwords.com' }
    ]
  },
  {
    title: 'VPS & Cloud Server',
    desc: 'Memberikan kontrol lebih besar untuk menjalankan aplikasi, mengatur lingkungan server, dan memasang teknologi yang dibutuhkan.',
    color: 'green',
    providers: [
      { name: 'DigitalOcean', url: 'www.digitalocean.com' },
      { name: 'Biznet Gio', url: 'www.biznetgio.com' },
      { name: 'Vultr', url: 'www.vultr.com' }
    ]
  },
  {
    title: 'PaaS (Platform as a Service)',
    desc: 'Memudahkan deployment aplikasi tanpa harus mengelola seluruh konfigurasi server secara manual.',
    color: 'purple',
    providers: [
      { name: 'Vercel', url: 'www.vercel.com' },
      { name: 'Railway', url: 'www.railway.com' },
      { name: 'Render', url: 'www.render.com' }
    ],
    note: 'Dukungan teknologi, database, dan fitur setiap platform bergantung pada layanan serta paket yang dipilih.'
  }
]

const thirdPartyServices = [
  { name: 'Midtrans', url: 'www.midtrans.com', type: 'Pembayaran digital' },
  { name: 'Xendit', url: 'www.xendit.co', type: 'Pembayaran digital' },
  { name: 'Cloudinary', url: 'www.cloudinary.com', type: 'Penyimpanan file & media' },
  { name: 'Amazon S3', url: 'aws.amazon.com/s3', type: 'Penyimpanan file & media' },
  { name: 'Resend', url: 'www.resend.com', type: 'Email transaksional' },
  { name: 'Google Maps Platform', url: 'mapsplatform.google.com', type: 'Peta dan lokasi' },
]

// --- TECH STACK LENGKAP ---
const techStackItems = [
  { name: 'HTML5', cat: 'Frontend', color: 'text-orange-600 bg-orange-50 border-orange-200' },
  { name: 'CSS3', cat: 'Frontend', color: 'text-blue-600 bg-blue-50 border-blue-200' },
  { name: 'JavaScript', cat: 'Frontend', color: 'text-yellow-600 bg-yellow-50 border-yellow-200' },
  { name: 'TypeScript', cat: 'Frontend', color: 'text-blue-800 bg-blue-100 border-blue-300' },
  { name: 'Bootstrap', cat: 'Frontend', color: 'text-purple-600 bg-purple-50 border-purple-200' },
  { name: 'Tailwind CSS', cat: 'Frontend', color: 'text-cyan-600 bg-cyan-50 border-cyan-200' },
  { name: 'React.js', cat: 'Frontend', color: 'text-sky-600 bg-sky-50 border-sky-200' },
  { name: 'Next.js', cat: 'Frontend', color: 'text-slate-900 bg-slate-100 border-slate-300' },
  { name: 'Vue.js', cat: 'Frontend', color: 'text-green-600 bg-green-50 border-green-200' },
  { name: 'Express.js', cat: 'Backend', color: 'text-gray-800 bg-gray-100 border-gray-300' },
  { name: 'Laravel', cat: 'Backend', color: 'text-red-600 bg-red-50 border-red-200' },
  { name: 'MySQL', cat: 'Database', color: 'text-blue-700 bg-blue-50 border-blue-200' },
  { name: 'PostgreSQL', cat: 'Database', color: 'text-indigo-700 bg-indigo-50 border-indigo-200' },
  { name: 'MongoDB', cat: 'Database', color: 'text-green-700 bg-green-50 border-green-200' },
  { name: 'Redis', cat: 'Database', color: 'text-red-700 bg-red-50 border-red-200' },
  { name: 'Docker', cat: 'DevOps', color: 'text-blue-600 bg-blue-50 border-blue-200' },
  { name: 'Git', cat: 'DevOps', color: 'text-orange-700 bg-orange-50 border-orange-200' },
]

const contactLinks = [
  { label: 'Instagram Bisnis', value: '@nexudid', url: 'https://instagram.com/nexudid' },
  { label: 'WhatsApp Bisnis', value: '082157303890', url: 'https://wa.me/6282157303890' },
  { label: 'LinkedIn', value: 'ria_rh', url: 'https://linkedin.com/in/ria_rh' },
  { label: 'GitHub', value: 'Nrarhmd', url: 'https://github.com/Nrarhmd' },
  { label: 'YouTube', value: 'nexud.id', url: 'https://youtube.com/@nexud.id' },
]

const getColorClasses = (color) => {
  const map = {
    blue: { bg: 'bg-blue-50', border: 'border-blue-100', text: 'text-blue-600', iconBg: 'bg-blue-100' },
    green: { bg: 'bg-green-50', border: 'border-green-100', text: 'text-green-600', iconBg: 'bg-green-100' },
    orange: { bg: 'bg-orange-50', border: 'border-orange-100', text: 'text-orange-600', iconBg: 'bg-orange-100' },
    purple: { bg: 'bg-purple-50', border: 'border-purple-100', text: 'text-purple-600', iconBg: 'bg-purple-100' },
    cyan: { bg: 'bg-cyan-50', border: 'border-cyan-100', text: 'text-cyan-600', iconBg: 'bg-cyan-100' },
    rose: { bg: 'bg-rose-50', border: 'border-rose-100', text: 'text-rose-600', iconBg: 'bg-rose-100' },
  }
  return map[color] || map.blue
}
</script>

<template>
  <div class="min-h-screen bg-white text-slate-800 font-sans selection:bg-primary-200">
    
    <!-- NAVBAR -->
    <nav class="sticky top-0 z-50 bg-white/90 backdrop-blur-md border-b border-slate-100">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex items-center justify-between h-16">
        <a href="#" class="flex items-center gap-2 group">
          <span class="text-2xl font-black text-primary-600 group-hover:scale-110 transition-transform">N</span>
          <span class="text-xl font-bold text-slate-900 tracking-tight">nexud<span class="text-primary-600">.tech</span></span>
        </a>

        <div class="hidden md:flex items-center gap-8 text-sm font-medium text-slate-600">
          <a href="#layanan" class="hover:text-primary-600 transition-colors">Layanan</a>
          <a href="#teknologi" class="hover:text-primary-600 transition-colors">Teknologi</a>
          <a href="#alur" class="hover:text-primary-600 transition-colors">Alur Kerja</a>
          <a href="#konsultasi" class="hover:text-primary-600 transition-colors">Kenapa Konsul?</a>
          
          <!-- TAMBAHAN: Link Portofolio Pribadi di Navbar -->
          <a href="https://portnexd.vercel.app" target="_blank" rel="noopener noreferrer" class="hover:text-primary-600 transition-colors flex items-center gap-1">
            Portofolio <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/></svg>
          </a>
          
          <a href="#kontak" class="bg-primary-600 text-white px-5 py-2.5 rounded-full hover:bg-primary-700 hover:shadow-lg hover:shadow-primary-200 transition-all">
            Konsultasi
          </a>
        </div>

        <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden p-2 rounded-lg hover:bg-slate-100 text-slate-600 transition">
          <svg v-if="!mobileMenuOpen" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/></svg>
          <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/></svg>
        </button>
      </div>

      <Transition enter-active-class="transition ease-out duration-200" enter-from-class="opacity-0 -translate-y-2" enter-to-class="opacity-100 translate-y-0">
        <div v-if="mobileMenuOpen" class="md:hidden border-t border-slate-100 bg-white px-4 py-4 space-y-3 shadow-xl">
          <!-- TAMBAHAN: Link Portofolio di Mobile Menu -->
          <a v-for="link in ['Layanan', 'Teknologi', 'Alur Kerja', 'Kenapa Konsul?', 'Portofolio', 'Kontak']" :key="link" 
             :href="link === 'Portofolio' ? 'https://portnexd.vercel.app' : '#' + link.toLowerCase().replace(/[? ]/g, '-')" 
             :target="link === 'Portofolio' ? '_blank' : undefined"
             @click="mobileMenuOpen = false"
             class="block text-sm font-medium text-slate-600 hover:text-primary-600 py-2">
            {{ link }}
          </a>
        </div>
      </Transition>
    </nav>

    <!-- HERO SECTION (CLEAN & MINIMALIST - NO MOCKUP) -->
    <section class="relative overflow-hidden pt-32 pb-32 lg:pt-48 lg:pb-48 bg-gradient-to-b from-primary-50/50 to-white">
      <!-- Subtle Background Glow -->
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-[800px] h-[800px] bg-primary-100/30 rounded-full blur-3xl pointer-events-none"></div>
      
      <div class="relative max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-primary-100/50 border border-primary-200 text-primary-700 text-xs font-bold uppercase tracking-wider mb-8 animate-fade-in-up">
          Digital Solutions for Business 
        </div>
        
        <h1 class="text-5xl sm:text-6xl lg:text-7xl font-black text-slate-900 leading-[1.1] mb-8 tracking-tight animate-fade-in-up" style="animation-delay: 0.1s;">
          Bisnis Anda Membutuhkan <br />
          <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary-600 to-accent-600">Solusi Digital?</span>
        </h1>
        
        <p class="text-lg sm:text-xl text-slate-600 mb-12 leading-relaxed max-w-2xl mx-auto animate-fade-in-up" style="animation-delay: 0.2s;">
          Di era digital, bisnis tidak cukup hanya mengandalkan promosi. Website dan aplikasi web dapat membantu bisnis menjangkau pelanggan, mengelola operasional, mengotomatisasi pekerjaan, dan mengembangkan layanan.
        </p>
        
        <div class="flex flex-wrap justify-center gap-4 animate-fade-in-up" style="animation-delay: 0.3s;">
          <a href="https://wa.me/6282157303890" target="_blank" class="inline-flex items-center gap-2 bg-green-600 text-white px-8 py-4 rounded-full font-bold text-base hover:bg-green-700 hover:shadow-xl hover:shadow-green-200 hover:-translate-y-1 transition-all duration-300">
            Konsultasi via WhatsApp
          </a>
          <a href="#layanan" class="inline-flex items-center gap-2 border-2 border-slate-200 text-slate-700 px-8 py-4 rounded-full font-bold text-base hover:border-primary-600 hover:text-primary-600 hover:bg-primary-50 transition-all duration-300">
            Jelajahi Layanan
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/></svg>
          </a>
        </div>
      </div>
    </section>

    <!-- KENAPA BUTUH WEBSITE -->
    <section class="py-20 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center gap-3 mb-12">
          <div class="w-12 h-12 bg-yellow-100 rounded-xl flex items-center justify-center text-2xl">💡</div>
          <h2 class="text-2xl lg:text-3xl font-black text-slate-900">KENAPA BISNIS ANDA MEMBUTUHKAN <span class="text-primary-600">WEBSITE?</span></h2>
        </div>

        <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="group">
            <div class="w-14 h-14 bg-primary-50 rounded-2xl flex items-center justify-center text-primary-600 mb-4 group-hover:bg-primary-600 group-hover:text-white transition-colors duration-300">
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">1. Meningkatkan Kredibilitas Bisnis</h3>
            <p class="text-sm text-slate-600">Tampilkan profil perusahaan, produk, layanan, portofolio, dan informasi kontak secara profesional.</p>
          </div>
          <div class="group">
            <div class="w-14 h-14 bg-accent-50 rounded-2xl flex items-center justify-center text-accent-600 mb-4 group-hover:bg-accent-600 group-hover:text-white transition-colors duration-300">
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">2. Menjangkau Lebih Banyak Pelanggan</h3>
            <p class="text-sm text-slate-600">Bantu calon pelanggan menemukan informasi bisnis Anda secara online kapan saja.</p>
          </div>
          <div class="group">
            <div class="w-14 h-14 bg-purple-50 rounded-2xl flex items-center justify-center text-purple-600 mb-4 group-hover:bg-purple-600 group-hover:text-white transition-colors duration-300">
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.066 2.573c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.573 1.066c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.066-2.573c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"/><circle cx="12" cy="12" r="3"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">3. Mengurangi Pekerjaan Manual</h3>
            <p class="text-sm text-slate-600">Otomatisasi pencatatan data, pendaftaran, pemesanan, inventaris, dan laporan melalui sistem terintegrasi.</p>
          </div>
          <div class="group">
            <div class="w-14 h-14 bg-green-50 rounded-2xl flex items-center justify-center text-green-600 mb-4 group-hover:bg-green-600 group-hover:text-white transition-colors duration-300">
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">4. Mempermudah Pengelolaan Bisnis</h3>
            <p class="text-sm text-slate-600">Pantau pelanggan, stok, transaksi, dan aktivitas operasional melalui dashboard.</p>
          </div>
          <div class="group">
            <div class="w-14 h-14 bg-orange-50 rounded-2xl flex items-center justify-center text-orange-600 mb-4 group-hover:bg-orange-600 group-hover:text-white transition-colors duration-300">
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">5. Memperluas Penjualan</h3>
            <p class="text-sm text-slate-600">Hadirkan katalog produk, toko online, pemesanan, checkout, dan pengelolaan pesanan.</p>
          </div>
          <div class="group">
            <div class="w-14 h-14 bg-cyan-50 rounded-2xl flex items-center justify-center text-cyan-600 mb-4 group-hover:bg-cyan-600 group-hover:text-white transition-colors duration-300">
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">6. Meningkatkan Pelayanan Pelanggan</h3>
            <p class="text-sm text-slate-600">Sediakan formulir kontak, sistem tiket bantuan, chat realtime, dan notifikasi sesuai kebutuhan.</p>
          </div>
          <div class="group sm:col-span-2 lg:col-span-2">
            <div class="w-14 h-14 bg-rose-50 rounded-2xl flex items-center justify-center text-rose-600 mb-4 group-hover:bg-rose-600 group-hover:text-white transition-colors duration-300">
              <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">7. Mengintegrasikan Sistem Bisnis</h3>
            <p class="text-sm text-slate-600">Hubungkan aplikasi dengan database, REST API, layanan pembayaran, dan layanan pihak ketiga.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- LAYANAN GRID -->
    <section id="layanan" class="py-24 bg-slate-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-3xl mx-auto mb-16">
          <span class="inline-block bg-primary-100 text-primary-700 text-xs font-bold uppercase tracking-widest px-4 py-1.5 rounded-full mb-4">Layanan Kami</span>
          <h2 class="text-3xl lg:text-4xl font-black text-slate-900 mb-4">Website & Aplikasi yang Bisa Dikembangkan</h2>
        </div>

        <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
          <div v-for="service in services" :key="service.num" 
               :class="[getColorClasses(service.color).bg, getColorClasses(service.color).border, 'rounded-2xl p-6 border transition-all duration-300 hover:shadow-lg hover:-translate-y-1']">
            <div class="flex items-center gap-3 mb-6">
              <div :class="[getColorClasses(service.color).iconBg, 'w-12 h-12 rounded-xl flex items-center justify-center text-xl']">
                <span v-if="service.num === '01'">🌐</span>
                <span v-else-if="service.num === '02'">🗄️</span>
                <span v-else-if="service.num === '03'">🛒</span>
                <span v-else-if="service.num === '04'"></span>
                <span v-else-if="service.num === '05'">&lt;/&gt;</span>
                <span v-else>⚙️</span>
              </div>
              <div>
                <span :class="['text-[10px] font-bold px-2 py-0.5 rounded-full bg-white/60', getColorClasses(service.color).text]">{{ service.num }}</span>
                <h3 :class="['text-lg font-bold mt-1', getColorClasses(service.color).text]">{{ service.title }}</h3>
              </div>
            </div>
            
            <ul class="space-y-2">
              <li v-for="item in service.items" :key="item" class="flex items-start gap-2 text-sm text-slate-700">
                <svg class="w-4 h-4 mt-0.5 shrink-0 opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/></svg>
                {{ item }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- TEKNOLOGI & INFRASTRUKTUR -->
    <section id="teknologi" class="py-24 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-3xl mx-auto mb-16">
          <span class="inline-block bg-slate-100 text-slate-700 text-xs font-bold uppercase tracking-widest px-4 py-1.5 rounded-full mb-4">Infrastructure & Stack</span>
          <h2 class="text-3xl lg:text-4xl font-black text-slate-900 mb-4">Teknologi & Layanan untuk Solusi Digital Anda</h2>
          <p class="text-slate-600 text-lg">Kami menggunakan teknologi terbaik dan layanan terpercaya untuk membantu bisnis Anda membangun website dan aplikasi web yang stabil, aman, dan siap berkembang.</p>
        </div>

        <!-- Tech Stack Grid -->
        <div class="mb-16">
          <h3 class="text-xl font-bold text-slate-900 mb-6 flex items-center gap-2">
            <svg class="w-6 h-6 text-primary-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.384-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"/></svg>
            Technology Stack Modern
          </h3>
          <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6 gap-4">
            <div v-for="tech in techStackItems" :key="tech.name" 
                 :class="[tech.color, 'border rounded-xl p-4 flex flex-col items-center justify-center gap-2 hover:shadow-md hover:scale-105 transition-all duration-300 cursor-default']">
              <span class="text-lg font-bold">{{ tech.name }}</span>
              <span class="text-[10px] uppercase tracking-wider opacity-70">{{ tech.cat }}</span>
            </div>
          </div>
        </div>

        <!-- Hosting Categories -->
        <div class="grid lg:grid-cols-3 gap-6 mb-12">
          <div v-for="cat in infraCategories" :key="cat.title" 
               :class="[getColorClasses(cat.color).bg, 'rounded-2xl p-6 border', getColorClasses(cat.color).border]">
            <div class="flex items-center gap-3 mb-4">
              <div :class="[getColorClasses(cat.color).iconBg, 'w-10 h-10 rounded-xl flex items-center justify-center']">
                <svg v-if="cat.title.includes('Shared')" class="w-6 h-6" :class="getColorClasses(cat.color).text" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2"/></svg>
                <svg v-else-if="cat.title.includes('VPS')" class="w-6 h-6" :class="getColorClasses(cat.color).text" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 15a4 4 0 004 4h9a5 5 0 10-.1-9.999 5.002 5.002 0 10-9.78 2.096A4.001 4.001 0 003 15z"/></svg>
                <svg v-else class="w-6 h-6" :class="getColorClasses(cat.color).text" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16a4 4 0 01-.88-7.903A5 5 0 1115.9 6L16 6a5 5 0 011 9.9M15 13l-3-3m0 0l-3 3m3-3v12"/></svg>
              </div>
              <h3 class="text-xl font-bold text-slate-900">{{ cat.title }}</h3>
            </div>
            <p class="text-sm text-slate-600 mb-6 min-h-[60px]">{{ cat.desc }}</p>
            
            <div class="grid grid-cols-3 gap-3">
              <div v-for="prov in cat.providers" :key="prov.name" class="bg-white rounded-xl p-3 border border-slate-100 text-center hover:shadow-md transition">
                <div class="h-8 flex items-center justify-center font-bold text-slate-800 text-xs mb-1">{{ prov.name }}</div>
                <a :href="'https://' + prov.url" target="_blank" class="text-[10px] text-primary-600 hover:underline truncate block">{{ prov.url }}</a>
              </div>
            </div>
            <p v-if="cat.note" class="text-[10px] text-slate-500 mt-4 italic">{{ cat.note }}</p>
          </div>
        </div>

        <!-- Third Party & Tools -->
        <div class="grid md:grid-cols-2 gap-8">
          <!-- Third Party -->
          <div class="bg-slate-50 rounded-2xl p-8 border border-slate-200">
            <div class="flex items-center gap-3 mb-6">
              <div class="w-10 h-10 bg-blue-100 rounded-xl flex items-center justify-center text-blue-600">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1"/></svg>
              </div>
              <div>
                <h3 class="text-xl font-bold text-slate-900">Layanan Pihak Ketiga</h3>
                <p class="text-xs text-slate-500">Third-Party Services Integration</p>
              </div>
            </div>
            <p class="text-sm text-slate-600 mb-6">Menambahkan fitur tertentu ke dalam aplikasi tanpa harus membangun semuanya dari awal.</p>
            
            <div class="grid grid-cols-2 sm:grid-cols-3 gap-4 mb-6">
              <div v-for="svc in thirdPartyServices" :key="svc.name" class="bg-white rounded-xl p-3 border border-slate-200 text-center hover:border-blue-300 transition">
                <div class="font-bold text-slate-800 text-sm mb-1">{{ svc.name }}</div>
                <div class="text-[10px] text-slate-500 truncate">{{ svc.url }}</div>
              </div>
            </div>
            
            <div class="bg-blue-50 rounded-xl p-4 border border-blue-100">
              <ul class="space-y-2">
                <li v-for="svc in thirdPartyServices" :key="svc.type" class="flex items-center gap-2 text-xs text-blue-800 font-medium">
                  <svg class="w-4 h-4 text-blue-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/></svg>
                  {{ svc.type }}
                </li>
              </ul>
            </div>
          </div>

          <!-- Dev Tools -->
          <div class="bg-slate-50 rounded-2xl p-8 border border-slate-200">
            <div class="flex items-center gap-3 mb-6">
              <div class="w-10 h-10 bg-cyan-100 rounded-xl flex items-center justify-center text-cyan-600">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"/></svg>
              </div>
              <div>
                <h3 class="text-xl font-bold text-slate-900">Tools Pengembangan</h3>
                <p class="text-xs text-slate-500">Development & Deployment</p>
              </div>
            </div>
            <p class="text-sm text-slate-600 mb-6">Membantu proses pengembangan, kolaborasi, dan deployment agar lebih mudah dan terstruktur.</p>
            
            <div class="grid grid-cols-3 gap-4 mb-8">
              <div v-for="tool in [{name:'Git',url:'git-scm.com'},{name:'GitHub',url:'github.com'},{name:'Docker',url:'docker.com'}]" :key="tool.name" class="bg-white rounded-xl p-4 border border-slate-200 text-center hover:shadow-md transition">
                <div class="font-bold text-slate-800 mb-1">{{ tool.name }}</div>
                <div class="text-[10px] text-slate-500">{{ tool.url }}</div>
              </div>
            </div>

            <div class="grid grid-cols-2 gap-4">
              <div class="bg-white rounded-xl p-4 border border-slate-200">
                <div class="flex items-center gap-2 mb-2">
                  <div class="w-8 h-8 bg-indigo-100 rounded-lg flex items-center justify-center text-indigo-600">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9"/></svg>
                  </div>
                  <h4 class="font-bold text-sm text-slate-900">Domain, DNS & SSL</h4>
                </div>
                <p class="text-xs text-slate-600">Menghubungkan aplikasi ke alamat website dan mengaktifkan koneksi HTTPS.</p>
              </div>
              <div class="bg-white rounded-xl p-4 border border-slate-200">
                <div class="flex items-center gap-2 mb-2">
                  <div class="w-8 h-8 bg-emerald-100 rounded-lg flex items-center justify-center text-emerald-600">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>
                  </div>
                  <h4 class="font-bold text-sm text-slate-900">Deployment</h4>
                </div>
                <p class="text-xs text-slate-600">Menjaga aplikasi tetap online, cepat, dan aman.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ALUR KERJA & PEMBAYARAN -->
    <section id="alur" class="py-24 bg-primary-50/50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        
        <!-- Header Alur -->
        <div class="text-center max-w-3xl mx-auto mb-16">
          <span class="inline-block bg-primary-100 text-primary-700 text-xs font-bold uppercase tracking-widest px-4 py-1.5 rounded-full mb-4">Workflow</span>
          <h2 class="text-3xl lg:text-4xl font-black text-slate-900 mb-4">Alur Kerja & Pembayaran</h2>
          <p class="text-slate-600 text-lg">Proses yang jelas, komunikasi yang terbuka, serta pembayaran yang fleksibel. Semua untuk memastikan proyek Anda berjalan lancar hingga selesai.</p>
        </div>

        <!-- Alur Kerja Steps -->
        <div class="mb-20">
          <div class="flex items-center gap-3 mb-8">
            <div class="w-12 h-12 bg-primary-600 rounded-xl flex items-center justify-center text-white">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.066 2.573c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.573 1.066c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.066-2.573c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"/><circle cx="12" cy="12" r="3"/></svg>
            </div>
            <div>
              <h3 class="text-2xl font-black text-slate-900">ALUR KERJA PROYEK</h3>
              <p class="text-sm text-slate-600">Setiap langkah dikerjakan secara terstruktur agar hasilnya sesuai harapan.</p>
            </div>
          </div>

          <div class="grid sm:grid-cols-2 lg:grid-cols-5 gap-4 relative">
            <!-- Connector Line Desktop -->
            <div class="hidden lg:block absolute top-1/2 left-0 right-0 h-0.5 bg-primary-200 -translate-y-1/2 z-0"></div>
            
            <div v-for="(step, idx) in workflowSteps" :key="step.num" 
                 class="relative z-10 bg-white rounded-2xl p-6 border border-primary-100 shadow-sm hover:shadow-md hover:border-primary-300 transition-all duration-300 group">
              <div class="flex items-center justify-between mb-4">
                <span class="text-xs font-bold text-primary-600 bg-primary-50 px-2 py-1 rounded-full border border-primary-100">{{ step.num }}</span>
                <span class="text-2xl group-hover:scale-110 transition-transform">{{ step.icon }}</span>
              </div>
              <h4 class="font-bold text-slate-900 mb-2 text-sm leading-snug">{{ step.title }}</h4>
              <p class="text-xs text-slate-600 leading-relaxed">{{ step.desc }}</p>
              
              <!-- Arrow for desktop -->
              <div v-if="idx < workflowSteps.length - 1" class="hidden lg:block absolute -right-3 top-1/2 -translate-y-1/2 text-primary-300 z-20">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/></svg>
              </div>
            </div>
          </div>
        </div>

        <!-- Pembayaran Steps -->
        <div>
          <div class="flex items-center gap-3 mb-8">
            <div class="w-12 h-12 bg-primary-600 rounded-xl flex items-center justify-center text-white">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z"/></svg>
            </div>
            <div>
              <h3 class="text-2xl font-black text-slate-900">PEMBAYARAN</h3>
              <p class="text-sm text-slate-600">Fleksibel, transparan, dan aman.</p>
            </div>
          </div>

          <div class="grid md:grid-cols-3 gap-6 mb-8">
            <div v-for="(pay, idx) in paymentSteps" :key="pay.num" 
                 class="bg-white rounded-2xl p-6 border border-slate-200 shadow-sm relative overflow-hidden group hover:border-primary-300 transition">
              <div class="flex items-center gap-3 mb-4">
                <div class="w-10 h-10 bg-primary-100 rounded-full flex items-center justify-center text-primary-700 font-bold text-lg">{{ pay.num }}</div>
                <div class="w-10 h-10 bg-primary-50 rounded-full flex items-center justify-center text-primary-600">
                  <svg v-if="pay.num === '1'" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 9V7a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2m2 4h10a2 2 0 002-2v-6a2 2 0 00-2-2H9a2 2 0 00-2 2v6a2 2 0 002 2zm7-5a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
                  <svg v-else-if="pay.num === '2'" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
                  <svg v-else class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
                </div>
              </div>
              
              <h4 class="font-bold text-slate-900 mb-2">{{ pay.title }}</h4>
              <p class="text-sm text-slate-600 mb-6 min-h-[40px]">{{ pay.desc }}</p>
              
              <div class="flex items-center gap-3 mb-2">
                <span class="bg-primary-600 text-white text-xs font-bold px-3 py-1 rounded-full">{{ pay.percent }}</span>
              </div>
              
              <!-- Progress Bar -->
              <div class="w-full bg-slate-100 rounded-full h-2 overflow-hidden">
                <div :class="['h-full bg-primary-500 rounded-full transition-all duration-1000', pay.progress]"></div>
              </div>

              <!-- Arrow between cards -->
              <div v-if="idx < paymentSteps.length - 1" class="hidden md:block absolute -right-3 top-1/2 -translate-y-1/2 text-slate-300 z-10 bg-white p-1">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/></svg>
              </div>
            </div>
          </div>

          <!-- Info Note -->
          <div class="bg-blue-50 border border-blue-100 rounded-xl p-4 flex items-start gap-3">
            <div class="w-8 h-8 bg-blue-600 rounded-full flex items-center justify-center text-white shrink-0 font-bold">i</div>
            <p class="text-sm text-blue-800 leading-relaxed">
              <strong>Biaya domain, hosting, dan layanan tambahan</strong> (jika ada) akan diinformasikan secara transparan sejak awal, sesuai kebutuhan proyek.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- BARU: ALASAN HARUS KONSULTASI -->
    <section id="konsultasi" class="py-24 bg-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-3xl mx-auto mb-16">
          <span class="inline-block bg-accent-100 text-accent-700 text-xs font-bold uppercase tracking-widest px-4 py-1.5 rounded-full mb-4">Kenapa Harus Konsultasi?</span>
          <h2 class="text-3xl lg:text-4xl font-black text-slate-900 mb-4">Diskusi Dulu, Baru Eksekusi!</h2>
          <p class="text-slate-600 text-lg">Kami percaya bahwa solusi digital yang tepat dimulai dari pemahaman mendalam terhadap kebutuhan Anda. Berikut alasan mengapa konsultasi awal sangat penting:</p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
          <div class="bg-slate-50 rounded-2xl p-6 border border-slate-200 hover:border-primary-300 hover:shadow-lg transition-all duration-300 group">
            <div class="w-12 h-12 bg-primary-100 rounded-xl flex items-center justify-center text-primary-600 mb-4 group-hover:bg-primary-600 group-hover:text-white transition-colors">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">1. Pemetaan Kebutuhan Akurat</h3>
            <p class="text-sm text-slate-600">Setiap bisnis unik. Konsultasi membantu kami memahami masalah spesifik Anda sehingga solusi yang dibangun benar-benar relevan dan tidak membuang fitur yang tidak perlu.</p>
          </div>

          <div class="bg-slate-50 rounded-2xl p-6 border border-slate-200 hover:border-accent-300 hover:shadow-lg transition-all duration-300 group">
            <div class="w-12 h-12 bg-accent-100 rounded-xl flex items-center justify-center text-accent-600 mb-4 group-hover:bg-accent-600 group-hover:text-white transition-colors">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">2. Estimasi Biaya Transparan</h3>
            <p class="text-sm text-slate-600">Dengan diskusi awal, kami bisa memberikan estimasi biaya yang realistis dan detail. Tidak ada biaya tersembunyi atau kejutan di tengah pengerjaan proyek.</p>
          </div>

          <div class="bg-slate-50 rounded-2xl p-6 border border-slate-200 hover:border-green-300 hover:shadow-lg transition-all duration-300 group">
            <div class="w-12 h-12 bg-green-100 rounded-xl flex items-center justify-center text-green-600 mb-4 group-hover:bg-green-600 group-hover:text-white transition-colors">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">3. Rekomendasi Teknologi Tepat</h3>
            <p class="text-sm text-slate-600">Tidak semua proyek butuh teknologi yang sama. Kami akan menyarankan stack (React, Vue, Laravel, dll) yang paling efisien, scalable, dan sesuai budget Anda.</p>
          </div>

          <div class="bg-slate-50 rounded-2xl p-6 border border-slate-200 hover:border-purple-300 hover:shadow-lg transition-all duration-300 group">
            <div class="w-12 h-12 bg-purple-100 rounded-xl flex items-center justify-center text-purple-600 mb-4 group-hover:bg-purple-600 group-hover:text-white transition-colors">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"/></svg>
            </div>
            <h3 class="font-bold text-slate-900 mb-2">4. Rasa Tenang & Nyaman</h3>
            <p class="text-sm text-slate-600">Seperti motto kami: "Diskusi dulu, baru eksekusi! Jadi, kamu bisa lebih tenang." Konsultasi memastikan Anda merasa aman dan dipahami sebelum komitmen finansial.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- KONTAK / FOOTER CTA -->
    <section id="kontak" class="py-24 bg-slate-900 text-white relative overflow-hidden">
      <div class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PGNpcmNsZSBjeD0iMiIgY3k9IjIiIHI9IjEiIGZpbGw9InJnYmEoMjU1LDI1NSwyNTUsMC4wNSkiLz48L3N2Zz4=')] opacity-20"></div>
      
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
          <div>
            <div class="font-handwriting text-3xl text-primary-400 mb-6 transform -rotate-2">Ide Anda, solusi digital saya.</div>
            <h2 class="text-4xl lg:text-5xl font-black mb-6 leading-tight">Bersama nexud.tech,<br/>wujudkan ide Anda menjadi<br/>solusi digital yang nyata.</h2>
            <p class="text-slate-400 text-lg mb-8">Dari pengembangan aplikasi hingga deployment dan integrasi layanan pihak ketiga, semua bisa disesuaikan dengan kebutuhan bisnis Anda.</p>
            
            <a href="https://wa.me/6282157303890" target="_blank" class="inline-flex items-center gap-2 bg-primary-600 text-white px-8 py-4 rounded-full font-bold text-lg hover:bg-primary-500 hover:scale-105 transition-all shadow-lg shadow-primary-900/50">
              Konsultasi Sekarang
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"/></svg>
            </a>
          </div>

          <div class="bg-slate-800/50 backdrop-blur-sm rounded-3xl p-8 border border-slate-700">
            <h3 class="text-xl font-bold mb-6 flex items-center gap-2">
              <svg class="w-6 h-6 text-primary-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>
              Hubungi Saya
            </h3>
            
            <div class="space-y-4">
              <a v-for="link in contactLinks" :key="link.label" :href="link.url" target="_blank" 
                 class="flex items-center justify-between p-4 bg-slate-900/50 rounded-xl border border-slate-700 hover:border-primary-500 hover:bg-slate-800 transition group">
                <div class="flex items-center gap-4">
                  <span class="text-slate-400 group-hover:text-primary-400 transition">
                    <svg v-if="link.label.includes('Instagram')" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                    <svg v-else-if="link.label.includes('WhatsApp')" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.625.846 5.059 2.284 7.034L.789 23.492a.5.5 0 00.611.611l4.458-1.495A11.952 11.952 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 22c-2.37 0-4.567-.7-6.417-1.9l-.45-.298-3.178 1.064 1.064-3.178-.298-.45A9.953 9.953 0 012 12C2 6.477 6.477 2 12 2s10 4.477 10 10-4.477 10-10 10z"/></svg>
                    <svg v-else-if="link.label.includes('LinkedIn')" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
                    <svg v-else-if="link.label.includes('GitHub')" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
                    <svg v-else class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>
                  </span>
                  <div>
                    <p class="text-xs text-slate-400">{{ link.label }}</p>
                    <p class="font-semibold text-white group-hover:text-primary-400 transition">{{ link.value }}</p>
                  </div>
                </div>
                <svg class="w-5 h-5 text-slate-600 group-hover:text-primary-400 group-hover:translate-x-1 transition-all" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/></svg>
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-slate-950 text-slate-400 py-12 border-t border-slate-900">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-4 gap-8 mb-12">
          <div class="md:col-span-2">
            <div class="flex items-center gap-2 mb-4">
              <span class="text-2xl font-black text-primary-600">N</span>
              <span class="text-xl font-bold text-white">nexud<span class="text-primary-600">.tech</span></span>
            </div>
            <p class="text-sm leading-relaxed max-w-sm mb-6">
              Bersama nexud.tech, wujudkan kebutuhan bisnis menjadi website dan aplikasi web yang dirancang sesuai kebutuhan, alur kerja, dan tujuan Anda.
            </p>
            <!-- TAMBAHAN: Link Portofolio Pribadi di Footer -->
            <a href="https://portnexd.vercel.app" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 text-primary-400 hover:text-primary-300 transition text-sm font-medium">
              Lihat Portofolio Founder <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/></svg>
            </a>
          </div>
          
          <div>
            <h4 class="text-white font-bold mb-4">Layanan Utama</h4>
            <ul class="space-y-2 text-sm">
              <li><a href="#layanan" class="hover:text-primary-400 transition">Website Bisnis</a></li>
              <li><a href="#layanan" class="hover:text-primary-400 transition">Aplikasi Kustom</a></li>
              <li><a href="#layanan" class="hover:text-primary-400 transition">Sistem Informasi</a></li>
              <li><a href="#layanan" class="hover:text-primary-400 transition">E-commerce</a></li>
              <li><a href="#layanan" class="hover:text-primary-400 transition">Integrasi Layanan</a></li>
            </ul>
          </div>
          
          <div>
            <h4 class="text-white font-bold mb-4">Konsultasi Awal Gratis!</h4>
            <ul class="space-y-2 text-sm">
              <li class="flex items-center gap-2">
                <svg class="w-4 h-4 text-green-500" fill="currentColor" viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.625.846 5.059 2.284 7.034L.789 23.492a.5.5 0 00.611.611l4.458-1.495A11.952 11.952 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 22c-2.37 0-4.567-.7-6.417-1.9l-.45-.298-3.178 1.064 1.064-3.178-.298-.45A9.953 9.953 0 012 12C2 6.477 6.477 2 12 2s10 4.477 10 10-4.477 10-10 10z"/></svg>
                +62 812 3456 7890
              </li>
              <li class="flex items-center gap-2">
                <svg class="w-4 h-4 text-pink-500" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
                @nexud.tech
              </li>
              <li class="flex items-center gap-2">
                <svg class="w-4 h-4 text-blue-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9"/></svg>
                www.nexud.tech
              </li>
              <li class="flex items-center gap-2">
                <svg class="w-4 h-4 text-red-500" fill="currentColor" viewBox="0 0 24 24"><path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>
                nexud.id
              </li>
            </ul>
          </div>
        </div>
        
        <div class="border-t border-slate-900 pt-8 flex flex-col md:flex-row justify-between items-center gap-4 text-xs text-slate-600">
          <p>&copy; 2026 nexud.tech. Seluruh hak cipta dilindungi.</p>
          <p>Dibuat dengan ❤️ menggunakan Vue 3 & Tailwind CSS v4</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Custom Scrollbar */
::-webkit-scrollbar { width: 8px; }
::-webkit-scrollbar-track { background: #f1f5f9; }
::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 4px; }
::-webkit-scrollbar-thumb:hover { background: #94a3b8; }

/* Animation Utilities */
@keyframes fade-in-up {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
.animate-fade-in-up { animation: fade-in-up 0.8s ease-out forwards; }
</style>