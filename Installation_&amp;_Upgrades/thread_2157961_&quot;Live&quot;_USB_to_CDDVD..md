---
title: "&quot;Live&quot; USB to CD/DVD."
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by TNFrank on 2013-06-27
I'm pretty sure I know the answer but want to double check. So, if I want to transfer a "Live" USB iso to a CD or DVD all I have to do is drag and drop the files from the USB to the CD/DVD and burn em', right?  No need to go through UNetbootin or other software other then the software used to burn the CD/DVD.

---

### Post by VMC on 2013-06-27
You don't need to drag it, just have Brasero burn the ISO to you DVD. Although dragging it may do the same thing.

---

### Post by Cheesemill on 2013-06-27
Dragging the files over won't work. You need to use the 'Burn Image' option in your burning software (I recommend [xfburn]("apt://xfburn") if you're interested).

---

### Post by TNFrank on 2013-06-27
I could swear that the CD/DVD burner software that I have installed has a spot where you drag the files you want to be burned but basically you're just saying to burn the Live Image off of the USB to disk, not the raw .iso, right?  That way it'll boot from the CD/DVD player unlike the raw .iso image which will not boot.

P.S.
Just checked and with Brasero you do drag the files to the open area to burn them to disk.

---

### Post by Cheesemill on 2013-06-27
As I said above, dragging and dropping the files wont work. You'll end up with a burnt CD that has the correct files but doesn't have a bootloader on it.

In your burning software select 'Burn Image' and then select the image file (.iso file) you want to burn to disc.

---

### Post by C.S.Cameron on 2013-06-27
If you want to put a customized USB install on a CD you probably need to use something like Remastersys to build an iso of the install and then burn that iso to the CD/DVD otherwise the CD/DVD will probably fail to boot.

---

### Post by ADDICTED2GRAVITY on 2013-06-27
if i want to load programs into ubuntu will this work if I can't get an internet connection and are most files iso? i am knew at this ubuntu my learning curve right now is straight down lol

---

### Post by TNFrank on 2013-06-27
I've done the "Burn Image" of the .iso with Brasero and all I got was a dead image of the .iso that wouldn't boot. I guess I could use Startup Disk Creator to burn the image to CD/DVD so it'd boot but it also seems like a bootable LIVE USB burned directly to a CD/DVD would boot the same as the USB since the file structure would be the same.

---

### Post by C.S.Cameron on 2013-06-28
> **TNFrank said:**
> I've done the "Burn Image" of the .iso with Brasero and all I got was a dead image of the .iso that wouldn't boot. I guess I could use Startup Disk Creator to burn the image to CD/DVD so it'd boot but it also seems like a bootable LIVE USB burned directly to a CD/DVD would boot the same as the USB since the file structure would be the same.

The DVD needs to be able to tell the computer it is bootable, when you burn the iso to DVD it makes it bootable, just dragging files to the DVD does not do this.

I think there is a way using dd, but I don't recall the method.

---

### Post by C.S.Cameron on 2013-06-28
> **ADDICTED2GRAVITY said:**
> if i want to load programs into ubuntu will this work if I can't get an internet connection and are most files iso? i am knew at this ubuntu my learning curve right now is straight down lol

Welcome to the Forums.
Probably best to start a new thread concerning your specific question.

You will probably require the internet to download the programs.

---

### Post by Cheesemill on 2013-06-28
> **TNFrank said:**
> I've done the "Burn Image" of the .iso with Brasero and all I got was a dead image of the .iso that wouldn't boot. I guess I could use Startup Disk Creator to burn the image to CD/DVD so it'd boot but it also seems like a bootable LIVE USB burned directly to a CD/DVD would boot the same as the USB since the file structure would be the same.

It doesn't work like that. Bootable CD iso files and bootable USB's use different methods of booting.

When you use a program such as Startup Disk Creator or UNetBootin to create a bootable USB from an iso file it doesn't make an exact copy. Instead it copies just the files from the iso and then installs a bootloader such as syslinux onto the USB drive. The information needed to boot from a CD lives in the header of the CD, not in the actual filesystem so it can't be extracted in the same way that the files can.

This means that the image you now have on your USB drive doesn't contain any of the code needed for a bootable CD anymore, so copying the image back to a CD will result in an unbootable disc (as you've found out).

PS - What I've just described is an over-simplification of what actually happens, I'm just trying to get my point across in laymans terms.
PPS - Despite the name Startup Disc Creater can't be used for making CD's. It can only be used for making bootable USB drives.

---

### Post by TNFrank on 2013-06-28
Ahh, ok, that makes sense since USB and CD are differet forms of media.  I still don't know why the CD's I made weren't "Live" then since I did the drag and drop like the burner software said to do and it did burn the .iso to the disk but it won't boot.  Should I have extraced the files first then burned those?

---

### Post by Cheesemill on 2013-06-28
Neither method would work as the image that you are using doesn't have any bootable CD code on it any more.

---

### Post by TNFrank on 2013-06-29
> **Cheesemill said:**
> Neither method would work as the image that you are using doesn't have any bootable CD code on it any more.

Ok, so if you can would you please walk me through what I'd have to do to make a "Live" bootable DVD from the .iso that I download?  I should be getting my new CD/DVD RW drive on Monday and once I stick it into my laptop I'd like to burn some Live DVD's of some of the .iso Op Systems I've downloaded to keep in my CD/DVD case.  Thanks. :D

---

### Post by Cheesemill on 2013-06-29
If it's an iso that you've just downloaded then just use the 'Burn Image' option of your burning software to write it to a disc.

It's only once you've put an image on to a USB drive that it can't be transferred to a CD any more.

---

### Post by TNFrank on 2013-06-29
> **Cheesemill said:**
> 

It's only once you've put an image on to a USB drive that it can't be transferred to a CD any more.

I know you mean once you made a "Live" USB Image, right? I do have all my .iso's stored as they were originally downloaded stored over on my 32GB USB stick and on that 120GB hard drive I put in the enclosure. I'd like to get em' all on "Live" DVD's too though.

---

### Post by oldfred on 2013-06-29
New versions of Ubuntu are oversize so only DVDs will work. Others may be smaller and a CD will work.

Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

---

### Post by TNFrank on 2013-07-01
Got my CD/DVD RW Optical Drive in today and gave it a try. Picked up some DVD's and did the "Burn Image" and it worked like a charm. Totally bootable and everything. Now I have a DVD bootable copy of Ubuntu 12.04 and Back Box 3.05 on DVD. Thanks for all the help guys. :KS

---

### Post by sudodus on 2013-07-02
Why do you want the iso files on CD/DVD as well as on USB (and HDD)?

Do you want to boot some old PC that won't boot from USB? In that case you can try Plop. It boots from CD, and installs a driver so that your USB boot device can be used for booting. See this link

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by TNFrank on 2013-07-02
I'd just like to have bootable copies on CD and DVD to keep. My USB's are just to test drive .iso's and when I find one I like and want to hang onto I'll just make a bootable copy to either CD if it's small enough or DVD and put it in my CD/DVD case for future use. Besides, I got 50, 4.7GB DVD's for $20 bucks so they're cheaper then USB sticks.

---

### Post by sudodus on 2013-07-03
This is a good reason :-)

It also means that you need not save the iso files (if you don't want to spend HDD space for them). And remember, that all bootable USB drives do not correspond to iso files, that make bootable CD/DVD disks. In such cases you should keep the image file (stored as a file).

---

