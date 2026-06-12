---
title: "[SOLVED] suspicious added GRUB menu doesn't work"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Mr.Wellington on 2008-05-28
Hello all
My Computer: HP DV6409 laptop
My Distro: Ubuntu 8.04 Hardy Heron

Boot Options in GRUB: (abbreviated)
Ubuntu 8.04 (recently appeared)
safe mode (recently appeared)
Ubuntu 8.04 (again)(this is the one that works)
safe mode
memtest86
others:
Windows XP

After a recent update to my machine, a new grub option has appeared at the top.  It autoloads (after the 5 seconds, of course) a setup that is almost exactly like my actual desktop, except there is no wireless to connect to my router with. 

My question is: How do I either take away this option or take away that desktop
~and~ 
will this option affect the long term use and/or security of this comptuer?

---

### Post by iaculallad on 2008-05-28
> **Mr.Wellington said:**
> Hello all
My Computer: HP DV6409 laptop
My Distro: Ubuntu 8.04 Hardy Heron

Boot Options in GRUB: (abbreviated)
Ubuntu 8.04 (recently appeared)
safe mode (recently appeared)
Ubuntu 8.04 (again)(this is the one that works)
safe mode
memtest86
others:
Windows XP

After a recent update to my machine, a new grub option has appeared at the top.  It autoloads (after the 5 seconds, of course) a setup that is almost exactly like my actual desktop, except there is no wireless to connect to my router with. 

My question is: How do I either take away this option or take away that desktop
~and~ 
will this option affect the long term use and/or security of this comptuer?

You could edit you /boot/grub/menu.lst, that's where those options are located. Just be careful of what you're removing. Remove it if you're sure that it's not being used.

---

### Post by Herman on 2008-05-28
When we are given a new kernel in an update for Ubuntu, the script called 'update-grub' is run, and that reads the 'debian automagic kernels list' in our /boot/grub/menu.lst file and makes a new menu.lst for us with the booting stanzas added to the top of the list for the new kernel.

For most people it's generally better to boot the latest kernel, but you don't have to. 
If you find that there's something that doesn't work in your system with the new kernel, you can keep on using the older kernel, just by selecting that from your GRUB menu at boot time.

If you decide you don't ever want to use the newest kernel, you can either '[hash out]("http://users.bigpond.net.au/hermanzone/p15.htm#hide_items")', or delete the boot stanzas for it, or just copy them and paste them further down in your menu.lst file.

With luck, the next kernel will come out after some time and you'll be updated to that one and it won't give you any problems.
Updates are sometimes security related, but many updates are for fixing problems with various kinds of hardware. By the sounds of things, you were just unlucky and instead of fixing a problem with your hardware, the new kernel has a problem with your hardware that the older kernel didn't have.

To edit your /boot/grub/menu.lst file in Ubuntu, you'll need to open up a terminl and run a command like this,
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Mr.Wellington on 2008-05-29
> **Herman said:**
> When we are given a new kernel in an update for Ubuntu, the script called 'update-grub' is run, and that reads the 'debian automagic kernels list' in our /boot/grub/menu.lst file and makes a new menu.lst for us with the booting stanzas added to the top of the list for the new kernel.

For most people it's generally better to boot the latest kernel, but you don't have to. 
If you find that there's something that doesn't work in your system with the new kernel, you can keep on using the older kernel, just by selecting that from your GRUB menu at boot time.

If you decide you don't ever want to use the newest kernel, you can either '[hash out]("http://users.bigpond.net.au/hermanzone/p15.htm#hide_items")', or delete the boot stanzas for it, or just copy them and paste them further down in your menu.lst file.

With luck, the next kernel will come out after some time and you'll be updated to that one and it won't give you any problems.
Updates are sometimes security related, but many updates are for fixing problems with various kinds of hardware. By the sounds of things, you were just unlucky and instead of fixing a problem with your hardware, the new kernel has a problem with your hardware that the older kernel didn't have.

To edit your /boot/grub/menu.lst file in Ubuntu, you'll need to open up a terminl and run a command like this,
```
gksudo gedit /boot/grub/menu.lst
```

Wow, thanks. Do all debian-based Distro's do this? Or just Ubuntu that anyone knows of?
I think i'll just try setting up wireless under the new kernal.  I assume it wouldn't work automagically; this is Linux afterall.
It shouldn't be tough. 

Thanks for all the help!

---

### Post by Herman on 2008-05-29
> Wow, thanks. Do all debian-based Distro's do this? Or just Ubuntu that anyone knows of? All Debian based distros should do that, at least as far as I know. It's a wonderful feature.
> I think i'll just try setting up wireless under the new kernal. I assume it wouldn't work automagically; this is Linux after all. It shouldn't be tough.  Yes, do try and see if you can get it going. If it won't work, and you're sure it's a bug, (it seems like one to me), you might be able to help developers by submitting a bug report in case there's a mistake somewhere in the new kernel.

As a co-incidence, I was just browsing in the Community Cafe section area of the forums, and there's a 'sticky' there leading to some very interesting videos which give some insight into the way developers work. 
Here's an interview with MR. Brian Murray, Ubuntu's bug master, [UDS Prague (Intrepid Ibex) - Brian Murray]("http://www.youtube.com/watch?v=UpnAyzYXvwU").
Here's another one from Ubuntu's kernel developers, [UDS Prague (Intrepid Ibex) - Kernel Team Briefing]("http://www.youtube.com/watch?v=rmYsCf0Phbw&feature=related").
Wowee! In that second video, Colin King say there are over 9 million lines of code in a Linux kernel and around a million of them might be changed between one kernel version and another! 

It would only take as much as one punctuation mark or mis-spelled command or a whitespce in the wrong place to cause a bug somewhere in those 9 million lines! 
(Lucky it doesn't invovle me or Ubuntu would be in some trouble! :lolflag:)

Here's the link leading to all those films, (there are  lot more),                                                                 [Videos from the Ubuntu Developer Summit (UDS)]("http://ubuntuforums.org/showthread.php?t=800874"). I' think they're extremely interesting although I'm struggling to be able to comprehend all the specailized lingo. I'm going to keep watching them all to try to improve my knowledge.

---

