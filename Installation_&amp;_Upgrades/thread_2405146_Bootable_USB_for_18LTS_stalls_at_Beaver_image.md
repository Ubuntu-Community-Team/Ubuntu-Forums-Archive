---
title: "Bootable USB for 18LTS stalls at Beaver image"
date: 2018-11-01
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2018-11-01
I'm trying to install Ubuntu 18LTS to dual boot on a Windows 10 desktop machine, and the bootable USB stalls repeatedly.

 I downloaded the Desktop ISO from the "releases.ubuntu.com" site, and made the USB using the Rufus tool. I went into BIOS, moved the USB stick to first position, and reset. 
After a couple of screen messages passing so quickly I had to photograph them to read them, I get the "Ubuntu" word, screen centre, with the usual row of dots beneath it, then the image of the Bionic Beaver, and that's all.

I've tried this process several times, downloaded a new ISO each time, cleaned the USB with mkusb on a 64bit laptop running Xubuntu and started afresh, back in the Windows machine with Rufus. Each time I get the same result.

The spec of the desktop machine is: 
[SIZE=2]Intel i5-2400
Asus P8Z68-V LX Mainboard
8GB Kingston HyperX DDR3
*Edit: Graphics card, newly installed by my local shop to cope with the latest Windows update, is NVIDIA GT 710/REV 1.0*
CoolerMaster Centurion 530 Case
DVD-RW
320GB Hard Disk
USB Wifi adapter 
Windows 10 Pro x64

I used the instructions at [https://www.linuxtechi.com/dual-boot-ubuntu-18-04-lts-with-windows-10/](https://www.linuxtechi.com/dual-boot-ubuntu-18-04-lts-with-windows-10/) to shrink the C partition and create a 40GB empty partition.

 My technical knowledge is very limited, and while I can follow step-by-step instructions as long as things behave, my understanding of what I'm doing and why is almost completely non-existent. This method has allowed me to run another desktop on Ubuntu 12 and then 14 for several years perfectly successfully, likewise several ancient laptops, but when things go astray I'm almost completely in the dark.
 Please tailor any answers to account for this lack of understanding :-)

I took images of the various stages shown on screen. They will mean more to you reading this than they do to me!

[ATTACH=CONFIG]281504[/ATTACH]Bios screen with USB disc moved into prime position.

[ATTACH=CONFIG]281505[/ATTACH]
This "Couldn't get size" message flashes across too quick to read properly. I suspect it's important.
[ATTACH=CONFIG]281506[/ATTACH]
The proper options then appear. I did try the Check Disc option, and it declared it to be free of errors.

But then just the Bionic Beaver, which is still sitting patiently there around 2 hours after I started this latest attempt.

I will be very grateful for any advice which I can follow to install 18LTS on this newer desktop machine, and so move us on from 14LTS on our old 32bit desktop machine which is currently struggling to keep up. The newer one I'm trying to use was built in 2011/12, but I was assured it would be able to cope with the needs of Ubuntu.

Thanks.




[/SIZE]

---

### Post by riverfr0zen on 2018-11-01
EDIT: Nevermind. I had a questioin about your boot order, but that can't be the problem since the live USB is booting

---

### Post by riverfr0zen on 2018-11-01
It looks like you may be experiencing the same problem as those in [this thread]("https://ubuntuforums.org/showthread.php?t=2390291").

---

### Post by Richard_York on 2018-11-02
> **riverfr0zen said:**
> It looks like you may be experiencing the same problem as those in [this thread]("https://ubuntuforums.org/showthread.php?t=2390291").

Thanks. The problem indeed appears the same, yes. And the new card is an NVIDIA GT 710/REV 1.0, and Nvidia cards are mentioned.

The thread you helpfully link to in turn links to another discussion on "How do I set 'nomodeset' after I've already installed Ubuntu?"
My two hurdles here are, i) it's beyond my comprehension, and ii) I haven't already installed Ubuntu. There is a reference to already running on Ubuntu16 - should I perhaps try installing an earlier Ubuntu on this Windows 10 machine? Would that give me any advantage? 
I note that one suggestion written there in May is "Then I suggest that you stay with Ubuntu Mate version 16.04 at least  until the first point release 18.04.1 LTS (late July or August). By that  time there will be several bug fixes and it is more likely that the new  point release will work in your computer."    ... it would seem that particular bug fix isn't working for me if it's there now.

---

### Post by riverfr0zen on 2018-11-02
Re: Setting 'nomodeset', see posts #8 and #9 in the thread that I linked to. The instruction in #9 should get you to a screen where you can add 'nomodeset' in a fashion similar to what is explained in the second link you mention (the one that is for installed setups). I can't be 100% sure about this because I don't have a live usb at hand, but basically the idea is that you are editing the boot options (I think on a live usb there are just different options like "try, install..." than those present on an installed system).

Otherwise, yes, you can try an earlier (e.g. 17.04 or 17.10) version of Ubuntu, or you could also try the latest 18.10 .

---

### Post by Richard_York on 2018-11-02
Thanks. 

 I pressed "e" when the Grub menu appeared, and it led me to a screen showing:
[ATTACH=CONFIG]281520[/ATTACH]  this appeared. 
And at the foot of the screen:

[ATTACH=CONFIG]281521[/ATTACH]

This looks hopeful, but before I press anything else, aware that the terminal confers the ability to make changes I don't understand and probably can't reverse, I'll be grateful to know what steps to make next to get to the point where I find and edit the nomodeset line.

---

### Post by riverfr0zen on 2018-11-02
It looks like you have a cursor over there to edit. So go ahead and edit the line that starts with 'linux' as explained in the other thread.

When you're done, follow the instructions on the second image. I don't think there are any irreversible changes you can make here. If it doesn't boot to the live cd distro, you just restart your computer.

---

### Post by Richard_York on 2018-11-02
Seriously impressed !! Thank you.
 I'm now looking at the BIonic Beaver plus icons down the left bar and "Install Ubuntu 18.04LTS on the main screen, which is much better.
Thank you again for your patience. It's help like this which makes me respect and trust this forum so well.

Now to see if I can install successfully alongside Windows.  :-)

---

### Post by riverfr0zen on 2018-11-02
Glad it worked out for you. Don't forget that you may face a similar problem with booting after you've installed.

---

