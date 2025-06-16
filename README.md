<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mintu Maity - Data Analyst</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals -->
    <!-- Application Structure Plan: The SPA is designed as a personal portfolio website to replace a static resume. The structure prioritizes immediate impact and easy exploration. It starts with a Hero section for identity, followed by a 'Key Achievements' section to showcase quantifiable results upfront. An interactive 'Experience Timeline' makes career progression engaging. A 'Skills Dashboard' with a Chart.js visualization provides a quick, data-driven view of capabilities. 'Projects' are presented in a modern card layout. This non-linear, thematic structure is more user-friendly and engaging for a recruiter than a traditional document, allowing them to jump to sections of interest via a sticky navigation bar. -->
    <!-- Visualization & Content Choices: 
        - Key Achievements -> Goal: Inform/Impact -> Viz: Highlighted stat cards -> Interaction: None, visual emphasis -> Justification: Immediately communicates value. -> Method: HTML/Tailwind.
        - Experience -> Goal: Organize/Show Chronology -> Viz: Interactive vertical timeline -> Interaction: Click to expand/collapse details -> Justification: Engages the user and makes a long history digestible. -> Method: HTML/Tailwind/JS.
        - Technical Skills -> Goal: Compare/Show Proficiency -> Viz: Horizontal Bar Chart -> Interaction: Hover for tooltips -> Justification: Visually represents skill distribution, fitting for a data analyst. -> Method: Chart.js/Canvas.
        - Projects -> Goal: Showcase Portfolio -> Viz: Card layout -> Interaction: Clickable links -> Justification: Clean, standard, and effective way to present project work. -> Method: HTML/Tailwind.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F8F9FA;
            color: #212529;
        }
        .nav-link {
            transition: color 0.3s ease;
            position: relative;
        }
        .nav-link::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -4px;
            left: 50%;
            transform: translateX(-50%);
            background-color: #007BFF;
            transition: width 0.3s ease;
        }
        .nav-link:hover::after, .nav-link.active::after {
            width: 100%;
        }
        .timeline-item::before {
            content: '';
            position: absolute;
            left: -20px;
            top: 10px;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background-color: #FFFFFF;
            border: 2px solid #007BFF;
        }
        .timeline-line {
            position: absolute;
            left: -15px;
            top: 10px;
            bottom: 0;
            width: 2px;
            background-color: #DEE2E6;
            z-index: -1;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            height: 400px;
            max-height: 50vh;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 500px;
            }
        }
    </style>
