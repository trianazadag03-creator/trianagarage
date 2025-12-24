<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Triana Garage - 24/7 Roadside Assistance</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap');
        
        html, body {
            font-family: 'Inter', sans-serif;
            margin: 0;
            padding: 0;
            scroll-behavior: smooth;
            background-color: #fff;
            -webkit-tap-highlight-color: transparent;
            overflow-x: hidden;
        }

        .hero-section {
            background-color: #000;
            background-image: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.8)), 
                              url('https://images.unsplash.com/photo-1486006396193-471a6f58bcb3?auto=format&fit=crop&q=80&w=2000');
            background-size: cover;
            background-position: center;
            padding: 100px 20px;
            text-align: center;
            color: #fff;
        }

        .modal-simple {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 10000;
            padding: 10px;
            align-items: center;
            justify-content: center;
            overflow-y: auto;
        }
        
        .modal-simple.show {
            display: flex;
        }

        .lang-switch-container {
            display: flex;
            background-color: #111;
            border: 1px solid #333;
            border-radius: 9999px;
            padding: 2px;
        }

        .lang-btn {
            padding: 6px 12px;
            border-radius: 9999px;
            font-size: 0.75rem;
            font-weight: 800;
            transition: all 0.2s;
            color: #888;
            cursor: pointer;
        }

        .lang-btn.active {
            background-color: #eab308;
            color: #000;
        }

        .email-bubble {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background-color: #eab308;
            color: #000;
            width: 65px;
            height: 65px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 10px 30px rgba(234, 179, 8, 0.4);
            z-index: 9999;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: none;
            cursor: pointer;
        }

        .email-bubble:active {
            transform: scale(0.9);
        }

        input, textarea {
            border: 1px solid #ddd;
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            outline: none;
            font-size: 16px;
        }
        
        input:focus, textarea:focus {
            border-color: #eab308;
        }

        button {
            touch-action: manipulation;
        }
    </style>
</head>
<body>

