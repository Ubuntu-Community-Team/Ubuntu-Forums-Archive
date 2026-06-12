---
title: "Multibooting GRUB issues"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by The-Russ on 2008-04-04
What's up everyone,

I have been using Ubuntu for quite some time now and, when I began studying for the CompTIA Linux+ exam, I was informed that the exam is geared more toward other distributions (namely: Fedora, openSUSE, and Mandriva). I decided I'd go ahead and give Fedora and openSUSE a try, but it seems I made a terrible error while installing Fedora. Here's the situation:

I have 2 hard drives. The primary master contains Windows XP, and the primary slave contains Ubuntu (first partition), and Fedora (second partition). The installation went pretty well, except Fedora's GRUB menu took over Ubuntu's, which I liked much more because it was so basic looking. At first, I couldn't even access either of my other partitions, so I edited menu.lst and found that "Other", was pointing to hd0,0. I redirected it to hd0,1 and now I can access Windows XP again, but I'm having trouble getting the GRUB menu to point to my Ubuntu partition.

Ideally, I would prefer to get Ubuntu's version of the GRUB to show up when I boot, and then I could select my OS from there. However, if this isn't possible, or if it would be insanely difficult, I would at least like to be able to access Ubuntu again from Fedora's GRUB menu. I am willing to go to pretty great lengths to get Ubuntu's GRUB loader back, though. My current entry in Fedora's menu.lst file appears as:

title Ubuntu
	root (hd1,1)
	kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4065bf65-544c-4a9c-8157-162b7d7ca525 ro quiet splash
	initrd		/boot/initrd.img-2.6.22-14-generic

I just copied the entry from Ubuntu's menu.lst file (which I accessed through Fedora). I'm not very good at this just yet so I'm not sure what changes need to be made. If I select Ubuntu from the GRUB loader, I receive a message that the partition can't be mounted, which I assume is because my entry in the menu.lst file is just completely wrong. If anybody can help me with this, it would be greatly appreciated. Thank you in advance.

---

### Post by confused57 on 2008-04-04
Your root for Ubuntu should probably be (hd1,0), if Ubuntu is on the first partition.

You can also use the live cd to reinstall Ubuntu's grub to the primary boot drive's mbr:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd1,0)", to install Ubuntu's grub:
```
root (hd1,0)
setup (hd0)
quit
```

Then you can add a configfile entry to Ubuntu's menu.lst to boot Fedora:
```
title  Fedora
configfile  (hd1,1)/boot/grub/menu.lst
```

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

---

### Post by The-Russ on 2008-04-04
That worked perfectly! You're a genius! I can't thank you enough for your help. But at least I can say, with sincerity, thank you very much for your help.

---

### Post by confused57 on 2008-04-04
> **The-Russ said:**
> That worked perfectly! You're a genius! I can't thank you enough for your help. But at least I can say, with sincerity, thank you very much for your help.
Glad to have helped...I've booted my share of different distros & it's the method I prefer.

---

