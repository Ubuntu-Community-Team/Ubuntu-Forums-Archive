---
title: "Can't load my Netbook Maverick liveCD or USB"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by globetrotter4life on 2011-01-08
Hi all,

I'm in a bit of a jam here. I have an Acer Aspire One ZG5 netbook onto which i'm trying to install Ubuntu Netbook, but every liveCD and liveUSB I make gives me the same problem: I can't even load it, it gives me the following error:

```

No init found. Try passing init=bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

```

I know, this message has bothered plenty of people already and there are a ton of threads about it, but none of them have solved my problem yet...

In the meantime I'm stuck with the native Linpus Lite, which works but is far from being as flexible as I'd like it to be...

I could also try to install 10.04 and do the incremental upgrade, but that would take forever and isn't as clean...

---

### Post by maumaudon on 2011-01-12
i have this exact problem man. did you solve it?

---

### Post by amsterdamharu on 2011-01-12
Did you use unetbootin to create the USB? It looks like either the iso is corrupt or the path to the initrd is wrong.

After creating the USB check out the syslinux.cfg on the root of the USB stick.

---

### Post by maumaudon on 2011-01-12
amsterdamharu am befriending you.

---

### Post by globetrotter4life on 2011-01-15
Thanks amsterdamharu, i'll give that a shot.

Yes, i used unetbootin to create the usb key, and i've tried downloading the iso several times so i doubt every one of them was corrupt... Not only that, the Maverick Desktop iso i downloaded doesn't work either! must be either of the two other things you mentioned...

I'm not that big a programmer so I'm not quite sure how to do things...
what should i be looking for/setting in sysconfig?
what should the initrd path be and how can i find it/set it?

---

### Post by amsterdamharu on 2011-01-15
could you post the syslinux.cfg that's on the usb stick?

When you see the [FONT=monospace]
[/FONT]```
[FONT=monospace](initramfs)_
```

If you type help are there a lot of commands?

I wonder if this command works:

[/FONT]```
cat /var/log kern.log
```[FONT=monospace]
or
[/FONT]```
exit
```
And then
```
cat /var/log kern.log
```[FONT=monospace]
[/FONT]
[FONT=monospace]
[/FONT]

---

### Post by mjc314 on 2011-06-28
well looks like I am reviving this thread I am trying to put 10.10 netbook remix on my brothers netbook and this is what my syslinux.cfg reads



default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit vga=788 rescue/enable=true -- quiet

label ubnentry0
menu label ^Back..
kernel /ubnkern
append initrd=/ubninit 



Also those 2 commands amsterdamharu listed I did those and first one  I got gave me 

cat: can't open '/var/log' : No such file or directory
cat: can't open 'kern.log' : No such file or directory 

and the exit command put it in to panic (what ever that means)

---

