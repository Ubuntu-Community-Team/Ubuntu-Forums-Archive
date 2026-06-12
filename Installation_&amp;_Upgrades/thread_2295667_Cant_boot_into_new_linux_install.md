---
title: "Cant boot into new linux install"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by dan193 on 2015-09-20
I got an older PC to use to learn Linux, and having an issue. Ive tried  installing Ubuntu, Mint, and elementaryOS all with the same issue. 

Install goes smooth, but when its done and I reboot, it sits at a black  screen. No curser, no nothing. Ive tried fixing grub via [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) method and [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/) to no avail. Im not dual booting.

One suggestion that coming up was to set nomodeset in grub. Thats the thing...unless my Google-Fu is failing, the instructions I  found say to get into the grub file, at BIOS splash screen press and  hold the right shift key and it should pop up....it doesnt. I couldnt find a  way to access it via live CD, although it seems like I should be able to  mount the drive and access it? How to do that I have no idea.

I did put the live cd in and booted holding the shift key down, to boot  into the...what is it...basic non-gui menu. One of the options under F6  (advanced options) is nomodeset. I checked it, and rebooted. No luck. I  have a feeling those were options for the live session.

Any ideas?

Hardware: 
[http://arrowdirect.com/hp-compaq-na-xw4600-3-16ghz-core-2-duo-tower-250gb-8192mb.html](http://arrowdirect.com/hp-compaq-na-xw4600-3-16ghz-core-2-duo-tower-250gb-8192mb.html)

Ive reinstalled several times with the same issue. Since its happening on every distro Ive tried, Im suspecting its something *I* am doing wrong, but honestly Im niot trying anything fancy. Installing and clicking next, next, next etc on the install walk through.

I did pull a boot repair right after installion, which is here: [http://paste.ubuntu.com/12490003/](http://paste.ubuntu.com/12490003/)

Ive wiped and reformatted the hard erive several times also, which looks like this:
Pre-install: [https://www.dropbox.com/s/hrm8qc6ic8pvgyg/20150919_124310.jpg?dl=0](https://www.dropbox.com/s/hrm8qc6ic8pvgyg/20150919_124310.jpg?dl=0)
Post install: [https://www.dropbox.com/s/nany04kj4cu1mk0/2015-09-19%2013.08.01.jpg?dl=0](https://www.dropbox.com/s/nany04kj4cu1mk0/2015-09-19%2013.08.01.jpg?dl=0)

Im pretty frustrated at this point, but Im not giving up ;)

---

### Post by Bucky Ball on 2015-09-20
*Thread moved to **Installation & Upgrades**.*

Welcome. First off, we don't officially support Elementary or Mint here. You would be better posting on their forums for help with them.

To set 'nomodeset' you don't need to get into the grub file. You need to access the list of kernels at boot and if you are not seeing it, hit shift just after the manufacturer splash. 

Highlight the kernel you want to boot, hit 'e' and find the kernel line ending in 'quiet splash'. Add 'nomodeset' after a space at the end. 'quiet splash nomodeset'.

You should be able to boot into the BIOS by hitting a key (possible escape or delete) at boot and check you are booting from the hard drive and not the install media. 

If all this fails, grab a supported Ubuntu or flavour, 12.04 LTS, 14.04 LTS or 15.04 (the LTS releases are supported for five years, 2017 and 2019 respectively). Create the install media, boot from it, 'Try Ubuntu'. Can you get to a desktop?

---

### Post by dan193 on 2015-09-20
Thanks for the quick reply! The main one Im trying to use is Ubuntu 15.04, and the boot log I posted is from my Ubuntu install.

Ive gone into my BIOS and verified my boot order (DVD drive then HD (theres only one HD on this box)), and live CD works just fine. I can get to desktop and navigate properly.

---

### Post by Bucky Ball on 2015-09-20
If you are trying to boot into a new Linux install you should have all install media removed and the BIOS set to boot from the hard drive Ubuntu is installed on. Yes?

---

### Post by dan193 on 2015-09-20
Well, I didnt change the boot order in BIOS (DVD, HD) but I did go into my BIOS boot menu and choose HD. Do I need to explicitly change by boot order for HD *first*? And yes, I removed media.

---

### Post by Bucky Ball on 2015-09-20
Yes, the hard drive need to be the first boot device. Mind you, there is nothing in the others, so theoretically it should skip them and look for the first available bootable device. 

To be sure though, make the hard drive the first boot device. You can also hit F12 on a lot of machines and get a 'boot device' menu so you can choose the hard drive. Might be a different key on your machine. It will tell you which quickly at boot.

---

### Post by dan193 on 2015-09-20
OK then no, I didnt do that. But as I said, I did get into the BIOS boot menu at startup and choose HD. Ill try hard setting it in the BIOS.

Question though: wouldnt getting into the boot menu of BIOS be the same as hard setting it? Or no?

edit: does anything look out of place in my boot log I posted?

---

### Post by Bucky Ball on 2015-09-20
Create a current bootinfo using Boot Repair (there is an option when it launches) and post the pastebin address. You can install and run [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") in a live session with internet connection.

---

### Post by dan193 on 2015-09-20
The boot repair log I posted is current. The only thing Ive done since running that one is power off the PC and finish my drink last night :D

[http://paste.ubuntu.com/12490003/](http://paste.ubuntu.com/12490003/)

---

### Post by Bashing-om on 2015-09-20
dan193; Hello;

My welcome to the forum.
I look over the info provided, and I do see several problems -> leading me to the conclusion you should wipe that hard drive and re-install with a 64 bit operating system.
1) Your specs show that the machine has 8 Gigs of memory .. -> 64 bit rather than a 32 bit ( i686) install ;
2) Your partitions are not aligned to the hard drive - >  
> 
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, [color=blue]488397168[/color] sectors
/dev/sda1  *         2048 484204543 [color=red]484202496[/color] 230.9G 83 Linux

3) I have to question where you installed grub to
> 
Unknown BootLoader on sda2

In this configuration you need grub installed to the Master Boot Record of the hard drive as 'sda' only .

On a problematic install, may I suggest that we go with release 14.04 as it is a Long Term Support release and "we" are the more familiar with it . 15.04 now is systemd based and many of us just do not have a great amount of experience with this initiate system .

wipe the sweat off, clean things up ->
[INDENT][INDENT][INDENT]install afresh
[/INDENT][/INDENT][/INDENT]

---

### Post by dan193 on 2015-09-20
Thanks bashing-om! However, Ive only got TWO gigs of memory installed :confused:

As to partitions not aligned to the hard drive...I dunno. If you look at my dropbox links, I first wiped it then created ONE partition, then installed. The Ubuntu installer created whatever partitions it needed (as shown in 2nd dropbox pic).

I can certainly try a LTR though.

---

### Post by Bucky Ball on 2015-09-20
Try the boot repair recommended repair again and reboot.

> =================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s

This may have something to do with it:

> Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       **/boot/grub/i386-pc/core.img**

The line in bold I'm not sure is right. It doesn't correspond with what I have on four different installs:
> 
Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       **/boot/extlinux/extlinux.conf**

Might be somewhere to start digging.

I've got to hit the sack as here it is 3:30am. Remember, patience is a virtue if someone else doesn't arrive sooner than later. If there is no action in 12 hours, feel free to bump the thread by posting 'bump' or keep us updated with any progress/breakthroughs at any time. Both will result in the thread being taken to the top of the new posts list. 

Good luck.

---

### Post by Bashing-om on 2015-09-20
dan193; Humm ...

Bottom line, the numbers do not lie  - your partition is out-of-bounds .
from you spec link - the seller provided:
> 
Memory 8192
 maybe the truth is abused , but I would not think so .
But the terminal command - from a liveDVD(USB) 
```

sudo dmidecode

``` will tell a lot of tales .

And it appears the boot loader is confused as to where the boot code is located.

I am just saying what I would do. If it were me I would take the time to wipe that drive with the 'dd' tool - will take about 3 hours - and install a 64 bit version of linux. I will not advise on what desktop environment ( flavor) ; as my own personal preference is xfce due to it simplicity and configure ability. The desk top YOU prefer is just that, your preference.

Believe me;
[INDENT][INDENT][INDENT]we will get you through this
[/INDENT][/INDENT][/INDENT]

---

### Post by dan193 on 2015-09-20
Bucky and Bashing- THANK YOU. 

Thinking back, when I got that HP machine I got it with the sole intention of learning Linux. First thing I did when I got it was swap out the crappy vid card and memory that came with it and install some better stuff I had laying around. It very well couldve been two 4gig sticks I put in there as Ive run 8 gigs on my rigs for a long time.

Another thing, is doing some reading, it appears for most people ext3 is the preferred filesystem. I formatted to ext4 (newer is better, right?).

My task list is as follows:
1. Format the entire disk with a dd-type tool (please recommend one?)
2. Download Ubuntu LTS release in 64 bit
3. Reinstall onto a ext3 formatted drive.
4. After installation, boot into the BIOS and hard set boot order to hard drive FIRST.
5. Cross fingers!

Look like a solid plan?

---

### Post by Bashing-om on 2015-09-20
dan193; OK !

Now we are going to cook with Crisco !
1)
> 
Format the entire disk with a dd-type tool (please recommend one?)

That tool is 'dd' !
from a liveDVD run:
```

dd if=/dev/zero of=/dev/sda bs=1M

```
If you desire to get a status of 'dd' the instructions to do so are in the manual:
```

man dd

``` from an additional opened termimal .

2) [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

3) Nope, you do want ext4 as the file system. ext4 has several enhancements ( release 4 !) and is the default.
In the installation, I have no heartburn with you selecting " erase disk and install ubuntu" and allow the install wizard to make all the decisions on formatting/partitioning. The wizard will do just that, take the whole disk to install a default system - and will be just fine good and dandy for a 1st time install.

