---
title: "Possible to include customise boot CD?"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by dskw on 2007-09-21
Hi all, I just installed Ubuntu on a VM with Vista as host OS, and it works great (tip: use VirtualBox, and not MS VPC). Anyway, I noticed that Ubuntu on boot has the option where pressing 'Esc' will enable you to select between:

1) boot normally
2) boot into recovery mode
3) run memtest

I was thinking whether I can edit the CD such that I can include my copy on Spinrite onto it. For those who do not know, Spinrite is an application which checks and corrects hard disk errors. It can only be run from a bootable floppy/cd. Memtest is also similar, so I was thinking if I could have:

4) run Spinrite

So I looked at the Ubuntu CD, and memtest is located at E:\pool\main\m\memtest86+. Furthermore, the filename is memtest86+_1.65-1ubuntu2_i386.deb. Now, what is the deb file extension? Is it the same as .iso, or is it an iso image repackaged or recompiled in some way? Is there any method that I can follow to customise my Ubuntu CD such that I can include ISO images inside so that they can be booted on startup?

TIA

---

### Post by Herman on 2007-09-21
Hello dskw,
That sounds like an interesting project, I haven't tried to modify a Ubuntu LiveCD yet, but it should be possible. I have done something like what you are suggesting, but with Super Grub Disk, GParted LiveCD and Puppy Linux.
Here is the link, [How To Build a Super Grub Disk/GParted CD / DVD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted").

Basically, you copy the contents of the .iso files to one directory and use a genisoimage command to make them into one new .iso file. You can configure Super Grub Disk easily with the right information to boot the other operating systems on the CD before you do that.

You might be able to do something similar with Ubuntu and Spinrite. That link might help give you some ideas to get started with anyway.  I hope you can get it to work.

Regards, Herman :)

---

### Post by dskw on 2007-09-21
Hi Herman, thanks for your site. Yes, it was certainly informative. I searched the Ubuntu CD for menu.lst, but no go. That's why I do not know how Ubuntu lists the boot options.

---

### Post by Herman on 2007-09-21
Hello  		Hello dskw,
Look in Ubuntu 7.04 i386/isolinux/isolinux.cfg
You'll find all the boot options you're looking for in that file.

Regards, Herman :)

---

### Post by dskw on 2007-09-21
Hi, Herman. Again, thanks for the reply. I checked /isolinux/isolinux.cfg. The relevant line is as below:

> 
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -


Now, this is where things get pretty confusing. Why does isolinux.cfg points to /install/mt86plus instead of pool\main\m\memtest86+? And what is the difference between these two files? I used the file command to check these two files out, and here are the results:

u07@sun:~[86]$ file mt86plus
mt86plus:       data
u07@sun:~[88]$ file memtest86+_1.65-1ubuntu2_i386.deb 
memtest86+_1.65-1ubuntu2_i386.deb:      current ar archive, not a dynamic executable or shared object

---

### Post by Herman on 2007-09-21
Hello dskw,
```
title   memtest86plus
kernel $(grub_device)/install/mt86plus
```I just added this boot entry to my /boot/grub/menu.lst in the directory that the new .iso file will be made from, created the .iso and then booted it.

That boots Memtest 86+ okay. Super Grub boots up all right for me too, but so far the Ubuntu LiveCD doesn't boot all the way properly yet, I must be doing something wrong. It seems to be booting but I just end up with a black screen with a white flashing underscore in the top left corner...

I have tried a few entries something like the following to try to get Ubuntu to boot up, but obviously I'm missing something,
```
title Ubuntu LiveCD 
kernel $(grub_device)/casper/vmlinuz file=/preseed/ubuntu.seed boot=casper quiet splash --  
initrd $(grub_device)/casper/initrd.gz
```I'll keep on trying, I'm probably close. do you have any suggestions?

Another potential problem will be the size of the .iso image, mine is 700 mb or 701 mb, without adding any more programs like your Spinrite, so I think you'll need to go up to a DVD/RW disk.

Regards, Herman :)

---

### Post by dskw on 2007-09-23
Hi Herman,

No suggestions from me, bro. In fact, this is the most I have ever delved into Ubuntu (and consequently, Linux), so I guess I'm running around blind. :D The SpinRite iso file is about 1.5mb, So if I want to fit that in, maybe I need to remove some other applications, which will cause even more of a headache. 

In fact, I don't understand your 2nd quote. How is this pointing to an iso file? Is casper your iso file?

Regards,
dskw

---

### Post by Herman on 2007-09-23
I have mounted both the Super Grub Disk .iso file and the Ubuntu .iso file and copied all the files from both .isos into a new directory.
The new directory is the one I am making into an .iso file to burn to the CD. 
I don't think we can have more than one .iso per CD or at least I don't know how to do that, so it's just a big mixture of directories and files in one big .iso, some of them belong to Super Grub Disk, and others belong to the Ubuntu Live CD.

To try to get it to boot, I am modifying Super Grub Disk's /boot/grub/menu.lst file with entries similar to some old ones that used to work to boot GParted LiveCD when it used to be booted by syslinux boot loader.
Nowadays GParted LiveCD is booted by GRUB so it's easier.

