---
title: "Please help me get my old laptop usable again"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by oingk on 2010-06-18
Hi, 
I'm not sure where I should post this question.

 I have a laptop, quite old (~5 years old). It run Windows XP all its life until it died. Now, when trying to turn on it shows a bluescreen saying there's an error (a c00005 error, or something like that). I can, however, access it in safe mode, so via safe mode I managed to save all my files. 
In safe-mode, my computer seems to work quite finely. Now I also want to get the computer running again. I would like to install Linux on it (I already have some experience with Ubuntu). 
 As I understand, I should normally be able to insert an Ubuntu Live CD and when turning on the computer, it would run the disk automatically, assuming that it's set to do this on BIOS. And indeed, I have set it on BIOS to do so. But it doesn't. So what can I try, in order to fix it?  

This laptop is a Sony Vaio. Has MS win XP Home SP2. Seems to have no malware/virus/etc. Has Intel Pentium M processor, 1.73GHz, 502MB RAM.

EDIT: In safe mode when I try to access the CD Drive (F:) it gives me this error: > F:\ is not accessible. The request could not be performed because of an I/O device error.

---

### Post by darkod on 2010-06-18
The cd might be bad, even if it was created now, a simply bad burn. Or the cd drive of the laptop might be gone.

Did you try if you can boot with the ubuntu cd on another computer?

---

### Post by oingk on 2010-06-18
Yea I installed Ubuntu from this CD before on a different computer.
I also have Live CDs of Slax and Debian, which give me the same result.

Maybe it is the CD Drive as you say. I don't remember its condition before my computer broke, it was a long time ago.

Any other possibilities? If not, would it be really complicated to try to install Ubuntu or some other OS via USB stick?

---

### Post by darkod on 2010-06-18
It's not complicated at all as long as the computer can boot from usb. Just use any ubuntu computer, or simply boot the cd in live mode, and use the Startup Disc Creator. You will have to have the image file at hand also.

You can even create the stick on windows computer by using the Universal USB Installer and the ubuntu image file.

---

### Post by oingk on 2010-06-19
I don't think it can boot from USB aafter all. Only options in BIOS are

-optical disk drive
-floppy disk drive
-hard disk drive
-network

---

### Post by oingk on 2010-06-19
Hi

From safe mode I did a Windows System Restore, which restores the Windows to the previous state that worked. So now it seems to work. It can also connect to the internet.

So I wanted to ask if I can install Ubuntu, or some other Linux, without CD or USB. Is there a way to do this?

Thanks

---

### Post by oingk on 2010-06-19
What I mean is, I know how to install Ubuntu by downloading and burning on a DVD and then putting in the computer. But is there a way to just download it and install it without needing a DVD as mediator?

---

### Post by darkod on 2010-06-19
Without cd or usb boot possibility, I guess the only option is network or PXE boot. If you can handle the procedure which doesn't look too easy:
[https://help.ubuntu.com/10.04/installation-guide/amd64/install-tftp.html](https://help.ubuntu.com/10.04/installation-guide/amd64/install-tftp.html)

---

### Post by spcwingo on 2010-06-19
In some BIOSs after inserting the USB flash and booting it will show in the BIOS under HDDs...you might want to give that a look.  ;)

---

