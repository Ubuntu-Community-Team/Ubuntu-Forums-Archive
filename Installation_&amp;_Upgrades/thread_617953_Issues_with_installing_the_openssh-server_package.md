---
title: "Issues with installing the openssh-server package"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by wjh on 2007-11-19
Greetings all, I have a newish install of Ubuntu 7.04 (LAMP)Server x86, and I was installing the openssh-server package, when two things (so far!) came up that I'm hoping you can help me with. I first updated the packages database, by typing “sudo aptitude update” and it told me to run an apt-get upgrade, so I sudo'd “apt-get update” and it draws a few lines and then repeats the request to “run the apt-get update” ie: a loop.....why?

I went on to the install, typing “sudo aptitude install openssh-server,” and when it prompted me for the ubuntu install cd, I put it in the tray and pressed enter, but I get the error “cdrom: failed setting in the lba address space.” I tried hitting enter a few times, removed and reinserted the cd but no joy, so I <ctrl>-C'd out. I tried “sudo unmount /media/cdrom”, thinking I might unmount and remount the cd (which shows up OK in BIOS), but no better.

Any help in understanding these points is appreciated.

Thank You.

Best,
Walter.

---

### Post by taurus on 2007-11-19
You don't have to install it from a CD if you don't want.  Just edit /etc/apt/sources.list

```
sudo nano /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Save it with <Ctrl>o and exit with <Ctrl>x.  Then run

```
sudo aptitude update
sudo aptitude install openssh-server
```

---

### Post by wjh on 2007-11-20
Thank you for the reply, Taurus-- that sounds like a great work around that will allow me to install the package, which is wonderful! I am still wondering, though...  Any idea why the CDROM did not work, and do I need to "fix" it, somehow? 

Also, could you, or someone, please explain why the "apt-get" loop is showing up?

Thank you again, 

Best,
Walter.

---

### Post by wjh on 2007-11-20
PS -- The cdrom drive worked fine yesterday, when I used it to install Ubuntu!

---

### Post by wjh on 2007-11-22
I commented out the line pointing to the cdrom in /etc/apt/sources.list, and installed the package without delay. The system told me that the package could not be verified, and asked if I wanted to install anyway. I did. 

Why could it not be verified? Does it need the cdrom to verify? What will be the consequences of not verifying?

The cdrom is still broken, with its "lba address space" error, but I am able to install (unverified) packages via the workaround kindly supplied, above.

---

### Post by taurus on 2007-11-22
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

