---
title: "Feisty Boot Fails where Edgy worked"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by wlanphear on 2007-04-21
Hello,
I am having a problem installing feisty. I downloaded the iso and burned a cd. The live operating system starts, everything seems to be working. I ran the full install using the full disk (wiping everything there). However, when I start the computer I get a grub starting message, then a blank screen.

I used the same procedure to install Edgy, and had no problems.

I am not sure what steps to take to debug the problem.
Can anyone offer any help?

Thanks
Will

---

### Post by pepsi_max2k on 2007-04-21
sounds like it might be a grub error. where did you install grub to and are you sure the entry for ubuntu in /boot/grub/menu.lst is correct?

---

### Post by wlanphear on 2007-04-21
I figured out some more information.
In the grub menu, if I select 'kernel 2.6.20-15-generic (recovery mode)', the system will boot to a terminal.
If at the terminal I press escape, the computer boots normally.
I am able to login and use the system (that's what I am doing now)

However, if I select 'kernel 2.6.20-15-generic', I do not see anything past the grub loading message.

Please let me know if I can provide any more information.

Will

---

### Post by wlanphear on 2007-04-21
Here are the lines from menu.lst

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=30e620b2-3460-440a-8fb4-059699c5512f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=30e620b2-3460-440a-8fb4-059699c5512f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

Like I said, recovery mode seems to work, but just generic does not

Will

---

### Post by B-&gt;J-&gt;Eagle on 2007-04-21
i have got the same problem, and i do not have a clue what to do. In grub i cant use any of the boot modes.

My system are one 150disk and one 300disk
the 150 is partitioned into 4
30 for win
30 for linux
0.1024 for swap
and the rest as a normal storage partition

the win partion is not mounted
the linux partion is mounted as ''/''
the swap is swap
and the rest is mounted /media/sda4

the other 300gb drive is mounted /media/sdb1

but the error 17 just says. Cannot mount selected partition.

what selected partition.....
ive been running 6.10 with no problem before

help me

---

### Post by Lemony Fresh on 2007-04-21
I am having the same exact problem.  I installed 32 bit Feisty last night with no problems.  I descided to install 64 bit this morning and the same problem as above happened to me.  I couldn't get to the live install without choosing 800x600 in the f4 vga option.  I tried to adjust my xorg.conf, thinking a resolution problem may be the culprit.  No love.  I am puzzled at the moment unless it has something to do with my ATI x800 (it worked in edgy fine.)

---

### Post by wlanphear on 2007-04-21
I figured out my problem.

I found this post:
[http://ubuntuforums.org/showthread.php?t=416474](http://ubuntuforums.org/showthread.php?t=416474)

Removing splash from "kernel 2.6.20-15-generic" in menu.lst solved allowed to computer to boot normally.

Anyone have any ideas why this might be necessary?

Will

---

### Post by pepsi_max2k on 2007-04-21
that "splash" bit looks a little suspect... the only reference i can find to it on google is "splash=silent" which stops a load of bootup text being shown at the start (looks kinda like bios stuff, but lots of it). that said, i've got exactly the same in mine and it works fine. try "splash=silent" anyway, it's not like you can see the text with the load bar image there anyway.

---

### Post by Lemony Fresh on 2007-04-21
It seems to be a resolution problem.  Or a refresh problem.

---

