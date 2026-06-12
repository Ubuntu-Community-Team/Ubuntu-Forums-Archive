---
title: "Help with new installation"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by coasthi on 2005-06-03
Greetings all , I been using linux SuSE for a wile and last night I installed Ubuntu on my new computer I been hearing lot of good things about it and wanted to try it out and run it as my main OS. The problem I’m having is after the installation every time I boot up my computer the login screen doesn’t want to appear all I’m getting is a black screen with white writing and it asks for a user name and pass word after I type it in it still stays as black screen with white writing, I tried a few things but still can’t get to the main desktop. Any help would be greatly appreciated

---

### Post by codejunkie on 2005-06-03
what is happening is the xserver can't start what kind of video card do you have by chance?
and also you did'nt do a server install did you because if you did, the server install does'nt include a gui interface by default.

---

### Post by coasthi on 2005-06-03
Thank you very much for your reply codejunkie I have ATI sapphire radeon 9200SE  I can’t get to the main desktop it looks like it’s in recovery mode for some reason

---

### Post by coasthi on 2005-06-03
When I did the installation it didn’t ask what type of installation I wanted it just went ahead and installed it self. I know the other versions of Linux ask for what type of installation you want but this time it didn’t so I don’t know if it is a server install or not.

---

### Post by codejunkie on 2005-06-03
if you just pressed enter without specifing commands it's probably a standard install 
here is a binary driver howto form the wiki about installing the ati driver hope it helps 
[http://www.ubuntulinux.org/wiki/FinishInstallationHowto/view?searchterm=binary%20driver](http://www.ubuntulinux.org/wiki/FinishInstallationHowto/view?searchterm=binary%20driver)
it may be more help to you than i am because i dont have an ati card and i don't want to tell you something that's not wright. if this doesn't answer your questions or you need help with something else let me know i'll try me best to help you.

---

### Post by coasthi on 2005-06-03
Thank you codejunkie I will have read of it and  give it a try and see how go.

---

### Post by codejunkie on 2005-06-03
i was just thinking you said you just switched from suse if your card worked with suse out of the box suse uses the vesa driver for a default install so you could just manually edit your xorg.conf file with nano /etc/X11/xfree86.conf to use the vesa driver to get the gui working until you install the ati driver or use the command,
sudo dpkg-reconfigure xserver-xfree86 just choose vesa for the driver in the first section and follow the steps it usually autodetects everything like keyboard mouse and monitor so just pressing enter works perfectly but it gives you the option to change seetings if you want hope this helps.

---

### Post by coasthi on 2005-06-03
Thank you codejunkie for your help I did have a read of  [http://www.ubuntulinux.org/wiki/Fin...binary%20driver](http://www.ubuntulinux.org/wiki/Fin...binary%20driver) and it was some help because now I have the “fglrx-driver installed but I still can’t get on to my desktop. I am running a AMD64 and it’s Ubuntu 4.10 “Warty Warthog”  any more help would be greatly appreciated and don’t worry if it doesn’t work I can always reinstall the OS it is no problems to do.

---

### Post by codejunkie on 2005-06-03
well since your using warty i give you a little wrong advice there sorry about that i just assumed you were using hoary cause i found the post the hoary section try this
it should work if the card worked in suse.
sudo dpkg-reconfigure xserver-xfree86 and follow these steps 

just choose vesa for the driver in the first section and follow the steps it usually autodetects everything like keyboard mouse and monitor so just pressing enter works perfectly but it gives you the option to change seetings if you want hope this helps.

---

### Post by coasthi on 2005-06-03
Very sorry codejunkie I’m new to this forum and still trying to find my way around. I didn't know I was in the rong section, I will give it a go and let you know how I go. Thank you again very much for your help

---

### Post by codejunkie on 2005-06-03
sorry for similar posts i just had to change the xorg to xfree86 that warty uses since they switched to the newer xserver in the latest releases i hope this helps i was also  reading about the amd64 on the forums and someone said that the only way warty would work for him is by doing a server install and the sudo apt-get update and then sudo apt-get install ubuntu-desktop that might be something to try if all else fails 
and by the way as an ex suse user once ubuntu is installed you love it no more dependency issues and no more searching the web all day for rpms to fix those dependency issues just smooth sailing.

---

### Post by codejunkie on 2005-06-03
[QUOTE=coasthi]Very sorry codejunkie I’m new to this forum and still trying to find my way around. I didn't know I was in the rong section, I will give it a go and let you know how I go. Thank you again very much for your help[/QUOTE]

no problem im happy to help i just did'nt want to tell you the wrong thing and it take you longer to install and you give up on it it's a great distro and i just did'nt want you to get fed up trying to get x up and running hang in there it's worth it.

---

### Post by coasthi on 2005-06-03
YEPPPPY :) I managed to get it working! Thank you very much for all your time and help codejunkie I’m very grateful for your help. Yes it is a great distro and looking forward to using it and getting a lot of enjoyment out of it. And also thank you for the great and friendly forum it’s very helpful.

---

### Post by codejunkie on 2005-06-04
glad to help and welcome to ubuntu  :) i also recommend you check out [www.ubuntuguide.org](www.ubuntuguide.org) it shows a lot of great howtos like installing java and flash 
dvd mp3 playback stuff that can't be installed by default because of copyright restrictions plus it's an allaround great linux howto.

---

