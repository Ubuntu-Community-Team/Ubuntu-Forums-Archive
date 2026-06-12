---
title: "X won't start"
date: 2004-10-27
forum: Installation &amp; Upgrades
---

### Post by zetamannsky on 2004-10-27
[FONT=Times New Roman]I am a complete noobie. The live CD worked fine but when I installed the official version, I could not get X to start.  I have a Dell XPS with an ATI Radeon 9800 XT graphics card. When ubuntu boots, it gets as far as "Starting  Gnome Display Manager". Then the screen blanks for a second or two and reboots adinfinitum. What can I do?[/FONT]

---

### Post by Rancoras on 2004-10-27
Are there any error messages?

---

### Post by zetamannsky on 2004-10-27
[FONT=Times New Roman]There are no error messages. The system just reboots.[/FONT]

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=zetamannsky][FONT=Times New Roman]I am a complete noobie. The live CD worked fine but when I installed the official version, I could not get X to start.  I have a Dell XPS with an ATI Radeon 9800 XT graphics card. When ubuntu boots, it gets as far as "Starting  Gnome Display Manager". Then the screen blanks for a second or two and reboots adinfinitum. What can I do?[/FONT][/QUOTE]


I agree with my 6th sense believing that this is a video card driver problem.  But I can't be certain.  I haven't took a look at the Live CD.

Note: This should go under the Live CD Forum.

---

### Post by Rancoras on 2004-10-27
[QUOTE=FLeiXiuS]Note: This should go under the Live CD Forum.[/QUOTE]

I disagree, it's the regular version giving the problems not the liveCD.  See?


> The live CD worked fine but when I installed the official version

zetamannsky: Do you notice anything unusual during the boot process?  Anything that says "warning" or "failed"?

---

### Post by zetamannsky on 2004-10-27
[FONT=Times New Roman]Are there other video drivers for the ATI Radeon 9800 XT card than came with the official ubuntu CD?[/FONT]

---

### Post by zetamannsky on 2004-10-27
[FONT=Times New Roman]Yes. There was. I can not exactly remember but there was a modprobe failure concerning some pci chip. I would have to go back and look again.[/FONT]

---

### Post by Rancoras on 2004-10-27
Yes, try here:  [http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)

That may help, post back and let us know.

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=Rancoras]Yes, try here:  [http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)

That may help, post back and let us know.[/QUOTE]


Ahh #-o , I thought he meant his LiveCD wasn't working correctly.

Sorry, Its getting a bit late..  :lol:

---

### Post by zetamannsky on 2004-10-27
[FONT=Times New Roman]I will return later. I am now going to reboot ubuntu. Thanks for the help so far.[/FONT][

---

### Post by FLeiXiuS on 2004-10-27
Have you folllowed the instruction for install fglrx?  If so please return feedback, i see you staring at the forum :-P lol, so I had to post!

---

### Post by zetamannsky on 2004-10-27
Zetamannsky back: Rancoras, I went back to look at the boot process. I got two fatal error messages.

(1)  modprobe: Fatal: Error inserting pciehp (/lib/modules/2.6.8.1-3-    386/kernel/drivers/pci/hotplug/pciehp.ko) Operation not permitted.

(2)  modprobe: Fatal: Error inserting shpchp (/lib/modules/2.6.8.1-3-    386/kernel/drivers/pci/hotplug/shpchp.ko) Operation not permitted

---

### Post by FLeiXiuS on 2004-10-27
Are you running as root/sudo?

---

### Post by zetamannsky on 2004-10-27
FleiXius, please forgive my ignorance but what is fglrx? How do I install it?

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=zetamannsky]FleiXius, please forgive my ignorance but what is fglrx? How do I install it?[/QUOTE]

Forgiven :-)

fglrx is the moduble Ubuntu uses for ATI drivers.  

[QUOTE=Rancoras]
Yes, try here: [http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)
[/QUOTE]

Take a look at that page.  It'll show you everything you need to know.

---

### Post by cacofonix on 2004-10-28
[QUOTE=zetamannsky]Zetamannsky back: Rancoras, I went back to look at the boot process. I got two fatal error messages.

(1)  modprobe: Fatal: Error inserting pciehp (/lib/modules/2.6.8.1-3-    386/kernel/drivers/pci/hotplug/pciehp.ko) Operation not permitted.

(2)  modprobe: Fatal: Error inserting shpchp (/lib/modules/2.6.8.1-3-    386/kernel/drivers/pci/hotplug/shpchp.ko) Operation not permitted[/QUOTE]

I used to get the shpchp error message myself I dont think they would be causing the problem (I could be way of the mark though). 

[QUOTE=zetamannsky]FleiXius, please forgive my ignorance but what is fglrx? How do I install it?[/QUOTE]

fglrx is the driver you need to make 3d acceleration work with your radeon card in linux. 

heres a howto to install your drivers 
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

---

### Post by zetamannsky on 2004-10-28
I am going to that page now. Thank you, FleiXius. I will report back on what happens. Thanks again

---

### Post by zetamannsky on 2004-10-28
I just had the opportunity to install fglrx. X then finally started. But I had to change all the references of "ati" to "fglrx" in XF86Config-4. I want to thank everyone for their help. I really appreciate this forum. Keep up the good work.

By the way, if I may. What is the meaning of those modprobe errors that occur on boot up that I posted above?

---

### Post by daniels on 2004-10-28
You can ignore those two errors.  It's trying to load drivers to see if that hardware is installed, but it's failing.  That's not a problem -- you just don't have that hardware.  It should really be quiet about this, but it's not, which is a bug; albeit a minor one.

As for fglrx, all Radeons up to and including the 9200 series (r2xx) are fully supported for 3D acceleration.  You only need fglrx for 3D for r3xx/r4xx (9550/9600 and above).  2D should work just fine on your card -- please report a bug at [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) with the output of lspci, and /var/log/XFree86.0.log.

---

