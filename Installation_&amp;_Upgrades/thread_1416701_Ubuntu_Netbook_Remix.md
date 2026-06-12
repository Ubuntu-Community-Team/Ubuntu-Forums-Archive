---
title: "Ubuntu Netbook Remix"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by JavaEsse on 2010-02-26
Hello,

I've been running dual operating systems on my netbook with Windows XP and Ubuntu Netbook Remix for a few months and all seemed fine.   I recently did a system update via the synaptic package manager update and when I restarted the machine I got an error when I tried to boot Ubuntu and it looks like I was taken to the Grub command line.  When I type exit, I get an Operating System Not Found message (or something like that).  Typing boot fails as well.  I'm not sure what happened.  Any ideas as to why this may be happening?  Any suggestions as to how I can go about correcting it?

Thank you in advance for the assistance.

---

### Post by darkod on 2010-02-26
If you still have the usb stick you used to install around, boot into the live desktop (Try Ubuntu option) and follow these instructions:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of your results file here and it will show details about the boot process.

Also, if the update was about new kernel, for example -19, check in your grub menu for older kernels like -17, -16, etc. Try booting one of them, because they were working previously for you.

---

### Post by JavaEsse on 2010-03-15
Hi darkod, thanks for the response.  Unfortunately I did not download Ubuntu onto a USB stick.  I downloaded the windows installer onto my XP desktop and installed it.  When I double click it, it asks to uninstall the existing version of Ubuntu, but I have files on there that I'd really like to avoid losing.

UPDATE: Can I download Ubuntu to my USB drive now and try those instructions?

---

