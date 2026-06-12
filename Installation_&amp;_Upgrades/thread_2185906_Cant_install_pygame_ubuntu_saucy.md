---
title: "Cant install pygame ubuntu saucy"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by sakuritita on 2013-11-04
Hello:

I've been trying to install pygame for ubuntun saucy. Im using the text editor for my code and the terminal for running the code. I tried to install it according to the instructions i found in the pygame website but i get an error when installing dependecies

[COLOR=#808080]*#install dependencies*[/COLOR]
sudo apt-get install mercurial python3-dev python3-numpy ffmpeg \
    libsdl-image1.[COLOR=#ff4500]2[/COLOR]-dev libsdl-mixer1.[COLOR=#ff4500]2[/COLOR]-dev libsdl-ttf2.[COLOR=#ff4500]0[/COLOR]-dev libsmpeg-dev \
    libsdl1.[COLOR=#ff4500]2[/COLOR]-dev  libportmidi-dev libswscale-dev libavformat-dev libavcodec-dev
 
[COLOR=#808080]*# Grab source*[/COLOR]
hg clone [https://bitbucket](https://bitbucket).[COLOR=black]org[/COLOR]/pygame/pygame
 
[COLOR=#808080]*# Finally build and install*[/COLOR]
[COLOR=#dc143c]cd[/COLOR] pygame
python3 setup.[COLOR=black]py[/COLOR] build
sudo python3 setup.[COLOR=black]py[/COLOR] install

This is the error 

E: Package 'mercurial' has no installation candidate
E: Unable to locate package libsdl-image1-2-dev
E: Unable to locate package libsdl-mixer1.2-dev
E: Couldn't find any package by regex 'libsdl-mixer1.2-dev'
E: Unable to locate package libsdl-ttf2.0-dev
E: Couldn't find any package by regex 'libsdl-ttf2.0-dev'
E: Unable to locate package libsmpeg-dev
E: Unable to locate package libpormidi-dev

Anyone kwows a solution for this? THanks

---

