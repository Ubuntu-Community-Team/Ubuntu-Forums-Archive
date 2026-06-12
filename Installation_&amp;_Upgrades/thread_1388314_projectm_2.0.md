---
title: "projectm 2.0"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by spiritech on 2010-01-22
ive tried to install projectm 2.0

i create the directories run cmake then make && sudo make install

and i then get this message

make: *** No rule to make target `install'. Stop.

can anyone help.

---

### Post by spiritech on 2010-01-23
i now get this message

make: *** No targets specified and no makefile found. Stop

do i need to make my own make file maybe?

someone please help i am completely new to all this and trying my best. i figure i need a make file. shouldnt it come with the download or is that the point of opensource you have to make your own. i tried 2 threads for projectm one didnt install the othet by sammyD worked but kept crashing when clicking on playlist or settings/config etc. might just stick with that for now. 

it would be nice to understand the stages at which software gets released and inturn how much work is involved on the install.

---

### Post by spiritech on 2010-01-23
ok i managed to make && make sudo install   projectM 2.0.1 
is up and running ok now.

---

### Post by spiritech on 2010-01-23
/src

---

### Post by revslaughter on 2010-01-23
Totally cryptic, but you managed to fix exactly the same problem I was having.

I navigated to /src in the tar they had on sourceforge, ran cmake . && sudo make install. Worked great.

Now, to get PulseAudio to work...

---

### Post by spiritech on 2010-01-23
its still not running 100%. the preset duration keeps jumping around, the smooth transition isnot workink either just hardcuts to next preset, no smoothness atall. :confused: f2 & f3 not working either.

maybe its a problem just with projectM 2.0.1 so have to decided uninstall and try older version then reinstall 2.0.1 and see if it updates and uses both.? 

is there another way i can do this.

---

### Post by spiritech on 2010-01-23
did you uninstall in the synaptic might resolve some conflicts.

---

### Post by revslaughter on 2010-01-23
I'm assuming you're talking about PusleAudio?

hmmm...actually projectM isn't working: 

```
projectM-pulseaudio: error while loading shared libraries: libprojectM-qt.so.1: cannot open shared object file: No such file or directory

```

I can find links to this library in the source directory I downloaded, but not the library itself - and even if I did find it, I wouldn't know where projectM is looking for it.

---

### Post by spiritech on 2010-01-23
> **revslaughter said:**
> I'm assuming you're talking about PusleAudio?

hmmm...actually projectM isn't working: 

```
projectM-pulseaudio: error while loading shared libraries: libprojectM-qt.so.1: cannot open shared object file: No such file or directory

```I can find links to this library in the source directory I downloaded, but not the library itself - and even if I did find it, I wouldn't know where projectM is looking for it.

are you running ubuntu 9.10?

---

