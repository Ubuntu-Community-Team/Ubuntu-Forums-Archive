---
title: "grub always returns &quot;invalid or damaged bottable partition&quot; , can't boot"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by loddite on 2011-08-10
hi. I've been running a dual-boot ubuntu 11.04 64-bit and windows 7 64-bit for a while now, and recently got a new computer. I moved the hard drives to the new computer (one had both os's on it, the other was just a storage drive) and windows 7 would not boot, so I reinstalled it. I used a live cd to repair grub using boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and everything looked to be going swell. But when I tried to boot I got "invalid or damaged bootable partition" instead of a grub menu. so I went back and, copying and pasting the commands the program gave me, I manually removed and reinstalled grub on my ubuntu partition. same error. so, I backed up all my documents onto a third drive, wiped everything out, and started again. I installed win7 on one drive, and then when that was done, I installed ubuntu on the other. lo and behold when I tried to boot I got the same error message, and now I can't even boot from my windows drive. The ubuntu drive is fairly new and according to disk utility has no errors. Is this some problem with grub or what? I'd really appreciate some help with this, I'm at my wit's end and would like to get my computer back :( 

oh dang I messed up the title :P

---

### Post by YannBuntu on 2011-08-10
Hello,
After the last time you reinstalled Windows, and before reinstalling Ubuntu, did you manage to boot to Windows ?

Please could you follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1821980") and indicate here the resulting URL ?

---

### Post by loddite on 2011-08-10
> **YannBuntu said:**
> Hello,
After the last time you reinstalled Windows, and before reinstalling Ubuntu, did you manage to boot to Windows ?

Please could you follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1821980") and indicate here the resulting URL ?
[http://paste.ubuntu.com/663059/](http://paste.ubuntu.com/663059/)

After the first reinstall of windows, it was able to boot just fine, although as I said I wasn't able to boot anything after I installed grub. After the second reinstall I'm not sure; I booted the live cd and reinstalled grub right after I'd installed windows.

edit: I'm going to try to place grub on all disks and see if that works. If it doesn't I'll paste a new url here.

---

### Post by YannBuntu on 2011-08-10
ok, I saw you have a problem in you GRUB conf file.

Please run Boot-Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
, click on "Advanced Options", tick "Create BooInfo", and validate.

(and show us the new URL :) )

---

### Post by loddite on 2011-08-10
[http://paste.ubuntu.com/663094/](http://paste.ubuntu.com/663094/)

I actually fixed the problem myself, somehow. I installed grub on all disks and booted from my windows disk. I was able to boot ubuntu but not win7. I ended up installing windows boot files on all drives, and ran update-grub on all drives. Now I can boot both OS's, but, here's what's interesting, I am also able to boot from the original drive I was having problems from. So apparently completely wiping the drive didn't fix the problem but running update-grub did? *shrugs*

If you notice any problems in that file please let me know, also if you could maybe explain why what I did worked for my benefit and whoever might see this thread in the future. Thanks!

---

### Post by YannBuntu on 2011-08-11
In your previous BootInfo summary your Windows sda1 partition was erased (ext4 format), and now it is restored and contains the appropriate boot files:
```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
```

so I guess it was repaired by your Windows CD. And then when you reinstalled GRUB it was detected correctly. :)

---

