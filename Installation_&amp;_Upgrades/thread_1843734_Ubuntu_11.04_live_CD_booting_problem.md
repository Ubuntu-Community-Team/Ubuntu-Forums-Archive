---
title: "Ubuntu 11.04 live CD booting problem"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by coolnfunky_raj on 2011-09-13
Hello

I have an Ubuntu 11.04 32-bit live CD. I am trying to boot my 5 year old Dell desktop (Optiplex GX280) with that. The CD is detected and boot starts. After the first screen, the computer automatically restarts and this is happening in an infinite loop. The CD boots fine in a newer Dell laptop. Will 11.04 not boot in older hardware? Is there anything I have to change to make the desktop boot with Ubuntu 11.04? Will older versions work?

Any help is appreciated!

Thanks
Raj

---

### Post by bradenn on 2011-09-13
How much RAM does the old desktop have? I tried installing ubuntu 10.04 on older hardware last year and had some weird responses (erratic behavior and failure to run the live cd or boot the live cd). Turns out that they didn't have enough RAM (I think 10.04 required 512, but not sure). Take a look at the system requirements for 11.04. If those aren't met by your older machine, I think you're wasting your time.

---

### Post by coolnfunky_raj on 2011-09-14
Thanks bradenn for the suggestion. My desktop has 1 GB RAM and 120GB hard drive. This is above minimum required specs. So I dont think that is the problem.

---

### Post by fdrake on 2011-09-14
can you check your bios. try by changing the boot order:
first hdd then cd-rom  or first cd-rom and then hdd. also I advice you to install a LTS release  Ubuntu 10.04 Lucid Lynx , you will find more support for it.

---

### Post by psrdotcom on 2011-09-14
Does the Ubuntu start up screen is coming when you are booting from the cd?

---

### Post by coolnfunky_raj on 2011-09-14
I have already changed the boot order to have cd-rom before hard drive. Booting process actually starts from the disk. I am seeing the first screen (of ubuntu) but then, before it loads the next screen, the system restarts.

---

### Post by mörgæs on 2011-09-14
One of my computers is a GX270, which runs 10.10 well. Have not tried 11.04 on this one, though.

From the boot menu, do you get the option of choosing a memory test?

---

### Post by Linux_junkie on 2011-09-14
> **coolnfunky_raj said:**
> Hello

I have an Ubuntu 11.04 32-bit live CD. I am trying to boot my 5 year old Dell desktop (Optiplex GX280) with that. The CD is detected and boot starts. After the first screen, the computer automatically restarts and this is happening in an infinite loop. The CD boots fine in a newer Dell laptop. Will 11.04 not boot in older hardware? Is there anything I have to change to make the desktop boot with Ubuntu 11.04? Will older versions work?

Any help is appreciated!

Thanks
Raj

From my understanding of 11.04 I believe it requires a graphics card that supports 3D and so it may not support the graphics card you have in your desktop.

---

### Post by foresthill on 2011-09-14
I don't think you need 3D support just to install.

OP, have you tried hitting F6 while the disc is booting up to the purple screen, and using any of the options there, such as "ACPI=off"?'

Might also be a bad disc burn. Have you done a checksum of the disc image?

---

### Post by coolnfunky_raj on 2011-09-15
thanks everyone for responding. I tried all suggestions, but it did not work. I am now running ubuntu 10.04 LTE and it works fine.

---

### Post by mörgæs on 2011-09-15
That is not a bad option! 
If you want the 11.04 release, you could try Xubuntu.

---

