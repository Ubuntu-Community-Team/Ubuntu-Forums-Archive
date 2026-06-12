---
title: "winXP boot failure"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by r3mu on 2006-10-08
hi..

i really need a help on this..i've googled for half a day on this topic but still can't get any working solutions..i cannot boot my winXP and it return errors:
"xmnt2002 was not found-skipping autochk" 
"autochk was not fount- skipping autochk"

the problem occur when i use partition magic 8.0 to resize my partition and give a space for ubuntu linux. i use partition magic's 'install another OS' option.my linux works fine but i can't get to the winXP login as the blue screen with the error message appear..then, after the error message, my screen becomes black..

[B]*i've tried linux's fdisk to change the hidden windows partition to NTFS, but i got the error message "unable to open /dev/hda1", "cannot open /dev/hda1"..i've tried every fdisk command and still, the error occur..
[/B]
*i've tried booting in safe mode in winXP, but i still get the black screen..then i try the "last known good config.." and the xmnt error was not shown, only the autochk..but the black screen still there..

any help?..plzz..

thanx..

---

### Post by Kateikyoushi on 2006-10-08
Something might have gone wrong when you resized the partition.
I used pq magic several times and it worked out fine.

How does your partition table looks now ?

```
sudo fdisk -l
```

---

### Post by r3mu on 2006-10-08
thanx for the reply..i've managed to display it..

disk /dev/hda: 60GB
255 heads, 63 sectors/track, 7296 cylinders
units=cylinders of 16065*512=8225280 bytes

device   boot  start  end  blocks     id  system
/dev/hda1 *     1     2196 17639338+  17  Hidden HPFS/NTFS
/dev/hda2      6723   7296  4610655   83  Linux
/dev/hda3      2197   2260  514080    82  Linux swap/solaris
/dev/hda4      2261   6722  35841015  f   w95 ext'd (LBA)
/dev/hda5      2261   6722  25840983  7   HPFS/NTFS

now..what should i do to make my windows available?..

thanx in advance..

---

### Post by Kateikyoushi on 2006-10-08
Can you see files on the windows drive ? Is it mounted automatically ?
If  not this will mount the drive.

```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1/ -t ntfs -o nls=utf8,umask=0222
```

---

### Post by r3mu on 2006-10-08
i can access the windows drive via linux, but it's read-only..

mount: /dev/hda1 already mounted or /media/hda1/ busy
mount: according to mtab, /dev/hda1 is mounted on /media/hda1

err..the next step plzz..
thanx for the quick reply..

---

### Post by Kateikyoushi on 2006-10-08
Good your partition seems to be intact, the problem is within windows.

[Read here.]("http://service1.symantec.com/SUPPORT/powerquest.nsf/56d21993ad4e6baa88256e91005066ad/b0316214f90fadd888256e9f00607ba5?OpenDocument&prod=PartitionMagic&ver=8.0&src=sg&pcode=pmagic&svy=&csm=no")

The problem is you can not boot windows to repair it. :mad: 
I found no way to repair this.
So what you can do is backup your important files from that partition and reinstall windows if you have enough space you can install windows without reformatting the partition. You have to restore your bootloader after the installation.

Maybe someone who knows windows better might come up with a better solution for you.

---

### Post by r3mu on 2006-10-08
i've read the symantec's solutions..it's just that i can't get into windows..that's why i still can't manage to solve this horrible problem..anyway, thanx a lot for ur help..

if anybody who's expert in windows/ know how to fix this probs, plzz help me..i need to get my important files on windows..

thanx..

---

### Post by Kateikyoushi on 2006-10-08
You can backup your files from linux, just copy them to your linux partition.

---

### Post by r3mu on 2006-10-08
owh~..the thing is that my linux partition have a small disk space ~5GB, while my windows have 30+GB..so, i can't move all my files..just some.. :P

---

### Post by dcstar on 2006-10-08
> **r3mu said:**
> i've read the symantec's solutions..it's just that i can't get into windows..that's why i still can't manage to solve this horrible problem..anyway, thanx a lot for ur help..

if anybody who's expert in windows/ know how to fix this probs, plzz help me..i need to get my important files on windows..

thanx..

Get your XP Setup disk, boot off it and select "Install", then select "Repair" when it gets to that point.

It should just re-install XP and keep all of your data (if it can detect an existing installation).

---

### Post by r3mu on 2006-10-08
err..what if it can't detect the previous installation?..then i have to format it all again..rite?..:-k

---

### Post by Kateikyoushi on 2006-10-08
It is also neceserry to have enough space on the drive if you repair it.

If you ahve to format it, backup your data to dvd via ubuntu.

---

### Post by r3mu on 2006-10-08
ahh~..ur rite..thanx

---

