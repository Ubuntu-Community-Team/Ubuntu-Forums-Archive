---
title: "Ubuntu Server 12.04 LTS Haswell problems"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by developerzero on 2013-06-18
I'm working on a new system build based on Intel's new Haswell platform, and I've run into a problem: I can get into the BIOS, boot the disc, run memtest, but if I select Install Ubuntu Server, the screen goes black. Here is my relevant info:

Hardware
MSI MPower Z87 (stock v1.0 BIOS, flashed BIOS A to v1.2)
[http://us.msi.com/product/mb/Z87-MPOWER.html](http://us.msi.com/product/mb/Z87-MPOWER.html)
Intel i7-4770 (base model)
16 GB (2x8) PC3-15000 1866MHz (clocked at 1600MHz to match CPU) Patriot Memory (PD000327-PVI316G186C0K)
*NVidia Quadro FX1800
*ATI Radeon 2600XT
LG WH14NS40 OEM Blu-Ray Burner
Several old stock SATA Hard Drives (various Makes/Models) non-RAID
LEPA G1000-MA PSU
Corsair H110 Liquid CPU Cooler
Cooler Master Storm Trooper Case

*=Stock parts I had on hand I used for testing. Probably won't end up in final build once I can afford some newer graphics cards.

As mentioned above, I'm trying to install Ubuntu Server 12.04 LTS, and when I click Install Ubuntu Server, the screen just goes black.

Here's what I've tried so far:
-checked all the hardware, connections, etc.
-Ran memtest (~10 hours, almost 6 passes)
-Checked the disc (on a different computer, wouldn't run on this system). I also used the same disc to install another system a couple weeks ago, so I'm fairly certain the disc isn't the issue.
-Tried all the above graphics devices (onboard, Quadro, & Radeon) with two different known working displays, including the NOMODESET flag.

I'm down to just a couple possible ideas, but was wondering if anyone has any suggestions. The only two parts I can think of that might be giving me errors are the Blu-Ray drive (I've never used either a Blu-Ray drive nor a SATA Disc drive, and don't know if that might give me problems) and the Displayport ports on the GPUs (all my monitors are DVI/VGA/HDMI, I haven't gotten my DP-DVI adapter yet, and I've never used DisplayPort) and I doubt either of those is the cause, since I've otherwise been able to load the disc and see output, except when I try to install the OS.

Any Suggestions?

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by sanderj on 2013-06-18
From the Ubuntu boot options, press F6, then select boot options and remove "quiet splash". See [https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line](https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line)
Then boot, and follow what is going on.

If that doesn't work, play with the ACPI / APIC / etc settings in the boot options.

---

### Post by developerzero on 2013-06-18
Just a quick follow-up: I noticed I was using 12.04.1 LTS, and burned a copy of 12.04.2 LTS. It now gets past the "Install Ubuntu Server" screen, but locks up on the "Detecting Hardware to find CD-ROM drives" screen. I'll try so more stuff later. Any other suggestions?

---

### Post by developerzero on 2013-06-19
Well, I've located the problem, and have a temporary solution, but it's not ideal.

Turns out there's something wrong with the ASMedia 1061 SATA ports on the board (I had my disc drive plugged in there so I could reserve the Intel ports for RAID) that causes boot-time errors; apparently it's been a problem for a couple of years. I've managed to get the OS installed by plugging the disc drive ino the Intel ports, but I'd rather have the Intel Ports reserved for RAID (I'd like to get 5x 4TB drives in a RAID 5, plus a 128-256+ GB mSATA SSD for the OS). Note that I also tried plugging the disc drive back into the ASMedia ports after the OS was installed and working, but it still prevented the OS from booting.

Ive got a couple other things I'm going to look at after I get some sleep.

---

### Post by stefaneb on 2013-06-25
I just had a long argument with a Z87 based Asus motherboard.  In the BIOS, it shipped with the secure boot set to only boot Windows OSes.  Believe me, my son learned some new words after I discovered this.  Switching the BIOS to allow any OS to boot and the install went well, now working on graphics support (not going so well).

---

### Post by gordintoronto on 2013-06-25
Is there some reason you need to use Server? Desktop can do everything Server can do, and it's a lot easier to manage.

If Ubuntu is the only OS on your SSD, 32 GB is more than enough. About once a year, you should run: sudo apt-get clean

Usually a black-screen problem is the video card, interesting to see another option.

---

