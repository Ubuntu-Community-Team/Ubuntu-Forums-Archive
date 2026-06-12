---
title: "Ubunto 9.10 livecd will not boot"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by netkabuki on 2010-02-10
Intel core2 duo on dg965wh board, 4G ram. 500Gb HD partitioned 100G for W xp sp3 and the rest unpartitioned. Motherboard has latest bios and is set to boot from CD.

The 9.10 download burnt on CD will boot, ask for language option and go to the main screen. I cannot make it proceed to installation.  I can go to F1, F4 etc, but selecting any of the options on the screen simply sits there - there is some minimal activity in the CD and then it just reverts back to nothing.

Any suggestions will be welcome. 

I realize I can use WUBI but I prefer not to be under the windoze umbrella and would like to have a true raw boot of ubuntu preferably with a core boot manager that is also outside of windows.

---

### Post by mörgæs on 2010-02-11
Is the checksum of the CD correct? 

Does it work with a 9.04 CD? 
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

(and don't forget to defragment XP a couple of times before installing).

---

### Post by netkabuki on 2010-02-12
Thanks - I have not verified the checksum - which I will but like most people here with similar problems that may not be the issue.  

I am already looking at the 9.04 -> 9.10 route and I am glad to see that some of the experts are looking to that as well.

Just curious - why does defragging the disk help - especially if the space for Ubuntu is physically separate from windoze?

---

### Post by darkod on 2010-02-12
> **netkabuki said:**
> Thanks - I have not verified the checksum - which I will but like most people here with similar problems that may not be the issue.  

I am already looking at the 9.04 -> 9.10 route and I am glad to see that some of the experts are looking to that as well.

Just curious - why does defragging the disk help - especially if the space for Ubuntu is physically separate from windoze?

If the live desktop does not load properly for 9.10, hold on with upgrading 9.04 -> 9.10. It could mean it has some issues either with hardware or what ever. After upgrade there is big chance it won't work too.
The first step is to load the live desktop correctly.

---

### Post by mörgæs on 2010-02-14
If the space for Ubuntu is physically separate, defragmenting does not matter. It is only important if the two systems are sitting on the same drive. 

I second the opinion of maybe staying with 9.04. It is supported through most of the year, and when the support ends you will have the option of going straight to 10.04.

---

