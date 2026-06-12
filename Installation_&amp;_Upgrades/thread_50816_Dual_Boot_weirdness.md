---
title: "Dual Boot weirdness"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by joker on 2005-07-21
After having a good deal of success with my home built PVR running knoppmyth (another linux distro specifically for TIVO like functionality) I decided I would try out Linux on my desktop, after looking around, Ubuntu looked like a winner.  So I decided to install.

My system is currently a Tri Boot setup, Win 2000, Win 98, and Ubuntu.  Win 98 and Ubuntu both boot and work fine.  Win 2000 on the other hand will boot under protest but is almost unusable once booted.  Let me explain:
1: At Grub boot menu I select win 2000
2: Win 2000 boot sequence starts: then insists the E: drive is corrupted, this is the location of Ubuntu (EXT3 partition), I tell windown not to "FIX" it.
3: Windows continues to boot but very slowly
4: Windows system comes up but everything is excessively slow, I can hear the hard drive going crazy the whole time the system is up but task manager reports 99% cpu free.

The primary hard drive has 4 partitions
1: win 2000 - Fat 32
2: win 98 - Fat 32
3: ubuntu - EXT3 - previously Fat 32
4: storage - NTFS

The win 2000 install worked fine before the Ubuntu install.  I know this is most likely a Windows problem not directly Ubuntu's, but it sure hope someone can help me out.

---

### Post by joker on 2005-07-21
My machine is  a: 
AMD 2100+  
256MB ram
Nvidia TI-4400

and I did not create a swap partition for Ubuntu, oops, but it runs fine FYI

---

### Post by joker on 2005-08-03
I solved my own problem... after a little of this  :-x and a little of that ](*,) and a full system reinstall  I finally found the bleedingly obvious problem/solution \\:D/ 

I went into the windows logical drive manager and removed my E: drive (there is a dropdown where you can assign a drive letter, I changed it from E: to none)  Now all is well.   I don't really understand why this caused windows such a problem, but there ya go.

---

