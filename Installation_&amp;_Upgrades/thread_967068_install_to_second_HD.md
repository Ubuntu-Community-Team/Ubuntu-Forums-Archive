---
title: "install to second HD"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by fredfelter on 2008-11-01
I have a Thinkpad T22 in which I have installed a second HD in place of the DVD drive. I would like to run Ubuntu from that drive by starting it from the BIOS boot menu. My problem is that the laptop doesn't support USB booting, so with the hard drive replacing the optical drive I have limited installation possibilities. Could I just purchase an external USB CD drive and copy the Ubuntu files from the installation CD to the second drive and then open/install from there or would I still have a problem with the "no USB boot" deficiency of the laptop?

What I had done once before was to literally replace the primary HD with the second HD in the primary HD receptacle, upload and install from the CD and then move it back to the ultrabay slot and put the primary HD back into it's proper slot. It worked but was a pain so I'm looking for alternatives.

Thanks in advance.

---

### Post by Pumalite on 2008-11-01
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by fredfelter on 2008-11-01
Thanks Pumalite but it's not exactly what I want or can do. Firstly, as I mentioned, I cannot install Ubuntu in a conventional manner since I have no optical drive (replaced by new HD) and I have no USB booting capability. I also don't mind doing the BIOS boot since I do not plan to go back and forth frequently between OSs.

---

### Post by Pumalite on 2008-11-01
Sorry.
If your BIOS does not allow boot from USB, a new USB CD would not be useful.
If you have an OS installed in the other drive; you could try unetbootin:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by fredfelter on 2008-11-02
Would this work? If this is off the wall I apologize since I'm just a novice.

Thinkpad T22, second HD (where I want to install Ubuntu) in ultrabay (which means I can not have a running CD drive at the same time), computer doesn't support USB booting.

If I were to create a bootable floppy for Ubuntu and were to purchase an external CD drive would the fact that I boot initially from the floppy disk likely allow the computer to see, install and open Ubuntu from the installation CD loaded in the external USB drive onto my second HD? If so I would then not have further need for the floppy boot, right?

---

### Post by Pumalite on 2008-11-02
Unetbootin works with an installed OS. It's all with the Internet.

---

### Post by neu2buntu on 2008-11-02
> **fredfelter said:**
> I have a Thinkpad T22 in which I have installed a second HD in place of the DVD drive. I would like to run Ubuntu from that drive by starting it from the BIOS boot menu. My problem is that the laptop doesn't support USB booting, so with the hard drive replacing the optical drive I have limited installation possibilities. Could I just purchase an external USB CD drive and copy the Ubuntu files from the installation CD to the second drive and then open/install from there or would I still have a problem with the "no USB boot" deficiency of the laptop?

What I had done once before was to literally replace the primary HD with the second HD in the primary HD receptacle, upload and install from the CD and then move it back to the ultrabay slot and put the primary HD back into it's proper slot. It worked but was a pain so I'm looking for alternatives.

Thanks in advance.
hi...fredfelter,  im a bit of a noob but have you tried using a virtual cdrom drive like qemulator and running ubuntu iso in that

---

### Post by neu2buntu on 2008-11-02
> **fredfelter said:**
> I have a Thinkpad T22 in which I have installed a second HD in place of the DVD drive. I would like to run Ubuntu from that drive by starting it from the BIOS boot menu. My problem is that the laptop doesn't support USB booting, so with the hard drive replacing the optical drive I have limited installation possibilities. Could I just purchase an external USB CD drive and copy the Ubuntu files from the installation CD to the second drive and then open/install from there or would I still have a problem with the "no USB boot" deficiency of the laptop?

What I had done once before was to literally replace the primary HD with the second HD in the primary HD receptacle, upload and install from the CD and then move it back to the ultrabay slot and put the primary HD back into it's proper slot. It worked but was a pain so I'm looking for alternatives.

Thanks in advance.
hi...fredfelter,  im a bit of a noob but have you tried using a virtual cdrom drive like qemulator and running ubuntu iso in that

---

### Post by fredfelter on 2008-11-03
> **Pumalite said:**
> Unetbootin works with an installed OS. It's all with the Internet.

Pumalite: You finally convinced me to take a look at Unetbootin and it did appear to be a solution. However after apparently successfully installing the deb/ubuntu package on my present Linux drive (the one I want to replace with a fresh Ubuntu) > rebooted > chose Unetbootin from the Grub options > "Error 15 File not found". I ran into some mention of the need to create a new partition to install Unetbootin into but the official web site mentions nothing of the like and I'm not sure I'd know how to do that anyway.

---

### Post by caljohnsmith on 2008-11-03
I think the bottom line is, what drives does your computer support booting from? Only your internal drive? If that is true, then to boot Ubuntu from any other drive you would need to put all of Ubuntu's boot files on your internal drive. All you need is a ~200 MB partition for Ubuntu's /boot directory on a drive that will boot, and then the main Ubuntu install can be on any other drive you want. Would this maybe work for you?

---

### Post by fredfelter on 2008-11-03
> **caljohnsmith said:**
> I think the bottom line is, what drives does your computer support booting from? Only your internal drive? If that is true, then to boot Ubuntu from any other drive you would need to put all of Ubuntu's boot files on your internal drive. All you need is a ~200 MB partition for Ubuntu's /boot directory on a drive that will boot, and then the main Ubuntu install can be on any other drive you want. Would this maybe work for you?

I can boot from either HD once the boot data is written to the disk - the problem is getting it there.  
I'm trying to install the new Ubuntu package on that second drive without having the use of an optical drive nor the ability to boot from a USB device and I really want each HD to boot independently (no data from the other system on either disk). I have sacrificed having a CD drive by replacing it with the second HD (ultrabay). 
What I initially did to install the present Linux version on that drive was to take out the primary HD and temporarily replace it with this drive, installing using the then available CD drive. I then moved the HDs to their desired locations  (removing the CD drive), and it booted nicely from the BIOS menu; just what I wanted. The downside of that method is that it is not good for HDs to be connecting and disconnecting them like that, not to mention the time that it takes so I was hoping there would be an alternative way, easy enough for me to use.

---

