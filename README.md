<!DOCTYPE html>
<html lang="id">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Informasi TKA & SKL 2026 | SD Islam Sultan Agung 4</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap"
        rel="stylesheet">

    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f8fafc;
            background-image:
                radial-gradient(circle at 100% 100%, rgba(37, 78, 186, 0.05) 0, transparent 50%),
                radial-gradient(circle at 0% 0%, rgba(37, 78, 186, 0.05) 0, transparent 50%);
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .fade-in {
            animation: fadeIn 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .custom-shadow {
            box-shadow: 0 10px 40px -10px rgba(0, 0, 0, 0.08);
        }

        /* Smooth tab transition */
        .tab-btn {
            position: relative;
            transition: all 0.3s ease;
        }

        .tab-btn::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 100%;
            height: 3px;
            background-color: #2563eb;
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .tab-active::after {
            transform: scaleX(1);
        }
    </style>
</head>

<body>

    <header class="bg-gradient-to-r from-[#1e3a8a] to-[#2563eb] text-white py-8 shadow-lg relative z-10">
        <div class="container mx-auto px-4 text-center">
            <div class="inline-flex items-center justify-center p-3 bg-white/10 rounded-full mb-3 backdrop-blur-sm">
                <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l9-5-9-5-9 5 9 5z">
                    </path>
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M12 14l9-5-9-5-9 5 9 5zm0 0v6m0-6l-9-5m9 5l9-5"></path>
                </svg>
            </div>
            <h1 class="text-2xl md:text-3xl font-bold tracking-wide">Portal Layanan Akademik Siswa</h1>
            <p class="text-lg mt-2 font-medium text-blue-100">SD Islam Sultan Agung 4</p>
            <p class="text-sm font-light mt-1 text-blue-200">Dinas Pendidikan Kota Semarang - Tahun 2026</p>
        </div>
    </header>

    <main class="flex-grow container mx-auto px-4 py-10 flex flex-col items-center justify-center relative">

        <div
            class="w-full max-w-2xl bg-white rounded-2xl custom-shadow border border-gray-100 overflow-hidden relative z-10 min-h-[420px]">

            <div class="flex bg-slate-50 border-b border-gray-200">
                <button onclick="switchTab('TKA')" id="tabTKA"
                    class="tab-btn tab-active flex-1 py-4 text-sm md:text-base font-semibold text-blue-700 hover:bg-slate-100 transition-colors">
                    Hasil Ujian TKA
                </button>
                <button onclick="switchTab('SKL')" id="tabSKL"
                    class="tab-btn flex-1 py-4 text-sm md:text-base font-semibold text-gray-500 hover:text-gray-700 hover:bg-slate-100 transition-colors">
                    Surat Keterangan Lulus
                </button>
            </div>

            <div id="formContainer" class="p-6 md:p-10 fade-in">
                <div class="text-center mb-8">
                    <h2 id="formTitle" class="text-[#1e3a8a] text-2xl font-bold">Cek Hasil Tes Kemampuan Akademik</h2>
                    <p id="formSubtitle" class="text-gray-500 text-sm mt-2 leading-relaxed">Masukkan NISN dan Tanggal
                        Lahir Siswa dengan benar untuk mengakses portal layanan.</p>
                </div>

                <form onsubmit="handleFormSubmit(event)" class="space-y-6">
                    <div>
                        <label for="nisnInput" class="block text-sm font-semibold text-gray-700 mb-2">Nomor Induk Siswa
                            Nasional (NISN)</label>
                        <div class="relative">
                            <div class="absolute inset-y-0 left-0 pl-4 flex items-center pointer-events-none">
                                <svg class="h-5 w-5 text-gray-400" fill="none" stroke="currentColor"
                                    viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M10 6H5a2 2 0 00-2 2v9a2 2 0 002 2h14a2 2 0 002-2V8a2 2 0 00-2-2h-5m-4 0V5a2 2 0 114 0v1m-4 0a2 2 0 104 0m-5 8a2 2 0 100-4 2 2 0 000 4zm0 0c1.306 0 2.417.835 2.83 2M9 14a3.001 3.001 0 00-2.83 2M15 11h3m-3 4h2">
                                    </path>
                                </svg>
                            </div>
                            <input type="text" id="nisnInput" required placeholder="Contoh: 0135842803"
                                class="w-full pl-11 pr-4 py-3 bg-gray-50 border border-gray-300 rounded-xl focus:ring-2 focus:ring-blue-500 focus:border-blue-500 focus:bg-white outline-none transition-all text-gray-700 font-medium tracking-wide">
                        </div>
                    </div>
                    <div>
                        <label for="ttlInput" class="block text-sm font-semibold text-gray-700 mb-2">Tanggal Lahir
                            Siswa</label>
                        <div class="relative">
                            <div class="absolute inset-y-0 left-0 pl-4 flex items-center pointer-events-none">
                                <svg class="h-5 w-5 text-gray-400" fill="none" stroke="currentColor"
                                    viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                        d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z">
                                    </path>
                                </svg>
                            </div>
                            <input type="date" id="ttlInput" required
                                class="w-full pl-11 pr-4 py-3 bg-gray-50 border border-gray-300 rounded-xl focus:ring-2 focus:ring-blue-500 focus:border-blue-500 focus:bg-white outline-none transition-all text-gray-700 font-medium">
                        </div>
                    </div>
                    <button type="submit" id="btnSubmit"
                        class="w-full bg-gradient-to-r from-blue-600 to-blue-700 hover:from-blue-700 hover:to-blue-800 text-white font-bold py-3.5 px-4 rounded-xl shadow-lg hover:shadow-xl transform hover:-translate-y-0.5 transition-all duration-200">
                        Cek Hasil TKA
                    </button>
                </form>

                <div id="errorMessage"
                    class="hidden mt-6 p-4 bg-red-50 border-l-4 border-red-500 rounded-r-xl flex items-start">
                    <svg class="w-5 h-5 text-red-500 mr-3 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                    </svg>
                    <p class="text-sm text-red-700">Data tidak ditemukan. Silakan periksa kembali kombinasi <span
                            class="font-bold">NISN</span> dan <span class="font-bold">Tanggal Lahir</span> Anda.</p>
                </div>
            </div>

            <div id="resultTkaLunas" class="hidden fade-in p-6 md:p-10">
                <div class="text-center mb-6">
                    <span
                        class="bg-blue-100 text-blue-800 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider">Hasil
                        TKA 2026</span>
                    <h2 class="text-[#1e3a8a] text-2xl font-bold mt-3">Detail Nilai Akademik</h2>
                </div>

                <div class="bg-white border border-gray-200 shadow-sm rounded-xl p-5 mb-8">
                    <div class="flex items-center gap-3 border-b border-gray-100 pb-3 mb-3">
                        <div class="bg-blue-100 p-2 rounded-lg">
                            <svg class="w-5 h-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path>
                            </svg>
                        </div>
                        <div>
                            <p class="text-gray-500 text-xs font-semibold uppercase tracking-wider">Nama Lengkap</p>
                            <p class="text-gray-900 font-bold uppercase text-sm md:text-base" id="resNamaTkaL"></p>
                        </div>
                    </div>
                    <div class="flex items-center gap-3">
                        <div class="bg-slate-100 p-2 rounded-lg">
                            <svg class="w-5 h-5 text-slate-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M10 6H5a2 2 0 00-2 2v9a2 2 0 002 2h14a2 2 0 002-2V8a2 2 0 00-2-2h-5m-4 0V5a2 2 0 114 0v1m-4 0a2 2 0 104 0m-5 8a2 2 0 100-4 2 2 0 000 4zm0 0c1.306 0 2.417.835 2.83 2M9 14a3.001 3.001 0 00-2.83 2M15 11h3m-3 4h2">
                                </path>
                            </svg>
                        </div>
                        <div>
                            <p class="text-gray-500 text-xs font-semibold uppercase tracking-wider">NISN</p>
                            <p class="text-gray-900 font-medium text-sm md:text-base" id="resNisnTkaL"></p>
                        </div>
                    </div>
                </div>

                <div class="grid grid-cols-2 gap-4 mb-8">
                    <div
                        class="bg-blue-50 rounded-2xl p-5 text-center border border-blue-100 relative overflow-hidden group hover:shadow-md transition-all">
                        <div
                            class="absolute top-0 right-0 w-16 h-16 bg-blue-100 rounded-bl-full -mr-8 -mt-8 opacity-50 transition-transform group-hover:scale-110">
                        </div>
                        <p class="text-xs text-blue-600 font-bold uppercase tracking-wider mb-2 relative z-10">
                            Matematika</p>
                        <p class="text-4xl font-black text-[#1e3a8a] relative z-10" id="resMtkTka"></p>
                        <p class="text-sm font-semibold bg-white inline-block px-3 py-1 rounded-full text-blue-600 mt-3 shadow-sm border border-blue-50 relative z-10"
                            id="resMtkKetTka"></p>
                    </div>
                    <div
                        class="bg-emerald-50 rounded-2xl p-5 text-center border border-emerald-100 relative overflow-hidden group hover:shadow-md transition-all">
                        <div
                            class="absolute top-0 right-0 w-16 h-16 bg-emerald-100 rounded-bl-full -mr-8 -mt-8 opacity-50 transition-transform group-hover:scale-110">
                        </div>
                        <p class="text-xs text-emerald-600 font-bold uppercase tracking-wider mb-2 relative z-10">B.
                            Indonesia</p>
                        <p class="text-4xl font-black text-emerald-700 relative z-10" id="resIndoTka"></p>
                        <p class="text-sm font-semibold bg-white inline-block px-3 py-1 rounded-full text-emerald-600 mt-3 shadow-sm border border-emerald-50 relative z-10"
                            id="resIndoKetTka"></p>
                    </div>
                </div>

                <div class="text-center">
                    <button onclick="resetViews()"
                        class="inline-flex items-center justify-center px-6 py-2.5 border border-gray-300 rounded-xl text-gray-700 font-medium hover:bg-gray-50 hover:text-blue-600 transition-all">
                        <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M10 19l-7-7m0 0l7-7m-7 7h18"></path>
                        </svg>
                        Kembali
                    </button>
                </div>
            </div>

            <div id="resultTkaTerkunci" class="hidden fade-in p-6 md:p-10 text-center">
                <div class="inline-flex items-center justify-center w-20 h-20 bg-red-50 rounded-full mb-6 relative">
                    <div class="absolute inset-0 bg-red-100 rounded-full animate-ping opacity-20"></div>
                    <svg class="w-10 h-10 text-red-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
                    </svg>
                </div>

                <h2 class="text-xl font-black text-gray-800 mb-1 uppercase tracking-wide" id="resNamaTkaM"></h2>
                <p class="text-sm text-gray-500 font-medium mb-6 bg-gray-100 inline-block px-4 py-1 rounded-full"
                    id="resNisnTkaM"></p>

                <div
                    class="bg-white border-2 border-red-100 shadow-sm rounded-2xl p-5 mb-8 text-left relative overflow-hidden">
                    <div class="absolute top-0 left-0 w-2 h-full bg-red-500"></div>
                    <div class="flex items-start">
                        <svg class="w-6 h-6 text-red-500 mr-3 mt-1 flex-shrink-0" fill="none" stroke="currentColor"
                            viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z">
                            </path>
                        </svg>
                        <div>
                            <p class="font-bold text-red-800 mb-1 text-lg">Akses TKA Diblokir</p>
                            <p class="text-gray-600 text-sm leading-relaxed">Mohon maaf, pengumuman kelulusan dapat
                                diambil di sekolah (ruang Tata Usaha) kami</p>
                        </div>
                    </div>
                </div>

                <button onclick="resetViews()"
                    class="inline-flex items-center justify-center px-6 py-2.5 border border-gray-300 rounded-xl text-gray-700 font-medium hover:bg-gray-50 hover:text-blue-600 transition-all">
                    Kembali ke Pencarian
                </button>
            </div>

            <div id="resultSklLunas" class="hidden fade-in p-6 md:p-10 text-center">
                <div class="inline-flex items-center justify-center w-20 h-20 bg-green-50 rounded-full mb-4 relative">
                    <div class="absolute inset-0 bg-green-100 rounded-full animate-ping opacity-20"></div>
                    <svg class="w-10 h-10 text-green-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg>
                </div>

                <div class="mb-4">
                    <span
                        class="bg-green-100 text-green-800 border border-green-200 text-sm font-black px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">
                        STATUS: LULUS
                    </span>
                </div>

                <h2 class="text-center text-[#1e3a8a] text-2xl font-bold mb-6">Surat Keterangan Lulus (SKL)</h2>

                <div class="bg-white border border-gray-200 shadow-sm rounded-xl p-5 mb-8 text-left">
                    <div class="flex items-center gap-3 border-b border-gray-100 pb-3 mb-3">
                        <div class="bg-green-50 p-2 rounded-lg">
                            <svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path>
                            </svg>
                        </div>
                        <div>
                            <p class="text-gray-500 text-xs font-semibold uppercase tracking-wider">Nama Lengkap</p>
                            <p class="text-gray-900 font-bold uppercase text-sm md:text-base" id="resNamaSklL"></p>
                        </div>
                    </div>
                    <div class="flex items-center gap-3">
                        <div class="bg-slate-100 p-2 rounded-lg">
                            <svg class="w-5 h-5 text-slate-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M10 6H5a2 2 0 00-2 2v9a2 2 0 002 2h14a2 2 0 002-2V8a2 2 0 00-2-2h-5m-4 0V5a2 2 0 114 0v1m-4 0a2 2 0 104 0m-5 8a2 2 0 100-4 2 2 0 000 4zm0 0c1.306 0 2.417.835 2.83 2M9 14a3.001 3.001 0 00-2.83 2M15 11h3m-3 4h2">
                                </path>
                            </svg>
                        </div>
                        <div>
                            <p class="text-gray-500 text-xs font-semibold uppercase tracking-wider">NISN</p>
                            <p class="text-gray-900 font-medium text-sm md:text-base" id="resNisnSklL"></p>
                        </div>
                    </div>
                </div>

                <div class="mb-8">
                    <a href="#" id="linkDownloadSkl" target="_blank"
                        class="inline-flex items-center justify-center w-full bg-gradient-to-r from-green-600 to-emerald-600 hover:from-green-700 hover:to-emerald-700 text-white font-bold py-4 px-6 rounded-xl shadow-lg hover:shadow-xl transform hover:-translate-y-0.5 transition-all duration-200">
                        <svg class="w-6 h-6 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                            xmlns="http://www.w3.org/2000/svg">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"></path>
                        </svg>
                        Download Dokumen SKL (PDF)
                    </a>
                </div>

                <div class="text-center">
                    <button onclick="resetViews()"
                        class="inline-flex items-center justify-center px-6 py-2.5 border border-gray-300 rounded-xl text-gray-700 font-medium hover:bg-gray-50 hover:text-blue-600 transition-all">
                        Kembali ke Pencarian
                    </button>
                </div>
            </div>

            <div id="resultSklTerkunci" class="hidden fade-in p-6 md:p-10 text-center">
                <div class="inline-flex items-center justify-center w-20 h-20 bg-red-50 rounded-full mb-4 relative">
                    <div class="absolute inset-0 bg-red-100 rounded-full animate-ping opacity-20"></div>
                    <svg class="w-10 h-10 text-red-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
                    </svg>
                </div>

                <div class="mb-4">
                    <span
                        class="bg-red-100 text-red-800 border border-red-200 text-sm font-black px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">
                        STATUS: DITANGGUHKAN
                    </span>
                </div>

                <h2 class="text-xl font-black text-gray-800 mb-1 uppercase tracking-wide" id="resNamaSklM"></h2>
                <p class="text-sm text-gray-500 font-medium mb-6 bg-gray-100 inline-block px-4 py-1 rounded-full"
                    id="resNisnSklM"></p>

                <div
                    class="bg-white border-2 border-red-100 shadow-sm rounded-2xl p-5 mb-8 text-left relative overflow-hidden">
                    <div class="absolute top-0 left-0 w-2 h-full bg-red-500"></div>
                    <div class="flex items-start">
                        <svg class="w-6 h-6 text-red-500 mr-3 mt-1 flex-shrink-0" fill="none" stroke="currentColor"
                            viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                        </svg>
                        <div>
                            <p class="font-bold text-red-800 mb-1 text-lg">Akses SKL Belum Tersedia</p>
                            <p class="text-gray-600 text-sm leading-relaxed">Mohon maaf, pengumuman kelulusan dapat
                                diambil di Sekolah kami (ruang Tata Usaha).
                            </p>
                        </div>
                    </div>
                </div>

                <button onclick="resetViews()"
                    class="inline-flex items-center justify-center px-6 py-2.5 border border-gray-300 rounded-xl text-gray-700 font-medium hover:bg-gray-50 hover:text-blue-600 transition-all">
                    Kembali ke Pencarian
                </button>
            </div>

        </div>
    </main>

    <footer class="bg-white border-t border-gray-200 text-gray-500 text-center py-6 text-sm z-10 w-full mt-auto">
        <p>&copy; 2026 SD Islam Sultan Agung 4 Semarang. Hak Cipta Dilindungi.</p>
    </footer>

    <script>
        // Variabel untuk menyimpan status tab yang sedang aktif
        let activeTab = 'TKA'; // Default tab

        // --- DATA 53 SISWA TERBUKA ---
        const databaseSiswa = [
            { nisn: "0135842803", nama: "MUHAMMAD AZMI KANZA MAZAYA", ttl: "2013-11-29", isLunas: true, tkaMtk: "63.33", tkaMtkKet: "Baik", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1P8MJF2UiVGD1Yn01su7Uvb7XZD3to6t1/view?usp=drive_link" },
            { nisn: "0148076661", nama: "Muhammad Rizal Ababil", ttl: "2014-02-12", isLunas: true, tkaMtk: "63.33", tkaMtkKet: "Baik", tkaIndo: "43.33", tkaIndoKet: "Kurang", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1KXO19UydNqLdvN2cZFsX59EBOCxSsAIc/view?usp=drive_link" },
            { nisn: "0147387218", nama: "HABIBAH MAHZA CANTIKA SYAHRUL", ttl: "2014-03-05", isLunas: true, tkaMtk: "46.67", tkaMtkKet: "Memadai", tkaIndo: "80.00", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1lgc48Y-N7XMIly9-3b_DvsJWhFGXdeB9/view?usp=drive_link" },
            { nisn: "0143223416", nama: "Alvaro Gavriel Putra", ttl: "2014-06-02", isLunas: true, tkaMtk: "50.00", tkaMtkKet: "Memadai", tkaIndo: "60.00", tkaIndoKet: "Memadai", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0143285427", nama: "NAJWA FEBRIANI", ttl: "2014-02-19", isLunas: true, tkaMtk: "53.33", tkaMtkKet: "Memadai", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1QzryE5by4kBO5FMSCz7M4Tr56ID2pyzv/view?usp=drive_link" },
            { nisn: "0135147720", nama: "MUHAMMAD FARHAN PURNOMO", ttl: "2013-08-24", isLunas: true, tkaMtk: "56.67", tkaMtkKet: "Baik", tkaIndo: "83.33", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/11e9BoQhg4uODQBXmchSAkvzTKMV_AsuP/view?usp=drive_link" },
            { nisn: "3135783058", nama: "Muhammad Dzaky Faeyza Eshan", ttl: "2013-10-03", isLunas: true, tkaMtk: "43.33", tkaMtkKet: "Memadai", tkaIndo: "63.33", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1sw95mykcKZd5Q8xFv8NlZRWh8y5ghGiD/view?usp=drive_link" },
            { nisn: "0138579281", nama: "Azzam El Fatahillah", ttl: "2013-12-04", isLunas: true, tkaMtk: "73.33", tkaMtkKet: "Baik", tkaIndo: "83.33", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1pLZrPt460EkjzTtFNOKl0Lt7QnFnZ9tX/view?usp=drive_link" },
            { nisn: "0135156214", nama: "Aqilah Sania Az-Zahra", ttl: "2013-11-13", isLunas: true, tkaMtk: "76.67", tkaMtkKet: "Baik", tkaIndo: "86.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1hgrasSV6HZJaZ_s61jmFJ5-_44PHADEC/view?usp=drive_link" },
            { nisn: "0143282396", nama: "BILQIS AZKA ADZKIA", ttl: "2014-04-27", isLunas: true, tkaMtk: "36.67", tkaMtkKet: "Memadai", tkaIndo: "33.33", tkaIndoKet: "Kurang", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1vc5AoxL7ZEYV8bJzIsHZ0u5UUF1-_BLS/view?usp=drive_link" },
            { nisn: "3149785202", nama: "Jovita Darla Callista", ttl: "2014-07-10", isLunas: true, tkaMtk: "53.33", tkaMtkKet: "Memadai", tkaIndo: "83.33", tkaIndoKet: "Baik", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0144985290", nama: "NISWA SHABIRA RAMADHANI", ttl: "2014-07-15", isLunas: true, tkaMtk: "46.67", tkaMtkKet: "Memadai", tkaIndo: "70.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/17dhSfADHULDTcPiDBbJG-ypAlQrPZ8Oa/view?usp=drive_link" },
            { nisn: "0148574434", nama: "SABILILLAH RASYA BRAWIJAYA", ttl: "2014-06-03", isLunas: true, tkaMtk: "60.00", tkaMtkKet: "Baik", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "3132455130", nama: "SYIFA AMIRA RAMADHANI", ttl: "2013-07-25", isLunas: true, tkaMtk: "70.00", tkaMtkKet: "Baik", tkaIndo: "86.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1UIvkIa_UVIzpsEDyxfQ-8bFPjV5HpMWF/view?usp=drive_link" },
            { nisn: "0133335301", nama: "Alfatin Shiddiqiyyah", ttl: "2013-09-16", isLunas: true, tkaMtk: "70.00", tkaMtkKet: "Baik", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1nnqfeVTwHfSqkh-yX1Mste9OFSsE6sqM/view?usp=drive_link" },
            { nisn: "0138334867", nama: "Allena Hasiana Tondang", ttl: "2013-10-07", isLunas: true, tkaMtk: "40.00", tkaMtkKet: "Memadai", tkaIndo: "63.33", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1L5xQv5dx3sR1q9taM8QM66svQ3pOmh0M/view?usp=drive_link" },
            { nisn: "0132748560", nama: "Mohammad Rafi Saputra", ttl: "2013-04-01", isLunas: true, tkaMtk: "46.67", tkaMtkKet: "Memadai", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1y298sOXHQ9CTeu0qjNcr7e92RF3E9urW/view?usp=drive_link" },
            { nisn: "3140534208", nama: "Namia Saufa Tatung", ttl: "2014-08-21", isLunas: true, tkaMtk: "50.00", tkaMtkKet: "Memadai", tkaIndo: "66.67", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1QeHDXRGbZWdLUUAv1SdOc-Ijm1ABI9sP/view?usp=drive_link" },
            { nisn: "3137491418", nama: "Azkafa Imammil Hakim", ttl: "2013-12-13", isLunas: true, tkaMtk: "76.67", tkaMtkKet: "Baik", tkaIndo: "70.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1rzqMuMuuCbSWXDzsJbo4L51DbtOOyTwf/view?usp=drive_link" },
            { nisn: "0141988810", nama: "Muhammad Nur Fa'iz", ttl: "2014-05-13", isLunas: true, tkaMtk: "40.00", tkaMtkKet: "Memadai", tkaIndo: "66.67", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1Zh-QCFDwui5ahzVrrZfoeJGRhYjc3UL8/view?usp=drive_link" },
            { nisn: "0142739625", nama: "VIRZHA SATRIA ANAMSYAH", ttl: "2014-06-04", isLunas: true, tkaMtk: "50.00", tkaMtkKet: "Memadai", tkaIndo: "56.67", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1xkqcYTftThb6mpwZnB9ZjVgEc8ACTPV_/view?usp=drive_link" },
            { nisn: "0142658145", nama: "GIUSEPPE MEAZZA NUGROHO", ttl: "2014-02-23", isLunas: true, tkaMtk: "50.00", tkaMtkKet: "Memadai", tkaIndo: "70.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/12AyNZ8YBh9X1i2kf6Ng7hmk7IpeC0BS1/view?usp=drive_link" },
            { nisn: "0134745525", nama: "KINAN MEISYA LISTIYANI", ttl: "2013-05-13", isLunas: true, tkaMtk: "40.00", tkaMtkKet: "Memadai", tkaIndo: "73.33", tkaIndoKet: "Memadai", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0142491633", nama: "FIEBYA AZ ZAHRA SYARAFANA", ttl: "2014-02-07", isLunas: true, tkaMtk: "83.33", tkaMtkKet: "Baik", tkaIndo: "83.33", tkaIndoKet: "Baik", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0131070979", nama: "WILDAN TAUFIQURROHMAN SETYAWAN", ttl: "2013-04-07", isLunas: true, tkaMtk: "36.67", tkaMtkKet: "Memadai", tkaIndo: "56.67", tkaIndoKet: "Memadai", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0136760226", nama: "Devin Azka Abidin", ttl: "2013-09-27", isLunas: true, tkaMtk: "73.33", tkaMtkKet: "Baik", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1Q2-0ijYgZdVZzBltqbu_M86LwvuDwUpj/view?usp=drive_link" },
            { nisn: "0137551333", nama: "MUHAMMAD RASKA YUDHA", ttl: "2013-06-23", isLunas: true, tkaMtk: "53.33", tkaMtkKet: "Memadai", tkaIndo: "70.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1xoqTUCkBweFcRY58Rg31LIFspGvmAlnE/view?usp=drive_link" },
            { nisn: "0139213089", nama: "JIHAN MIRZA LIANA", ttl: "2013-11-18", isLunas: true, tkaMtk: "30.00", tkaMtkKet: "Kurang", tkaIndo: "60.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1yMYJCHjFg4AYNkK1lj5IuRd5u2Plc_Pv/view?usp=drive_link" },
            { nisn: "0147335009", nama: "Syaffira Kayla Krissandewa", ttl: "2014-08-22", isLunas: true, tkaMtk: "66.67", tkaMtkKet: "Baik", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1Q9D-FvKWasRhfxkncAbn4-b1aVsDiguj/view?usp=drive_link" },
            { nisn: "3149998747", nama: "GAYATRI CONDRORINI", ttl: "2014-01-08", isLunas: true, tkaMtk: "66.67", tkaMtkKet: "Baik", tkaIndo: "80.00", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1CK7OR_bs8JrR3bhFuCoAf1QUYG5cTSI0/view?usp=drive_link" },
            { nisn: "0138534800", nama: "DAMIA DEWI KHAIRUNISA", ttl: "2013-06-26", isLunas: true, tkaMtk: "53.33", tkaMtkKet: "Memadai", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1UToEK_T8PAP09PgtXW1r2Db5eRqbvBT7/view?usp=drive_link" },
            { nisn: "0145016379", nama: "MUHAMMAD DZAKY SAPUTRA", ttl: "2014-04-25", isLunas: true, tkaMtk: "36.67", tkaMtkKet: "Memadai", tkaIndo: "50.00", tkaIndoKet: "Memadai", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0144945158", nama: "LATFIA PERMATASARI", ttl: "2014-03-01", isLunas: true, tkaMtk: "26.67", tkaMtkKet: "Kurang", tkaIndo: "80.00", tkaIndoKet: "Baik", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0141926348", nama: "AFFAN BAKHTIAR", ttl: "2014-03-21", isLunas: true, tkaMtk: "63.33", tkaMtkKet: "Baik", tkaIndo: "50.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1hB3E1cY77zDZXoGXCTtgq6pmG-LC5MR2/view?usp=drive_link" },
            { nisn: "0131024281", nama: "Aqila Yusra Jihantoro", ttl: "2013-08-28", isLunas: true, tkaMtk: "50.00", tkaMtkKet: "Memadai", tkaIndo: "76.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/18hUh-DTZNHeW732OgSJJLlA0-GhGiMad/view?usp=drive_link" },
            { nisn: "0147027600", nama: "NAVYSHA AQILLA MAULIDA AZZAHRA", ttl: "2014-01-26", isLunas: true, tkaMtk: "66.67", tkaMtkKet: "Baik", tkaIndo: "86.67", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1OMNlmMOIO-i-_5fOL0UJ6cVJ33Ab05L9/view?usp=drive_link" },
            { nisn: "0146304412", nama: "ADZKIA KHAIRUNNISA", ttl: "2014-06-25", isLunas: true, tkaMtk: "20.00", tkaMtkKet: "Kurang", tkaIndo: "40.00", tkaIndoKet: "Kurang", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "3141762816", nama: "Alesha Davina Aditya Maharani", ttl: "2014-05-16", isLunas: true, tkaMtk: "90.00", tkaMtkKet: "Baik", tkaIndo: "90.00", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1L3Uf5hzUg5Gkkkbfje5jHGpvD_rAM5Ey/view?usp=drive_link" },
            { nisn: "0139979532", nama: "Mochammad Ghias Maulana", ttl: "2013-11-27", isLunas: true, tkaMtk: "56.67", tkaMtkKet: "Baik", tkaIndo: "66.67", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1T1ARp9UsIzlAzBCakYNDBoa6MONX7P_i/view?usp=drive_link" },
            { nisn: "0139235906", nama: "AZKA KUSUMA RAFLI", ttl: "2013-06-19", isLunas: true, tkaMtk: "43.33", tkaMtkKet: "Memadai", tkaIndo: "66.67", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1t8d4QmRY2_qbR_QPUDUg0HFkNjMfvtc8/view?usp=drive_link" },
            { nisn: "0139361226", nama: "FAHRI TSAQIF ARRASYID", ttl: "2013-12-09", isLunas: true, tkaMtk: "60.00", tkaMtkKet: "Baik", tkaIndo: "93.33", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1PDSiwh0ulDsF5F-W61-2hBzEDZdb25Gd/view?usp=drive_link" },
            { nisn: "0139957550", nama: "Jovita Darla Callista", ttl: "2013-11-23", isLunas: true, tkaMtk: "56.67", tkaMtkKet: "Baik", tkaIndo: "90.00", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1Tm1imFxgc5IGciAnEjQ6ILfMjmjzRMxG/view?usp=drive_link" },
            { nisn: "3137169358", nama: "Abdillah Gustan Satvik", ttl: "2013-12-17", isLunas: true, tkaMtk: "60.00", tkaMtkKet: "Baik", tkaIndo: "83.33", tkaIndoKet: "Baik", sppLunas: false, linkSkl: "https://drive.google.com/file/d/1bPIHTzMz9DuH81q7f2N3rzk1-flh8989/view?usp=sharing" },
            { nisn: "0134713573", nama: "IFFA IZZA HISANIYA", ttl: "2013-09-22", isLunas: true, tkaMtk: "66.67", tkaMtkKet: "Baik", tkaIndo: "73.33", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1y8DBTWiarQq637O33YEONNJXdBVAWq3b/view?usp=drive_link" },
            { nisn: "0133464886", nama: "MAULANA DZAKWAN HAFIZUDDIN", ttl: "2013-03-23", isLunas: true, tkaMtk: "60.00", tkaMtkKet: "Baik", tkaIndo: "66.67", tkaIndoKet: "Memadai", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0136027543", nama: "SHALSHA EDHITA NOVI PRIMADANI", ttl: "2013-11-08", isLunas: true, tkaMtk: "53.33", tkaMtkKet: "Memadai", tkaIndo: "60.00", tkaIndoKet: "Memadai", sppLunas: false, linkSkl: "https://drive.google.com/file/d/CONTOH_LINK_PDF/view" },
            { nisn: "0145176473", nama: "MUHAMMAD NOOR AL HUDA", ttl: "2014-02-07", isLunas: true, tkaMtk: "60.00", tkaMtkKet: "Baik", tkaIndo: "70.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1WogwLtEHfcN2lCS2keLM2AQCa_Q7Bx8n/view?usp=drive_link" },
            { nisn: "0147798028", nama: "NADIYA DZAKIRA", ttl: "2014-03-26", isLunas: true, tkaMtk: "63.33", tkaMtkKet: "Baik", tkaIndo: "80.00", tkaIndoKet: "Baik", sppLunas: false, linkSkl: "[https://drive.google.com/file/d/CONTOH_LINK_PDF/view](https://drive.google.com/file/d/1SdLTWRi-z-VHRIgu-unEYbv5F54x5_vm/view?usp=sharing)" },
            { nisn: "3142071602", nama: "Talita Uswah Zaenada", ttl: "2014-06-08", isLunas: true, tkaMtk: "56.67", tkaMtkKet: "Baik", tkaIndo: "70.00", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1UULUI66jbvKgWVeQH0wgZNQTPhkK5UON/view?usp=drive_link" },
            { nisn: "0144813932", nama: "MUHAMMAD EMYR FIRDAUS", ttl: "2014-03-06", isLunas: true, tkaMtk: "46.67", tkaMtkKet: "Memadai", tkaIndo: "80.00", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1iOfee0QAz-wieTCWWqGR6tByhKAX6Uj5/view?usp=drive_link" },
            { nisn: "0144403569", nama: "NAJWA ASSYIFA", ttl: "2014-09-10", isLunas: true, tkaMtk: "73.33", tkaMtkKet: "Baik", tkaIndo: "90.00", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/11jYeV6NHnLl0CRWeStAwBft3GcuwYKHA/view?usp=sharing" },
            { nisn: "0136035834", nama: "ABDUL KHALIK", ttl: "2013-04-28", isLunas: true, tkaMtk: "86.67", tkaMtkKet: "Baik", tkaIndo: "90.00", tkaIndoKet: "Baik", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1U_GJH-hR7gr8OTdU6UIIHgN2Pn8ig2CL/view?usp=drive_link" },
            { nisn: "0141298962", nama: "AL MAY RAIHAN DZAKY PRAYITNO", ttl: "2014-05-24", isLunas: true, tkaMtk: "63.33", tkaMtkKet: "Baik", tkaIndo: "73.33", tkaIndoKet: "Memadai", sppLunas: true, linkSkl: "https://drive.google.com/file/d/1QW_bhm0G-E2PuO3gKaLQHqNxEI0pAPSN/view?usp=drive_link" }
        ];

        // --- FUNGSI PINDAH TAB ---
        function switchTab(tab) {
            activeTab = tab;
            resetViews();

            const tabTKA = document.getElementById('tabTKA');
            const tabSKL = document.getElementById('tabSKL');
            const formTitle = document.getElementById('formTitle');
            const formSubtitle = document.getElementById('formSubtitle');
            const btnSubmit = document.getElementById('btnSubmit');

            if (tab === 'TKA') {
                tabTKA.classList.add('tab-active', 'text-blue-700');
                tabTKA.classList.remove('text-gray-500');
                tabSKL.classList.remove('tab-active', 'text-blue-700');
                tabSKL.classList.add('text-gray-500');

                formTitle.innerText = "Cek Hasil Tes Kemampuan Akademik";
                formSubtitle.innerText = "Masukkan NISN dan Tanggal Lahir Siswa dengan benar untuk mengakses nilai ujian TKA.";
                btnSubmit.innerText = "Cek Hasil TKA";
            } else {
                tabSKL.classList.add('tab-active', 'text-blue-700');
                tabSKL.classList.remove('text-gray-500');
                tabTKA.classList.remove('tab-active', 'text-blue-700');
                tabTKA.classList.add('text-gray-500');

                formTitle.innerText = "Portal Dokumen SKL";
                formSubtitle.innerText = "Masukkan NISN dan Tanggal Lahir Siswa untuk mengunduh Surat Keterangan Lulus (SKL).";
                btnSubmit.innerText = "Cek & Unduh SKL";
            }
        }

        // --- HANDLER CEK DATA ---
        function handleFormSubmit(e) {
            e.preventDefault();
            const inputNisn = document.getElementById('nisnInput').value.trim();
            const inputTtl = document.getElementById('ttlInput').value;

            // Cari kecocokan data siswa
            const siswa = databaseSiswa.find(s => s.nisn === inputNisn && s.ttl === inputTtl);

            if (siswa) {
                document.getElementById('errorMessage').classList.add('hidden');
                document.getElementById('formContainer').classList.add('hidden');

                if (activeTab === 'TKA') {
                    if (siswa.isLunas) {
                        document.getElementById('resNamaTkaL').innerText = siswa.nama;
                        document.getElementById('resNisnTkaL').innerText = siswa.nisn;
                        document.getElementById('resMtkTka').innerText = siswa.tkaMtk;
                        document.getElementById('resMtkKetTka').innerText = `${siswa.tkaMtkKet}`;
                        document.getElementById('resIndoTka').innerText = siswa.tkaIndo;
                        document.getElementById('resIndoKetTka').innerText = `${siswa.tkaIndoKet}`;
                        document.getElementById('resultTkaLunas').classList.remove('hidden');
                    } else {
                        document.getElementById('resNamaTkaM').innerText = siswa.nama;
                        document.getElementById('resNisnTkaM').innerText = `NISN: ${siswa.nisn}`;
                        document.getElementById('resultTkaTerkunci').classList.remove('hidden');
                    }
                } else if (activeTab === 'SKL') {
                    if (siswa.sppLunas) {
                        document.getElementById('resNamaSklL').innerText = siswa.nama;
                        document.getElementById('resNisnSklL').innerText = siswa.nisn;
                        document.getElementById('linkDownloadSkl').href = siswa.linkSkl;
                        document.getElementById('resultSklLunas').classList.remove('hidden');
                    } else {
                        document.getElementById('resNamaSklM').innerText = siswa.nama;
                        document.getElementById('resNisnSklM').innerText = `NISN: ${siswa.nisn}`;
                        document.getElementById('resultSklTerkunci').classList.remove('hidden');
                    }
                }

            } else {
                // JIKA DATA TIDAK COCOK / SALAH INPUT
                document.getElementById('errorMessage').classList.remove('hidden');
            }
        }

        // --- RE-SET KE LAYAR PENCARIAN AWAL ---
        function resetViews() {
            document.getElementById('nisnInput').value = '';
            document.getElementById('ttlInput').value = '';
            document.getElementById('errorMessage').classList.add('hidden');

            // Sembunyikan semua hasil TKA & SKL
            document.getElementById('resultTkaLunas').classList.add('hidden');
            document.getElementById('resultTkaTerkunci').classList.add('hidden');
            document.getElementById('resultSklLunas').classList.add('hidden');
            document.getElementById('resultSklTerkunci').classList.add('hidden');

            // Munculkan kembali form
            document.getElementById('formContainer').classList.remove('hidden');
        }
    </script>
</body>

</html>
