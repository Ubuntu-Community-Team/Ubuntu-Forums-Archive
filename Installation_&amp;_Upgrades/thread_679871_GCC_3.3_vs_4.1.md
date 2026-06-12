---
title: "GCC 3.3 vs 4.1"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by urangela on 2008-01-27
I need to install the mozilla java plugin (and also the JRE ?) to access some online educational materials.
When I went into synaptic, I easily found the Sun-Java6-plugin packages, and I was about 
to install them, when I noticed that In addition to the package itself, the "To be Installed" window indicated that gcc 3.3, and libstdc++ 5. I opened up the terminal, and used locate and grep to determine that I have gcc version 4.1, and libstdc++ version 6.0.9 already installed. So I have a few questions:

1. Is there any way to install the java stuff I need, and still keep my current versions of
 gcc and libstdc++ ? 

2. If I do just go ahead with the installation, (using synaptic) will those changes affect my system? -- I noticed severl files in /usr/share/doc with gcc 3.4 in the name, but when I entered the command gcc -v it listed the version as 4.1.3. 

I am rather new to Ubuntu, and linux in general, and I am still really confused as to how dependencies work, but I would assume that installing gcc 3.3 would create problems for any applications that rely on the newer version. I'm less apprehensive about installing libstdc++ 5, because ( I think) it is just a matter of adding a new library to the contents of /usr/lib. Of course it might be that there is no problem, and I should just go ahead w/ the install; but I am kind of in a time crunch and at the moment I can't afford to have to re-partition/re-install the OS.

Any advice is appreciated

---Adam

I am running ubuntustudio, Gutsy (ver. 7.10) with a realtime kernel (2.6.22-14-rt)
and Gnome 2.20.1; on an acer aspire (5570z) 32 bit dual core

---

