---
title: "My Windows 7 &amp; Ubuntu Boot Problems"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by zonerover on 2010-03-27
Recently I thought that my old Windows Vista install was getting too old and slow, so I took the opportunity to install fresh copies of Windows 7, OSX and the Ubuntu 10.04 beta to my PC. When I install Ubuntu last, I end up with a perfectly acceptable tri-boot system, and here's where most people end up stopping. However, because I want to use Truecrypt to encrypt the entire drive and this only works in Windows with it controlling the MBR, I'm forced to use the Windows 7 bootloader.

I've used EasyBCD in the past with the original version of GRUB, and while it was a little fiddly at times, I got it to work. However, while the beta of EasyBCD 2 provides 'support' for GRUB 2, every time I hit enter on my Ubuntu entry, it takes me back to the Windows bootloader as if nothing happened. I'm no expert at manually editing the MBR, especially in Windows, but when I try to manually enter details of GRUB using information found in grub.cfg or the grub.d folder, I still don't get anywhere. Unless there's an alternative encryption system I can use for all of my partitions, can anyone suggest a way I can get this working?

---

### Post by stlsaint on 2010-03-28
This is risk that is taken when it comes to depending on a windows native bootloader to control grub2. Im thinking that something is wrong in your easybcd settings. Maybe its pointing to the windows parititon instead of the correct linux one.

---

### Post by zonerover on 2010-03-28
Thanks @stlsaint for the reply. I'm pretty sure that I've done the right thing in linking my partitions to the appropriate Ubuntu drives since I did this in the past with GRUB. However after some thought, I think that the premise behind my question might be invalid because I went in assuming that system encryption was possible in Ubuntu using Truecrypt, and that there was some magical way to connect Windows and Ubuntu using that single encryption solution. While that would have been great, this isn't possible. Based on this, I'll probably do a basic search for system encryption solutions in Ubuntu that I can decrypt in Windows, and if I run into any problems I'll probably start a new thread.

---

