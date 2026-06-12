---
title: "Virtual PC"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by Thomas Delbeke on 2007-08-22
Hi,

I installed 7.04 on Virtual PC 2007 and followed the community docs for virtual PC 2004. My system is Dell Latitude D510 with XP Home. The installation showed some bugs but almost all could be solved with community docs, but I can't make internet connection. I disabled Windows Live Onecare, but it doesn't help. I tried to install virtual machine additions but it wouldn't autorun. I tried to open virtual CD-ROM drive, and there I can run the DOS/OS2/Windows setup files, but they are all .exe files! I don't have the Wine emulator installed and I can't downlaod it, cause I have no internet connection!

Anyone please?

---

### Post by Thomas Delbeke on 2007-08-27
Hi, nobody replied but I am running for the highscore of views in the unanswered posts listing, so I take it some people want to help. Anyway, I recently upgraded to vista ultimate. When I install 7.04 in virtual pc, I can't proceed because the cursor doesn't work with the touchpad. I stole my moms mouse but it doesn't work either. I installed dapper. Touchpad works but badly. Then I did: $ update-manager -c ; now I have 6.10 (edgy), also with bad touchpad response. Now I just used update manager graphically and went to 7.04 and now the cursor doesn't respond anymore at all to the touchpad. So, I ran device manager in Windows, found that I had PS/2 mouse driver, no updates available. So, I did alt ctrl F5 in feisty and cd /etc and then sudo vim modules. Here I already added tulip on a separate line to get internet connection in dapper (forget to mention earlier in post). Now I changed the psmouse line in ps2mouse, cause I thought that was a bright idea. It was not. So my system is: Dell Latitude D510. Can anyone predict the unix touchpad driver I need? Then I can go apt -get driver. 
Please help me out!
Thank you,
Thomas

---

### Post by maybeway36 on 2007-08-27
Just use [VirtualBox]("http://www.virtualbox.org") instead. I know that works.

---

### Post by Thomas Delbeke on 2007-08-27
Thanks a lot! This is really helpful.

Thomas

---

### Post by Thomas Delbeke on 2007-08-27
Hi, still on Virtual PC 2007:

I figured out I need tpconfig. Problem is: E: Invalid operation tpconfig. So me: apt-get update and sudo vim /etc/apt/sources.list change main repo to universe and apt-get install tpconfig and ... : E:Invalid operation tpconfig.

Any help?

Please, please, please, thank you.

---

### Post by Thomas Delbeke on 2007-08-28
Hi,

so I changed dapper to feisty and added universe and multiverse after main and restricted. Then I did apt-get update. It said some packages were not renewed or something and failed to fetch au.ubuntu.*. I used the site that was in the community docs, then I tried a Belgian mirro. It still wouldn't work. Does anyone know the correct site for that? Thank you.

---

