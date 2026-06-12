---
title: "Four operating system, how to install in order"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by ubuntogenius on 2008-03-24
I have a dell system PE 1950 with 2 hard drive, 500 GB each, setup Raid 0, two quad core 2.0GH, 8GB of RAM.
I want to install four OS on this system. Here is the info

1. Ubuntu 7.10 32bit Desktop Version (Main OS, 600GB, EXT3)
2. Ubuntu 6.10 32bit Server Version (50GB. EXT3)
3. SLES 9 SP3 64bit (50GB, ReiserFS)
4. SLES 10 64bit (Use the rest of the disk space avaiable, 200GB+, ReiserFS)

My question is which os should I install first and how?
Please help in step by step.

---

### Post by lcason on 2008-03-25
Pardon, but what is missing from your question is **_WHY _**you might want to multiboot these four flavors of Linux on the same box. If it is an academic exercise, then my practical suggestions below, gained from experience, won't help. And since you are asking for a step-by-step answer, I'll assume you are not doing looking to do this for the intrinsic reward of solving the puzzle. So you must be running some kind of test bed and need to boot these four flavors for testing.
[B]
THE HARD, BUT PURE TECHIE WAY: SCRIPT YOUR OWN BOOT LOADER, I.E. GRUB[/B]
Here's a [[COLOR="Blue"]GRUB recipe[/COLOR]]("http://books.google.com/books?id=FOZY-usVl6cC&pg=PA205&lpg=PA205&dq=multiboot+%22different+linux+distributions%22&source=web&ots=Rn7JXW9xSJ&sig=t3WUOO06H1nD8RD4k2ImmYixFtg&hl=en#PPA205,M1") from a cookbook. In theory it shouldn't matter what order you install these in and most Linux installers detect the presence of existing partitions, and ask you how you'd like to handle--overwrite or install in a different partition. Of course, you should have a sufficient number of separate partitions for all of this. And there is no shortage of opinions on how all those partitions should be setup. The favorite thing many Linux techies like to talk about is [[COLOR="Blue"]different distros[/COLOR]]("http://distrowatch.com/"). The next favorite thing is how to best partition HDs.

**IF YOU HAVE TO DO PERFORMANCE TESTING: Buy a commercial boot manager**
I was faced with a similar problem years ago building a multiboot 486 for DOS 6.2, OS2/Warp 3, Slackware Linux 1.x, MS Windows for Workgroups 3.1 and Windows 95 Beta. The OS2 boot loader was supposed to be able to handle it all--in theory. After buring a lot of money on long distance support calls to IBM, someone finally suggested a product written specifically for managing any OS that will boot on x86 hardware.  It is [COLOR="Blue"][[COLOR="Blue"]System Commander[/COLOR]]("http://vcom.avanquest.com/cat/prod.php?pid=2824") [/COLOR] It works very well and takes care of all the house keeping for you. Well worth the $69 if your time is of value. 
[B]
IF YOU ARE ONLY DOING FUNCTIONAL TESTING: Buy a Virtual Machine Manager[/B]
If you are doing functional rather than performance testing of code, VMware Workstation for Linux would be a good investment to look at. With 8 GB of RAM you could run all four flavors at once and forget about the multiboot idea.  BTW, you could pay a whole lot more money for ESX Server, but if you're using this as a test box, I doubt if it would help you much over Workstation. 

**FOURTH CHOICE: Use A Special Linux Tool**
[INDENT]**LUBI  **   [http://www.suseforums.net/index.php?showtopic=35420](http://www.suseforums.net/index.php?showtopic=35420)[/INDENT]
[INDENT]**User Mode Linux **   [http://user-mode-linux.sourceforge.net/](http://user-mode-linux.sourceforge.net/)[/INDENT]

Sorry that I didn't provide the exact step-by-step answer you were looking for but I hope that  this helps you decide how best to proceed.

Lee

---

