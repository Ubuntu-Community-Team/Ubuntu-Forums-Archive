---
title: "Is it Grub or Grub2 you decide"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by jlbprof on 2010-02-04
I am so confused in regards to Grub.  I am dual booting a netbook with XP and 9.10 Desktop.  It works great, just want to make a few minor edits.

Here is the issue, after looking at the structures of the files and directories etc.  It looks like I have Grub2.  I don't have a menu.lst I have a grub.cfg.   I have the /etc/grub.d directory with the files that look like init files.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

So I go find the docs for Grub2, and here is the kicker.  As the Grub2 docs say to find out what version you have of Grub I type:

grub-install -v

And the response is:

grub-install (GNU GRUB 0.97)

Yet the Grub2 doc says it should be 1.97, so I have the file structures for Grub2, but the executable for Grub 1.

What is going on?

Thanx

Julian

---

### Post by Ginsu543 on 2010-02-05
What does the opening grub screen say when you first boot up, 0.97 or 1.97? I believe that you have GRUB legacy installed, not GRUB2. My system also has the file structures for GRUB2 but it is definitely booting off GRUB legacy. My guess is that when I installed the OS on my RAID0 array, it first tried to install GRUB2 but downgraded to GRUB because GRUB2 is incompatible (I was using the Live CD, not the alternate CD) with RAID arrays. Since I have no issues booting all three of my OSes (Karmic, Jaunty, and Win XP) with GRUB, it never concerned me that I have GRUB legacy rather than GRUB2.

---

### Post by adam814 on 2010-02-05
I'm skeptical about this missing menu.lst.  Some distros (i.e. Gentoo) symlink grub.cfg to menu.lst, but of course the grub.cfg uses the legacy grub syntax since a file intended for GRUB2 would be incompatible.

You could see which packages you have installed like this:
```
dpkg --list | grep grub
```

I wouldn't be surprised if you have packages for both installed, with GRUB2 actually on the MBR.

---

### Post by jlbprof on 2010-02-06
```

julian@Julian-netbook:~$ dpkg --list | grep grub
ii  grub                                 0.97-29ubuntu59                            GRand Unified Bootloader
ii  grub-choose-default                  0.2-6                                      Control Grub Default through a GUI
ii  grub-common                          1.97~beta4-1ubuntu4.1                      GRand Unified Bootloader, version 2 (common 
rc  grub-pc                              1.97~beta4-1ubuntu4.1                      GRand Unified Bootloader, version 2 (PC/BIOS
julian@Julian-netbook:~$ 

```

It appears I have both, I will reboot now and see what it says when grub is on the screen.

Julian


> **adam814 said:**
> I'm skeptical about this missing menu.lst.  Some distros (i.e. Gentoo) symlink grub.cfg to menu.lst, but of course the grub.cfg uses the legacy grub syntax since a file intended for GRUB2 would be incompatible.

You could see which packages you have installed like this:
```
dpkg --list | grep grub
```

I wouldn't be surprised if you have packages for both installed, with GRUB2 actually on the MBR.

---

### Post by jlbprof on 2010-02-06
When I reboot, Grub says 1.97 so I have 1.97 but also the old one.   Mystery solved, thanx.

Julian

---

