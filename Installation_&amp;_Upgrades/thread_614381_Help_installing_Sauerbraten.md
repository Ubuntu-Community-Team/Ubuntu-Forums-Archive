---
title: "Help installing Sauerbraten"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by anliveyak on 2007-11-15
i need help installing the game sauerbraten. i have installed it once before but i lost the files. i can go through all of the instalition steps...
cd sauerbraten/src
make clean
make
make install
all of the commands can be ran with returning no error but i find no "sauerbraten_unix" file like i did last time

---

### Post by Roque2 on 2007-11-16
why not just install it using the synaptic repo. Its on there

---

### Post by anliveyak on 2007-11-16
the install they are offering is an older version and i am looking ot install 2007-8-29

---

### Post by Roque2 on 2007-11-17
whats the difference in that version

---

### Post by ssugrim on 2007-11-18
The version that comes from the Multiverse Repo isn't able to connect to most servers as there is some difference in the protocol between client versions.

---

### Post by groovomata on 2007-12-06
I just did a google search 'sauerbraten debian' and got this page:
[http://packages.debian.org/unstable/games/sauerbraten](http://packages.debian.org/unstable/games/sauerbraten)
It has debian packages from August 19th, 2007. 
I'm gonna give 'em a try and post back.
Erik.

---

### Post by groovomata on 2007-12-06
Well, I seem to be having some problems running sauerbraten too. I ran sauerbraten and got this back in the terminal:
> erik@silver-surfer:/usr/lib/games/sauerbraten$ sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: GeForce Go 7300/PCI/SSE2 (NVIDIA Corporation)
Driver: 2.1.1 NVIDIA 100.14.19
Rendering using the OpenGL 1.5 GLSL shader path.
init: console
cannot find font definitions


Anyone know what this means?

---

### Post by groovomata on 2007-12-06
I did a reinstall and now it seems to work!

---

### Post by ssugrim on 2007-12-11
Howdy, I tired that deb too. I got the amd64 version, cuz I'm running the 64 bit 7.10 ubuntu. I got the same error 

init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: GeForce 6800 Series GPU/PCI/SSE2 (NVIDIA Corporation)
Driver: 2.1.1 NVIDIA 100.14.19
Rendering using the OpenGL 1.5 GLSL shader path.
init: console
cannot find font definitions

but reinstalling did help me. :(

---

### Post by ssugrim on 2007-12-12
Fixed it! the deb that was linked updated the engine, but not the data. I installed the deb linked to before via: dpkg -i debname. 

I then went to the debian repo and looked up [http://packages.debian.org/sid/sauerbraten-data](http://packages.debian.org/sid/sauerbraten-data)

Sure enough there was an updated version of the sauerbraten-data deb as well. dpkg -l | grep sauerbraten showed I had the older data deb installed. Once I installed the new one, it ran great!

Thanks for all the help guys!:)

---

