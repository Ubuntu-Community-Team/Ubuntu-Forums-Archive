---
title: "Having A Really Bad Experience With Ubuntu.  Please help."
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by Frsutrato on 2012-07-06
Hi I'm having terrible trouble with Ubuntu.  I've just installed it and it's virtually dysfunctional.  I've timed windows opening to about 4mins.
Running: AMD Athlon 64 988 MHz 1.00 GB of RAM.  Windows XP Home.

I've done the Windows type installation.  I can't seem to figure out how to do any other kind of installation.  The hope was to ditch Windows XP for Ubuntu but it's terrible, I can't get it do do anything.

I've used the update manager to see if that would help but now it just seems worse.  That took an age and it's done nothing at all useful.

Now I would like to reformat my hard drive and start again but I can't get into the CMOS to do that.  I've forgotten which function key to press but I've tried dozens of times and I keep getting taken to the screen which gives me the Windows or Ubuntu choice of OS.

Please can someone help me?  I'm in a terrible mess with it all and have no clue as to what to do next.

---

### Post by Mr.Dee on 2012-07-06
Need more details on how you tried to install. Wubi?  When you boot up your PC does it as you what you want to boot up?
 
Not sure why you need access to the cmos... You should only need to reset the cmos if you are experiencing hardware issues.

---

### Post by Frsutrato on 2012-07-06
CMOS is where I can set the boot drives and so forth, to re-install.  I just need some idea of how to re-format the drive so I can start again, as everything is a complete mess.  I've done it before, when I installed Windows but I can't remember what it entailed.  I know you have to press a function key and then type something, but it's been a long time and I've forgotten the process.

Wubi is one of the programs on the disc I installed for Ubuntu, yes.  I downloaded the Ubuntu desktop link, extracted the files and burned them to disc.  Then I put the CD-R in while in Windows and followed the steps.  When finished, I chose to "Reboot now" and when the computer rebooted, I got options to choose "Windows" or "Ubuntu".  I did this so I could try Ubuntu to see if I like it.  I can't tell if I like it or not because it's not working as it should.

Now I can't work out how to uninstall Ubunto, either.  I'm totally stuck.

---

### Post by Mr.Dee on 2012-07-06
I think you might be thinking CMOS is BIOS? Anyhow if it is the BIOS you are trying to access.  You should be able to access it by holding F2 or F10 on boot up, some computers have different buttons so just give some of those F keys a try.   You mentioned the function key, i'm guessing you are using a laptop.
 
I've read about wubi, but never really used it since it did not interest me so I cannot give you too much advice on how to uninstall it.  It should however not be too difficult to uninstall since it is supppose to be user friendly.  It is also installed next to windows so it should be easy to remove by using windows.
 
Once you restore your machine... I recommend you try a live cd.  You can try ubuntu without installing or breaking anything with a live cd!

---

### Post by coffeecat on 2012-07-06
@Frsutrato, a few points.

> **Frsutrato said:**
> 
Now I can't work out how to uninstall Ubunto, either.  I'm totally stuck.

If that's a wubi install and you want to remove it, you simply uninstall it as though you were uninstalling a Windows application. In Windows XP go to Add/Remove in Control Panel. I'm going from memory here so someone may be able to correct where you go in Windows to uninstall things.

> **Frsutrato said:**
> CMOS is where I can set the boot drives and so forth, to re-install.

As Mr.Dee said, you are thnking of the BIOS. You may need to set the BIOS to boot from the optical drive first, but you do not need the BIOS to format anything.

> **Frsutrato said:**
> 
I've done it before, when I installed Windows but I can't remember what it entailed.  I know you have to press a function key and then type something, but it's been a long time and I've forgotten the process.


That would be machine specific and would only be relevant for re-installing Windows - probably from a restore partition - in your machine. It won't help to install Ubuntu.

If you don't have the Ubuntu ISO already burnt to CD, you can download it here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Instructions for burning a live CD:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And a useful guide for installing Ubuntu to its own partition as a dual-boot with Windows:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Last thing. Wubi installs do tend to run slow, so they are not a fair test of Ubuntu installed natively to its own partition. However, your installation does seem to be far too slow. What graphics card do you have? Be aware also that a live CD session will run slow.

---

### Post by Frsutrato on 2012-07-06
This is too much of a mess for me to understand.   When I select CMOS it gives me options to change the boot sequence and so forth.

Please can you instruct me on how to format my hard drive?  Everything is too much of a mess to continue.

I do not even have the disc in and the boot drive is set to CD.  I have the hard drive deselected, yet here I am, typing in Firefox, in Ubuntu.

Nothing makes sense any more.  I need to wipe my hard drive clean and install Ubuntu but I cannot work out how.

---

### Post by scottpledger on 2012-07-08
> **Frsutrato said:**
> 
Please can you instruct me on how to format my hard drive?  

