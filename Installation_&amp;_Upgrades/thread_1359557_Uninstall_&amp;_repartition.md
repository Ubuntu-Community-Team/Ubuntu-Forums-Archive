---
title: "Uninstall &amp; repartition"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by topdog2009 on 2009-12-19
Having partitioned my hard drive and installed Ubuntu. I find that, because of the problems that I am having with getting on line either using wifi or a Bell USB stick that Ubuntu is not for me. Pity.

I now wish to uninstall Ubuntu and repartition my drive to where it was before I installed Ubuntu. I installed from a CD and therefore I think I can use WUBI to uninstall Ubuntu. Can I also use that to repartition to my former self and, if not can I use something like Partition Majic?

---

### Post by raymondh on 2009-12-19
> **topdog2009 said:**
> Having partitioned my hard drive and installed Ubuntu. I find that, because of the problems that I am having with getting on line either using wifi or a Bell USB stick that Ubuntu is not for me. Pity.

I now wish to uninstall Ubuntu and repartition my drive to where it was before I installed Ubuntu. I installed from a CD and therefore I think I can use WUBI to uninstall Ubuntu. Can I also use that to repartition to my former self and, if not can I use something like Partition Majic?

If this (ubuntu) was originally installed thru wubi as you ***may have*** hinted above, you can use windows' add/remove utility in control panel to remove ubuntu.  Afterwards, you will need to manually edit the boot.ini file in windows to remove the WUBI-related line.  Be careful about this part and **ONLY THE WUBI-RELATED LINE** or you risk losing your windows boot.

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

If Ubuntu was installed in its' own partition (as you also hinted above), you will need a windows install disc (not the recovery CD given by the manufacturer)

-   Boot into windows and access its' disk management utility.
-  Use that to erase the Ubuntu partitions.  Remember, it will involve Ubuntu, SWAP and*** possibly*** an extended partition that housed those 2
-  After, resize/enlarge the windows partition
-  Exit and boot into the windows install disc. Choose the language
If XP, select R and at the prompt, type (one at a time)

fixboot
fixmbr
(and if success) exit

If Vista/win7, select REPAIR COMPUTER > COMMAND PROMPT and type

bootrec.exe/fixmbr

Exit .... and restart.  Let windows run a checkdisk.

EDIT : this is assuming you have windows installed :).  Otherwise, post back and we can also try apple

Regards,

---

### Post by topdog2009 on 2009-12-20
Thanks for the prompt reply. Being a newbie to the world of computers, this seems like a potentially dangerous operation. Must say I am not really impressed with Ubuntu for making it easy to install and difficult to remove.

Using Vista, where would I find the boot.ini file?

---

### Post by darkod on 2009-12-20
> **topdog2009 said:**
> Thanks for the prompt reply. Being a newbie to the world of computers, this seems like a potentially dangerous operation. Must say I am not really impressed with Ubuntu for making it easy to install and difficult to remove.

Using Vista, where would I find the boot.ini file?

It isn't difficult to remove at all. But if you want to install an OS yourself than you do need to learn few basic things and specify what kind of setup you have. Then we can give you more exact recommendation but only if we know more (because we can't take a look at your PC).

So, for a start, did you install ubuntu from within windows (with windows already running) or you booted your PC with the ubuntu cd and selected the Install Ubuntu option? If you installed from inside windows, just go in add/remove programs and uninstall ubuntu just like any other windows program. "Problem" solved.

If you installed it differently, let us know, there are other instructions (not to scare you here writing all at once).

---

### Post by topdog2009 on 2009-12-20
OK - problem - the Ubuntu directory is not there!! 

To install Ubuntu I used the CD supplied by Canonical. Guess I assumed it used wubi.

What now?

:confused:

---

### Post by phillw on 2009-12-20
> **topdog2009 said:**
> Thanks for the prompt reply. Being a newbie to the world of computers, this seems like a potentially dangerous operation. Must say I am not really impressed with Ubuntu for making it easy to install and difficult to remove.

Using Vista, where would I find the boot.ini file?

The removing is easy.

The above answer was referring to the torutous loops you have to go though to put Win 100% on, without loosing your data.

If you are true dual boot and NOT WUBI then you can just set windows to be the boot system. That is, handing over your MBR (Master Boot Record) over to Win from Grub, which is the Ubuntu boot system.

That can be done quickly via this method --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once that is done - you can safely remove all traces of the Ubuntu System.

Phill.

---

### Post by phillw on 2009-12-20
> **topdog2009 said:**
> OK - problem - the Ubuntu directory is not there!! 