Originally, I got the idea for how to boot GParted from a how-to by adrian15 , the developer of Super Grub Disk about how to combine Super Grub Disk with a Knoppix LiveCD. The same, (or similar) commands as adrian15 had for that used to also work for GParted LiveCD. So, I was hoping it would be easy enough to boot Ubuntu too, but so far I have tried many times and not been able to boot Ubuntu all the way, it stops booting about half way each time. Probably I am close, but there must be just one or two small changes I need to make in the boot options. 

/casper is the name of the directory in the Ubuntu LiveCD that has the kernel and initrd.image in it.

There are still lots of other ideas I could try out. 
The genisoimage command that I use to make the whole thing into an .iso can be modified to make Syslinux the main bootloader for the CD, I haven't tried doing that yet, and I could try to learn how to modify syslinux to boot Super Grub DIsk instead. That would be doing things the other way around. I don't know if it will be easier, but it might be interesting to try.

I might not be able to do this in a short time like I thought, I might have been a little too optimistic to begin with, or, maybe the next time I try, it will work. But I'm out of time and out of ideas for now. I will have to study live CD booting for a while to get some fresh ideas.
The easiest thing for you would be to make the [Super Grub Disk/GParted CD / DVD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted") and start with that. At least I know that should work, and there will be lots of room left over on the CD for another operating system too.
Then you just have to figure out how to boot your SpinRite.iso from Super Grub Disk.

I haven't got a copy of Sprinrite  yet, is it a free download from somewhere? I would need to be able to look into it and see if I can find out how it boots. 
EDIT, -Oh, I think I have already found it here: [http://xona.com/2004/06/07.html](http://xona.com/2004/06/07.html)

Anyway, I haven't given up yet, this is a great way to learn things -try to do something you don't know how to do, and don't give up until you solve it! :p
But it might take time.

adrian15 has a new how to here: [Want to know how to build a custom cdrom with SGD on it?]("http://supergrub.forjamari.linex.org/?section=documentation#SEC4") You should look at that too and see if it gives you any ideas. I could bother adrian15 and he will probably help, he is a very nice fellow will probably help anyone who asks, but so far I'm trying to figure this out by myself. 
adrian15 already explains in that last link how to boot Super Grub Disk with Isolinux (Syslinux) too, but I haven't tried it yet, but it will probably work. 

Actually, it you try that, and it works, then try making your CD-RW again with your SpinRite in it and you can see if you can boot SpinRite from either Syslinux or by Super Grub Disk, you'll have two chances then. :p

Anyway, if there is something you want to do with computers that you think should be possible, just keep trying and keep learning and never, ever give up and some day you will succeed! :p

Regards, Herman :p

---

### Post by dskw on 2007-09-24
Hi Herman,

This is getting more complex than I thought. Originally, since memtest86+ is bundled as an iso image, and the ubuntu folks have managed to package it into the LiveCD, I thought that it would just be a simple editing of lines of code and adding the spinrite.iso image into the LiveCD and it should work! I guess what I need to do now is find out how they integrated memtest86+ into ubuntu (did they just add the iso into the folder, or was it recompiled in some way to a .deb file..) 

Based on my (limited) understanding, what you are proposing is to:
1) use SGD to load syslinux/isolinux
2) edit the SGD's menu.lst file to point to:
    a) Ubuntu iso
    b) Spinrite iso

Am I right?

I must say, you have been most helpful so far! Thanks!

Regards,
Dominic

---

### Post by Herman on 2007-09-24
Well it's getting more complicated all the time because now that I have read all about Spinrite I see that it is 'proprietary' software that we have to pay for. There would be legal restrictions on its use, we might not be allowed to modify it. It would be necessary to read the EULA and possibly send an email to the organization who makes it to check if it's okay to do anything with it other than use it the way it was made.

memtest86+ is a program that can be added to any live CD, it looks like all that is needed is a directory with two or three files in it and the right directions in menu.lst for booting it with GRUB.
It would be simpler if Spinrite was an open source program that can just be pasted inside a Linux operating system.
At this stage I'm not sure what Spinrite actually is made up of, but I'm guessing since it's an .iso file that it has some kind of an operating system of its own, 

According to this article in wikipedia, [http://en.wikipedia.org/wiki/SpinRite](http://en.wikipedia.org/wiki/SpinRite) there are some quite good open source alternatives to Spinrite. They might not do exactly the same thing, but something close. You may need to use several different programs too, not just one. Those are listed in the bottom paragraph of the wikipedia page under the heading 'Alternatives'.  Those would be simple to install in a Ubuntu LiveCD,  Normally you just boot the LiveCD and 'install' the same way as you would for a hard disk install, you could use the programs, but the changes wouldn't be 'permanent' in a LiveCD, you would lose the programs when you shut the computer down or reboot. That's because the programs would not be able to be written to the CD, but would be stored in your computers memory for a little while, as long as you have the CD booted.
If you made a usb pendrive with a dedicated /home for Ubuntu like many people do with Knoppix, you should be able to install the programs you want and keep them. Here is a Ubuntu wiki page about that here: [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-inter.png[/IMG]LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") 

Also, read my [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html"), it's quick and easy to do that with Knoppix.

After reading the Spinrite site though, I don't blame you for being impressed, it certainly looks like great software from the sales blurb. Probably it would be worth its own CD if it can run on its own.

Regards, Herman :)

---

