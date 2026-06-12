---
title: "Ubuntu 9.04 only boots up with escape at load up bar then have to hit enter"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by Throbbing Gristle on 2010-02-12
Been chasing this problem for awhile ! Not sure what to say or ask at this point. Can anyone help? This is effecting fsck check too as it will freeze up till I hit escape. After which it runs fine at boot up. It has drove me batty trying to correct. Worked on 8.04 but my Alfa wireless usb would not run on that Kernel. 

Up graded to 8.10 worked fine no Alfa wirless. Last upgraded to 9.04 Alfa working great but boot up is not right? Can any one Help. I am new to Linux and don't want to give up! Battling this for two months now I think..

---

### Post by Throbbing Gristle on 2010-02-12
Any body know where I can look to read up on this for myself?

---

### Post by raymondh on 2010-02-12
I saw this thread this morning and it baffled me as well.  Anyway, let's get some info and hopefully we can spot something ... or another member can chime in.

You're using 9.04 and GRUB-legacy, right?  Single-boot or dual?  If dual, with what OS?

There's a [bootinfoscrip]("http://sourceforge.net/projects/bootinfoscript/")t that has proved very helpful in understanding not only your HD but your boot process as well.  [Instructions here]("http://ubuntuforums.org/showpost.php?p=8104352&postcount=1").  That will provide a results.txt file (usually saved to your desktop by default).  Kindly paste that file in your next post.  Also (to make it easier to read) when you post the file, kindly highlight the whole file and then wrap in in codes.  Codes is the # icon amongst the toolbars in your reply window.

Absent that (or should you have difficulties), pls. share the HD set-up and the /boot/grub/menu.lst.  Access a terminal (applications > accessories) and type :

```
sudo fdisk -l
```

That will give us the set-up of your HD

```
gksudo gedit /boot/grub/menu.lst
```

Gedit will output the file.  Just highlight it and COPY & paste in your next post.

Lastly ... did you have this strange boot behavior when you tried 8.04?  Also, what happens if you unmount the wireless USB and reboot ... do you have the boot behavior still?

No guarantees .... but will give this a shot/look :)

Raymond

---