<div id="app-root">
    <!-- Botón Flotante de Email -->
    <button type="button" onclick="launchAction('mailto:triana.zada.g03@gmail.com')" class="email-bubble shadow-xl">
        <i class="fas fa-envelope text-2xl"></i>
    </button>

    <nav class="bg-black text-white p-4 sticky top-0 z-50 shadow-lg">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <!-- Logo -->
            <div class="flex items-center gap-2">
                <i class="fas fa-wrench text-yellow-500 text-2xl"></i>
                <span class="font-black text-xl uppercase tracking-tighter">Triana<span class="text-yellow-500">Garage</span></span>
            </div>
            
            <!-- Controles -->
            <div class="flex items-center gap-3 md:gap-6">
                <!-- Selector de Idioma -->
                <div class="lang-switch-container">
                    <button type="button" onclick="setLanguage('es')" id="btn-es" class="lang-btn">ES</button>
                    <button type="button" onclick="setLanguage('en')" id="btn-en" class="lang-btn active">EN</button>
                </div>

                <!-- Enlaces Escritorio -->
                <div class="hidden md:flex gap-6 items-center font-bold">
                    <a href="#servicios" class="text-white hover:text-yellow-500" data-i18n="nav-services">Services</a>
                    <a href="#contacto" class="text-white hover:text-yellow-500" data-i18n="nav-contact">Contact</a>
                    <button type="button" onclick="launchAction('tel:+19049167532')" class="bg-yellow-500 text-black px-6 py-2 rounded-full font-black flex items-center gap-2 transition active:scale-95">
                        <i class="fas fa-phone-alt"></i> 904 916 7532
                    </button>
                </div>

                <!-- Botón Menú Móvil -->
                <button type="button" onclick="toggleMenu()" class="md:hidden text-yellow-500 text-2xl p-1">
                    <i class="fas fa-bars"></i>
                </button>
            </div>
        </div>

        <!-- Menú Móvil -->
        <div id="mobile-links" class="hidden flex flex-col gap-4 py-4 text-center md:hidden border-t border-gray-900 mt-2 bg-black">
            <a href="#servicios" class="text-white py-2 font-bold uppercase" data-i18n="nav-services" onclick="toggleMenu()">Services</a>
            <a href="#contacto" class="text-white py-2 font-bold uppercase" data-i18n="nav-contact" onclick="toggleMenu()">Contact</a>
            <button type="button" onclick="launchAction('tel:+19049167532')" class="bg-yellow-500 text-black py-4 rounded font-black uppercase mx-4 flex items-center justify-center gap-2 transition active:scale-95">
                <i class="fas fa-phone-alt"></i> 904 916 7532
            </button>
        </div>
    </nav>

    <header class="hero-section">
        <div class="max-w-4xl mx-auto px-4">
            <h1 class="text-4xl md:text-7xl font-black mb-4 uppercase">
                <span data-i18n="hero-title-1">Roadside Help</span> <span class="text-yellow-500">24/7</span>
            </h1>
            <p class="text-lg md:text-xl mb-8 text-gray-200 uppercase font-bold" data-i18n="hero-subtitle">Jacksonville, Florida</p>
            <button type="button" onclick="launchAction('tel:+19049167532')" class="bg-yellow-500 text-black px-10 py-5 rounded-full font-black text-xl uppercase inline-block shadow-2xl transition transform hover:scale-105 active:scale-95">
                <i class="fas fa-phone-alt mr-2"></i> <span data-i18n="hero-btn">Call Emergency</span>
            </button>
        </div>
    </header>

    <section id="servicios" class="py-16 px-4 max-w-6xl mx-auto">
        <h2 class="text-3xl font-black text-center mb-10 uppercase" data-i18n="services-title">Our Services</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
            <div onclick="openModal('Mecánica', 'Mechanics')" class="cursor-pointer bg-gray-100 p-8 text-center rounded-xl border-b-4 border-yellow-500 hover:bg-yellow-50 transition active:scale-95">
                <i class="fas fa-tools text-3xl mb-4 text-black"></i>
                <h3 class="font-bold uppercase text-sm" data-i18n="service-mechanics">Mechanics</h3>
                <p class="text-xs text-gray-400 mt-2 uppercase font-bold" data-i18n="tap-to-book">Book now</p>
            </div>
            <div onclick="openModal('Batería', 'Battery')" class="cursor-pointer bg-gray-100 p-8 text-center rounded-xl border-b-4 border-yellow-500 hover:bg-yellow-50 transition active:scale-95">
                <i class="fas fa-car-battery text-3xl mb-4 text-black"></i>
                <h3 class="font-bold uppercase text-sm" data-i18n="service-battery">Battery</h3>
                <p class="text-xs text-gray-400 mt-2 uppercase font-bold" data-i18n="tap-to-book">Book now</p>
            </div>
            <div onclick="openModal('Llantas', 'Tires')" class="cursor-pointer bg-gray-100 p-8 text-center rounded-xl border-b-4 border-yellow-500 hover:bg-yellow-50 transition active:scale-95">
                <i class="fas fa-tire text-3xl mb-4 text-black"></i>
                <h3 class="font-bold uppercase text-sm" data-i18n="service-tires">Tires</h3>
                <p class="text-xs text-gray-400 mt-2 uppercase font-bold" data-i18n="tap-to-book">Book now</p>
            </div>
            <div onclick="openModal('Gasolina', 'Fuel')" class="cursor-pointer bg-gray-100 p-8 text-center rounded-xl border-b-4 border-yellow-500 hover:bg-yellow-50 transition active:scale-95">
                <i class="fas fa-gas-pump text-3xl mb-4 text-black"></i>
                <h3 class="font-bold uppercase text-sm" data-i18n="service-fuel">Fuel</h3>
                <p class="text-xs text-gray-400 mt-2 uppercase font-bold" data-i18n="tap-to-book">Book now</p>
            </div>
            <div onclick="openModal('Apertura de Puertas', 'Lockout Service')" class="cursor-pointer bg-gray-100 p-8 text-center rounded-xl border-b-4 border-yellow-500 hover:bg-yellow-50 transition active:scale-95">
                <i class="fas fa-key text-3xl mb-4 text-black"></i>
                <h3 class="font-bold uppercase text-sm" data-i18n="service-lockout">Lockout Service</h3>
                <p class="text-xs text-gray-400 mt-2 uppercase font-bold" data-i18n="tap-to-book">Book now</p>
            </div>
            <div onclick="openModal('Otros', 'Others')" class="cursor-pointer bg-gray-100 p-8 text-center rounded-xl border-b-4 border-yellow-500 hover:bg-yellow-50 transition active:scale-95">
                <i class="fas fa-plus-circle text-3xl mb-4 text-black"></i>
                <h3 class="font-bold uppercase text-sm" data-i18n="service-others">Others</h3>
                <p class="text-xs text-gray-400 mt-2 uppercase font-bold" data-i18n="tap-to-book">Book now</p>
            </div>
        </div>
    </section>

    <section id="contacto" class="bg-black text-white py-16 px-4">
        <div class="max-w-5xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-10">
            <div>
                <h2 class="text-4xl font-black text-yellow-500 mb-4 uppercase" data-i18n="contact-title">Write Us</h2>
                <p class="text-gray-400 mb-2 font-bold uppercase" data-i18n="contact-subtitle">Immediate help</p>
                <p class="text-yellow-500 mb-6 text-sm font-bold">triana.zada.g03@gmail.com</p>
                <button type="button" onclick="launchAction('tel:+19049167532')" class="text-3xl font-black text-white hover:text-yellow-500 flex items-center gap-3 transition active:scale-95">
                    <i class="fas fa-phone-alt text-yellow-500"></i> 904 916 7532
                </button>
            </div>

            <div class="bg-white p-6 rounded-2xl text-black">
                <form onsubmit="return false;" class="flex flex-col gap-4">
                    <input type="text" id="form-name" placeholder="Your Name">
                    <textarea id="form-msg" placeholder="What is the issue?" rows="3"></textarea>
                    <button type="button" onclick="prepareContactMail(event)" class="bg-black text-yellow-500 font-black py-4 rounded-lg uppercase text-center block hover:bg-yellow-500 hover:text-black transition active:scale-95 w-full">
                        <span data-i18n="contact-send">Send via Gmail</span>
                    </button>
                </form>
            </div>
        </div>
    </section>

    <div id="mBox" class="modal-simple" onclick="closeModal()">
        <div class="bg-white p-6 rounded-2xl max-w-sm w-full text-black shadow-2xl relative" onclick="event.stopPropagation()">
            <h3 id="mTitle" class="text-xl font-black mb-4 uppercase text-center border-b-2 border-yellow-500 pb-2">Book Service</h3>
            <form onsubmit="return false;" class="flex flex-col gap-4">
                <input type="hidden" id="sInput">
                <div id="others-container" class="hidden">
                    <label class="text-[10px] font-bold uppercase text-gray-400 ml-1" data-i18n="label-specify">Specify Service (max 100 chars)</label>
                    <input type="text" id="modal-specify" maxlength="100" placeholder="What service do you need?" class="bg-yellow-50">
                </div>
                <input type="text" id="modal-name" placeholder="Your Name">
                <input type="tel" id="modal-phone" placeholder="Your Phone">
                <input type="text" id="modal-loc" placeholder="Location">
                <button type="button" onclick="prepareBookingMail(event)" class="bg-black text-white font-black py-4 rounded-lg uppercase text-center block shadow-lg w-full active:scale-95">
                    <span data-i18n="modal-confirm">Confirm via Gmail</span>
                </button>
                <button type="button" onclick="closeModal()" class="text-xs text-gray-400 font-bold uppercase mt-2 w-full">
                    <span data-i18n="modal-close">Cancel</span>
                </button>
            </form>
        </div>
    </div>

    <footer class="bg-gray-100 py-12 text-center">
        <p class="text-xs text-gray-400 font-black uppercase">© 2025 Triana Garage - Roadside Assistance</p>
    </footer>
