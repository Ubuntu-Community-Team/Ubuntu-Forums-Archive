---
title: "Lenovo 3000 J series P4 can't upgrade past 11.10"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by sweet13af on 2014-02-02
[IMG]https://pbs.twimg.com/profile_images/378800000786845236/6ac1a5d4db13eb7f65d8b6cb47195ea7_bigger.jpeg[/IMG]
Help Hoped For? 
Hello I am attempting to upgrade Ubuntu 11.10 to 12.04 OR 13.10 on a (VERY) old machine. the hardware in question

Lenovo 3000 J series P4 Desktop 10+ years old
ubuntu11.10 currently installed
About this machine
Ram= 970.3
CPU= intel Pentium 4 3.20Ghz x2
Graphics= VESA: 6330
OS Type 32-bit
HD= 156.5 GB

I have tried many versions of ubuntu. Blackbuntu 10.10(works-unsupported=problems), Ubuntu 12.04,13.10, Lubuntu 13.10, Mint,Xbuntu 13.10(No WORK)

Primary goal with machine
1. Browser with Flash and Silverlight/Pipelight 
2. Wine with Minecraft/silverlight
3. Music Player
4. Photo Storage
5. Basic Document Development

Building this for little boy he is 6 1/2 but reads at a hi level, not sure but he says level 3. i say he reads "read me" files pretty good. He primarily plays flash games and netflix shark shows. ANy ideas i have taken some photo's and shot video of the result which appears to be a video issue. Most my friends own antiquated machines, been trying to help them revive um, but i'm a green bean with the Ubuntu. All my windows friends live in the realm of the infected, trying to help um with Ubuntu. I read a few posts where peeps had the same machine, but yet to see any resolutions. I guess some nVidia video drivers were retired after Version 11.   H    E    L    P


My Machine Hp Probook 4530s
Triple Boot with Shared Storage Partition
Mac OSX 10.7.5 - Primary Multi-Media Dev Video Editing 
Windoze 7 - you never know when you need it

Ubuntu 13.10 Saucy - Internet Use
RAM= 4Gig
CPU= i3 2350M@2.30Ghz x2
Graphics= intel SandyBridge Mobile
OS Type= 64bit
Partition= 120Gig

Thanks
S.Sweetleaf-

---

### Post by Bucky Ball on 2014-02-03
Are you trying to install from disk or USB? Please post exactly what is happening when you try to boot the install media and where it is stalling and any error messages.

You could try booting from the install media, when you are at the purple screen with the two icons at the bottom, hit F6 and choose 'nomodeset'. Proceed. Any luck?

(If you have taken some photos then post one here showing the issue. Attach it by 'Go Advanced' and using the paperclip icon rather than inserting into the body of your post. Thanks.)

---

### Post by mörgæs on 2014-02-03
It looks like a SIS graphics problem. To be sure, please run (using any Buntu version)
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by sweet13af on 2014-02-03
Thank You for the help. turns out i was able to successfully install backbox.org linux everything is working. thanks for the time and effort

---

### Post by Bucky Ball on 2014-02-03
All good. Please mark the thread as solved. Thanks.

---

