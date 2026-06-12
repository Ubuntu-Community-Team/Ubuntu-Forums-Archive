---
title: "Sil 3124 W/ Port Multiplier support"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Schwyl on 2008-01-08
Hi there,

well i made the jump to Linux because i thought this hardware had support.

Here is the web site i found that supposedly has this hardware driver

[http://home-tj.org/wiki/index.php/Libata-tj-stable]("http://home-tj.org/wiki/index.php/Libata-tj-stable")

Now it seems like the latest on their site is too new for my install. Im RUnning Ubuntu Desktop 7.10.

So i went to my manufacturers website for my card and tried follwing these steps. 

[http://www.addonics.com/support/faqs/faq-pmsupport_desktop.asp]("http://www.addonics.com/support/faqs/faq-pmsupport_desktop.asp")

THe only thing i changed was instead of using the 2.6.17 versions i used the 2.6.22 because well thats what my machine has in it. I followed it step by step and everythign seem to go right. THen i was at the make menuconfig part and when i went into  r Device Drivers > SCSI device support > SCSI low-level drivers, check if Silicon Image 3124/3132 SATA support is a module <M>. 

That module isnt listed. Im a newb to linux and im not really sure what info you guys need.

---

### Post by rupert on 2008-02-02
is there already port multiplier support in the latest kernel? I read Suse does have it by default.
Do I have hotplug support when I connect 4 Drives to a multiplied SATA port?

thx

---

### Post by mavila on 2008-02-12
Ive seen similar behavior - meaning that I can see the FIRST drive in the 3124's BIOS at boot, but nothing subsequent, It appears that to actually use additional drives behind the multiplexer you need a custom compiled kernel.... I found a link ([http://home-tj.org/wiki/index.php/Libata-tj-stable](http://home-tj.org/wiki/index.php/Libata-tj-stable)) but I cant seem to get into the site - hence haven't been able to test/use the patch.

From what I can gather (as documentation seems scarce) the BIOS will only see the first drive thats attached to a multiplexer and anything else REQUIRES some type of driver. On the SiI website there looks to be drivers for RedHat, Fedora , and SUSE.... just nothing yet for UBUNTU.

If you find anything please post it back to this thread.... thanks

---

### Post by mavila on 2008-02-12
Well - it was a long morning, but I was able to contact the kernel developer (in Hong Kong) that's added support for this.... the quick answer was to upgrade to 2.6.24 kernel (this is in the Hardy distro)... so how DO you in fact accomplish this (and keep compiz from breaking?)

If you follow the instructions on this thread (and use the perl script - it works), youll be all set in about 10 minutes or so. Do it manually (like I did - and miss a step) and youll be fixing compiz all afternoon) - ESPECIALLY wiht NVIDIA drivers!

[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

So, this gives you a kernel that has PMP support for the SiI chips that support PMP, and using the script (read again, follow the directions carefully) your up in 10 minutes or so.

Cheers & good luck!

---

### Post by rupert on 2008-02-13
good news, getting mine by end of the week,
When the kernel upgrade doesnt break the usual system, i dont use compiz, 
than im happy with this.

---

### Post by mavila on 2008-02-14
From what Im seeing on the IO front the 3124 solution is actually quite nice! I had a SAYA (or something like that) card that I returned... the documentation and supplied software left something to be desired.... well, I cant read "Chinglish". Anyway, I now kinda wish that I kept it as it had 2 internal AND 2 external ports - the NORCO that Im now running is 4 external only ports.... so Im chewing up an extra slot for internal disk.

All that said however, running the new kernel seems to be fine - compiz leaves a little artifacting and has some minor flakiness, but I can live with that. What really fried me this morning is I have an AVISION 210 scanner that SANE no longer sees. Im quite sure that there is an issue with usb drivers on the new kernel (I only upgraded the kernel and NVIDIA drivers) - so my "solution" to scan is reboot into the old kernel (and 640x480 resolution), get it done, then back to the new kernel.... kludgy, but Im not willing to do a distro upgrade till UBUNTU has more of the kinks worked out. Besides, Im a hack at best and not a good coder.

As I wanted to setup a 3+1 R5 group ~1.5TB in the external enclosure, Im probably going to have to wait a couple months for an "official" release as Im simply not going to put this machine at risk with flakey stuff. Seeing support for the 3124 PM solution is nice however. If anyone sees a script to bring it into the Gutsy kernel, drop me a message... appreciate it

---

### Post by oeperez on 2008-02-18
Worked the first time on a new 7.10 installation on a Dell PowerEdge 1600SC using SATA PMP (Port Multiplier).

---

### Post by rupert on 2008-02-19
can you tell us waht PMP you used and if the kernel is custom made? 

thx

---

### Post by rupert on 2008-02-23
So i have my setup running, just bootet with 2 disks attached to the PMP. i can see them both and use them.
great thing!

---

### Post by makaali on 2008-04-01
Please can you elaborate how you made the PMP to work in 7.10. I have a sil3132 onnected to 4 port external sil4726 enclosure.

---

### Post by drl2 on 2008-05-14
I've been trying to get a similar setup to work on a fresh 8.04 install but it will only recognize the first of a pair of drives plugged into a Sil3124 via a port multiplier.  Kernel is 2.6.24-16-server which I thought featured PMP support.  Two drives on a separate 3114 controller are recognized fine, as is a regular IDE drive in the system.  Is there some module I need to add to the kernel, or some configuration file I need to edit, to get this working?

---

### Post by blackoper on 2008-05-25
I can't get it to work in 8.04 either. I'm going to test in fedora 9 and see if the 2.6.25 kernel supports it. I've had it working before with customer compiled kernels

---

### Post by disasm on 2008-06-06
Well, I got my card in today. I'm running Hardy, and the card seemed to work fine. lsmod shows sata_sil24 module loaded. Hooked up sbox (sil3726 multiplier 5 drives), and...

nothing...

No error message or anything else of the like. The driver cd does include a firmware update cd iso, so I might try that and see if it helps.

Any ideas to get this working?

Sam

---

### Post by mavila on 2008-06-12
I completely forgot all the issues that I went through with this card, but I do recall chatting with a developer that said the support was in the hardy kernel (I went so far as to run that for a couple months before the Hardy release). At any rate, Im on an Intel 64 bit platform and had the bright idea to upgrade THIS machine to Hardy 64 ( a complete new install), and guess what... the darn Sil 3124 card isnt loading something correctly under 64 bit!

Ive seen an "issue" in the kernel.log that Id guess is something, but not being a developer I dont know for sure. Its identifying a "Port Multiplier vendor mismatch  '0x101' != '0x1095'. This seems to appear when power cycling the external enclosure - so it may be something.... Ill have to look at this again under 32 bit Hardy, but for the moment its back to figuring this one out again.

---

### Post by disasm on 2008-06-13
> **disasm said:**
> Well, I got my card in today. I'm running Hardy, and the card seemed to work fine. lsmod shows sata_sil24 module loaded. Hooked up sbox (sil3726 multiplier 5 drives), and...

nothing...

No error message or anything else of the like. The driver cd does include a firmware update cd iso, so I might try that and see if it helps.

Any ideas to get this working?

Sam

Just an update, it does recognize with the 18 revision of the kernel just fine. I ran into some problems though with raid 5 and xfs, where md0 would stop responding with 30 seconds of doing a file transfer on it. Custom compiling 2.6.25 kernel resolved all issues with the card, but created other issues with the nvidia driver. Luckily, the researcher that will be using this raid doesn't use 3d acceleration, so I can switch him to the "nv" driver instead.

Sam

---

