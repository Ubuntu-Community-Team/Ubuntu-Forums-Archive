---
title: "Can't access windows 7 after installation of ubuntu 11.04"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by tekas1234 on 2011-05-07
Earlier I had XP as my System Partition and Windows 7 installed parallel to it.
Then I installed ubuntu 11.04 by formatting the XP drive .....and installing in that drive...
  I created a new 25 gig ext4 partition (with a / mount point) in the free space of my drive, and no SWAP space.
Then when I restarted my computer it didn't ask me which OS i want to start. It started ubuntu directly.
and after logging into ubuntu i can see my other drives are safe....and no data has lost.
I can access my Windows 7 drive partition from there . So this means that windows is still there ...safe in tis place.

Now how can i run my windows 7 OS ?? What can be done to get it back ????
Plz Help .....

Thanks in Advance ...

---

### Post by Quackers on 2011-05-07
If you open a terminal and type in (or copy/paste) ```
sudo update-grub
``` then press enter then type your password and press enter you can watch as grub.cfg is run to see if the Windows Loader is recognised. If it is, reboot and you should now get a grub menu with both operating systems listed.

---

### Post by tekas1234 on 2011-05-08
When i run the command :
sudo update-grub

It gave the output as :

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done

I think this is not detectiog the windows 7......definiteky these 3 are for linux only.....
So now what can be done to run windows 7 again....????

---

### Post by wilee-nilee on 2011-05-08
> **tekas1234 said:**
> Earlier **I had XP as my System Partition and Windows 7 installed parallel to it**.
Then I installed ubuntu 11.04 by **formatting the XP drive** .....and installing in that drive...
  I created a new 25 gig ext4 partition (with a / mount point) in the free space of my drive, and no SWAP space.
Then when I restarted my computer it didn't ask me which OS i want to start. It started ubuntu directly.
and after logging into ubuntu i can see my other drives are safe....and no data has lost.
I can access my Windows 7 drive partition from there . So this means that windows is still there ...safe in tis place.

Now how can i run my windows 7 OS ?? What can be done to get it back ????
Plz Help .....

Thanks in Advance ...

More then likely you had the xp and w7 boot intertwined no biggie, follow these instructions so we can see. 

State if you have a W7 recovery or install cd/dvd/thumb.

So from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

If you have no recovery disc get this one and get set up to use it, you may need it in the future if not now.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by Rubi1200 on 2011-05-08
You should definitely follow the advice posted by wilee-nilee as far as the boot script is concerned.

But, you could also try this command to see if it picks up the Windows install:

```
sudo os-prober
```

---

### Post by xp15 on 2011-07-20
thank [Rubi1200]("http://ubuntuforums.org/member.php?u=1040746"), you helped me so much! :D

---

