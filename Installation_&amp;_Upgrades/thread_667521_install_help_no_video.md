---
title: "install help no video"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by soulreaver2991 on 2008-01-14
hey guys new to linux i've been using gusty 7.10 on my laptop for about two months now and having no problems with it other than the aircard but thats not the problem
installed gusty on my desktop pc from alternate install cd due to live cd would not allow my viedo card to work. once installed i get the ubuntu loading screen but instead of going to the login screen i get a no signal on my screen i don't have a cable to use the built in video on the motherboard and i think that it's toast anyway. i found some threads that say it could need the restricted drivers installed to allow system to use the video card but i have no idea on how to go abouts doing it. any help would be very much appreciated   thanks in advance 

Greg

---

### Post by polmir on 2008-01-14
```
 sudo update-pciids
```

and display info:

```
lspci -vv
```

---

### Post by soulreaver2991 on 2008-01-14
ok thanks will that code allow me to install the drivers and if so how would i get to a single user mode while loading up. because i cant even get to the log on screen i only can see the ubuntu screen with loading bar then nothing, do i have to press esc  upon loading to get into a terminal window?

---

### Post by soulreaver2991 on 2008-01-15
ok so i tried to enter the codes provided in the command line upon start up but still not able to get to my desktop. the machine boots up normal and i get the loading screen i hear the login chime but i get not display monitor just flashes no signal.

is there a way to access the restricted drivers from the command line start up without having to have internet access. i have my ethernet plugged in but if i try any command that requires the system to download anything i get a host look up failed message.

i'm not sure if it would do anything different but could i may have a better chance with installing kbubuntu instead ?? or i'm i just looking at the same issue 

once again thanks for the help 

oh and the video card i have in the machine is a ati radeion rv100 if that helps at all

---

### Post by Sef on 2008-01-15
Have you gone into the BIOS and and booted up from recovery mode?

---

### Post by soulreaver2991 on 2008-01-15
i've tried going into recovery mode but to be honest i really have no idea what to do 
i get a comand line and looks like i'm running terminal but not sure where to start from there

---

### Post by soulreaver2991 on 2008-01-16
ok so after further digging through terminal i find a i/o error so i'm thinking that its coming down to the video card is shot so i'm going to go get a new one and try that out anyone have any suggestion on what cards to go with or stay away from ?

---

### Post by soulreaver2991 on 2008-02-12
fixed the issue thanks to digging around on here and to everyone that helped 

had to completly disable the floppy drive from the bios and the motherboard jumpers 
so back up and running just having fun getting my ati card working to a way that i like 

thanks again everyone

---

