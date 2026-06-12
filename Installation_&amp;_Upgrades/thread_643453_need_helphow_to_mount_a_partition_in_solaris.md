---
title: "need help:how to mount a partition in solaris"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by alex1996arm on 2007-12-17
i am running 

title		PC-BSD
root		(hd0,2)
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=579c851f-983d-47bd-bd62-5e07cd6f2c49 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

reactos  (hd0,1

NEXENTA OS (HD0,3

i need a way to mount the nexenta partition from the live shell in the install

any help would be very much apreciated

                                            thanks:confused:

---

### Post by Pumalite on 2007-12-17
Post:
sudo fdisk -lu

---

### Post by alex1996arm on 2007-12-18
is it for nexenta livecd??
      if not thanks anyways.
      sorry my mistake
it was wrong of me:lolflag:

---

### Post by alex1996arm on 2007-12-20
please:(:(

---

### Post by Pumalite on 2007-12-20
You have to post the output of the command from the Ubuntu Terminal (copy cand paste here)

---

### Post by alex1996arm on 2007-12-21
i put this in
```
installgrub -m <stage1> <stage2> /dev/rdsk/<root slice>
```
but i know that nexenta is hd0(3,1)
i dont know how to put the drive grub format  into this 
solaris system format

---

### Post by alex1996arm on 2007-12-21
mount dev/rdsk/c0t1d0s1:z

and 
mount:mount point cannot be determined

and im very sorry about previous post 
                            and thanks

---

### Post by alex1996arm on 2007-12-22
is it that no one can or they dont want to?:confused:

---

### Post by louieb on 2007-12-22
Sorry but your post is very confusing - not clear what you want to do.
mount a solaris partition so you can read/write to it?
configure GRUB to boot a solaris install? 
or do you have solaris up and running but need to mount a partition for read / write?

For the first two need the stuff pumalite asked for 
```
sudo fdisk -lu
```

---

### Post by alex1996arm on 2007-12-23
ok im on the solaris livecd shell and i need to mount partition 3 to run the installgrub command because i overwrited the master boot record with ubuntu.

---

### Post by louieb on 2007-12-23
So I take it you are trying to get Solaris  to boot using GRUB. Is that correct?
GRUB can boot a Solaris install by chainloading.  Found this
[**     How to use grub to boot the triple OS: windows,linux,solaris?**]("http://www.linuxquestions.org/questions/solaris-opensolaris-20/how-to-use-grub-to-boot-the-triple-os-windowslinuxsolaris-298718/")

not much help here other that that. Good luck.

BTW [LinuxQuestions.org]("http://www.linuxquestions.org/questions/") has a Solaris section. More likely to find someone who know what to do there.

---

### Post by alex1996arm on 2007-12-23
oh thanks :):)
to everyone who helped me.
it is working!!!!!!!!!!!!!!!!!!!!!!!!!!!
all 4 operating system!!!
on an acer aspire 5100 ***_LAPTOP_***!!!

---

