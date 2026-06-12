---
title: "Running Adobe Creative Suite CS4?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by hhtmp88 on 2010-01-31
Dear all,

If I want to run Adobe Creative Suite CS3 or CS4 on Ubuntu 9.10, which one should I use:
-> WINE?
-> or VirtualBox?


My first target is to run Photoshop CS3 and Adobe Illustration CS4

Anyone successfully doing so?

Thanks for any kind of help!
Rgds,

---

### Post by zvacet on 2010-02-01
You will have less or no trouble if you run it in Vbox,because you will install Windows in Vbox and then you can install any Windows software.Only limitatio  can be ram,because host OS and OS inside Vbox share ram and if you want to use Photoshop you know it is ram consuming.

---

### Post by hhtmp88 on 2010-02-02
Thanks zvacet for your suggestion!

Actually I am intended to buy Giada N10 Full HD media PC with:
[FONT=Wingdings][/FONT][FONT=Arial]Processor[/FONT]
                                       [FONT=Arial]Intel® dual-core ATOM™ N330 1.6GHz[/FONT]
                                                         [FONT=Arial]GPU[/FONT]
                                       [FONT=Arial]nVidia® Ion™, Support 1080P movie[/FONT]
                                                         [FONT=Arial]Memory[/FONT]
                                       [FONT=Arial] 2GBDDR2 RAM[/FONT]
-> [http://giada.cc/chanpinzhongxin/minipc/slim%20series/2009-10-30/1.html#ecms](http://giada.cc/chanpinzhongxin/minipc/slim%20series/2009-10-30/1.html#ecms)

so is this configuration enough for running ?
Ubuntu Netbook Remix  
+ Virtual Box
+ WinXP SP3
+ Photoshop CS4
+ Illustration CS4


Rgds,

---

### Post by zvacet on 2010-02-03
I think it will work,but slowly when you start Photoshop.Illustrator is not that much ram consumig .Maybe someboddy else know better but I believe it will work.

---

### Post by snowpine on 2010-02-03
The Intel Atom 330 is a bad choice if you plan to run virtual machines. The Atom does not have virtualization hardware support built in to the CPU.

[http://en.wikipedia.org/wiki/Intel_VT#Intel_Virtualization_Technology_for_x86_.28Intel_VT-x.29](http://en.wikipedia.org/wiki/Intel_VT#Intel_Virtualization_Technology_for_x86_.28Intel_VT-x.29)

I have tried to run Adobe CS inside Windows XP in Virtualbox on my Atom 330 computer. Performance is very poor.

On low end hardware, best performance will be achieved by dual-booting Windows/Ubuntu and installing native Windows apps (like Adobe CS) within Windows.

---

### Post by hhtmp88 on 2010-02-04
Thanks all for your comments!

Dual booting seems to be the only choice, however...
-> as I will use Giada mainly for Movie Seeing & Listening to music
-> fast booting... and without any key-in of login name & passwords are prefered

-> so, I am asking if anyone has tried
Giada N10 (or the similar)
+ Ubuntu Netbook Remix  
+ [SIZE=4][COLOR=SeaGreen]**Wine**[/COLOR][/SIZE]
+ Photoshop CS4
+ Illustration CS4

Rgds,

---

