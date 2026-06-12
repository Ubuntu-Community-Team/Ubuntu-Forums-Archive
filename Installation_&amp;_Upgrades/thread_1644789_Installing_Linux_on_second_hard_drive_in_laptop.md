---
title: "Installing Linux on second hard drive in laptop"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by hpng on 2010-12-13
Installing Linux on second hard drive in laptop

I hope to get a laptop with two hard drives.
I like to know if UBUNTU comes with installer that would easily let me install UBUNTU on
the second hard drive.  And also let me select which OS to boot on startup.

Win 7-64-bits will be on the first hard drive, Linux will be on 2nd / other hard drive.
I prefer NOT to use Wubi to install linux  in Win 7's primary partition because should I
reinstall Win7 with recovery disks, it will wipe out Linux.

Has anyone done this before?

Still new to Linux and UBUNTU.

Thanks

---

### Post by tommcd on 2010-12-13
You can easily do this. Just install Ubuntu to the second hard drive. Then allow Ubuntu to install grub to the Master Boot Record (MBR) of your first (boot) hard drive. This way you will be able to easily select whether you want to boot Windows or Ubuntu.

Just out of curiosity, which laptop is this that has 2 hard drives?

---

### Post by PRC09 on 2010-12-13
As an alternate to the above suggestion you could also remove/disconnect the windows drive and install Ubuntu as a stand-alone install.Then re-connect your windows drive BUT select the Ubuntu drive as first boot device and then update grub.You will then have a dual boot without messing with your windows mbr.The advantage of this is if you wish to change versions or distros it doesnt mess with the windows mbr.....

---

### Post by hpng on 2010-12-14
[tommcd]("http://ubuntuforums.org/member.php?u=34402"):

HP have laptops that can handle 2 hard drives.
Look at Dv7 series with custom component select options.

Thanks.

---

### Post by Quackers on 2010-12-14
A few Vaio's too!

---

### Post by hpng on 2010-12-14
> **PRC09 said:**
> As an alternate to the above suggestion you could also remove/disconnect the windows drive and install Ubuntu as a stand-alone install.Then re-connect your windows drive BUT select the Ubuntu drive as first boot device and then update grub.You will then have a dual boot without messing with your windows mbr.The advantage of this is if you wish to change versions or distros it doesnt mess with the windows mbr.....


I have not taken a new HP laptop apart before.
I am also not sure how to set 2 1/2" SATA drives as master and slaves.

I would assume SATA works just like USB, but how do you set master and slave order?

i assume when i disconnect the disk drive that has WIndows 7, AND
I have to set the other SATA drive to become a master by setting some kind
 of jumper like the old IDE drives, right?.

It could be messy taking apart a laptop to do all that, right? 
  
I like to know if you have done this personally?

---

### Post by Quackers on 2010-12-14
That's a bit fiddly and not really recommended for a laptop. There are ways around it.

---

### Post by PRC09 on 2010-12-14
I was assuming you would be adding the drive yourself.Tha ones that I have worked on have had both drives located side by side under a panel on the bottom of the laptop so sorry on that.As for master and slave there is no jumper that I have seen but just the setting in bios for boot order.I guess you could turn off the drive(windows) in the bios as well if needed instead of remove or disconnect.

---

### Post by oldfred on 2010-12-14
With dual drives you do want to be sure to install grub to the second drives MBR. Check that you can boot second drive in BIOS.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by tommcd on 2010-12-14
> **hpng said:**
> 
I am also not sure how to set 2 1/2" SATA drives as master and slaves.
I would assume SATA works just like USB, but how do you set master and slave order?

There is no master / slave jumpers on SATA drives like there are with IDE drives.
If you want to try PRC09's suggestion, then as an alternative to opening up the laptop, you could set the second hard drive to boot before the Windows drive in the BIOS. Then boot from the live CD and install Ubuntu to that hard drive. It will pick up your Windows install and allow you to boot Ubuntu or Windows.

EDIT: I did not see tyhe last 2 posts above this before I posted. Sorry if this info is redundant.

---

### Post by hpng on 2010-12-15
> **PRC09 said:**
> I was assuming you would be adding the drive yourself.Tha ones that I have worked on have had both drives located side by side under a panel on the bottom of the laptop so sorry on that.As for master and slave there is no jumper that I have seen but just the setting in bios for boot order.I guess you could turn off the drive(windows) in the bios as well if needed instead of remove or disconnect.

Yes, I willbe installing the hard drive myself....
OK, I open up a new dv7-4173us HP laptop.
I saw the first hard drive, and there a slot for a 2nd hard drive.
I remove the first hard drive and took a look at tis connector.
Then I look at the manual for the 2nd connector location.
I found the 2nd hard drive connector on he mother board.
Problem is that the connector on the motherboard for the 2nd harddrive
is not the same as the first hard drive......

I am not sure if the 2nd connector for the 2nd hard drive is a SATA connector.
Cannot get much help from HP.

If you or anyone else who has used a hp laptop ( typically one with 17" screen;
they will have slot for 2nd hard drive), let me know if the 2nd hard drive connector is a standard SATA connector.

By the way, getting tech support to see if I can purchase a second hard drive from HP is like pulling teeth.  Just very poor customer service.... 

Thanks.

---

### Post by oldfred on 2010-12-15
Which of these does it look like:

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

---

### Post by PRC09 on 2010-12-16
According to HP you will need a kit containing rails,cable adapter and such to add the extra hard drive.See pg 47,48,50 of the maintenance manual at the following link.

[http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&site=null&docname=c02499438&product=4308509&key=null&](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&site=null&docname=c02499438&product=4308509&key=null&)

I also found this on an HP service forum.

[http://h30434.www3.hp.com/t5/Hardware/adding-2nd-hdd-on-dv7/td-p/317595](http://h30434.www3.hp.com/t5/Hardware/adding-2nd-hdd-on-dv7/td-p/317595)

I also found the part number thru HP partsurfer(see below) but I could not order it as was quoted in the above post, there was an error pop up when I tried to so you may have better luck from your country (I am in Canada).Have you considered an external drive instead..

[http://partsurfer.hp.com/Search.aspx?SearchText=605415-001](http://partsurfer.hp.com/Search.aspx?SearchText=605415-001)

Hope this helps....

---

