---
title: "For you experts"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by homeriq5 on 2008-05-12
Recently my thinkpad r40 (2.0 ghz pentium m, 246 mb ram) wouldnt boot into windows anymore, getting past the windows startup screen but then arriving at a blue window saying something about a registry file being corrupted and something wrong with the hard drive and would then restart.  I then decided to try to install ubuntu on the HD, but it would freeze at 15% at the detecting file systems stage. I tried just running from the live cd but it wouldnt load the time and network connections information ont eh top bar and would simply just freeze.  

My guess is that the HD is pwned and decided to remove the hard drive and hook up a 500 gb seagate external hard drive to the computer and install ubuntu on there. I tried to run the live cd again, but I got the same problem.  I tried to install ubuntu but it would freeze on the partitioning step.  

Will installing ubuntu not be possible on my computer?

---

### Post by Mr A Mouse on 2008-05-12
Instead of an external hdd, try replacing the internal one. I've had problems trying to boot from external devices, even from live cds.

---

### Post by homeriq5 on 2008-05-12
hmm, i guess I might have to although I was hoping to save myself 50 dollars and get away with using my usb.  I know booting from usb is possible having found a few threads out there with how-to's, but oh well.

---

### Post by Mr A Mouse on 2008-05-12
Heck, it was worth a shot! :D

Let us know how it turns out--I have a couple of r41s that may need to undergo a [SIZE="1"]religious conversion[/SIZE] Ubuntu install.

---

### Post by brigadoon on 2008-05-12
If you want to recover the Windows OS boot from the installation CD. Exit the install program when you get the chance. You should be kicked out to a terminal window, aka dos prompt. I don't know how familiar you are with dos so I'll be explicit.

At the dos prompt type ***C:*** and hit the enter key.

Next type ***CD\WINDOWS*** and hit the enter key. You may need to replace WINDOWS with the name of the directory that houses the OS. AKA WIN, WINNT, WINXP, etc...

Next type ***SETUP*** and hit the enter key. This shall start the install utility and also allow you to repair the windows OS at the same time. It may seem like a new install but it will fix corrupted or missing files. You may need to reinstall some programs to get them to work. With any luck you can get critical files off of it prior to doing a total wipe of the hard drive.

If you freeze up again or the Windows OS is gone use a utility like FDISK and delete the partition. All data on the hard drive shall be lost. If you don't have FDISK use the Ubuntu install program to delete the old partition and create a new one when asked. The repartitioned hard drive shall be checked for errors and formatted. If you keep locking up then install a new internal hard drive and install Ubuntu onto it. There may be a problem with the Ubuntu install CD. Try making another CD and install from that prior to getting another hard drive.

Let me know how it turned out.

---

### Post by homeriq5 on 2008-05-12
thanks for the reply!  I put the hard drive back into the laptop and removed the external, but when i started up without the ubuntu cd it said that no OS was detected.  Then I stuck the ubuntu cd in and followed your instructions, deleting the old partitions and creating the new ones.  However, during the actual install it again froze at 15%, checking file systems.  So, I guess I have to get a new internal hard drive.  Thanks for the help though!

---

