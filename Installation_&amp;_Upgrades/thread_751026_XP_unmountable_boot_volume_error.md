---
title: "XP unmountable boot volume error"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by drumworkz on 2008-04-10
Hi guys,

I've seen the many other threads about this problem but none really solved it for me :(

My situation is as such. I am using an ibm thinkpad that comes preinstalled with winxp pro - which takes up the entire partition. This disk has only one partition when I got it. I needed ubuntu for programming and thus I proceeded to boot using the ubuntu CD and got into the partition manager. What I did was to resize my xp partition, then selecting "manual mode" to further partition the free space into 3 directories, "/", "swap" and "/home". The XP partition itself is mounted as one of the media drives.

Ubuntu installed fine, I am ABLE to browse the files in my xp parition from ubuntu. However when I rebooted and went into grub and chose to boot into XP, the XP splash screen appeared for a brief moment before throwing a BSOD with error "UNMOUNTABLE_BOOT_VOLUME". 

I have quite some stuff in windows that I still need to RUN (programs, not files) and hopefully there's still hope in restoring it :S

Any advice will be greatly appreciated! :)

---

### Post by sh4d0w808 on 2008-04-10
Check [this]("http://www.techsupportforum.com/microsoft-support/windows-xp-support/119139-blue-screen-unmountable_boot_volume.html") matter (the last entry from Geekgirl), maybe it can help U.

---

### Post by drumworkz on 2008-04-10
:( anything that uses chkdsk don't seem to work because any arguments used with chkdsk will just spit this message: 
"there are one or more unrecoverable problems"

---

