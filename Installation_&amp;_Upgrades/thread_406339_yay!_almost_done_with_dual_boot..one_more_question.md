---
title: "yay! almost done with dual boot..one more question"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by cessna_89702 on 2007-04-10
I have partitioned my hard drive and it is ready for a dual boot. I have ntfs, swap, ext 3

Im on the part where it says prepare mount points and i have 3 choices


the first one says mount point /media/sda1 

thats my ntfs/windows. if i leave it with /media/sd1 that will create a dual boot and come up when i start for a boot up right?

then i have my swap which the mount point says swap. (so that ones right)

then i have my ext 3 which it says the mount name which is "/" (which i think is right)


So my question is just about that the /media/sda1 and if those seem wrong please say so thanks

---

### Post by cessna_89702 on 2007-04-10
oh one more thing the partitions i created for linux are coming up as the filesystem unknown when i look in gparted but i know which they are is that normal or should i click format and make them the what they are or something???

I formatted to ext 3 and it says 953. mb are used when nothing should be there??

---

### Post by cessna_89702 on 2007-04-10
Ok I fixed like one problem and ill just summarize what i have to ask.

1.Im on the part where it says prepare mount points and i have 3 choices


the first one says mount point /media/sda1

thats my ntfs/windows. if i leave it with /media/sd1 that will create a dual boot and come up when i start for a boot up right?

then i have my swap which the mount point says swap. (so that ones right)

then i have my ext 3 which it says the mount name which is "/" (which i think is right)


2.my ext 3 says like 950 mb have been used on it but they shouldnt right

---

### Post by neilengineer on 2007-04-10
> 
2.my ext 3 says like 950 mb have been used on it but they shouldnt right


Maybe the ext3 partition with 950MB used is not the one you formatted.  Or the ext3 filesystem takes 950MB ??   How about the capacity of your ext3 partition??

---

### Post by Kawinma on 2007-04-10
Everything should be right. Your ext3 should be /, your swap is perfect, and your windows partition is perfect as it is too.

If you leave your NTFS perfectly as it is, Ubuntu should detect it and dualboot it. If not, then I can certainly help you. (just went through it)

As for the 950MB being used, I got that too. Just ignore it, I'm doubting 950 was actually used.

---

### Post by cessna_89702 on 2007-04-10
ok i just hit install so if i doesnt dual boot can you exlpain what i would need to do since you said you just went through it

---