</div>

<script>
    const MY_EMAIL = "triana.zada.g03@gmail.com";

    const translations = {
        es: {
            "nav-services": "Servicios", "nav-contact": "Contacto",
            "hero-title-1": "Auxilio Vial", "hero-subtitle": "Jacksonville, Florida",
            "hero-btn": "Llamar Emergencia", "services-title": "Nuestros Servicios",
            "service-mechanics": "Mecánica", "service-battery": "Batería",
            "service-tires": "Llantas", "service-fuel": "Gasolina",
            "service-lockout": "Apertura de Puertas", "service-others": "Otros",
            "contact-title": "Escríbenos", "contact-subtitle": "Atención inmediata",
            "contact-send": "Enviar por Gmail", "modal-confirm": "Confirmar en Gmail",
            "modal-close": "Cancelar", "tap-to-book": "Agendar ahora",
            "mail-booking-subj": "Nueva Cita: ", "mail-contact-subj": "Solicitud de Auxilio Vial",
            "label-specify": "Especificar Servicio (máx 100 car.)"
        },
        en: {
            "nav-services": "Services", "nav-contact": "Contact",
            "hero-title-1": "Roadside Help", "hero-subtitle": "Jacksonville, Florida",
            "hero-btn": "Call Emergency", "services-title": "Our Services",
            "service-mechanics": "Mechanics", "service-battery": "Battery",
            "service-tires": "Tires", "service-fuel": "Fuel",
            "service-lockout": "Lockout Service", "service-others": "Others",
            "contact-title": "Write Us", "contact-subtitle": "Immediate help",
            "contact-send": "Send via Gmail", "modal-confirm": "Confirm via Gmail",
            "modal-close": "Cancel", "tap-to-book": "Book now",
            "mail-booking-subj": "New Booking: ", "mail-contact-subj": "Roadside Assistance Request",
            "label-specify": "Specify Service (max 100 chars)"
        }
    };

    let currentLang = 'en';

    function setLanguage(lang) {
        currentLang = lang;
        document.querySelectorAll('[data-i18n]').forEach(el => {
            const key = el.getAttribute('data-i18n');
            el.innerText = translations[lang][key];
        });
        
        document.getElementById('btn-es').classList.toggle('active', lang === 'es');
        document.getElementById('btn-en').classList.toggle('active', lang === 'en');
        
        document.getElementById('form-name').placeholder = lang === 'es' ? "Tu Nombre" : "Your Name";
        document.getElementById('form-msg').placeholder = lang === 'es' ? "¿Qué problema tienes?" : "What is the issue?";
        document.getElementById('modal-name').placeholder = lang === 'es' ? "Tu Nombre" : "Your Name";
        document.getElementById('modal-phone').placeholder = lang === 'es' ? "Tu Teléfono" : "Your Phone";
        document.getElementById('modal-loc').placeholder = lang === 'es' ? "Ubicación" : "Location";
        document.getElementById('modal-specify').placeholder = lang === 'es' ? "¿Qué servicio necesita?" : "What service do you need?";
    }

    function toggleMenu() {
        document.getElementById('mobile-links').classList.toggle('hidden');
    }

    function openModal(serviceEs, serviceEn) {
        const title = currentLang === 'es' ? serviceEs : serviceEn;
        document.getElementById('mTitle').innerText = title;
        document.getElementById('sInput').value = title;
        const othersContainer = document.getElementById('others-container');
        if (serviceEs === 'Otros' || serviceEn === 'Others') {
            othersContainer.classList.remove('hidden');
        } else {
            othersContainer.classList.add('hidden');
        }
        document.getElementById('mBox').classList.add('show');
        document.body.style.overflow = 'hidden';
    }

    function closeModal() {
        document.getElementById('mBox').classList.remove('show');
        document.body.style.overflow = 'auto';
    }

    function launchAction(url) {
        const dummy = document.createElement('a');
        dummy.href = url;
        dummy.target = '_blank';
        dummy.rel = 'noopener noreferrer';
        dummy.click();
        setTimeout(() => dummy.remove(), 100);
    }

    function prepareBookingMail(e) {
        if(e) { e.preventDefault(); e.stopPropagation(); }
        const service = document.getElementById('sInput').value;
        const specified = document.getElementById('modal-specify').value;
        const name = document.getElementById('modal-name').value || (currentLang === 'es' ? "Cliente" : "Customer");
        const phone = document.getElementById('modal-phone').value || "No provisto";
        const loc = document.getElementById('modal-loc').value || "No provista";
        let finalService = service;
        if (specified) finalService += ` (${specified})`;
        const subject = translations[currentLang]['mail-booking-subj'] + finalService;
        const body = `Hello Triana Garage,\n\nI request a booking for: ${finalService}\n\nName: ${name}\nPhone: ${phone}\nLocation: ${loc}`;
        const mailtoUrl = `mailto:${MY_EMAIL}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
        launchAction(mailtoUrl);
        setTimeout(closeModal, 300);
        return false;
    }

    function prepareContactMail(e) {
        if(e) { e.preventDefault(); e.stopPropagation(); }
        const name = document.getElementById('form-name').value || (currentLang === 'es' ? "Cliente" : "Customer");
        const msg = document.getElementById('form-msg').value || "";
        const subject = translations[currentLang]['mail-contact-subj'];
        const body = `Message from: ${name}\n\n${msg}`;
        const mailtoUrl = `mailto:${MY_EMAIL}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
        launchAction(mailtoUrl);
        return false;
    }

    document.addEventListener('DOMContentLoaded', () => setLanguage('en'));
</script>

</body>
</html>
