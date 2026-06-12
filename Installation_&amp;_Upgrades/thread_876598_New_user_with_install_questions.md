---
title: "New user with install questions"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by GramCleric on 2008-07-31
So after many years of reluctance, I decided to give a flavor of Linux a shot. I've read from a few sources that ubuntu is a good one to start off with. So here I am :-)

I've read around and haven't really found anything relating to my particular case, so I'm hoping I can be directed in the right spot.

I'm starting all over from scratch. It's that time of the year for my annual format. I'm forced to re-install my windows environment because of the VB programming and gaming I do.

My main question is...
In what order should I begin installing Ubuntu and Windows XP Pro?
After I format, my primary hard drive will be separated 50/50. Half going to Ubuntu, half going to windows. Should I install Windows first, then proceed to install Ubuntu, or vice versa?

Second, I am hoping that most of my hardware has Linux drivers developed by the company, but if not, is there a reliable source I can obtain drivers from third parties at? I'd rather not end up at some shifty source putting potentially harmful or even poorly written drivers on my system.

Thank you much in advance. I'm sorry if a lot of you end up repeating yourselves over and over again with these questions, but my search-fu is lacking tonite..I'm very tired lol.

---

### Post by llama320 on 2008-07-31
> **GramCleric said:**
> In what order should I begin installing Ubuntu and Windows XP Pro?

I would install XP first, then ubuntu. The other way will probably work, but I've never tried it.
> After I format, my primary hard drive will be separated 50/50. Half going to Ubuntu, half going to windows. 

I might also suggest a Transfer partition that can be read by both Ubuntu and XP to allow you to transfer stuff back and forth. That said, you'll be able to access XP from Ubuntu without a problem, so that could in theory serve as the transfer partition

> Second, I am hoping that most of my hardware has Linux drivers developed by the company, but if not, is there a reliable source I can obtain drivers from third parties at? 

In all likelihood, Ubuntu will recommend the right drivers that you can install right there. No searching the company website or anything..you'll see when you get there :)

The only manual install of a driver was for my graphics driver, which wasn't too bad. Also, as an aside, if you have an ATI drive, you may have a tough time because they're not nearly as well supported as nVidia is.

Good Luck & Welcome

---

### Post by tuxxy on 2008-07-31
Heres a link that may be useful for known supported hardware,


[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

---

### Post by GramCleric on 2008-07-31
> **llama320 said:**
> 
I might also suggest a Transfer partition that can be read by both Ubuntu and XP to allow you to transfer stuff back and forth. That said, you'll be able to access XP from Ubuntu without a problem, so that could in theory serve as the transfer partition

The only manual install of a driver was for my graphics driver, which wasn't too bad. Also, as an aside, if you have an ATI drive, you may have a tough time because they're not nearly as well supported as nVidia is.

Good Luck & Welcome

Thank you for the quick response. 

To the first comment above, I have a total of 4 hard drives. All storable content is located on one of my other 3 drives. My main drive is just for the installation of software. Music, Movies, Documents etc are located on other drives. With that said, I have looked over this link [http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows"), do these instructions apply for secondary drives without an Operating system installed, or does it also apply to hard drives using the ntfs partitioning regardless of an existing operating system?

As to the second comment, I do have an XFX Geforce 7800GTX, so I should be all set there :-)

---

### Post by tuxxy on 2008-07-31
You certainly should, that card should run flawlessly just install the driver :)

---

### Post by arvevans on 2008-08-01
If you install XP first and then Ubuntu, the Linux installer will find your XP boot part and make a dual-boot setup for you.

If you install Ubuntu first and then XP, the XP installer will ignore your Linux boot part and overwrite it with the XP boot loader.  This will then not give you the option of booting into Linux...it will automatically go to XP when you re-boot.
[INDENT]This is recoverable using the run-from-CD boot disk, but it is much easier if you do it in the preferred order the first time.[/INDENT]

You won't need a "transfer partition" unless you specifically want to do that.  Linux can read and write your MS-XP file format just fine.  It will appear in your file structure as any other mounted file system and Linux interface with it is automatic.

There are applications that allow your MS-XP to read and write to the Linux file system as well.  [INDENT]<http://www.fs-driver.org/> shows one such program[/INDENT]

There are many other possible ways to do what you are doing, but keeping it simple for the first time around makes things much easier and understandable.
_._

---

### Post by llama320 on 2008-08-01
> **GramCleric said:**
> 
do these instructions apply for secondary drives without an Operating system installed, or does it also apply to hard drives using the ntfs partitioning regardless of an existing operating system?


the instructions apply across the board for any partition you have, OS installed or not.

Looks like you're on the right track :)

---

