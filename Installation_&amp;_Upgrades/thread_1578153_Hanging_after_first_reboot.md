---
title: "Hanging after first reboot"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by Eno88 on 2010-09-20
Hello all,
 
There's a strange problem, after installing ubuntu 10.04.1 using wubi.
 
The installation goes fine in Windows, unpacks to an empty 15gb ntfs partition. After restarting to complete the installation, it would'n find the grldr but fixed that by copying over the wubi* files installed in C:.
 
Now the problem, the boot screen shows for a few seconds, switches to the default ubuntu wallpaper, the mouse cursor is there and working, and that's it. The installation doesn't continue, the keyboard won't work; Also I've tried all the additional options the installation offers when it asks to press Esc.
 
The system:
Wubi installed size: 15gb
32bit Ubuntu 10.04.1
4gb installed ram
nVidia 9800gx2
 
 
Using ubuntu for a month on my netbook determined me to add it to my desktop so I hope this gets fixed :popcorn:
 
Eno

---

### Post by bcbc on 2010-09-20
With 10.04 and nvidia there have been some problems. The way to get around it is to supply "nomodeset" as a boot option. When installing with wubi the ESC option doesn't give you an entry that includes this. Just press ESC, then 'e' on any of the options and within the big mess you find, look for 'quiet splash' then add 'nomodeset' after that i.e. 'quiet splash nomodeset' without the quotes - then CTRL+X to boot.

You will have to do this every time you boot until you can get the correct nvidia driver installed. If you want to you can edit /etc/default/grub and set it there in GRUB_CMDLINE_LINUX_DEFAULT
```
gksu gedit /etc/default/grub
# modify the cmdline default
sudo update-grub
```

---

### Post by Eno88 on 2010-09-20
That wasn't it. The system simply hangs showing the boot screen this time. 'noprompt' was in front of 'quiet splash' if it means anything...
 
P.s. Live cd has the same problem as in my first post.

---

### Post by bcbc on 2010-09-20
what computer brand/model is it?

---

### Post by Eno88 on 2010-09-20
It's not a pre-assembled. Here are the specs
 
[SIZE=1]Manufacturer:[/SIZE][SIZE=1]Gigabyte Technology Co., Ltd.[/SIZE]
[SIZE=1]Processor:[/SIZE][SIZE=1]Intel(R) Core(TM)2 Duo CPU E7500 @ 2.93GHz (2 CPUs), ~2.9GHz[/SIZE]
[SIZE=1]Memory:[/SIZE][SIZE=1]4096MB RAM[/SIZE]
[SIZE=1]Hard Drive:[/SIZE][SIZE=1]2 TB Total[/SIZE]
[SIZE=1]Video Card:[/SIZE][SIZE=1]NVIDIA GeForce 9800 GX2[/SIZE]
[SIZE=1]Monitors:[/SIZE][SIZE=1]Samsung SyncMaster 226bw - [/SIZE][SIZE=1]BENQ FP71G[/SIZE]
[SIZE=1]Sound Card:[/SIZE][SIZE=1]Sound Blaster X-Fi Xtreme Audio[/SIZE]
[SIZE=1]Speakers/Headphones:[/SIZE][SIZE=1]Logitech G51[/SIZE]
[SIZE=1]Keyboard:[/SIZE][SIZE=1]Logitech G25[/SIZE]
[SIZE=1]Mouse:[/SIZE][SIZE=1]Razer Mamba[/SIZE]
[SIZE=1]Mouse Surface:[/SIZE]
[SIZE=1]Operating System:[/SIZE][SIZE=1]Windows 7 Ultimate 32-bit[/SIZE]
[SIZE=1]Motherboard:[/SIZE][SIZE=1]Gigabyte EP31-DS3L[/SIZE]
[SIZE=1]Computer Case:[/SIZE][SIZE=1]NZXT Tempest[/SIZE]
 
 
[COLOR=silver]( yes... I'm a gamer :/ )[/COLOR]

---

### Post by bcbc on 2010-09-20
I can't see anything that should cause you problems other than nvidia, but the workaround should have taken care of that. Not sure why you are using wubi with all that disk space (as you likely have no problems partitioning). If you decided to try a direct install you could use the Alternate CD instead - it has more advanced installation options and *might* do a better job.

---

### Post by Eno88 on 2010-09-20
I'll give that a shot then. I'm quite-tech savvy and realize that shouldn't interfere with the first OS, being on another partition.

But I've had a lot of 'Murphy's law' situations lately, that's why I've used wubi; because it seemed safest, until I figure out how and what happens with the mbr and grub and windows' loader.. meh.

UPDATE:

Installed from the alternate cd (note: on logical partition), I can reach the login screen, enter the password, then it's back to problem #1,
When trying to use nomodeset, the screen just freezes at the ubuntu boot screen, as before.

Tried entering a tty while at the login screen, the display just shows the residual image of the login screen..

So... yeah :?

UPDATE 2:
I'm able to log into xterm, so I'm not completely locked out. Seems there might be a gnomey problem....

---

### Post by Eno88 on 2010-09-21
Bump. 'cause editing won't bump it :/

Edit: Solved, I think. Purging everything nvidia from xterm and rebooting seemed to do the trick.

... :D

---

