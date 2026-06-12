---
title: "Dual Booting Ubuntu and Windows 7 BUT giving Control to Windows Boot Loader"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by ramnarayan on 2010-10-08
Hi

Some time back i tried to install Ubuntu alongside Windows 7 on a New Dell Inspiron 14, 64 bit i5 processor. There were some problems (cannot say what caused it) but the computer crashed and the on board Dell recovery partitions went missing - so recovery did not work.

Apart from the bad press that it generated (the usual Ubuntu crashed computer bit) it was a bit of a headache to get the system repaired, luckily under warranty. Dell of course did not say what was wrong - just a yellow post it saying "afhrl debugging" (atleast the afhrl looked like a afhrl which could have been anything.

So my friend , who continues to be my friend even after the system crash, wants me to have another go at installing Ubuntu. Seems my good will from various linux based rescue ops outweighed the bad press. 

But this time i was thinking of doing something different - I want to install Ubuntu 10.04 along side windows 7 but want to give BOOT CONTROL to the windows boot loader. The current windows 7 has 3 partitions - the Win 7 OS, the dell recovery and dell utilities. The last time Ubuntu did mess up by not showing the dell recovery and the dell utilities making it impossible to recover the machine.

My main question is How do i give Windows Control of the boot process. Having never done it before my google searches are not coming up with good results and further i know from my friends on this forum i can expect good advice - mostly ;-)  

While my own preference would have been to give Ubuntu full control this case seems to be an exception  after all goodwill lasts only that much.

looking forward to advice

thanks
ram

---

### Post by sikander3786 on 2010-10-08
For me Grub has always proven to be a better and safer approach.

However, you can achieve what you are thinking of. Install Ubuntu as usual, just at step 8 of the installer, just before clicking Install, click Advanced and untick Install Bootloader.

After completion of installation process, boot into Windows 7 and then install EasyBCD.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by The_Mad_Hatter on 2010-10-08
windows 7 ........... control panel, system and security select "back up your computer" , "create a system repair disk" ............. if you go this route you can boot back off the cd and restore your recovery, although it will act as if it doesn't want to load in some cases just sit back it is slow .

---

### Post by Mark Phelps on 2010-10-08
> **ramnarayan said:**
> But this time i was thinking of doing something different - I want to install Ubuntu 10.04 along side windows 7 but want to give BOOT CONTROL to the windows boot loader.

In this forum, everyone will tell you to use GRUB -- which is NOT what your asking about.

You need to install and use EasyBCD to do what you want. Best way to do that is to go to the NeoSmart Technology forums, download EasyBCD from them, and read through their FAQs about what you want to do.  They also have live forums, so you should post your question there if the FAQs don't give you enough info.

And don't let folks here tell you it can't be done -- I've already done it myself on another PC.

---

### Post by ramnarayan on 2010-10-08
> **sikander3786 said:**
> For me Grub has always proven to be a better and safer approach.

Mostly true , however since you mention better and safer - what can go wrong with the windows boot loader


> **sikander3786 said:**
> However, you can achieve what you are thinking of. Install Ubuntu as usual, just at step 8 of the installer, just before clicking Install, click Advanced and untick Install Bootloader. 

Thanks, just what the Dr ordered, now i know how :-)

> **sikander3786 said:**
> 
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

ah ha, already done that, got the link while googling from another Ubuntu page.

So all that is left is to do it :-)

will let you know how goes.

thanks
ram

---

### Post by ramnarayan on 2010-10-08
> **Mark Phelps said:**
> In this forum, everyone will tell you to use GRUB -- which is NOT what your asking about.

<snipped>

And don't let folks here tell you it can't be done -- I've already done it myself on another PC.

Thanks Mark - Sikander pointed me in the right direction and you have just reinforced that.

much as i would like to give Grub the control in this case i need to make sure that windows performs well and Ubuntu too.

**
helping people get started with Linux (Ubuntu) is my passion and this tool just gives me more effective tools. Also its a much much better option than WUBI 

Last - the only reason i asked in the first place was another person i know had done it on his windows computer, had written to him first but he was / is out somewhere so risked posting here and sure enough am very lucky to get such clear and good responses so fast. Was half expecting a complicated how to and the other half was "WINcing" at the expectation of dragon flames ;-) 

thanks all and regards
ram
PS Mark Phelps - are you a relative of Michael Phelps, if so can you get his autograph ;-)

---

