---
title: "Ubuntu 18.04"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by g1gsw2 on 2018-08-02
What has happened in 18.04?  I have 2 old Packard Bell computers that in the past I just put in a CD or USB stick with the image on, booted and installed with 18.04, including the latest .01 release, I never get to the GUI on either machine.  My son has an old Aldi notebook that is the same.  I have retired the downloads from various sites and they all do the same.  I am not new to Ubuntu and have used it for a long time on desktops and servers in the past.  I used to work for a major IT company and used it on their servers, never having any problems.

I can boot from any other distribution I try and install it but not Ubuntu 18.04, 16.04 was fine on all 3 machines.

Come on Ubuntu [SIZE=5]fix it [SIZE=2]If other [/SIZE][/SIZE]distributions can boot and install why doesn't yours?

---

### Post by Autodave on 2018-08-02
I think that I would check your download to make sure it was good.  I have installed 18.04 on 9 machines: some quite old, and have no problems at all on any of them.

---

### Post by poorguy on 2018-08-02
Without knowing the*** model numbers ***and or*** system specs*** of those computers it is possible the ***18.04 kernel*** doesn't support the hardware being used in them.

I also suggest checking the iso downloads as already suggested by ***Audodave***.

[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

[https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

---

### Post by maglin2 on 2018-08-02
I recall having the same issue with an old E-machines PC on move to (I think) 12.04. I sorted it (for a while till the power supply died) by adding a kernel boot flag (nolapic if I recall correctly - but may have been acpi=off).

Or it could be a 32bit machine issue?

---

### Post by g1gsw2 on 2018-08-03
Autodave I have checked the md5sum of the downloads and they are fine, I am not new to Linux, I have used it for around 10 years plus and Ubuntu since early days.

poorguy One PC is a Packard Bell UT0W-BEN it has a triple core AMD processor and 4GB of ram, the other a Packard Bell imedia 1W800 which is an Intel Pentium dual core with 4GB of ram.  Both bought about 3 years ago secondhand.

maglin2 I have tried several different boot flags all to the same result it never brings up the gui sits with the Linux boot list on the screen with the cursor flashing.  acpi=off was one of them.  Up until 18.04 I have run Ubuntu with very little trouble.  The mother Linux Debian boots with no problems and runs Gnome fine on both machines the 1W800 still has 16.04 installed and it runs fine on that.

Looking around it does seem others have had similar issues and not been able to resolve them.

---

### Post by missmoondog on 2018-08-03
fwiw, and no real help to op, i have installed lubuntu 18.04 on all 7 of my machines with no issues what so ever. a couple of them are so old they don't even support sse2. 

your machines sound like they should be able to handle ubuntu though. maybe you do need that acpi=off switch though.

---

### Post by poorguy on 2018-08-03
Those look quite capable of running most ***Linux Distros*** and I had no idea that*** Packard Bell*** was still building computers.

If ***Ubuntu 16.04*** was installed and working on these I would reinstall ***Ubuntu 16.04*** as it is ***supported until 2021***.

---

### Post by Acharn on 2018-08-05
OK, I was never able to install 16.04. Apparently it was something to do with a change made to x-windows. The good people at bugzilla sent me a copy of 17.04 Alpha, and that had a fix and I was able to use it. Now with 18.04.1, I am able to boot the live DVD if I use the nomodeset setting, but it takes about 10 minutes and does not recognize my Nvidia GE Force GTX 1050 card. Instead, it says my graphics are "llvmpipe (LLVM 6.0, 128 bits). So I have a desktop distorted but usable at 1024x768. Other threads say I need to install the Nvidia proprietary drivers, which I cannot do with the live CD, and I am reluctant to install until I can see the graphics. I'm picking up fragments here and there, so apparently this is something to do with the x-windows default drivers, again, which is extremely annorying. Would it be worth waiting for a 18.04.2 or 3 and hope for a fix? I guess I could try to install to a USB stick.

---

