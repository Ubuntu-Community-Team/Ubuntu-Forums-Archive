---
title: "USB install, black screen"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by con.cept.me on 2013-02-07
I made a bootable usb.. and i see the 3 options, Run live | Install | Check disk
But all three options just give me a black screen.

Does anybody know how to fix this :(
Computer i try to install it on is.
                                                                                     **                                                 [Asus Zenbook UX52VS-CN021H]("http://www.laptopshop.nl/product/281202/category-180887-asus-laptops/asus-zenbook-ux52vs-cn021h.html")                                             **


[LIST]
[*]Intel Core i7 3517U
[*]500 GB HDD + 24 GB Cache-SSD
[*]NVIDIA GeForce GT 645M
[/LIST]

---

### Post by iamkuriouspurpleoranj on 2013-02-07
How did you make the USB?

---

### Post by con.cept.me on 2013-02-07
> **iamkuriouspurpleoranj said:**
> How did you make the USB?

with this app as described on the ubuntu wiki: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by Mark Phelps on 2013-02-07
You can do the same by going to pendrivelinux.com and following their directions.

---

### Post by con.cept.me on 2013-02-07
> **Mark Phelps said:**
> You can do the same by going to pendrivelinux.com and following their directions.

How is this different? It will be the same bootable usb correct ? The problem is I can boot from the usb, but after choosing an option i just get a black screen :(

---

### Post by MAFoElffen on 2013-02-07
Okay now--

When it first boots, before the menu you described, it goes to an aubergune colored (somewhat purplish black) with a keyboard/human icon centered on the bottom of that panel > press any key > the keybaord language panel will appear > press <Enter>...

Now you will be at the Advanced Bootup Menu (in low quality VGA Graphics)... Press <F6> for Other Options > <Arrow-Down> until you highlight the nomodeset option > Press <Enter>

Select the menu option you want...

*** So the problem is that you have a high-end NVidia Graphics Card, and you have to tell dkms not to set graphics modes. That is remedied on an install by using a specifics graphics driver for your video.

If you have skills with creating ISO's. You could remedy this with some work by creating a custom image either using that boot option as a default or by installing that video driver to the image. But then again, it would no longer be generic. I've done this for special users in the past...

Re: See the top of post #3 in my Graphics Resolution sticky in my sig line for more detailed instructions and pictures of the screens to lead you through it.

---

### Post by con.cept.me on 2013-02-08
The live linux program creates a black boot screen... I cannot see the keyboard button :( Is there a way to get the usb boot exactly as the cd ?

---

### Post by oldfred on 2013-02-08
Are you getting an UEFI boot menu?

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

    
Then I think the e works to get to a grub boot stanza and replace quiet splash with nomodeset.

But Intel SRT adds even more complications:
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

    
       Details in post #10 on an install that worked with SRT
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)


       
 Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by sandro4 on 2014-02-06
> **con.cept.me said:**
> I made a bootable usb.. and i see the 3 options, Run live | Install | Check disk
But all three options just give me a black screen.
[LIST]
[/LIST]


I had the same issue and just in case some other newbies like me come to this thread: Before following the other hints, try increasing your screen brightness when you think it's a "black screen" after choosing one of the three options! 
I spent a whole evening following the instructions mentioned in this thread and then did some more research and found the hint with the screen brightness, and it has been working all the time, I just didn't see it ;)
So be sure to try that first.

Also now when starting my laptop, this black-screen-"problem" still exists, although now it's not really a problem anymore, you just have to know about it ;)

---

