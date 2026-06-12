---
title: "Installation issue"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Supermatt01 on 2012-10-27
[COLOR=black][FONT=Tahoma]So I'm trying to install Ubuntu 12.10 on an Acer Aspire 4741. It' has 2 gb of ram and an i5 processor at 2.4 GHz. I'm running windows 7 home premium 64bit, I want to install the 32 bit Ubuntu; and I tried to install it to do dual boot but it won’t install properly I keep getting this message: AttributeError: 'NoneType' object has no attribute 'get_info' and I can't boot it up. It gives me an error log but I have no clue how to make that help me I just started doing Linux and I'm so lost, So then I thought ok I will make a drive partition special for Ubuntu so I did I made a 20 gb partition and tried again to install. I get the same message with the same log.[/FONT][/COLOR]
 
Any help out there in Ubuntu land?

---

### Post by roger_1960 on 2012-10-27
Hi

You need a partition with ext3 or ext4 formatting for ubuntu.  Is this what you did? If not, suggest you reformat your 20Gb partition and try installing to it.

---

### Post by NikTh on 2012-10-27
Hi , 
I assume you try to install Ubuntu from within Windows . Am I right ? This called wubi installer. 

I cannot help you with wubi installer , almost never used it and I considered as a minus of Ubuntu. (**but this is only my opinion**)

You can try to install Ubuntu "Alongside Windows" with this way

1) Download the .iso image of Ubuntu from here:  [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

2) Download the program Unetbootin from here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You will need a USB-Flash at least 2GB and with Unetbootin and the iso image of Ubuntu you will create a bootable Live-Usb of Ubuntu. (Unetbootin will make the Usb-Flash bootable automatically). 

Then boot from the USb (you may have to change the BIOS boot order) and install Ubuntu "Alongside Windows" , you will see this option at the installer window. **If you don't see it** do not proceed , just post back here. 

This is my suggestion. 

Thank you and good luck.

---

### Post by Bucky Ball on 2012-10-27
*Thread moved to** Installation & Upgrades***

---

### Post by newb85 on 2012-10-27
At this point, I recommend using 12.04, not 12.10.  12.10 has been released less than two weeks, and there are still some bugs to work out.

Also, I suggest you use 64-bit, not 32-bit.  If 64-bit Windows came on the machine, 64-bit Ubuntu will give you better performance than 32-bit.

Third, I suggest that you not use the Windows (Wubi) installer.  If you do, however, Ubuntu won't use its own partition.

---

### Post by jroa on 2012-10-27
Will the computer boot from a live CD/USB?  If not, then you might have a bad .iso or a bad burn.

---

### Post by Supermatt01 on 2012-10-27
Thank you all for the great help I will give all the listings a try from the top down and report back if any solve my issue. I'm thinking the 4ext may be my problem as I did not format in that format :-)

---

### Post by Bucky Ball on 2012-10-27
EXT4 you mean? That is not a problem. That is the only filesystem Ubuntu will install to. It won't install on NTFS or FAT32.

As mentioned, install 64bit to a spare partition, 12.04 LTS with support until April 2017 and stabler than the fledgling 12.10, forget Wubi as can be problematic anyway and only really intended to 'Try before you install'. Better user experience from full install. Good luck. ;)

---

### Post by Supermatt01 on 2012-10-28
[COLOR=black][FONT=Tahoma]Yes ext4 I meant, 4ext is Android. :-D anyway I tried out the reformat and that having been done my system can't read the partition so I can't install to it, and my bandwidth is really bad so I'm stuck with 12.10 for the time being that is why the 32 bit, I live in Indonesia and the modem and its UI is set up for windows 32 bit or Linux 32bit so I have to downgrade somewhere, so I want to try and make it work. How do I install to a drive partition that can't be read by windows? Ok so I'm downloading the 12.04 version too. I will repost if that helps anything I will be able to try it out in about a day(really bad bandwidth) :-) thanks for the help.[/FONT][/COLOR]
 
P.S. still can't find how to install to a non read partition.

---

### Post by newb85 on 2012-10-28
> **Supermatt01 said:**
> How do I install to a drive partition that can't be read by windows? 
...
P.S. still can't find how to install to a non read partition.

For that very reason, it is *impossible* to set your system up dual-boot from within Windows.  You *must* create a bootable medium (either a CD or USB).  Then, while running your machine from that bootable medium (i.e., Windows is still installed on your machine but not running), you install Ubuntu.


If choose to use a USB, follow NikTh's instructions in Post #3.

