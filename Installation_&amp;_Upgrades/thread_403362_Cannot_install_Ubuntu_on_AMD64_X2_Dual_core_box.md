---
title: "Cannot install Ubuntu on AMD64 X2 Dual core box"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by bpasham on 2007-04-06
I assembled my first AMD64 system with M2A-VM mother board 4x1GB 667 RAM and Athlon 64 X2 4200+ 65W processor and 2x300GB Seagate SATA2/300 disks. I was unable o install any version of Ubuntu on it. The maximum I reach is with 6.06LTS 64 server install .. and it cannot detect NIC device on the board . installation cannot continue after.

Any solution to this problem?

Once I select Install to Hard Disk .. the screen goes blank after the starting vmlinuz .....
I removed **Quite** from the install line by pressing F6 and now it gives an indication thast it is halting after getting Kernel Panic ..

Several people suggested to add noapic, nomce etc to boot line. But to add this on the install cd?

I even tried 7.04 beta editions .. same problem ..

Please Help me ....
__________________
Bhuvan

---

### Post by Blackforge on 2007-04-06
> **bpasham said:**
> I assembled my first AMD64 system with M2A-VM mother board 4x1GB 667 RAM and Athlon 64 X2 4200+ 65W processor and 2x300GB Seagate SATA2/300 disks. I was unable o install any version of Ubuntu on it. The maximum I reach is with 6.06LTS 64 server install .. and it cannot detect NIC device on the board . installation cannot continue after.

Any solution to this problem?

Once I select Install to Hard Disk .. the screen goes blank after the starting vmlinuz .....
I removed **Quite** from the install line by pressing F6 and now it gives an indication thast it is halting after getting Kernel Panic ..

Several people suggested to add noapic, nomce etc to boot line. But to add this on the install cd?

I even tried 7.04 beta editions .. same problem ..

Please Help me ....
__________________
Bhuvan

Hi, looks like that Asus board uses the Realtek RTL8111B Gb LAN chip.  Have you tried 6.10?  Looks like some people have gotten other motherboards that share this NIC chip, albeit with their own problems.

[http://ubuntuforums.org/showthread.php?t=388403](http://ubuntuforums.org/showthread.php?t=388403)

I also read somewhere about some people having problems with their NIC not being initialized properly in Linux without having to Warm boot to an OS that had the NIC working (such as Windows).  Just a quick something to try..

---

### Post by bpasham on 2007-04-08
Yep .. I tried 6.06, 6.10, 7.04 beta .. all editions (server, minimal boot, desktop, live cd) nothing works. Thought .. it might some problem with mother board or bios .. i changed the MotherBoard (at first I tried with ECS nForce4M-A) as well .. same problem ..

Please Help..
Bhuvan

---

### Post by maynoth on 2007-04-12
same problem here... running latest bios... windows xp loads fine.. :C

---

### Post by Blackforge on 2007-04-14
It wasn't clear if the LiveCD portion was working for you from the original post.  But if you're able to a terminal it shouldn't matter.

So here's a couple of ideas:

A)  This requires another computer to stuff.

You can try going to the Realtek site and downloading the network drivers:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

You will also need to download the kernel-headers and development tools in order to compile them and install.  You can download all of these from another machine and copy them to a CD/floppy/usb stick to install into the Live Distro (or whatever you decide to use).

B)  Compile driver in a VM before the install

You can pre-compile the module for the network driver before you attempt to install in a VM or something similar.  Then from there you can copy the compiled module to a disk to install in the Live session.

C)  Probably the easiest option but not cheapest.  

Buy a cheap network card or USB network adapter for the install and then update with the drivers above.  Then after that remove the added card and use the built in.

---

### Post by felker2 on 2007-05-06
I had the same with the 32-bit version of Kubuntu on my Asus M2A-VM HDMI with AMD 690G chipset, and solved this by adding the boot options "pci=nomsi irqpoll noapic acpi=off" to the live-CD-boot (F6), to the GRUB options (ESC, e, e, b) and to menu.lst. And then everything went OK.

And I have the onboard SATA chipset set to "IDE", not "AHCI" nor "RAID".

BTW: The 64-bit Kubuntu needs the same setting, but even then does not see the SATA drive.

---

