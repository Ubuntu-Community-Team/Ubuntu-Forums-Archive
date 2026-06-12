---
title: "Manuall Hard Drive install W/O CD"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by shaanr on 2007-10-17
Hey doods

How can I manually liek copy over Ubuntu to a hard drive and start that hard drive up in a  computer w/o a CD drive? its a laptop

Basically the laptop has a dead cd drive, and i have a 2.5" enclosure to run the laptop hard drive on my desktop. Is there a way to copy over ubuntu files to that laptop harddrive and then  move that laptop hard drive back into the laptop and voila, run ubuntu?

Thanks in advance!

---

### Post by shaanr on 2007-10-17
okay i tried running ubuntu live on another computer of mine,and then plugging in my laptop hard drive via usb, insalling ubuntu to the drive (default settings), but when i boot the laptop to that drive now it takes forever to load anything and then finally displays a screen which is blue with pink and red charachters all over the place

any help is appreciated!

---

### Post by Herman on 2007-10-17
Hello shaanr,
First you should download adrian15's free Super Grub Disk for USB, from this site: [Super Grub Disk Webpage: Home Page]("http://supergrub.forjamari.linex.org/") and install Super Grub Disk for USB in your laptop hard drive while it is inside the external USB case, plugged into your desktop.

Here is a link that should help you to do that, [                                        How to Make your Super Grub USB Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk").
              
Here is a link to a wiki page about how to install Ubuntu from files copied from a Ubuntu Live CD to a small partition you make in your hard drive and then you boot the partition as if it was a Live CD,  [https://help.ubuntu.com/community/In...tion/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux").

So when you have the necessary files copied into the hard drive you can unplug it from your desktop, remove your hard drive from your USB external hard drive enclosure, and put it in your laptop.

When you boot your laptop, Super Grub Disk should boot up. You need to get a Super Grub Command Line Interface by pressing your 'c' key from almost any menu. 
Here is a link about how to use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

The boot command you will need to type into your Super Grub Disk Command Line Interface is found in the [https://help.ubuntu.com/community/In...tion/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")  how-to.
That should boot the Ubuntu installer for you. You may need to modify those commands a little to get them to suit your computer's partition numbers. The Ubuntu installer should boot as if it was a Live CD and you should be able to try Ubuntu out and install it that way.

Regards, Herman :)

---

### Post by cudaman73 on 2007-10-17
You absolutely have to make sure that the host machine and the laptop are the same architecture, and at least similar in hardware.

Running the ubuntu installer, it is still going to configure ubuntu for the system that you're on.

Are the two computers both intel or both amd?

---

### Post by shaanr on 2007-10-17
thanks herman and cudman for the fast, detailed responces!

right now im actually setting up ubuntu 7.04 to be bootable via a flash drive as per [these ]("http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/")instructions

if that doesnt work, i'll try out herman's instructions. 

cudman -- no, they were two interily different architectures. The working desktop I used was a P4 HT and the laptop is a Pentium M centrino, i was hoping ubuntu'd make a generic installer -- o wells

thanks again for all your guys' help!

---

### Post by shaanr on 2007-10-17
gah this is annoying -- that usb drive tutorial didnt work, so i began trying herman's method

first i formated the drive to ext2 with gparted, and now my desktop running ubuntu live tells me that i dont have permissions to copy anything over! 

I Just tried formating it to fat32 and copying over the files from the usbpendrive tutorial onto the hard drive, but to no avail

> GRUB Loading stage1.5

grub loading, please wait....

error 17

---

### Post by chewearn on 2007-10-17
If you have an IDE-to-USB adapter, this will let you plug your IDE CD/DVD-ROM to the USB port of your laptop, and boot the liveCD from there.

I assume your laptop can boot from USB.  That's is how I install ubuntu to one of my PC, which has no optical drive.

---

### Post by Herman on 2007-10-17
> first i formated the drive to ext2 with gparted, and now my desktop running ubuntu live tells me that i dont have permissions to copy anything over!First, make sure you find out the name that your USB disk is mounted as in /media,
```
ls /media
```For example, it might simply be mounted as 'disk', unless it has a volume name.
When you know for sure what it's name is, you can chmod it, like this,
```
sudo chmod 777 /media/disk
```Then you should be able to write to it without needing to use any sudo commands. 

Regards, Herman :)

---

### Post by shaanr on 2007-10-17
herman! thank you for all your help. 

in a last moment of desperation/frustration, though, I burned off Ub 7.04 (i was using the 7.10 dvd thing before) and after a while it worked! 

its not that i don't have an optical drive, its just that its a really crappy one thats on the verge of dying. maybe it couldtn handle the dvd media, but it also failed many times when trying to install xp from the xp disk. I did a memtest, and my memory checked out

thanks again for your support, i really appreciate it. This is my first time on ubuntu and i can already tell that this'll be a pleasure to use at college.

regards,
shaan

---

### Post by Herman on 2007-10-17
Oh, good! :)

By the way it often helps to try cleaning your CD/DVD drive's optical lens with a Qtip (cotton bud) dipped in some denatured alcohol, (methylated spirits) if you can, That sometimes clears CD/DVD drive problems up.

Regards, Herman :)

---