If you choose to use a CD, follow the directions at [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto") to create the CD.   Then boot from the CD (again, you may have to change your BIOS boot order) and install Ubuntu "Alongside Windows"...

---

### Post by Supermatt01 on 2012-10-28
Ok I'm looking into the method from number three post and I'm having a bugger of a time trying to us a usb so maybe the cd is the way to go but I only have 700 mb cds and the program takes almost 750mb how do I get 750 mb onto a 700 mb disc?:confused: I tried it on a dvd but I get an error message that says this media not supported on this disc type.

---

### Post by NikTh on 2012-10-28
Hi ,
the Desktop CD iso is 695MB. It fits in a CD. 
Ubuntu 12.04 LTS Desktop CD 
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

---

### Post by newb85 on 2012-10-28
> **Supermatt01 said:**
> Ok I'm looking into the method from number three post and I'm having a bugger of a time trying to us a usb so maybe the cd is the way to go but I only have 700 mb cds and the program takes almost 750mb how do I get 750 mb onto a 700 mb disc?:confused: I tried it on a dvd but I get an error message that says this media not supported on this disc type.

All my Ubuntu disks are 700MB CDs.  In fact, I don't think I've ever seen a CD that was more than 700MB.

I'm not sure what program you're referring to when you say it takes almost 750MB.  If you mean the .iso is more than 700, you're correct.  You're not supposed to put the .iso on the CD.  You're supposed to use the .iso to create the CD.  For Windows 7, right-click the .iso file and hit "Burn disc image".  (This from the source I linked in my last post.  :|)

---

### Post by Bucky Ball on 2012-10-28
> **Supermatt01 said:**
> [COLOR=black][FONT=Tahoma]How do I install to a drive partition that can't be read by windows?[/FONT][/COLOR]

NO EXT* partition can be read by Win natively so this is really not your issue and not a concern.

Just leave free space where you want to install Ubuntu, as I have been saying, and choose 'Something Else' when you get to partitioning in the install. Set up partitions in the free space.

---

### Post by Supermatt01 on 2012-10-29
You guys are GREAT :-D I got the disc to burn the second time round. I still don't know why the error the first time but it now will boot! :-D I as well have never seen a cd with more than 700 mb :-) the dvd did the trick though I'm still not sure why I had to try it over. I'm now able to boot the version 12.10 I will also try the 12.04 as the download is finished. I tried to install the modem to Ubuntu and found that the plug and play UI does not pop up. is this normal for Ubuntu to not use plug and play options?

---

### Post by newb85 on 2012-10-29
> **Supermatt01 said:**
> I'm now able to boot the version 12.10 I will also try the 12.04 as the download is finished.
Sorry if my last post was misleading.  12.10 is indeed too large to fit on a 700MB CD.  It is the first release of Ubuntu that is too large to fit on a 700MB CD.  12.04.1 (which is undoubtedly what you're downloading) is a 732.2MB .iso file.  (I think NikTh's 695MB may have been 12.04.0.)  However, you *can* use it to burn a 700MB CD.

> **Supermatt01 said:**
> I tried to install the modem to Ubuntu and found that the plug and play UI does not pop up. is this normal for Ubuntu to not use plug and play options?

Storage devices are usually plug-and-play.  Other peripherals, in my experience, are sometimes not.  Best-case scenario--Ubuntu recognized your modem and has the drivers for it, and you just have to set it up by going to "Edit Connections..." in the Network menu in the Systray.  Worst-case scenario--drivers for that particular modem are not available for Linux, and you're basically stuck.  Somewhere in between is the possibility that the drivers are available for Linux but not in the default repositories, and you'll have to do some research and work to install them.

If you have further questions on your modem, go ahead and start a new thread.  ;)

---

### Post by Supermatt01 on 2012-10-29
Nope no more about the modem it works like a dream :-) but the UI that comes with the modem does not install (no loss there really other than calls and text function) Thank you all for your great help I'm up and running now :-D:guitar:

---

### Post by Supermatt01 on 2012-10-30
Ok well up and running on the CD (I'm typing this from Ubuntu :-) ) I installed it along side windows though, it wrote its self into the space provided like it should but I can't find how to boot into Ubuntu. It will only reboot into windows 7 every time. I'm not sure what step I missed.:confused:

---

### Post by newb85 on 2012-10-30
This should help:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Supermatt01 on 2012-10-30
Ok I got this installing. Will it stay installed though? Cause I'm booting from the disc. Last time I installed things to this on the disc boot up it didn't stay installed.

---

### Post by Bucky Ball on 2012-10-30
Try hitting shift after the BIOS screen That should bring up a list with Ubuntu and Windows on it. Boot Repair? Not at that stage I wouldn't have thought. Seems to be booting fine and you're not sure if you can boot into Ubuntu because doesn't sound like your getting the menu list at boot to try.

---

### Post by YannBuntu on 2012-10-30
> **Supermatt01 said:**
> Ok I got this installing. Will it stay installed though? Cause I'm booting from the disc. Last time I installed things to this on the disc boot up it didn't stay installed.

No, it won't stay installed, but that's not a problem as Boot-Repair is mainly useful when used from a liveCD (or liveUSB).
And if you need it in your installed Ubuntu, you can install it there too.

---

