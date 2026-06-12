---
title: "Ubuntu 6.10 upgrade to 7.04"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Steven.Moss on 2007-04-23
Hello All,
I have been reading through everything I can find on 6.10 upgrade to 7.04. See some hits about VmWare server. 

As with anything in IT  and internet, I see more negative than positive.  

My machine is a PC Chip Duron 1.4, 1G RAM,  2 internal IDE fixed disks, 1 IDE CD reader, 1 IDE DVD burner, 1 USB scanner and 1 USBusb IDE drive. Runs 6.10 pretty good now, minor problem with hangs on logouts from time to time??? Not sure why, have not dug too deep into it.

I have to run(well choose to use this solution) VmWare Server 1.0.2 for an XP VM for wife's work. 

I put 7.04 on my RD machine here at work. I did an install vs. upgrade due to shutting off my surge strip in the middle of the on-line. It sure looks like 7.04 runs smoother and faster, so I am real interested in upgrading my home machine.

Is there any advise or precautions that any of you all have for me?


Thanks,
Steven

---

### Post by zorkerz on 2007-04-23
You could search each piece of hardware to see if it is supported. That however is alot of work. If you are happy with the currently installed release there is no reason to upgrade seeing as it could very possibly cause problems. 

As to upgrading vs clean install the clean install is safer and more likely to be successful however you can always try to upgrade and be prepared to do a fresh install if bad things happen.

Personally i upgraded a month or so back to feisty with no problems but many others have had problems. 

Make sure you backup your data no matter what you do. You could also get a feisty cd and try it live to check out how all your hardware works and then install from there or reboot and upgrade.

I have not used vmware so cannot speak directly to that but in general i think feisty adds many new and very useful features. I would say if it works it is without a doubt a much improved release. The only question as always in my mind is if it will work without a hitch or not.

Hope that was helpful in some regard and thanks for providing some procrastination material.
Cheers

---

### Post by zvacet on 2007-04-24
If you are going to upgrade I belive you will have to reinstall vmware,because it depends of kernel.

---

### Post by Mongoose on 2007-04-24
VMWare kernel modules are provided by Ubuntu, and the packaged vmware-player working for me on my amd64 box.  I believe they have separate kernel module packages for server for each kernel package as well.   Do however test with a live cd first, or you may be sorry.  I can't stress that enough with all the problems some people are having.  You don't want to install something that may not: boot / have working video / have working input.

I'd suggest holding off it you use the machine for work, and tracking bugs you encounter with the live cd on launchpad to find out when it's safe to upgrade.

---

### Post by HolyJoe on 2007-04-24
Why you upgrade 6.10 to 7.04?
What's new in 7.04?

---

### Post by PradeepSridharan on 2007-04-24
Hi,
    I had initially installed 6.10 but later upgraded to 7.04 using the alternate-CD. My question is as follows.
when I had 6.10, I also installed KDE components from the Synaptic Package Manager by choosing kdebase first and then later adding few more KDE related items.
Now I have upgraded UBUNTU to 7.04 and my question is whether I need to upgrade my KDE as well to 7.04?
If there is a possibility of upgrading then how should I go about doing it.
Thanks & Regards,
Pradeep.

---

### Post by Steven.Moss on 2007-04-24
Well I wanted to correct some minor errors I was having with my machine and 6.10, I went ahead and let the update run. No guts no glory!

Upgrade did not go well at all for me. I did expect to blast VM server, but something broke bad and I lost all network functions, weird messages on boot and down. 

No data loss just hosed my machine up a tad bit, I could hack at it and get it working I imagine, but I can put a fresh install quicker. I will do that tonight.

I am testing qemu right now, that may replace VM server for me and I can use 7.04.  If not then I am just going to go back to 6.10 and forget about upgrading for a while. 

Thanks, SM

---

### Post by zorkerz on 2007-04-24
eh sorry to hear that.  Good luck with the clean up.

---

### Post by PradeepSridharan on 2007-04-25
I did go for the upgrade and I had the same problem of things not working properly. One of the pain points was I had Ubuntu and KDE was installed on top. When I upgraded the Ubuntu alone, I was having all sorts of problems with not only Ubuntu but also with KDE related stuff. I would get hell a lot of errors at logon, video players ceased functioning. However, after an upgrade of KDE as well, things have settled down a bit.However, I had to use the synaptic package manager extensively because certain custom entries in menu.lst were disabled. I had to enable them again, re-import the repositories, and install them all over again to get them working. However, I still have the problem of recording stuff from my mike and running GYACHI which were there even when I was on 6.10.

Good luck with your upgrades.
Pradeep.

---

