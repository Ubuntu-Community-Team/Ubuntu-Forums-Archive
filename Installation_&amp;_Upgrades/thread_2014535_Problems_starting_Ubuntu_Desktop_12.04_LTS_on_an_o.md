---
title: "Problems starting Ubuntu Desktop 12.04 LTS on an old Dell Inspiron 9300"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by roccia707 on 2012-07-02
Hello, please excuse my poor english, i'm italian.

I'm trying to use Ubuntu Desktop 12.04 LTS on an old Dell Inspiron 9300.

I wanted to try the "live" version of Ubuntu before installing it, just to read the content of my hard disk (Windows XP with personal data).

I downloaded Ubuntu ISO. First I've tried to burn it on a rewritable CD, but when I inserted it into my DELL DVD drive, the computer couldn't read it.

So I thought of burning the Ubuntu ISO on a 2 GB USB flash drive. I've used the process described here:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

that means that I used the "Universal USB Installer" program, and it "burned" the Ubuntu ISO on my pendrive. All the files have been correctly written on the pendrive.

So, after changing the boot sequence on my Dell pc (I moved the USB device before hard disk), I started the pc with the pendrive inserted.

An Ubuntu start menu appeared. I tried two of the functions in the list:

1) Run Ubuntu from this USB
2) Install Ubuntu on a Hard Disk

Then, in both cases, this appears on the screen:

Loading /casper/vmlinuz......
Loading /casper/initrd.lz.............ready.

But then, nothing. The cursors blinks and nothing happens. Why?

Thank you very much for your help! :)

PS: a second question: when I will be able to use Ubuntu, will I be able to see the Windows XP and personal files on the my hard disk?

---

### Post by sudodus on 2012-07-02
Welcome to the Ubuntu Forums :-)

Please specify the following data for your computer:

CPU, RAM, graphics chip

It will help us suggest what is the best choice of Ubuntu flavour and version :-)

---

### Post by roccia707 on 2012-07-02
Ok, I did some test and here are some new info.

First of all, I succeeded in starting up Ubuntu using the CD, one time. The DVD drive is not working correctly since many months, but sometimes it works. Actually I can't remember if the orange background appeared, but surely this was the last thing I read on the black screen:

--
* Starting configure network device security
* Starting configure network device 
* Starting crash report submission daemon
* Stopping anac(h)ronistic cron
* Stopiing CPU interrupts balancing daeomn
* Starting configure network device security
* Starting configure network device
* Checking battery state...
* Stopping System V runlevel compatibility

* Stopping log initial device creation
* Starting enable remaining boot-time encrypted block devices
* Starting configure virtual network devices
* Stopping configure virtual network devices
* Starting configure network device security
* Starting save udev log and update rules
* Stopping save udev log and update rules
* Stopping enable remaining boot-time encrypted block devices
--

Then nothing.

I can't start the installed Windows XP SO, and the laptop monitor is damaged (I can see only two thirds of the screen). So the only info I gathered are these:

- Pentium M
- 1.86 GHz
- 2 GB RAM
- 60 GB hard disk
- NVIDIA GeForce (don't know which one)
- CD/DVD+/-RW drive

Now, I'd like to talk about the same two experiments (starting Ubuntu via CD and via USB on my old Dell laptop) that I did some hours ago on a more recent notebook of mine, a Toshiba A200, with Windows Seven Ultimate SP1 installed (I now, it's an "old" pc, but not as old as the Dell Inspiron, I think).

Here are the Toshiba characteristics:

- Intel Core2 Duo
- 1.83GHz
- 2 GB RAM
- ATI Mobility Radeon HD 2400
- Hitachi hard disk (about 160 GB divided into two partitions: SO and data)
- TSSTcorp CD/DVDW TS-L632D ATA Device

I tried the Ubuntu CD on this pc, and it works correctly. I tested the SO without installing it, the orange background appeared, with menus, icons and windows, and I correctly read the files and folders in the two partitions of the hard disk. This demonstrates the the Ubuntu CD is valid. The problem is that works on the Toshiba but doesn't work on the Dell (because, as I already said, the DVD drive often doesn't read the disc, or, when the disc is read, the "starting" and "stopping" messages appears and finally everything stops.

So I tried the USB drive on the Toshiba, too. But I got the same results that I got when I used it on the Dell. The screen displayed:

--
Loading /casper/vmlinuz......
Loading /casper/initrd.lz.............ready.
--

So I deducted that my Peak II 2GB that I "burned" the Ubuntu CD ISO onto is not usable on my two PCs.

My Dell laptop is failing and I'd just wanted to read the data on its hard drive (formatted with NTFS), using a live OS, the smallest possible one, and, knowing nothing of Linux, I thought of Ubuntu. But it didn't work. The Windows XP installed on the Dell doesn't start because of hard disk errors, and anyway, I can't find my Dell Windows XP CD, so I can't try to repair it.

What can I do?

Thank you very much again!

PS: I have a "limited" Internet connection (5GB of traffic each month for 20 Euros) so I would like not to use other money to download a different version of Ubuntu or of Linux, if possible.

PPS: The "1) Run Ubuntu from this USB 2) Install Ubuntu on a Hard Disk" start menu that appears when I use my pendrive on both my laptops is not the one with the orange background and all the graphics. It's the simple one, on black background, a big Ubuntu logo and about 5 or 6 text rows to choose a startup function.

---

### Post by sudodus on 2012-07-02
In this case I would have recommended that you download Knoppix and boot a live session in order to save your personal data from the internal hard disk drive. Would it be possible to ask a friend or colleague, relative or neighbour to download it for you?

The reason is that Knoppix is very good at recognizing hardware in old and new computers to get them running. And you can add a cheat code (boot option is Ubuntu language) to run in text mode if the graphics mode would fail.

---

### Post by roccia707 on 2012-07-03
On knoppix.com I only found two version of Knoppix 7: a complete one (DVD 3.9GB) that is too large for my 2GB pendrive, and a "boot only version" (11MB) that I don't know if could be useful for me...

---

### Post by sudodus on 2012-07-03
> **roccia707 said:**
> On knoppix.com I only found two version of Knoppix 7: a complete one (DVD 3.9GB) that is too large for my 2GB pendrive, and a "boot only version" (11MB) that I don't know if could be useful for me...
Try [[COLOR="Red"]_ftp://ftp.uni-kl.de/pub/linux/knoppix/_[/COLOR]]("ftp://ftp.uni-kl.de/pub/linux/knoppix/")

---

### Post by roccia707 on 2012-07-05
Thank you very much Sudodus. For the moment I found a Windows XP CD and repaired the OS. I'll give Knoppix a try as soon as possible. Thanks again. :)

---

