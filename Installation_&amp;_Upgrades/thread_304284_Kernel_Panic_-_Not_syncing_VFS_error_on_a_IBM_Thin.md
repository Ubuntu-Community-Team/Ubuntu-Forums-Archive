---
title: "Kernel Panic - Not syncing VFS error on a IBM Thinkpad 600X"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by firelily on 2006-11-21
Hi guys,

I've looked around the forums and the internet and I can't seem to find a solution for this. 
I have Win2K on my laptop and I'd like to install Ubuntu. However, when I try to boot from the live CD, I get "Kernel Panic - Not syncing VFS: unable to mount root FS on unknown block". Now I tried this same CD on a regular Dell PC and it booted up just fine.

Any ideas? 

Thanks :)

---

### Post by Velox Letum on 2006-11-21
Sounds like the LiveCD isn't correctly detecting your Thinkpad's cdrom. The error you're getting is when it tries to mount the root filesystem, but cannot find the device specified. I'm not sure the solution to this, but you might search around about your Thinkpad's cdrom, or try the alternate install cd.

---

### Post by firelily on 2006-11-21
I will, thanks for the reply :)

Do you think it's a firmware issue?

---

### Post by pwcutajar on 2006-12-04
I have just the same laptop and problem, But I used a dell laptop to run the install and fitted the hdd to the ibm, not a fix but a getround, will keep you updated If i get a better fix

---

### Post by mikea128 on 2006-12-10
same problem here with xubuntu 6.10 live cd...anyone try the alternate install CD? 6.06 worked fine for me.

---

### Post by jasin on 2006-12-12
> **Velox Letum said:**
> Sounds like the LiveCD isn't correctly detecting your Thinkpad's cdrom. The error you're getting is when it tries to mount the root filesystem, but cannot find the device specified. I'm not sure the solution to this, but you might search around about your Thinkpad's cdrom, or try the alternate install cd.

I get the same error message after I compiled and installed a new kernel, kernel 2.6.19.1.

I think this error has something to do with the kernel not loading properly. Since you get this off a live cd tnen I  would suggest you either reburn the cd and/or get a new cd drive, one thats new and well supported by ubuntu.

Check this site here for hard ware supported by ubuntu.

[http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport)

---

### Post by mikea128 on 2006-12-12
> **jasin said:**
> I get the same error message after I compiled and installed a new kernel, kernel 2.6.19.1.

I think this error has something to do with the kernel not loading properly. Since you get this off a live cd tnen I  would suggest you either reburn the cd and/or get a new cd drive, one thats new and well supported by ubuntu.

Check this site here for hard ware supported by ubuntu.

[http://www.ubuntulinux.org/wiki/HardwareSupport](http://www.ubuntulinux.org/wiki/HardwareSupport)

No problems with 6.06 and I think it's just a standard IDE CD-ROM. I can't imagine what would change that would break compatibility there. The CD checks out fine...i'll try the alternate install cd in a day or two.

---

### Post by Hvannentir on 2006-12-15
Ive got same trouble and Ive burned alternate.
The alternate CD of Edgy Eft (6.10 ) boots fine on the thinkpad 600X.
I ll keep you informed if there's any problem.

Edit: All works fine. The alternate CD works perfectly on thinkpad 600X.

---

### Post by mikea128 on 2006-12-16
thanks for the info...downloading the alternate cd right now.

---

### Post by Jawalking on 2007-01-17
I had the same problem until I flashed the bios; Serarch for spsdit55.exe on google or lenovo's site. Unfortunatly that only got me past that point, Im still trying to get the gui to start. good luck in you ubuntu adventures.

---

### Post by KernelKen on 2007-01-20
I have the same problem just started looking for a solution.  Bad news is I have been using ubuntu on same laptop for sometime.  Both from a live cd and loaded to the hard drive.  

Problem just started for unknown reason.  So I don't believe it is a hardware problem, at least not in my case.

Good luck.

---