To re-format your hard drive, you need to do the following:
[LIST=1]
[*]***_BACK UP ALL OF YOUR DATA!!!!_*** I can't stress this enough. Reformatting your hard drive will completely wipe everything on your computer.
[*]Make an Ubuntu LiveCD (I assume that you already have this, since you have Ubuntu installed under Windows XP.
[*]Insert the Ubuntu LiveCD and boot from it. 
[LIST]
[*]If you want to dual-boot Windows and Ubuntu, select the 'Try it' option and do the following:
[LIST=1]
[*]Find the Partition Manager and open it. (This should be under the Ubuntu menu).
[*]When that screen appears, select your hard drive (probably /dev/sda).
[*]Remove every partition that it shows you. Then click apply. Your hard drive is now free of all data.
[*]Now you want to re-install Windows.
[*]Once Windows has been re-installed, boot up from the LiveCD again and select the 'Install' option.
[*]When asked where you want to install Ubuntu, select your hard drive and choose 'Resize other OS and install Ubuntu in free space'. (or something like that - I haven't re-installed plain ubuntu in a while).
[*]Complete the rest of the Ubuntu install. Once that's done you should be able to dual-boot with no problems.
[/LIST]
[*]If you just want to install Ubuntu and have no Windows then select the 'Install' option and do the following:
[LIST=1]
[*]When asked where you want to install Ubuntu, select your hard drive and choose 'Use entire hard disk for Ubuntu'. (or something like that - again, I haven't re-installed plain ubuntu in a while.)
[*]Complete the rest of the Ubuntu install. Once that's done you should be able to boot into Ubuntu with no problems.
[/LIST]
[/LIST]
[*]Now, you may want to copy that backup data back onto your hard drive so that you can get to it more easily.
[*]And finally, you're done!
[/LIST]

Hope that helps clear things up a bit!

Also, BIOS is the software that you're referring to that controls what starts up when. CMOS is just the physical memory hardware that it stores those settings in.

---

### Post by efflandt on 2012-07-08
First I am curious what computer you have from when, because I have a computer from 2004 with one of the earliest Athlon64 CPU's and it is a single core 3200+ that runs at 2 GHz.  But it still has 64-bit Ubuntu 10.04.

Although, I have more recent tablet PC with AMD C-50 that is 1 GHz 2 core running 64-bit 11.10 from SD card.  Is your computer some sort of netbook (small) and is its CD/DVD built-in or separate?

If you could figure out how to boot from an install CD or bootable install iso on USB you could start from scratch and install it using your entire hard drive.  That should be faster than running Linux under Windows, but will not exactly be a speed demon.

---

### Post by ssulaco on 2012-07-08
> **coffeecat said:**
> 
If that's a wubi install and you want to remove it, you simply uninstall it as though you were uninstalling a Windows application. In Windows XP go to Add/Remove in Control Panel. I'm going from memory here so someone may be able to correct where you go in Windows to uninstall things.

You are correct,coffeecat,use Add/Remove programs to uninstall Wubi.

---

### Post by mastablasta on 2012-07-09
> **Frsutrato said:**
> This is too much of a mess for me to understand. When I select CMOS it gives me options to change the boot sequence and so forth.
 
 
this is CMOS: [http://en.wikipedia.org/wiki/CMOS](http://en.wikipedia.org/wiki/CMOS) found in:  [http://en.wikipedia.org/wiki/Nonvolatile_BIOS_memory](http://en.wikipedia.org/wiki/Nonvolatile_BIOS_memory)
 
And this is BIOS: [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
 
[QUOTE]
Please can you instruct me on how to format my hard drive? Everything is too much of a mess to continue.

you do not need to format the hard drive to remove Ubuntu. you need to go to boot to windows, go to Start--> Control panel--> Add/Remove programmes--> find wubi and select to uninstall it.
 
wubi install itself in virtual disk space so it might be slower that side by side install. 
additionally as mentioned you need to give full system specs not just processor and ram. graphcis card is important as you might need to install additionall drivers for it. alternatively you can try lighter desktop environments that are found in other Ubuntu versions such as Xubuntu and Lubuntu. they work well with older maschines and use 140 and 80 MB ram respectively.
 
then slow down a bit, perhaps read the Ubuntu manual found in my signature with a lot of pictures and then ask again on how to install Ubuntu side by side next to windows XP. it is easy to do so when you know how.

---

### Post by black veils on 2012-07-09
if you just create a functioning bootable cd/usb then you can install ubuntu over the entire hard drive, which will of course wipe it clean of the previous stuff.  put .iso image to [usb flash drive]("http://unetbootin.sourceforge.net/")  or [cd/dvd]("http://infrarecorder.org/?page_id=5") (burn as image, and use slowest burning speed).

[install ubuntu]("http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/")

you might want to have Xubuntu instead, as a lighter alternative.

---

### Post by SeijiSensei on 2012-07-09
I've never used WUBI, but couldn't this just be a memory problem?  The OP has only 1G of memory so running Ubuntu inside Windows is going to push that to the limits, no?  Wouldn't Windows have to do a lot of swapping to manage a full Ubuntu installation inside of Windows?

OP, you might want to give the LiveCD method a try.  Burn an Ubuntu [desktop CD]("http://cdimage.ubuntu.com/releases/12.04/release/"), boot from it, then choose "Try Ubuntu" when it is offered.  Ubuntu will run entirely from the CD without using your hard drive, and it will have access to the entire 1 GB of memory in your machine.  Loading programs will be slow because they have to be read from the CD, but once you've got them loaded into memory, performance is usually decent.

As black veils said, you might want to try one of the more lightweight versions of Ubuntu like [Xubuntu]("http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/") or [Lubuntu]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/").

---

