---
title: "Trouble installing on Pentium II"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by rossmurray on 2007-02-21
I'm attempting to install Kubuntu 6.06 on a friends old Pentium 2. I'm not sure how successful it will be but I'm stuck at basic DOS stuff.

When I attempt to restart with the boot disc in the CD drive Windows 98 just overrides and starts instead. So I tried restarting in MS-DOS where the CD drive isn't even recognised. I then downloaded an updated DOS driver to flash that loaded successfully but still doesn't recognise a drive in DOS.

Do I need to try something else? I'm more used to my Mac and simply holding down C to load from a CD but to not even find the INTERNAL CD drive just makes me mad. Could I boot from a Start Up floppy and then somehow once the CD d rive is recognised THEN use the Kubuntu install?

Please somebody help me as I've spent weeks getting not very far. I'll even send you Love!!

 ](*,) ](*,)

---

### Post by deeptingler on 2007-02-21
Hi,  What you should find is that MOST modern pcs are able to boot directly from a CD.  This is what you will be able to do with your Kubuntu/Ubuntu CD but first you will need to go into the BIOS on your pc to ensure that the order it is trying to boot is CD then Hard-Drive.  If it is the other way around (Hard Drive then CD) it means Windows will get to boot up before it even looks at the CD at all.

PLEASE READ UP ON BIOS GUIDES ON THE INTERNET FIRST....... IF YOU CHANGE A SETTING YOU MAY STOP THE MACHINE FROM BOOTING OR EVEN DAMAGE EQUIPMENT.  IF YOU DO CHANGE A SETTING, MAKE SURE TO TRY AND DO ONLY ONE CHANGE AT A TIME AND MAKE A NOTE OF WHAT YOU CHANGED SO THAT YOU CAN CHANGE IT BACK.

The key things you are really looking for though are the "boot order" of devices.

Good Luck - you wont regret the change to Linux.

---

### Post by tgalati4 on 2007-02-21
Depending on the video card, you may have better luck with 6.06.1 as the KDE environment uses more graphic resources and CPU power than standard Ubuntu.

Have you tried to get into the BIOS (del, tab, esc, F2, F12 upon bootup)?  You should be able to select order of bootup:  Floppy, CDROM, DISK

The other option is to create a Grub floppy that will give you a bootup menu and then you can select Windows Boot, CDBoot, or modify it for more complicated boot situations.

Search grub floppy

Good luck
Terry

---

### Post by rossmurray on 2007-02-21
Wow thanks for the quick reply guys!!

I'll try this out.

---

### Post by louieb on 2007-02-21
Some of those older P2s and P1s won't boot to a Linux CD even if BIOS is set to boot there first. I get around that by using a Smart Boot Manager floppy.  This is my page on how to make and use one.     [http://louboldt.com/ilinuxsbm.htm](http://louboldt.com/ilinuxsbm.htm)

---

### Post by rossmurray on 2007-02-22
Thanks so much for your VERY helpful responses. The BIOS keys seemed to do the trick though I did use louieb's sbm floppy too. Kubuntu won't load though so I'm gonna try an old 5.1 version I have of Ubuntu.

I'm hoping to get her iPod operational and possibly even the digital camera. I don't know where 5.1 stands with that but I'm staying positive and people like you guys are realy helping the process now. Will 5.1 still upgrade online?

---

### Post by tgalati4 on 2007-02-22
Yes and No.  5.1 is stable but not current.  Dapper 6.06.1 is current and stable.  There have been some issues with on-line upgrading between 5.1 and 6.06.  We would hate for you to spend time to get a working system under 5.1 only to get it mucked up with a 6.06 upgrade.

GTKPod works fine with my shuffle, mini, and nano2  and I shift back and forth between by mac iTunes and gtkpod with no ill effects.

You will probably have the best luck with the "Alternate Install" for Dapper 6.06.1.  It uses a text-based installer which is quicker on old hardware.  Same Ubuntu goodness in a quicker and safer installer.

Post the steps that you took to get a successful install.  PII hardware is marginal for Ubuntu performance, but if you max out the memory and upgrade the video card, you can have a workable system.

---

### Post by Flying George on 2007-02-22
I'm not terribly experienced, but Xubuntu is supposed to be designed for older systems, I suggest giving that a try.

---

### Post by rossmurray on 2007-02-22
> **tgalati4 said:**
> Yes and No.  5.1 is stable but not current.  Dapper 6.06.1 is current and stable.  There have been some issues with on-line upgrading between 5.1 and 6.06.  We would hate for you to spend time to get a working system under 5.1 only to get it mucked up with a 6.06 upgrade.
.... you can have a workable system.



Yeah. Only time will tell. I'm now downloading Alternate 6.06.1 as you suggest and will try this Monday possibly. Excellent news on the iPod's she'll be stoked!  :guitar: 

Every time we restart her system at the moment there are numerous registry issues that just won't budge. So slow it's almost hilarious. You have no idea how much your help is going to be appreciated if it finally works!  :KS

---

### Post by rossmurray on 2007-02-22
> **Flying George said:**
> I'm not terribly experienced, but Xubuntu is supposed to be designed for older systems, I suggest giving that a try.

I've not even noticed this version before. Thanks for the heads up! :) 

I'll also download this one as a back up for Monday.

---

### Post by amrypma on 2007-02-22
Also you might want to install a 386 kernel. the generic kernels are build with 686 command sets. Which will instantly crash your mashiene.

;-)

---

### Post by tgalati4 on 2007-02-22
The Ubuntu live installers are pretty good at picking the right x86 kernel to match the hardware.  At least I have never seen such a failure.  But good point nonetheless.

---

### Post by AmazingAnt on 2007-03-02
Well, my problem computer is running a 500MHZ Celeron, not a P2, but it's the same problem.
I've followed the same instructions, and got the computer to boot the Smart Boot Manager from the floppy. But, for some reason, the list does not show the CD drive. It has a rather long list of "Removable Drives", and so I tried each and every one, but it just gave me a pop-up saying there is no Operating System in that drive.

??? What can I do?

---

### Post by AmazingAnt on 2007-03-03
Well I'm a little disappointed that nobody's answered yet, but I fixed the problem already. Turns out that if I convince my BIOS that there really is a CD drive there, it doesn't need the floppy at all.

---

### Post by tgalati4 on 2007-03-03
We're glad that you were able to fix your CD boot problem.  Some of us have other jobs and we can't check the forums every day.

You can always subscribe to PAID Ubuntu support.  Then you will get all kinds of support.  Otherwise, you will have to wait for the answer train like everybody else.

Keep the faith!

---

