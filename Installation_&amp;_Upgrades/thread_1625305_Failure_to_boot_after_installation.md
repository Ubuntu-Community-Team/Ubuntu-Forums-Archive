---
title: "Failure to boot after installation"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by jhupp85 on 2010-11-18
Hello--I'm new to the linux/ubuntu community. I have been attempting booting my new, bare system with both a flash drive, and a freshly acquired .iso/CD for 64-bit Ubuntu 10.10. both let me run it live from said sources, and let me 'install' Ubuntu. I'm currently *in* said Live mode, and life couldn't be greater--this OS is sleek, open; I'm in love . . .
However, when I reboot, all is for naught. here are there error messages I am receiving.

**for the first time after clicking 'suspend', i the installation (shutdown was not an option, just hibernate/suspend)**:

(process: 443): GLib-WARNING **: getpwuid_r(): failed due to unknown user ID (0)

**after reconfiguring BIOS to boot from HD**:

error: hd0,msdos1 out of disk.
error: no suitable mode found.

error: cannot read the Linux header.
error: you need to load the kernel first.
     Failed to boot both default and fallback entries.

. . . nothing sticks. any ideas? Again, I am an Ubuntu virgin. my grandmother raised me in a DOS prompt, though. is it a HD error? I can see it mounted on the desktop. . . any help would be truly appreciated

***-jhupp***

---

### Post by jhupp85 on 2010-11-20
I have recently tried the non-GUI alternate install as well, to no avail. Performed memtest, and the RAM is fine.

Utterly clueless on how to proceed! Anyone??

---

### Post by mionescu on 2010-11-20
Did you press suspend right after you finished installing Ubuntu? Did you press suspend from the live CD? If you install Ubuntu, it should reboot the system for you; that is, you should see a message telling you to press any key to reboot (and not to suspend) once the installation is finished. 
Can you describe in more details the steps you did? It seems to me that you suspended the computer from the live CD. If I am right, then the error is normal, because you don't use the CD anymore.

---

### Post by jhupp85 on 2010-11-21
Originally, yes, that's exactly what I did (again, it only presented me with two options, when I chose to keep running Live after the installation, but it needed to reboot to "complete" the install. I'm so n00b, I didn't think to  reboot via the terminal. However, I have tried installing it nearly a  dozen times, Live and not, USB .iso, and the disc I burnt... I still get the same errors.
1. Install Ubuntu (from Live, or without--regardless, it ejects my CD as it goes to reboot . . . I remove the disc.
2. error: hd0,msdos1 out of disk.
 error: no suitable mode found.
 
 error: cannot read the Linux header.
 error: you need to load the kernel first.
      Failed to boot both default and fallback entries.

that's as far as I can get. sometimes, still, it will give me a grub-rescue prompt, which doesn't let me use any commands (and I wouldn't know what to do even if I did know what commands were available.

Occasionally (its very tempermental) I will get a GNU boot menu, where I  can select from Ubuntu, and Ubuntu safe-mode, and two memtests. Out of  the four options, only one of the memtests work.
thanks for responding--I'm truly at my wit's end on this.

---

### Post by jhupp85 on 2010-11-29
Problem resolved. It *was* a bad hard drive.

---