4) Yeah, you can, Or just leave the boot order as CD 1st, hard drive 2nd and remove the CD. I often boot up liveDVDs thus I have the CD as 1st boot option. With bios not finding a bootable CD it defaults to booting the hard drive.

5) Wont hurt, but not required. We do Prior Prudent Planning. The plan will work !

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by dan193 on 2015-09-20
Awesome thanks! Ill try this when I get home tonight :)

---

### Post by Bucky Ball on 2015-09-20
EXT4 is right and correct. Don't worry about EXT3.

---

### Post by dan193 on 2015-09-28
First, THANK YOU Bashing-om and Bucky for all your assistance!

After several dd wipes and God knows what else I tried after hours of reading, I finally determined I have a bad HD. Kept getting alignment errors. So I ordered a new HD, and Ubuntu installed flawlessly, and Im up and running now...DRAMA FREE!

Thanks again guys for your patience with this linux n00b!

---

### Post by Bucky Ball on 2015-09-28
Great to hear! Enjoy the new OS, the forums and the learning curve. Please see the first link in my signature and please feel free to post a new thread for any further issues. Good luck. :)

---

### Post by Bashing-om on 2015-09-28
dan193; YeppeR 

What ^^ he said :)

[INDENT][INDENT]enjoy
[INDENT][INDENT][INDENT]up up and away 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

