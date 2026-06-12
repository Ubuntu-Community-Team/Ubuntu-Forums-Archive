---
title: "USB install from live CD"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by SANDIZ on 2008-06-12
I installed Ubuntu 8.04 on  a 4G USB. When I boot from the USB I get as far as the user login and Password and after that I get a blank screen. I'm not sure if it is doing something but I've left it for a couple of hours and still nothing. I'm new to linux. CAn anyone help?


Thanks,


Sandiz

---

### Post by Herman on 2008-06-12
Is it a blank screen, or a tan colored screen with a mouse pointer?

If it's a tan screen, see post #4 in the following thread, [** How to install ubuntu on USB drive and carry entire computing system in pocket?  **]("http://ubuntuforums.org/showthread.php?t=789528")

---

### Post by SANDIZ on 2008-06-13
Its a tan colored screen with a mouse pointer.

---

### Post by SANDIZ on 2008-06-13
> If it's a tan screen, see post #4 in the following thread, How to install ubuntu on USB drive and carry entire computing system in pocket? 


Thanks for the direction.

---

### Post by SANDIZ on 2008-06-14
I followed your post  from the other thread > How to install ubuntu on USB drive and carry entire computing system in pocket?  I am happy to say that I can now boot my USB all the way to the Desktop. My only concern is it does not prompt me  for username and password. How can I protect my USb from unauthorized use?

---

### Post by Herman on 2008-06-14
That's a very good question. :)

To begin with, not very many people would know how to boot a USB unless they happen to be a fellow Linux user.
A Windows user inserting your USB into a USB port to see what files are there would not be able to mount your ext3 file system. Windows wouldn't recognize ext3 unless it has special drivers. 
If they're honest and they were just trying to find out who owns it so they can give it back they wouldn't be able to find out anything.
If they were a thief or a dishonest finder they'd probably think there's nothing on it or it's defective and throw it away or reformat it with FAT32 or NTFS without thinking too much more about it.  
If someone a little smarter finds it, they might guess it's Linux and they can mount it when running a Linux liveCD or with ext3 drivers for Windows and nose through your stuff.

As far as booting it goes, with your Ubuntu login screen being skipped at boot-up, your system is vulnerable, anyone can boot it right up and be automatically logged in if they know how to boot a USB.

You can set up a GRUB password and edit your /boot/grub/menu.lst with a 'lock' command. That will help a little, it will make it harder for someone to boot it with it's own GRUB. I'll try that out myself today, it something I haven't bothered experimenting with before. I doubt if that will give you very much real protection, but it would be at least one hurdle for someone to overcome.
[Protecting your computer from cracking]("http://ubuntuforums.org/Protecting%20your%20computer%20from%20cracking") - GNU/GRUB Manual.

I tried the Ubuntu Hardy Heron Alternate CD's Encrypted install in a USB, but it only boots to a busybox shell for some reason, I haven't solved that problem yet. The same installation works perfectly in a hard disk, but not for a USB. That's unfortunate, because that would have provided the ultimate protection without too much inconvenience for the USB owner. 

Something you can do which will really give you some protection is to use Seahorse. When you set up Seahorse, you will be able to right-click on a file and encrypt or decrypt it by typing your Seahorse password.
Seahorse, AKA 'Passwords and Encryption Keys', comes standard in Hardy Heron, just look for it in your 'Applications menu, under 'Accessories'. You can easily encrypt all the personal files you want with Seahorse. (I wouldn't recommend encrypting any system or program files though, of course). 
That should be all you need though. It's a little bit inconvenient to have to remember to be encrypting and decrypting files every time you want to open and close them, but you could put all your sensitive files in one directory, call it 'private' if you like. 
Seahorse might be the better way to go, because full encryption for the entire file system can be as much a headache as a help anyway. As always, there's the security verses convenience balancing act. Then there's short term and long term implications to think of as well.  While an entire file system that's encrypted seems more convenient for daily use in the short term, it's harder to fsck an fully encrypted file system or rescue your files in the event of a system disaster if you have a fully encrypted file system. For most people, Seahorse will be the best option, my opinion.
[COLOR=#000000][**Seahorse** -Encryption Made Easy]("http://www.gnome.org/projects/seahorse/"), and [How to Set up Seahorse in Ubuntu]("http://users.bigpond.net.au/hermanzone/p5.htm#Install_Seahorse").

Regards, Herman  :)

