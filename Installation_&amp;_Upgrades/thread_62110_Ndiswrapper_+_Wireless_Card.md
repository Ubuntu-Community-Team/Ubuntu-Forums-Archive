---
title: "Ndiswrapper + Wireless Card"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by kekocsi20 on 2005-09-03
Hi, 

I just recently installed Ubuntu on my Averatec laptop and having problem getting my Lynksys wireless card working (PCMCIA). 
Lynksys card: WPC11 version 4. 

Reading through the hardware support site this card should work fine with Ubuntu. 
I am fairly new to Linux and don't have a lot of experience. 

I think I might have a problem with my ndiswrapper.  When I go to the usr/src folder there are two ndiswrapper folder (1.1 and 2.6 ) - not sure if this make any difference. 

Following instruction on Ubuntu Wiki's site I downloaded ndiswrapper 1.1 and installed it. (The instructions I followed: [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) )

When I install the wireless card driver (ndiswrapper -i file.inf) it installs the driver. When I want to view the installed driver (ndiswrapper -l) I get the following error: 
Driver installed: 
"driver name"  invalid driver

For my wireless card I tried two drivers: one that came with the card (from cd) and one I downloaded from Realtek website. 

If you know the solution please help.  I am ready to switch from Windows to Linux, but I need to get my wireless working. 

Thanks,

---

### Post by essexman on 2005-09-03
[QUOTE=kekocsi20]Hi, 

I just recently installed Ubuntu on my Averatec laptop and having problem getting my Lynksys wireless card working (PCMCIA). 
Lynksys card: WPC11 version 4. 

Reading through the hardware support site this card should work fine with Ubuntu. 
I am fairly new to Linux and don't have a lot of experience. 

I think I might have a problem with my ndiswrapper.  When I go to the usr/src folder there are two ndiswrapper folder (1.1 and 2.6 ) - not sure if this make any difference. 

Following instruction on Ubuntu Wiki's site I downloaded ndiswrapper 1.1 and installed it. (The instructions I followed: [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) )

When I install the wireless card driver (ndiswrapper -i file.inf) it installs the driver. When I want to view the installed driver (ndiswrapper -l) I get the following error: 
Driver installed: 
"driver name"  invalid driver

For my wireless card I tried two drivers: one that came with the card (from cd) and one I downloaded from Realtek website. 

If you know the solution please help.  I am ready to switch from Windows to Linux, but I need to get my wireless working. 

Thanks,[/QUOTE]
I have the same card and it it working fine using the same procedure on the ndiswrapper wiki that you used.
The difference is that I used the newer 1.2 version.
Keep trying and rechecking. Try checking you /root/bash_history file to see what you actually typed in.

 I used the Linksys driver from the supplied CD.
LSWLNDS5.INF
This is case sensitive.


Maybe have another try with these suggestions and let me know how you get on?

best of Luck

---

### Post by kekocsi20 on 2005-09-03
Hi, 

I tried it  couple more times and it is still not working. 
I installed ndiswrapper 1.2 then

ndiswrapper -l   > no drivers installed
ndiswrapper -i /media/cdrom0/WindXP/LSWLNDS5.INF (path to CD) > Installing lswlnds5
ndiswrapper -l > Installed ndis drivers: lswlnds5    invalid driver

I am keep getting this same error message. 
I also have a DELL 1350 card and when I tried to install the driver for it got the same error message. 

Not sure what to do next. 

Any help is much appreciated.

---

### Post by essexman on 2005-09-04
[QUOTE=kekocsi20]Hi, 

I tried it  couple more times and it is still not working. 
I installed ndiswrapper 1.2 then

ndiswrapper -l   > no drivers installed
ndiswrapper -i /media/cdrom0/WindXP/LSWLNDS5.INF (path to CD) > Installing lswlnds5
ndiswrapper -l > Installed ndis drivers: lswlnds5    invalid driver

I am keep getting this same error message. 
I also have a DELL 1350 card and when I tried to install the driver for it got the same error message. 

Not sure what to do next. 

Any help is much appreciated.[/QUOTE]

Hi

You are doing things correctly, it may be worth removing everything and starting again as detailed in the [Ndiswrapper HOWTO](http://ubuntuforums.org/showthread.php?t=25683&page=2&pp=10&highlight=ndiswrapper+invalid) 

Removing and starting again gives you the chance to use your knowledge afresh. 

Then check out advice given to someone with a different [Linksys Card](http://ubuntuforums.org/showthread.php?t=56572&highlight=ndiswrapper+invalid) The principles are the same and it may be the one thing that makes the difference.

also this [recent HOWTO](http://ubuntuforums.org/showthread.php?t=19978&highlight=ndiswrapper+invalid) gives the same advice in a different way.  The only things I can suggest changing are to copy the INF cat and SYS files to a seperate directory in you home folder and maybe to download the files from the Linksys website.  It is strange that this worked in Windows but not Linux.  It wont make you feel much better but I would like to reassure you that it can work in Linux.  My card is wouldn't work at all for Wndows2000, and my laptop now only runs Ubuntu.

Please keep trying

---

