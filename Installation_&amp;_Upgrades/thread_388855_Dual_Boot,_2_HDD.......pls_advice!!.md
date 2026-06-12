---
title: "Dual Boot, 2 HDD.......pls advice!!"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Dan Kay on 2007-03-20
OK...here's the deal.

I have one IDE drive already installed with a dual boot Edgy/WinXP....and everything is working great.....GRUB and everything works wonderful, no problems at all.

I just got a SATA drive I want to install Vsta onto (only Vista) and want to use both drives in my computer.

Obviously, GRUB is on the IDE drive with Edgy/WinXP.

Here are my questions......
With an IDE drive and a SATA drive there shouldn't be any problems with Master/Slave issues like there are with two IDE drives.....Are there??

If I set the computer's BIOS to boot the IDE drive first, GRUB should appear.... no problem...Right??

To have GRUB "point" to (or see) the SATA Vista drive, what do I have to do??

Edit GRUB and how??:confused: 

Could some of you wonderful community members help me with advise and (gosh I hope) the code I need to make this happen??:) 

There shouldn't be any problems with the two different drives and setup....right? Seeing that the three OS's are separated like this.....Am I on the right track?:confused: 

Thanks for all your help. (I'm a nOOB!!):confused:

---

### Post by confused57 on 2007-03-20
You "should" be able to set your system up this way with no problems...if I were you, I'd disconnect my IDE drive & set your SATA drive in bios as first hard drive booted.  Once you have Vista installed & up to date, then reconnect your IDE drive, change bios boot order to IDE, then SATA.
All you should need to do is add an entry to grub to boot Vista, maybe similar to this:

```
title              Windows Vista
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by Dan Kay on 2007-03-20
Thanks confused57!!

I was hoping it might (hopefully) be that easy.....COOL!

One question....What exactly do I type in the terminal to get to GRUB editor?

Thanks for your help....you're the dual boot guru!

---

### Post by confused57 on 2007-03-20
It "should" be this easy...at least by disconnecting your IDE drive, your current setup won't be affected, possibly by Vista installing it's IPL code to the IDE mbr.

This howto explains how to edit your menu.lst:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Good luck with it...I'm no guru, but I've picked up a few things here & there, especially from the first & second links in my sig.

---

### Post by Dan Kay on 2007-03-20
Excellent!....Thanks again for your help and quick response. I'll be sure to let you know how it goes.:biggrin:

---