To install Ubuntu I used the CD supplied by Canonical. Guess I assumed it used wubi.

What now?

:confused:


See post #4 !!!

Phill.

---

### Post by darkod on 2009-12-20
> **topdog2009 said:**
> OK - problem - the Ubuntu directory is not there!! 

To install Ubuntu I used the CD supplied by Canonical. Guess I assumed it used wubi.

What now?

:confused:

You mean there is no ubuntu entry in installed programs list? Be careful, directory means something else.

---

### Post by topdog2009 on 2009-12-20
Considering I installed Ubuntu a couple of months ago, I do not remember how it was installed. Because the Ubuntu directory is not in the Windows directory, I assume I booted direct from the Ubuntu CD.

---

### Post by topdog2009 on 2009-12-20
In response to # 8. I mean there is no directory but neither is the program listed in the program list.

---

### Post by darkod on 2009-12-20
> **topdog2009 said:**
> In response to # 8. I mean there is no directory but neither is the program listed in the program list.

OK. According to what you are saying, you do have a full ubuntu install on separate partitions with your vista.
In that case, if you want to get rid of ubuntu, you have to restore windows bootloader instead of grub on your hdd MBR. Instructions how to do that for vista are here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You will need a vista install dvd for that. If you do not have a vista dvd you can download image of vista repair cd. Just burn that image on a cd and it will allow you to repair the vista bootloader.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Once you have the bootloader restored, your computer should just boot straight into vista. You will not get option for ubuntu any more. When in vista, just delete the ubuntu partitions and create a new ntfs partition in that space which you can use with vista.

---

### Post by topdog2009 on 2009-12-20
Thanks.

Despite the fact that I am disappointed with Ubuntu - or at least the ability to access the web using either wifi or a Bell USB stick, I really do appreciate all of the assistance that Ubuntu users having given to me over the past two months.

Brian

---

### Post by darkod on 2009-12-20
> **topdog2009 said:**
> Thanks.

Despite the fact that I am disappointed with Ubuntu - or at least the ability to access the web using either wifi or a Bell USB stick, I really do appreciate all of the assistance that Ubuntu users having given to me over the past two months.

Brian

Unfortunately, instead of hardware manufacturers creating their own drivers for linux like they do for windows, usually it's up to the linux developers to do that. Sometimes the wi-fi support is not the greatest but I think they are doing their best.
If you wanted to spend some time on it, I think you could even get it working. Few chipset manufacturers actually developed linux drivers and it doesn't matter what brand is on the device, it matters what chipset is inside it. :)
That's how I got my wi-fi working, with driver from the chipset manufacturer website, not the device manufacturer.

---

### Post by topdog2009 on 2009-12-20
Before I take the plunge and get rid of Ubuntu, I might try that however, it will be a protracted exercise as my nearest wifi source is about 30 minutes drive from me and I have to make changes whilst online (using windows) and then go to wifi to see if it worked and then back again and again and again.

Having said that, I am willing to try because I do like using Ubuntu. I would even upgrade to the latest version to see if that helped but my current version (9.04) has not been upgraded with the latest updates - because of my connection problems.

So, if you are willing to continue to assist - How do I find out what chipset I have (told you I am a beginner)

---

### Post by darkod on 2009-12-20
Open terminal (in Application-Accessories) and for usb adapter execute:
sudo lsusb

That will list all your usb devices. Look around which one looks like your adapter. Mine had like
148F:3070 Ralink Tech
and that meant Ralink RT3070 chipset.

If it's a pci or mini-pci (laptop) device, use the command:
sudo lspci

That list is even bigger than for usb so you have to look carefully.

Once you find out the chipset (or what's looking like it), google is your friend. I bet someone already made it working under ubuntu, you just have to find the blog/tutorial/thread...

---

### Post by topdog2009 on 2009-12-20
Am i correct in assuming you are referring to the Bell USB stick and not to wifi?

---

### Post by darkod on 2009-12-20
> **topdog2009 said:**
> Am i correct in assuming you are referring to the Bell USB stick and not to wifi?

Well, what ever you want to get working with ubuntu. If by wifi you mean internal adapter in a laptop, you probably need to use the lspci command. For Bell usb stick, lsusb (I have no idea what Bell usb stick is :) ).

---

### Post by topdog2009 on 2009-12-20
Not knowing the linux language, I assume ls stands for List Services or something similar. Ideally I would like to get both wifi and the Bell USB working.

The Bell USB stick is a device used to connect to the internet by high speed (at least faster than dial up) using the mobile phone network.

I will give both of your suggestions a try but I have to sign off now.

Thanks for your assistance.

---

