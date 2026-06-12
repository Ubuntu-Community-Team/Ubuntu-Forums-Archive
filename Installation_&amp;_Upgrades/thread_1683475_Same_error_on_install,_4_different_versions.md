---
title: "Same error on install, 4 different versions"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by Szat on 2011-02-07
Hello,
 I've been having a lot of trouble installing Ubuntu on my [new netbook.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220850") I am 10+ hours on this issue. I have tried Ubuntu 10.10 desktop, 10.10 netbook, 10.10 Super OS, and Ubuntu desktop 10.04.1. I have used unetbootin and universal USB installer to make the bootable usb drive; and yes, I have read a lot of documentation and forum posts on this.

 All versions I have tried match the md5 check sum after download and the USB drive I am using has no defects. The error I am receiving is "Sorry, the program 'parted_server' closed unexpectedly. The installer freezes after the keyboard option (10.04) and the Preparing to Install Ubuntu option (10.10). Note: I only get this error after I quit the install and try to install it from the Live desktop it displays.

 I know it is not my netbook, because it does not work on my desktop either. Can someone please help me?  The hdd in my netbook is 100% free thanks to Parted Magic. This is driving me nuts and I haven't gotten to enjoy my new netbook yet. :( 

 As always, thanks for the help!

---

### Post by PRC09 on 2011-02-07
Some people have had similar errors and had to remove anything they had plugged into the machine such as SD cards extra usb drives or devices and such.....Maybe...

---

### Post by Quackers on 2011-02-07
Has the hard drive ever been used as part of a raid array?
Was it formatted using a Mac?

---

### Post by Szat on 2011-02-07
> **PRC09 said:**
> Some people have had similar errors and had to remove anything they had plugged into the machine such as SD cards extra usb drives or devices and such.....Maybe...

 I have read that too, nothing else is plugged into my netbook. I am creating the USB on my desktop though. Which machine are you referring to?


> **Quackers said:**
> Has the hard drive ever been used as part of a raid array?
Was it formatted using a Mac?

No the hard drives have never been used as an array and I am using Windows 7 Business x64 on my desktop.
The USB drive I am using is formatted in FAT32. Is this correct for creating a Ubuntu bootable USB?

---

### Post by Quackers on 2011-02-07
When booting from the live usb, when the first purple screen appears (with the  little man graphic at the bottom) press any key. Then choose language and then select the option to check the cd for errors. It doesn't matter that you are not using a cd. See if any errors are found - one error is probably too many.

---

### Post by PRC09 on 2011-02-07
If its happening on both machines,maybe try a different usb(flash)drive,I have a couple that just dont seem to work properly when using as a boot drive but work fine as storage...

---

### Post by Quackers on 2011-02-07
> **PRC09 said:**
> If its happening on both machines,maybe try a different usb(flash)drive,I have a couple that just dont seem to work properly when using as a boot drive but work fine as storage...

Somethig I have just learned today :-)
Sometimes (I don't know why) usb flash drives can be recognised in the bios as usb HDD's. One I bought today is like that. When I set usb HDD as first boot device it works just fine :-)

---

### Post by Szat on 2011-02-07
> **PRC09 said:**
> If its happening on both machines,maybe try a different usb(flash)drive,I have a couple that just dont seem to work properly when using as a boot drive but work fine as storage...

I have tried another USB drive, same issue.

> **Quackers said:**
> When booting from the live usb, when the first purple screen appears (with the  little man graphic at the bottom) press any key. Then choose language and then select the option to check the cd for errors. It doesn't matter that you are not using a cd. See if any errors are found - one error is probably too many.

I have checked the USB drive for errors, none found.

> **Quackers said:**
> Somethig I have just learned today :-)
Sometimes (I don't know why) usb flash drives can be recognised in the bios as usb HDD's. One I bought today is like that. When I set usb HDD as first boot device it works just fine :-)

BIOS is recognizing USB as USB: Patriot Memory in the HDD section of my BIOS. HDD: my HDD is also there. USB is set to the first boot device. Still having problem!

---

### Post by PRC09 on 2011-02-07
Strange....The only thing that would logically be next is what version of the software you are using to create the bootable usb. Dont know if the creater in Ubuntu versions is the same in all that you have tried or not and I have never used Unetbootin so....

---

### Post by Quackers on 2011-02-07
Quote
I have checked the USB drive for errors, none found.
How did you do that please? You need to check that the iso has been written to the usb correctly (without errors). You would do that as I described in post #5

---

### Post by Szat on 2011-02-07
(screwed up this post, sorry)

---

### Post by Szat on 2011-02-07
> **Quackers said:**
> Quote
I have checked the USB drive for errors, none found.
How did you do that please? You need to check that the iso has been written to the usb correctly (without errors). You would do that as I described in post #5

 When I boot into the USB, the Unetbootin options menu comes up and one of the options is to check for disk defects. I am currently trying to install SuperOS and I didn't see the little man at start up. I know what you mean by little man though. When I log out I see the little man, but there is no option for what you said in post 5. 

How do I check if the iso has been written to the usb correctly?

---

### Post by Quackers on 2011-02-07
By pressing any key at the little man screen :-)  Sadly it appears you are not getting that. I haven't used  unetbootin successfully myself, so don't know whether what you have tried is the same thing as what I am proposing.

---

### Post by Szat on 2011-02-07
> **Quackers said:**
> By pressing any key at the little man screen :-)  Sadly it appears you are not getting that. I haven't used  unetbootin successfully myself, so don't know whether what you have tried is the same thing as what I am proposing.

 I can use Universal USB installer if that helps, or whatever you're using.

---

### Post by Quackers on 2011-02-07
I used Startup Disk Creator, which is a program installed within Ubuntu. That's no good unless you have a working version of Ubuntu, I'm afraid (and it does have a problem making live usb's from within 10.10. It only seems to work properly from within 10.04 at the moment). So no good for you I'm afraid.
If you are trying to do it from within Windows, Universal USB may be a good option.

---

### Post by oldfred on 2011-02-07
With the Atom processor and the nVidia chip you are a little different than most. 

Have you checked here?
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/)

It has info on several Asus versions.

---

### Post by Szat on 2011-02-07
> **oldfred said:**
> With the Atom processor and the nVidia chip you are a little different than most. 

Have you checked here?
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/)

It has info on several Asus versions.


Thanks I have checked that out before, but I need Ubuntu installed before I can start using the command line.

---

### Post by presence1960 on 2011-02-07
> **Szat said:**
>  Note: **_I only get this error after I quit the install_** and try to install it from the Live desktop it displays.



Why are you quitting the install? Let it run.

---

### Post by Szat on 2011-02-07
> **presence1960 said:**
> Why are you quitting the install? Let it run.

I've let it run for over 2 hours at this point. I figured that was long enough for one step.

---

### Post by Quackers on 2011-02-07
What does gparted show, from the live cd/usb desktop?

---

### Post by presence1960 on 2011-02-07
> **Szat said:**
> I've let it run for over 2 hours at this point. I figured that was long enough for one step.

Well from your first post I would say it is the USB drive that is the problem because you said it does not work on your desktop either.

---

### Post by Szat on 2011-02-08
I have used another USB drive as well. This is crazy, I've never had trouble installing Ubuntu before.

---

### Post by Szat on 2011-02-08
**SOLVED!** Ubuntu 10 just isn't working! Ubuntu 9.1 installed without a hitch! I followed the same steps and had no problems with 9.1 (used unetbootin). Hopefully I will be able to upgrade to 10.10 via terminal after I get 9.1 up and running. Thanks for all your help! Hope this issue gets solved!

---