EDIT: I just found this, which would be another option worth considering, [Encrypt home partition with cryptsetup & LUKS]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Encrypt_home_partition_with_cryptsetup_.26_LUKS") - Ubuntu Guide.
[/COLOR]

---

### Post by SANDIZ on 2008-06-15
Thanks for that wealth of info. I was actually more concerned what happened to login prompt. Just making sure I followed the procedure right. I can live with thaqt as long as I can try ubuntu and save my changes and files.

Thanks again.

---

### Post by Herman on 2008-06-16
:) Okay, yes, unfortunately the work-around to get the installation to boot in a USB results in the loss of the login screen and your security could be compromised, as well as the multi-user capabilities of Ubuntu.
Hopefully an update will correct the underlying problem sometime soon and we can revert the settings back to normal again after that.

 I did try out the GRUB password myself too, by the way, I just neglected to post back here until now.
Setting a grub password is nowhere near as good as having your proper Ubuntu login screen, but it would be better than nothing under these circumstances.
I improved my GRUB Page's info on setting a grub password, [password]("http://users.bigpond.net.au/hermanzone/p15.htm#password"). thanks to your excellent question. 
Regards, Herman :)

---

### Post by SANDIZ on 2008-06-16
I'm only now learning to use this OS. I find tons of info on the web, some are way over my head. I' go visit your GRUB page. 

Something I'd like to do if its possible, since I can't boot my USB on my laptop, is to try and boot Grub from CD and then have GRUB load the rest of the kernel from USB. That way I can still run Ubuntu and save my changes. Is that possible?

Thanks. You'be great help. -Sandiz :)

---

### Post by Herman on 2008-06-16
It depends on what kind of hardware and BIOS your laptop has.
Most computers that can boot a USB have the ability to choose that from the BIOS at start-up.
In one of my computers I do something like this, [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key").

There could be some computers that can boot a USB if you have a Grub CD to boot the USB with, you can try with [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), that would be the easiest, you could try that and see if that works.
If it works, you can make your own GRUB CD later, [                                                                           How to make your own personalized GRUB CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD").

A knowledgeable friend of mine recently informed me that it's possible to create a separate /boot partition in the hard drive of a computer that normally can't boot a USB and get it to boot, with the / (root) of the operating system in the USB. 
That workaround might work when the problem is that the BIOS can't 'see' (or address'), the Linux kernel when it's in the USB device. It means you will need to make a small partition in your hard disk for GRUB and all the other files in your /boot directory. More details are in this link, [How to make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").-(contains the Linux kernel, initrd.img and GRUB files). That might be a little bit complicated for you if you're a new user.
If you need a separate /boot partition, it's easier to make one of those when you install Ubuntu. If you do that, you might as well just install Ubuntu to your hard drive, unless your only problem is lack of hard disk space.

With many laptops, it's only one small screw that needs to be removed to open the hard drive door underneath the case. Often there's only one or two more small screws to remove before the hard drive can slide off it's connection. Refer to your laptop's manual.
Normally it's as simple as changing a common light bulb to exchange the hard drive in most laptops for a different one.
If the reason you want to try Ubuntu out in a USB is because you're afraid it might harm your Windows in some way, then you might consider buying a new hard drive for Ubuntu and simply exchanging hard disk drives to change operating systems.
I have recently bought 8.0 GB USB flash memory sticks for $56.00 (Australain), and I'm getting a 160 GB external USB for $106.00, which would fit in my laptop if I remove it from it's case. As you can see, on a per GB basis, a real hard disk drive is a lot better value for money that flash memory at today's prices. 
If you decide to take that option, you'll probably find installing and booting Ubuntu will be very simple.

There are a few ideas, do whatever will make you happy. :)

Regards, Herman :)

---

### Post by SANDIZ on 2008-06-17
Actually, I think I have enough disc space in my HD. The problem is every time I try to install Ubuntu to the  HD it says there not a large enough contiguous space. I've defragmented the HD several times and still the same problem.  I'm not ready ti abandon Windows just yet until I can make my wireless card work in Ubuntu. I'm enjoying the adventure. I'll try Super Grub Disk for now. It will be a learning experience. Thanks for the suggestions.


Sandiz

---

