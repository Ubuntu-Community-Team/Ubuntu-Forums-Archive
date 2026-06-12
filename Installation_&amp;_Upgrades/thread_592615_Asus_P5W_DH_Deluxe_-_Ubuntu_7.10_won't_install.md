---
title: "Asus P5W DH Deluxe - Ubuntu 7.10 won't install"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by thomasmahler on 2007-10-26
I searched the other threads, but none of them are conclusive.

I'm on an Asus P5W DH Deluxe System, which is set to AHCI, so my SATA Drives work nicely. Doesn't matter whether the J-Micron Controller is on or off, the Ubuntu Live DVD won't even start at all.

Anyone who's using the same motherboard who could help out?

---

### Post by Pumalite on 2007-10-26
Try Alternate CD.

---

### Post by thomasmahler on 2007-10-26
I did. Same thing.

---

### Post by wpshooter on 2007-10-26
Are you saying that you don't get a Ubuntu boot screen menu at **all **or do you get some type of error message instead ?

---

### Post by Brebs on 2007-10-26
[This thread](http://forums.gentoo.org/viewtopic-t-536867.html) will probably be of interest, for the P5W.

If AHCI doesn't work, change that temporarily to "enhanced" in the BIOS. So you can install Linux and upgrade the kernel.

---

### Post by thomasmahler on 2007-10-27
Sorry for not posting any error messages or more informative things, haven't had the time to document this yet.

Well, I get to the boot screen where it says "Start or Install Ubuntu" - as soon as I press Enter, the screen goes black, it tries to load things up and then it just stops, the screen stays black, nothing ever happens.

So, what you're saying is that I can install Ubuntu in IDE Mode, update the kernel and then switch back to AHCI? If I install Windows in IDE and then switch to AHCI, I can't boot the thing at all anymore. This board seems to have a ******** of trouble with Ubuntu, sadly.

---

### Post by Brebs on 2007-10-27
Yeah, I've noticed that Windows has that incredibly stupid restriction about AHCI. Happily, Linux will use whatever method's been set in the BIOS, as long as the kernel is reasonably recent and has the right drivers.

It might be the display driver that is causing the black screen - boot in *text* mode.

This motherboard works with Linux, but I would recommend sticking to SATA drives, and thus ignoring the Jmicron controller and IDE drives.

---

### Post by ljuba on 2007-10-27
I have exactly the same problem, After booting the screen goes black and that's it.

I have Asus P5B Deluxe (Intel P965 chipset)
And I have SATA DVD-RW Optiarc, JMicron controller is disabled
Keyboard and mouse are both USB, and graphic card is Nvidia 8800.

Is there anyway that I can boot?

---

### Post by thomasmahler on 2007-10-27
Yeah, the P5B and the P5W DH are very close to one another - I also used to have a P5B, but gave it up for the P5W.

Text Mode installation won't work either, I've downloaded the alternate version by accident before and tried Text Mode - no joy.

---

### Post by infinitezero on 2007-10-27
I know this is not the perfect work around, but you could install 7.04 and then use apt-get to upgrade to 7.10. I have the Asus P5W DH Deluxe and it gives me nothing but problems, if have found that it also does not play nice with other Distros as well.


iz

---

### Post by thomasmahler on 2007-10-27
7.04 also doesn't boot up with AHCI enabled.

---

### Post by ergosteur on 2008-01-21
I installed on my P5W DH with the live cd, all i had to do was disable the jmicron controller for the installation.The ICH7 is in AHCI mode. AFter install, re-enable the jmicron controller in AHCI mode in the BIOS, and it works great. I'm using the Jmicron esata port and IDE port, and all the ICH7 SATA ports except for ez-backup.

Boot is a bit slow, verbose shows probing the sata2 port (ezbackup) and getting slow response. eventually this times out and all is fine.

---

### Post by cometcomputing on 2008-02-17
I have the same board, and I gave up on it after 2 days, maybe in a later release it will work better. 

Harry Yeh
[http://www.cometcomputing.com](http://www.cometcomputing.com)

---

### Post by Pumalite on 2008-02-17
It's the Intel 965 chipset. Google 'Ubuntu and Intel 965 chipset' and you'll get lots of hits.

---

### Post by ergosteur on 2008-02-19
> **Pumalite said:**
> It's the Intel 965 chipset. Google 'Ubuntu and Intel 965 chipset' and you'll get lots of hits.

The P5W DH Deluxe is 975X -based.

---

### Post by Pumalite on 2008-02-19
Thanks for the correction.

---

### Post by chazaw on 2008-03-22
I installed on the ASUS P5W DH Deluxe and the only problem I ran into was waiting for the probing of SATA2 to time out and worked fine.

I did have the JMicron controller disabled and ICH7 was in AHCI mode 

see [http://forums.pcper.com/showthread.php?t=444831 ]("http://forums.pcper.com/showthread.php?t=444831") for instructions on switching Windows to AHCI Mode

Other than that works fine except for every boot must wait for SATA probe to time out.

---

