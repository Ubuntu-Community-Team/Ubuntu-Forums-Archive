---
title: "Grub:  Playing with Fire"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by tshanno on 2008-05-26
I have a laptop which I use mainly for Windows Vista.  Every other computer I have runs Ubuntu.  Since I also use the laptop with Vista for travel, I wanted to have the option of installing linux for use in such situations with as little disturbance to the existing system as possible.  My solution to this was to buy an external HD and install 8.04 on it.  This works very well in that Windows and the existing HD were barely disturbed (except for the MBR which has grub).

However there is something that bothers me a great deal.  The system will no longer boot without the external HD hooked up to the USB port.  Instead, Grub enters stage 1.5 and throws error #21 ("Selected disk does not exist"). I have had two external HDs fail on me in the past and the idea of not being able to boot if this one does leaves me cold.  It would also be nice to be able to access Windows without hauling the external drive around.

Bottom line, I'd like to fix the system so that it will boot to Windows if the external drive isn't present.  I'd like to do it without totally screwing the whole computer up, something which I believe is quite easy to do when messing with grub.  Any ideas would be very helpful.

Thanks,
Tom S.

---

### Post by louieb on 2008-05-26
Replace GRUB in the MBR of the laptops hard drive.  Lots of  ways to do it.
[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Install GRUB to the MBR of external drive. Can be done from the Live CD or the [Super Grub Disk  ]("http://forjamari.linex.org/projects/supergrub/")is probably the easiest. 
You probably have some key combination that will make your laptop boot from the external.

---

### Post by Herman on 2008-05-26
Another way of doing things is to [make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") in your laptop.  
There is nothing to be feared about GRUB, it is the most useful boot loader in the world. It's easy to learn how to use GRUB, and there are all kinds of great tricks you can do with it.

Regards, Herman :)

---

### Post by tshanno on 2008-05-26
> **louieb said:**
> Replace GRUB in the MBR of the laptops hard drive.  Lots of  ways to do it.
[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Install GRUB to the MBR of external drive. Can be done from the Live CD or the [Super Grub Disk  ]("http://forjamari.linex.org/projects/supergrub/")is probably the easiest. 
You probably have some key combination that will make your laptop boot from the external.

Thanks to both you and Herman for replying.  Here's what ended up happening.

Super Grub is, indeed, "super".  Great program.  Removing Grub from the boot parition of the internal HD was easy and Windows booted perfectly fine once that was done.

I tried to install grub to the MBR of the external drive but, oddly, this didn't work.  The error message I got was to the effect that the external parition couldn't be mounted.

The next thing I tried was to simply make the linux parition active.  The OS didn't boot (no error messages, just a blank screen).

I do, however, consider this to be progress.  I have decided to boot linux by simply using Super Grub.  Should work perfectly fine for me in that I can easily keep multiple copied around.  Unless the CD drive completely fails (I've never had one do so) I should be pretty safe.  Windows will always boot with or without the disc and my other linux machines should be perfectly fine for recovering data from the external HD should that be necessary.

I think I'm reasonably safe here.  Thanks much.

Tom S.

---

### Post by meierfra. on 2008-05-26
Does the grub menu appear when you boot from the external drive? If yes, this will fix your problem:


Boot into Ubuntu with Super Grub. Then in a terminal


```
gksudo gedit /boot/grub/menu.lst
```


Look for the line  

#groot (hd1,3) 

(of course your numbers could be different.)

Change the first number to "0" but do NOT change the second number:

#groot (hd0,3)


You also need to edit your Visa title. I'm assuming you have only two hard drives

Change "root (hd0,2)"  to  "root (hd1,2)" (so change the first number to 1, and  do not change to second one.)


Save the file. Then

```
sudo update-grub
``` 

and you should be all set

---

### Post by tshanno on 2008-05-26
> **meierfra. said:**
> Does the grub menu appear when you boot from the external drive? If yes, this will fix your problem:


Boot into Ubuntu with Super Grub. Then in a terminal


```
gksudo gedit /boot/grub/menu.lst
```


Look for the line  

#groot (hd1,3) 

(of course your numbers could be different.)

Change the first number to "0" but do NOT change the second number:

#groot (hd0,3)


You also need to edit your Visa title. I'm assuming you have only two hard drives

Change "root (hd0,2)"  to  "root (hd1,2)" (so change the first number to 1, and  do not change to second one.)


Save the file. Then

```
sudo update-grub
``` 

and you should be all set

This worked like a charm.  It boots perfectly from the external HD.  Thanks loads.

Tom S.

---

### Post by louieb on 2008-05-26
> **Herman said:**
> Another way of doing things is to [make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") in your laptop.  
There is nothing to be feared about GRUB, it is the most useful boot loader in the world. It's easy to learn how to use GRUB, and there are all kinds of great tricks you can do with it.Regards, Herman :)

Thanks for the website. I refer to it all the time. I've put a dedicated on both my PCs. Makes playing around with Linux easier.

---

### Post by meierfra. on 2008-05-26
> Makes playing around with Linux easier.
I thought so too, but then I kept trying out more and more distros and used up my 15 partitions. So the dedicated grub had to go.:)

---

### Post by adrian15 on 2008-05-27
> **tshanno said:**
> The system will no longer boot without the external HD hooked up to the USB port.  Instead, Grub enters stage 1.5 and throws error #21 ("Selected disk does not exist"). 

I'd like to fix the system so that it will boot to Windows if the external drive isn't present.  

Any ideas would be very helpful.

Thanks,
Tom S.

If you do not want to [travel by plane](http://ubuntuforums.org/showthread.php?t=715864#6) it's better to read this howto:
[I have Linux installed on a second hard disk. When I remove it I cannot boot my Windows](http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDisk)(Check the  Non Hidden Linux method). 

adrian15

---

