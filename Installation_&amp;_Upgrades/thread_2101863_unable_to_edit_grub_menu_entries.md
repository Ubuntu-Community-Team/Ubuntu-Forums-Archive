---
title: "unable to edit grub menu entries"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by davethewave83 on 2013-01-05
with Grub 2 I went into /boot/grub/grub.cfg then edit the line where it says windows 7 loader is /dev/sda1 and changed that to /dev/sdb1 which is now the current correct location for this OS. This however does not really change anything and I don't understand why, at boot time when grub loads, it still maintains the old config settings and wants to boot from /dev/sda1, even though I edited the file and saved it. 

I tried what everyone says "grub-update" but that messed everything up, it auto-inserted OS partitions into the menu that I do not want to be there, but now I can't find a way to remove these auto-inserted entries. 

another site said to edit the menu.lst but this is old, for the pre-grub 2 

I have been trying to read/research but I keep finding old out-dated grub info. Can anyone tell me how to edit the grub and make it stick?

---

### Post by bogan on 2013-01-05
Hi!, **davethewave83,**

If you are running Ubuntu pre-12.04, as your Post shows, then your best bet is Grub Customizer.```
sudo apt-add-repository ppa:danielrichter2007/grub-customizer  
sudo apt-get update  
sudo apt-get install grub-customizer
```Chao!, **bogan**.

---

### Post by davethewave83 on 2013-01-05
> **bogan said:**
> Hi!, **davethewave83,**

If you are running Ubuntu pre-12.04, as your Post shows, then your best bet is Grub Customizer.```
sudo apt-add-repository ppa:danielrichter2007/grub-customizer  
sudo apt-get update  
sudo apt-get install grub-customizer
```Chao!, **bogan**.

hmm, i'd like to try this but when I boot up now it says error: no such partition 
grub rescue >

i tried grub-update here but it did nothing. how do i boot?

---

### Post by darkod on 2013-01-05
First, you shouldn't edit grub.cfg directly, there is a way to do that through the config files and that's the recommended way.

Second, if you have more than one installation you need to know which one is controlling grub2. It might be that you are editing files in the wrong one and in that case the editing would make no difference.

Third, is the message no such partition and the grub rescue peompt what is hapenning right now? That means the grub2 you are trying to boot is broken, doesn't relate to a correct root partition. It might be an old grub2 leftover.

Try booting from another disk, if you have more than one. Or if not, you will have to fix this grub2.

Do you have more than one disk?

PS. Running grub-update in the rescue prompt is pointless, it has only limited functionality. The command is update-grub and it needs to be run from a booted OS, not from a rescue prompt.

---

### Post by davethewave83 on 2013-01-05
i booted into Windows and diskinternals linux reader can still read the linux partition and files. in computer management I have Disk 0 (windows)
Disk 1 | old windows partition |* Swap | Linux | misc-storage *|

| | being primary and |* *| being extended

it used to be 
Disk 0 | system reserved |old windows partition |* Swap | Linux | storage *|

but I removed system reserved which messed up grub I think since it mounts by /dev/*** rather than UUID

now I re-created system reserve but it still says no such partition

I do know the linux partition is intact but I don't know my way around grub to point it to it.

I found the partition is (hd0,msdos5) and am in "normal" mode but don't yet know how to load a kernel or boot beyond this

---

### Post by darkod on 2013-01-05
If ubuntu is on disk 1, it would probably be (hd1,msdos5) instead of (hd0,msdos5). But you can try both.

And the system reserved is windows related, grub2 and ubuntu has nothing to do with it. Deleting that partition can't break grub.

To boot from grub rescue, you would execute one by one:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdos5)
linux /vmlinuz root=/dev/sda5
initrd initrd.img
boot
```

Note that it might be on (hd1,msdos5) as mentioned. In that case the root= in the linux line woult be root=/dev/sdb5. If you want, you can check where the vmlinuz and initrd.img files are before you start so you know where is root. In the rescue prompt you can list all partitions with:
ls

To see if vmlinuz and initrd.img are on a particular partition you can also try like:
ls (hd0,msdos5)

---

### Post by davethewave83 on 2013-01-05
thanks for the help. I did it a bit differently and did 
 set prefix=(hd0,msdos)/boot/grub
     set root=(hd0,msdos5)/
     insmod (hd0,msdos5)/boot/grub/normal.mod
     
apparently the next magic command I was looking for was "normal"

I typed normal and it booted now I need to repair grub :D

it all went more smoothly once I realized you can use the ls command

---

### Post by darkod on 2013-01-05
I suggest you reinstall it first so that it boots correctly with the full menu. Later you can adjust as you like:
```
sudo grub-install /dev/sda
sudo update-grub
```

That will reinstall it to the MBR. Later if you want to adjust it, you can copy the menuentry statements from grub.cfg to /etc/grub.d/40_custom and in there you can adjust the menuentry title as you like. Running update-grub will include these in grub.cfg. Once you are happy how it works with your manual entries, you can disable the os-prober with:
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

If you ever want to, you can always enable it again with +x.

---

