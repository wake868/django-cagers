# django-cagers
---

## TAILWINDCSS QUICK SETUP FOR DJANGO PROJECTS
---
##### CREATE A TAILWINDCSS FOLDER INSIDE ROOT DJANGO PROJECT FOLDER TO HOLD PACKAGES
mkdir _tailwindcss 
cd _tailwindcss

##### INSTALL AND INIT TAILWINDCSS
npm install -D tailwindcss
npx tailwindcss init

##### CONFIGURE TEMPLATE PATHS TO WATCH
module.exports = {
  content: ["./templates/**/*.{html,js}"], // THIS WOULD WATCH THE GLOBAL DJANGO TEMPLATES FOLDER
  theme: {
    extend: {},
  },
  plugins: [],
}

##### CREATE THE SOURCE CSS FILE (static/src/tailwind.css)
@tailwind base;
@tailwind components;
@tailwind utilities;

##### ADD YOUR COMPILED CSS FILE TO THE BASE TEMPLATE
{% load static %}
<link rel="stylesheet" href="{% static 'css/main.css' %}">


##### ADD THE GLOBAL STATIC & TEMPLATES DIR TO SETTINGS.PY
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [
            BASE_DIR / "templates",
        ]

STATICFILES_DIRS = [
    BASE_DIR / 'static',
]

##### BUILD/WATCH COMMAND (below builds to static/css/output.css)
npx tailwindcss -i ./static/src/tailwind.css -o ./static/css/main.css --watch