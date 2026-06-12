---
title: "xserver won't play nice"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by Daniel Rehm on 2005-08-20
I've been using Ubuntu for about 3 months but recently upgraded to an MSI K8N Neo4 mobo with a nice new Radeon X700 Pro. I got the hardware cobbled together, installed my windows partition (which I am happy to report went almost completely unused for the past few months) just to make sure everything worked, then I installed Ubuntu. Sadly, X just doesn't want to play nice with my new setup. I get an error saying that Ubuntu "cannot start the X Server. It is likely that it is not set up correctly." Then it tells me it's disabling X server and I will have to restart gdm when I get it reconfigured. 

I dug around a little and found the sudo dpkg-reconfigure xserver-xorg command, ran it, picked out my hardware, etc. Still no luck. 

Any input would be greatly appreciated.

---

### Post by Daniel Rehm on 2005-08-21
Pretty much the only advice I can find online is to reconfigure X. Unless there's some option I'm missing, I'm not sure what to do. It autodetects everything just fine.

---

### Post by FLeiXiuS on 2005-08-21
Could you possibly give us any log files?  /var/log/Xorg*

Also have you installed the ati drivers?  

If not try using the VESA display driver.  Edit /etc/X11/xorg.conf and navigate to your video card configurations.  Change the driver to vesa.

---

### Post by Tuna13 on 2005-08-28
[QUOTE=Daniel Rehm]I've been using Ubuntu for about 3 months but recently upgraded to an MSI K8N Neo4 mobo with a nice new Radeon X700 Pro. I got the hardware cobbled together, installed my windows partition (which I am happy to report went almost completely unused for the past few months) just to make sure everything worked, then I installed Ubuntu. Sadly, X just doesn't want to play nice with my new setup. I get an error saying that Ubuntu "cannot start the X Server. It is likely that it is not set up correctly." Then it tells me it's disabling X server and I will have to restart gdm when I get it reconfigured. 

I dug around a little and found the sudo dpkg-reconfigure xserver-xorg command, ran it, picked out my hardware, etc. Still no luck. 

Any input would be greatly appreciated.[/QUOTE]
 HEY! me got same problem! same videocard with same problem! installed ubuntu on my bro's com, 32bit processor with the ubuntu i386 and was fine. i'm using x86 and intel 64bit processor and with a ati x700 pro video card and i get the exact same problem! my bro uses 9600 pro and he's fine. someone help me tooo? linux noob here

---