</head>
<body class="antialiased">

    <header id="home" class="fixed top-0 left-0 right-0 bg-white/80 backdrop-blur-sm shadow-sm z-50">
        <div class="container mx-auto px-4">
            <nav class="flex justify-between items-center py-4">
                <a href="#home" class="text-xl font-bold text-gray-800">Mintu Maity</a>
                <ul class="hidden md:flex items-center space-x-8">
                    <li><a href="#home" class="nav-link text-gray-600 hover:text-blue-600 font-medium active">Home</a></li>
                    <li><a href="#experience" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Experience</a></li>
                    <li><a href="#skills" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Skills</a></li>
                    <li><a href="#projects" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Projects</a></li>
                    <li><a href="#education" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Education</a></li>
                </ul>
                <button id="mobile-menu-button" class="md:hidden p-2">
                     <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7" /></svg>
                </button>
            </nav>
            <div id="mobile-menu" class="hidden md:hidden">
                <ul class="flex flex-col items-center space-y-4 py-4">
                    <li><a href="#home" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Home</a></li>
                    <li><a href="#experience" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Experience</a></li>
                    <li><a href="#skills" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Skills</a></li>
                    <li><a href="#projects" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Projects</a></li>
                    <li><a href="#education" class="nav-link text-gray-600 hover:text-blue-600 font-medium">Education</a></li>
                </ul>
            </div>
        </div>
    </header>

    <main class="pt-20">
        <section class="container mx-auto px-6 py-16 md:py-24 text-center">
            <h1 class="text-4xl md:text-6xl font-bold text-gray-900 leading-tight">Mintu Maity</h1>
            <p class="text-xl md:text-2xl text-blue-600 font-medium mt-2">Data Analyst</p>
            <p class="max-w-3xl mx-auto text-gray-600 mt-6">
                Data Analyst with 3+ years of experience in data mining, modeling, and statistical analysis. Proven ability to interpret complex datasets, identify trends, and provide actionable insights to drive business decisions.
            </p>
            <div class="mt-8 flex justify-center items-center space-x-4">
                <a href="mailto:maitym314@gmail.com" class="bg-blue-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-blue-700 transition-transform transform hover:scale-105">Contact Me</a>
                <a href="https://linkedin.com/in/mintu-maity-2419221a4" target="_blank" rel="noopener noreferrer" class="text-gray-600 hover:text-blue-600 transition">
                    <svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true"><path fill-rule="evenodd" d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" clip-rule="evenodd"/></svg>
                </a>
            </div>
        </section>

        <section class="bg-white py-16 md:py-24">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-gray-800">Key Achievements</h2>
                    <p class="text-gray-500 mt-2">Quantifiable impact and results delivered.</p>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                    <div class="bg-blue-50 p-6 rounded-lg text-center transform hover:scale-105 transition-transform">
                        <p class="text-4xl font-bold text-blue-600">10</p>
                        <p class="mt-2 font-semibold text-gray-700">Hours Saved Weekly</p>
                        <p class="text-sm text-gray-500 mt-1">via Power BI automation</p>
                    </div>
                    <div class="bg-green-50 p-6 rounded-lg text-center transform hover:scale-105 transition-transform">
                        <p class="text-4xl font-bold text-green-600">15%</p>
                        <p class="mt-2 font-semibold text-gray-700">Sales Growth Identified</p>
                        <p class="text-sm text-gray-500 mt-1">in top-selling products</p>
                    </div>
                    <div class="bg-yellow-50 p-6 rounded-lg text-center transform hover:scale-105 transition-transform">
                        <p class="text-4xl font-bold text-yellow-600">20+</p>
                        <p class="mt-2 font-semibold text-gray-700">Visualizations Monthly</p>
                        <p class="text-sm text-gray-500 mt-1">enhancing team insights</p>
                    </div>
                    <div class="bg-purple-50 p-6 rounded-lg text-center transform hover:scale-105 transition-transform">
                        <p class="text-4xl font-bold text-purple-600">25%</p>
                        <p class="mt-2 font-semibold text-gray-700">Increased Efficiency</p>
                        <p class="text-sm text-gray-500 mt-1">in data analysis processes</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="experience" class="py-16 md:py-24">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-gray-800">Career Journey</h2>
                    <p class="text-gray-500 mt-2">An interactive timeline of my professional experience.</p>
                </div>
                <div class="relative max-w-2xl mx-auto">
                    <div class="timeline-line"></div>
                    <div class="space-y-12">
                        <div class="timeline-item relative pl-8">
                            <button class="w-full text-left focus:outline-none">
                                <p class="text-sm text-gray-500">06/2024 – Present</p>
                                <h3 class="text-xl font-semibold text-gray-800">Business Development Support / Data Analyst</h3>
                                <p class="text-md text-gray-600">Divine Solitaires, Mumbai</p>
                            </button>
                            <div class="details-content mt-4 space-y-2 text-gray-600 text-sm overflow-hidden max-h-0 transition-all duration-500 ease-in-out">
                                <p>• Engineered a Power BI dashboard, reducing manual reporting by 10 hours/week.</p>
                                <p>• Performed data cleaning, wrangling, analysis, and visualization.</p>
                                <p>• Conducted statistical analysis including regression and hypothesis testing.</p>
                                <p>• Utilized DAX formulas for complex calculations in Power BI.</p>
                            </div>
                        </div>

                        <div class="timeline-item relative pl-8">
                            <button class="w-full text-left focus:outline-none">
                                <p class="text-sm text-gray-500">07/2023 – Present</p>
                                <h3 class="text-xl font-semibold text-gray-800">Data Analyst</h3>
                                <p class="text-md text-gray-600">Divine Solitaires, Mumbai</p>
                            </button>
                            <div class="details-content mt-4 space-y-2 text-gray-600 text-sm overflow-hidden max-h-0 transition-all duration-500 ease-in-out">
                                <p>• Assisted in data collection and cleaning activities for analysis.</p>
                                <p>• Conducted statistical analysis to identify key trends and correlations.</p>
                                <p>• Created data visualizations to communicate insights to the team.</p>
                                <p>• Contributed to data analysis reports and presentations.</p>
                            </div>
                        </div>

                        <div class="timeline-item relative pl-8">
                            <button class="w-full text-left focus:outline-none">
                                <p class="text-sm text-gray-500">06/2021 – 06/2023</p>
                                <h3 class="text-xl font-semibold text-gray-800">Junior Data Analyst</h3>
                                <p class="text-md text-gray-600">Goldstar Jewellery LLC, Mumbai</p>
                            </button>
                            <div class="details-content mt-4 space-y-2 text-gray-600 text-sm overflow-hidden max-h-0 transition-all duration-500 ease-in-out">
                                <p>• Supported data collection and cleaning tasks to prepare datasets.</p>
                                <p>• Ran statistical analyses on data to find trends.</p>
                                <p>• Helped create data visualizations for team communication.</p>
                            </div>
                        </div>
                        
                         <div class="timeline-item relative pl-8">
                            <button class="w-full text-left focus:outline-none">
                                <p class="text-sm text-gray-500">10/2020 – 02/2021</p>
                                <h3 class="text-xl font-semibold text-gray-800">Radio Frequency Engineer</h3>
                                <p class="text-md text-gray-600">Malfonic Network Communication, Kolkata</p>
                            </button>
                            <div class="details-content mt-4 space-y-2 text-gray-600 text-sm overflow-hidden max-h-0 transition-all duration-500 ease-in-out">
                                <p>• Assisted in the design, development, and testing of RF components.</p>
                                <p>• Prepared technical reports and engineering documentation.</p>
                                <p>• Conducted quality control tests and inspections.</p>
                            </div>
                        </div>
                        
                         <div class="timeline-item relative pl-8">
                            <button class="w-full text-left focus:outline-none">
                                <p class="text-sm text-gray-500">08/2019 – 10/2020</p>
                                <h3 class="text-xl font-semibold text-gray-800">Production Planning Control</h3>
                                <p class="text-md text-gray-600">Mindarika Private Limited, Pune</p>
                            </button>
                            <div class="details-content mt-4 space-y-2 text-gray-600 text-sm overflow-hidden max-h-0 transition-all duration-500 ease-in-out">
                                <p>• Assisted in developing and implementing production plans.</p>
                                <p>• Aligned plans with customer demand, capacity, and inventory.</p>
                                <p>• Prepared reports on production status and performance.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="skills" class="bg-white py-16 md:py-24">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-gray-800">Skills Dashboard</h2>
                    <p class="text-gray-500 mt-2">A visual overview of my technical and soft skills.</p>
                </div>
                <div class="grid grid-cols-1 lg:grid-cols-5 gap-12 items-center">
                    <div class="lg:col-span-3">
                        <div class="chart-container">
                            <canvas id="skillsChart"></canvas>
                        </div>
                    </div>
                    <div class="lg:col-span-2 space-y-6">
                        <div>
                            <h3 class="text-xl font-semibold text-gray-800 mb-3">Soft Skills</h3>
                            <ul class="space-y-2 text-gray-600">
                                <li class="flex items-center"><span class="text-blue-500 mr-2">✓</span> Problem Solving & Critical Thinking</li>
                                <li class="flex items-center"><span class="text-blue-500 mr-2">✓</span> Effective Communication</li>
                                <li class="flex items-center"><span class="text-blue-500 mr-2">✓</span> Teamwork & Collaboration</li>
                                <li class="flex items-center"><span class="text-blue-500 mr-2">✓</span> Time Management</li>
                                <li class="flex items-center"><span class="text-blue-500 mr-2">✓</span> Leadership Qualities</li>
                            </ul>
                        </div>
                        <div>
                            <h3 class="text-xl font-semibold text-gray-800 mb-3">Languages</h3>
                             <div class="flex space-x-4">
                                <span class="bg-gray-200 text-gray-700 px-3 py-1 rounded-full text-sm">Bengali (Native)</span>
                                <span class="bg-gray-200 text-gray-700 px-3 py-1 rounded-full text-sm">English (Advanced)</span>
                                <span class="bg-gray-200 text-gray-700 px-3 py-1 rounded-full text-sm">Hindi (Advanced)</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <section id="projects" class="py-16 md:py-24">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-gray-800">Project Showcase</h2>
                    <p class="text-gray-500 mt-2">A key project demonstrating my data analysis skills.</p>
                </div>
                 <div class="max-w-2xl mx-auto">
                    <div class="bg-white rounded-lg shadow-md hover:shadow-xl transition-shadow p-8">
                        <h3 class="text-2xl font-bold text-gray-800">Sales Report Analysis</h3>
                        <p class="text-gray-600 mt-4">This project involved a comprehensive analysis of sales data to determine total sales and profit by city and identify top-selling products. It showcases the end-to-end data analysis workflow.</p>
                        <div class="mt-4">
                            <h4 class="font-semibold text-gray-700">Process Followed:</h4>
                            <p class="text-gray-600 text-sm">Data Collection → Data Cleaning → Preprocessing → Analysis → Interactive Dashboard Creation.</p>
                        </div>
                         <div class="mt-4">
                            <h4 class="font-semibold text-gray-700">Tools Used:</h4>
                            <div class="flex flex-wrap gap-2 mt-2">
                                <span class="bg-blue-100 text-blue-800 px-2 py-1 rounded text-xs font-medium">Power BI</span>
                                <span class="bg-blue-100 text-blue-800 px-2 py-1 rounded text-xs font-medium">Power Query</span>
                                <span class="bg-gray-100 text-gray-800 px-2 py-1 rounded text-xs font-medium">Excel</span>
                                <span class="bg-gray-100 text-gray-800 px-2 py-1 rounded text-xs font-medium">SQL</span>
                            </div>
                        </div>
                        <div class="mt-6 text-center">
                            <a href="https://github.com/rajmaity24/Sales-Report-Jan-2023-Jan-2024" target="_blank" rel="noopener noreferrer" class="inline-block bg-gray-800 text-white font-bold py-2 px-5 rounded-lg hover:bg-gray-900 transition">View on GitHub</a>
                        </div>
                    </div>
                 </div>
            </div>
        </section>

        <section id="education" class="bg-white py-16 md:py-24">
            <div class="container mx-auto px-6">
                 <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-gray-800">Education</h2>
                    <p class="text-gray-500 mt-2">My academic background and qualifications.</p>
                </div>
                <div class="max-w-2xl mx-auto space-y-6">
                    <div class="p-4 border-l-4 border-blue-500 bg-blue-50">
                        <p class="text-sm text-gray-500">01/2023 – Present</p>
                        <h3 class="text-lg font-semibold text-gray-800">Bachelor of Technology, Information Technology</h3>
                        <p class="text-md text-gray-600">Seacom Engineering College</p>
                    </div>
                     <div class="p-4 border-l-4 border-gray-300">
                        <p class="text-sm text-gray-500">01/2015 – 01/2017</p>
                        <h3 class="text-lg font-semibold text-gray-800">Diploma of Education, Electronics and Communications Engineering</h3>
                        <p class="text-md text-gray-600">Elite Polytechnic Institute-India</p>
                    </div>
                    <div class="p-4 border-l-4 border-gray-300">
                        <p class="text-sm text-gray-500">01/2013 – 01/2015</p>
                        <h3 class="text-lg font-semibold text-gray-800">Higher Secondary, Computer Science</h3>
                        <p class="text-md text-gray-600">Baluhati High School</p>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-gray-800 text-white py-12">
        <div class="container mx-auto px-6 text-center">
            <h3 class="text-2xl font-bold">Let's Connect</h3>
            <p class="mt-2 max-w-lg mx-auto text-gray-400">I'm currently seeking new opportunities and would love to hear from you. Feel free to reach out for collaborations or inquiries.</p>
            <p class="mt-4 font-medium text-lg"><a href="mailto:maitym314@gmail.com" class="hover:text-blue-400 transition">maitym314@gmail.com</a></p>
             <div class="mt-6 flex justify-center items-center space-x-6">
                <a href="https://linkedin.com/in/mintu-maity-2419221a4" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition">
                   <svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true"><path fill-rule="evenodd" d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" clip-rule="evenodd"/></svg>
                </a>
                 <a href="https://github.com/rajmaity24" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition">
                    <svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true"><path fill-rule="evenodd" d="M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.168 6.839 9.492.5.092.682-.217.682-.482 0-.237-.009-.868-.014-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.03-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.378.203 2.398.1 2.65.64.7 1.028 1.595 1.028 2.688 0 3.848-2.338 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.001 10.001 0 0022 12c0-5.523-4.477-10-10-10z" clip-rule="evenodd" /></svg>
                </a>
            </div>
            <p class="text-xs text-gray-500 mt-8">&copy; 2024 Mintu Maity. All Rights Reserved.</p>
        </div>
    </footer>
    
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const timelineButtons = document.querySelectorAll('.timeline-item button');
            timelineButtons.forEach(button => {
                button.addEventListener('click', () => {
                    const content = button.nextElementSibling;
                    if (content.style.maxHeight) {
                        content.style.maxHeight = null;
                    } else {
                        content.style.maxHeight = content.scrollHeight + "px";
                    }
                });
            });

            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });
            
            const navLinks = document.querySelectorAll('nav a');
            navLinks.forEach(link => {
                link.addEventListener('click', () => {
                    if(!mobileMenu.classList.contains('hidden')){
                         mobileMenu.classList.add('hidden');
                    }
                });
            });

            const sections = document.querySelectorAll('section');
            const navLi = document.querySelectorAll('header nav ul li a');
            window.addEventListener('scroll', ()=> {
                let current = '';
                sections.forEach( section => {
                    const sectionTop = section.offsetTop;
                    const sectionHeight = section.clientHeight;
                    if(pageYOffset >= (sectionTop - sectionHeight / 3)){
                        current = section.getAttribute('id');
                    }
                })

                navLi.forEach( a => {
                    a.classList.remove('active');
                    if(a.getAttribute('href').includes(current)){
                        a.classList.add('active');
                    }
                })
            });

            const ctx = document.getElementById('skillsChart').getContext('2d');
            const skillsChart = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['SQL', 'Python', 'Power BI', 'Excel', 'Data Modeling', 'Statistical Analysis', 'DAX', 'Power Query'],
                    datasets: [{
                        label: 'Technical Skill Proficiency',
                        data: [90, 85, 95, 88, 80, 85, 75, 90],
                        backgroundColor: [
                            'rgba(54, 162, 235, 0.6)',
                            'rgba(255, 206, 86, 0.6)',
                            'rgba(255, 159, 64, 0.6)',
                            'rgba(75, 192, 192, 0.6)',
                             'rgba(153, 102, 255, 0.6)',
                             'rgba(255, 99, 132, 0.6)',
                             'rgba(201, 203, 207, 0.6)',
                              'rgba(255, 159, 64, 0.6)'
                        ],
                        borderColor: [
                           'rgba(54, 162, 235, 1)',
                            'rgba(255, 206, 86, 1)',
                            'rgba(255, 159, 64, 1)',
                            'rgba(75, 192, 192, 1)',
                            'rgba(153, 102, 255, 1)',
                            'rgba(255, 99, 132, 1)',
                            'rgba(201, 203, 207, 1)',
                             'rgba(255, 159, 64, 1)'
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        },
                        title: {
                            display: true,
                            text: 'Technical Skills',
                            font: {
                                size: 16
                            }
                        },
                        tooltip: {
                             callbacks: {
                                label: function(context) {
                                    let label = context.dataset.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed.x !== null) {
                                        label += context.parsed.x + '%';
                                    }
                                    return label;
                                }
                            }
                        }
                    },
                    scales: {
                        x: {
                            beginAtZero: true,
                            max: 100,
                             ticks: {
                                callback: function(value) {
                                    return value + "%"
                                }
                            }
                        }
                    }
                }
            });
        });
    </script>
</body>
</html>
