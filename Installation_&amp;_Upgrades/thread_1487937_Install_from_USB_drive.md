---
title: "Install from USB drive"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by jwarreniii on 2010-05-19
Hello, all.

I recently decided to install Ubuntu on a couple of computers without CD drives (netbooks), so I followed these instructions to create a bootable flash drive:  [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/")

That worked fine for both netbooks.  Now I'm trying to use the same flash drive on a desktop currently running Windows Vista, but get his message when I try to boot from the flash drive:

No DEFAULT or UI configuration directive found!

Out of curiosity, I tried to boot one of the netbooks from the flash drive again and that still works.

I'm thinking a BIOS setting, but I have no idea what.  Thoughts?

Thanks in advance.

---

### Post by bondo101 on 2010-05-19
Does the net book's bios use usb's as boot options? Usb's are a little trickey, Re check what you loaded on the usb drive .it might matter what kind of Usb drive you are using, brand I mean there not all the same . Scandisk's usb's some time don't work because they have their own filing system built in. might con fuse the booting process.:)

---

### Post by jwarreniii on 2010-05-19
Yes, both netbooks boot from usb just fine.  It's the desktop that doesn't want to.  

It is, actually, a sandisk, but I removed the software that came on it.

After the error above, it leaves me at a "boot:" prompt.  Is there anything that I could type there to help it find something?

---

### Post by jwarreniii on 2010-05-20
Okay, I formatted and re-setup the flash drive from scratch.  Same results on my desktop:  No DEFAULT or UI configuration directive found!

But still works fine on the other computers (netbooks).  Does anyone have any idea why my desktop won't boot from the flash drive?

---

### Post by wilee-nilee on 2010-05-20
Have you tried downloading unetbootin for windows and formatting the thumb on the vista computer.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
format the thumb on the computer and load it on the computer and use the f12 or whatever key allows you to choose the boot from on the vista computer. I personally never change the boot order I just use the f12 option on my setups to choose the boot device.

---

### Post by jwarreniii on 2010-05-20
Yes.  That is exactly what I did.

---

### Post by jwarreniii on 2010-05-20
Does anyone have any idea why two computers would be able to boot from this flash drive and one won't?  I am stumped.

---

### Post by efflandt on 2010-05-20
If it is a Cruzer with U3 the U3 could be the issue.  That is a pseudo cdrom (sr device) that remains even if you totally remove everything and repartition/reformat the flash.  Maybe that system finds the fake cdrom and not the U3 software to go with it.

You might check your USB BIOS options for that computer, and try different ones (legacy, vs. auto vs. whatever else), because some options may not boot from USB.

You also might try web searching "linux u3" or "linux u3 removal".  Although, I had no issues booting an iso from a Cruzer with U3, except greatly extended boot time (twice as long).

---

### Post by jwarreniii on 2010-05-21
I checked that out, but I am really confused because it seems to try to boot from the flash drive, but then gives the syslinux error.  So it's at least getting that far.

SYSLINUX 3.85 2010-02-20 CBIOS Copyright (c) 1994-2010 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot:

---

### Post by metalf8801 on 2010-05-21
I can try to help you but I need to know a few things for sure I don't want to assume you've done something your haven't 

1st have you check the BIOS on the desktop to make sure you can boor from a USB drive?

2nd Are you trying to install the Ubuntu Netbook Remix or the regular desktop version of Ubuntu on your desktop? 

3rd have you tried boot your desktop from a Live CD? 

4th on a side note have you already partitioned the desktop using the build partitioner that comes with Windows Visa?  Just wondering because making a new partition on Windows Vista or Windows 7 is riskier then it is on Windows XP and I believe its safest to use the built partition program that comes with the newer versions of Windows. 

I hope I can help
Dan


Edit I just read your last post
The problem could be with Unetbootin the 2 ways (I know of) to see if that is the problem are to ether boot from a CD or make a boot flash drive using a Ubuntu program called usb-creator which you can make from a live CD or from a computer that Ubuntu has already been installed on so I think you will be able to use on your netbooks 
look for it Under System => Administration select "USB Startup Disk Creator"

---

### Post by jwarreniii on 2010-05-21
Hi, Dan

Thanks for the reply.

1.  Yes.  I have checked that I can boot from USB.  In fact, it gives that syslinux error, so I know that it is using the usb.

2.  I installed the regular Ubunutu install on the netbooks and that is also what I am trying on the desktop.

3.  I don't have a live CD to try.

4.  I installed an additional hard drive to install Ubuntu on.  I was afraid to mess with the drive that has Windows right now.

I see "Startup Disk Creator" but not "USB Startup Disk Creator" under administration.  Is that what you mean?

---

### Post by metalf8801 on 2010-05-21
> **jwarreniii said:**
> Hi, Dan

Thanks for the reply.

1.  Yes.  I have checked that I can boot from USB.  In fact, it gives that syslinux error, so I know that it is using the usb.

2.  I installed the regular Ubunutu install on the netbooks and that is also what I am trying on the desktop.

3.  I don't have a live CD to try.

4.  I installed an additional hard drive to install Ubuntu on.  I was afraid to mess with the drive that has Windows right now.

I see "Startup Disk Creator" but not "USB Startup Disk Creator" under administration.  Is that what you mean?

yes I think so sorry I'm not using Ubuntu right now so I can't check 

so yeah try that 
you might need to have a Ubuntu live CD ISO on the computer your making the live USB drive on 

Good luck 
Dan

---

### Post by jwarreniii on 2010-05-21
That worked like a champ.  Thank you very much.

---

### Post by metalf8801 on 2010-05-21
> **jwarreniii said:**
> That worked like a champ.  Thank you very much.

That's great!

You should mark this Thread as solved you do that my clicking on Thread Tools at the top of the page and selecting solved which should be at the bottom.

I hope you like Ubuntu 
Dan

---

### Post by Vee26 on 2010-07-08
> **bondo101 said:**
> Does the net book's bios use usb's as boot options? Usb's are a little trickey, Re check what you loaded on the usb drive .it might matter what kind of Usb drive you are using, brand I mean there not all the same . Scandisk's usb's some time don't work because they have their own filing system built in. might con fuse the booting process.:)

OMG I love you! 
I have been trying to install 10.04 netbook edition on my Aspire One (came with Linpus Lite which i hated) for 2 straight days, then i came to this forum and saw your reply about trying a different usb stick, turns out that was the problem all along! I changed from a 2GB HP Flash drive to a Sahara one and Voila! worked like magic.
I'm falling in love with my One all over again :D, registered just to thank you :D

---

### Post by Cason on 2010-07-19
I'm running into a very similar problem. I've actually got two different USB keys of different makes (one with 10.04 Desktop and one with 10.04 Netbook Remix) that are proven to work in 5 other computers. I've been getting the exact same "no default or UI configuration directive found" with both keys on one unit that I'm trying to get Ubuntu on. I also followed the directions to create the USB key from within Ubuntu. When I boot with *that* key, I get this message:
```
SYSLINUX 3.63 Debian-2008-07-15 CBIOS Copyright (C) 1994-2008 H. Peter Anvin
boot:
```
When I hit enter, it says: "could not find kernel image: linux"

So apparently, it's a similar error no matter how the USB booter is created. Any ideas? Since the USB keys have always worked well, I've never bothered to make an actual CD. I guess I'll try that, but I'd also really like to figure out why the heck the USB keys won't work with this one particularly stubborn unit. ;)

---

### Post by Cason on 2010-07-19
Well, the CD worked. I'm still quite confused about why the USB drives wouldn't work. Maybe the BIOS on the fairly old unit is just persnickety. Oh well... :P

---

### Post by alord on 2010-09-21
just rename folder on flash drive: isolinux -> syslinux, 
this help me)

---

### Post by iDonkey on 2010-09-25
I also needed to rename the isolinux.bin and isolinux.cfg files in the syslinux folder to syslinux.bin and syslinux.cfg and then it works.

---

### Post by danisnotstan on 2010-09-26
I have been using Ubuntu on and off for a few years (but I'm still like a noob haha) I finally decided to register so I can thank everyone for help with this problem. I have never had any issues running ubuntu from usb until recently. I decided to download a fresh version thinking mine may have been corrupt. I was able to boot after using the advise from alord and iDonkey, however, I'm still having some issues. It seems as though persistence isn't working? I noticed the version is now 10.4.1 LTS? I made the USB drive using the universal method from pendrivelinux and I used a 2gb casper. I downloaded updates and restarted and nothing was saved. I have always made the USB drive the same way and everything has always saved automatically. The only difference that I see is the 10.4.1 vs. 10.4. Any ideas what I can do? Thanks!

---

### Post by peakhead12 on 2010-09-26
> **iDonkey said:**
> I also needed to rename the isolinux.bin and isolinux.cfg files in the syslinux folder to syslinux.bin and syslinux.cfg and then it works.
Thx this worked for me!!

---

### Post by fastfourier on 2010-09-27
> i also needed to rename the isolinux.bin and isolinux.cfg files in the  syslinux folder to syslinux.bin and syslinux.cfg and then it works.

+1

---

### Post by HerwigMacho on 2010-09-29
Hi I had Similar problem (No DEFAULT od UI directive...)
 
Solved: USB -Stick formatted as FAT, not as FAT32 :):popcorn:
then I could use it as a boot stick for the following 
Hardware: EPATec 3800, 800Mhz, 256RAM, 2GB FlashDisk

---

### Post by Smiff2 on 2010-10-09
> **HerwigMacho said:**
> Hi I had Similar problem (No DEFAULT od UI directive...)
 
Solved: USB -Stick formatted as FAT, not as FAT32 :):popcorn:
then I could use it as a boot stick for the following 
Hardware: EPATec 3800, 800Mhz, 256RAM, 2GB FlashDisk

This was the issue for me also on an old (2006) Via KT400 based system. thanks for posting.

I needed to format the drive FAT then use pendrivelinux universal installer with the format option UNCHECKED (else it reformats in FAT32)

So i think you must have a USB drive with capacity 2GB or 4GB to be able to format FAT16 and still have enough space for a live DVD.

Quite a nasty cryptic error! thanks.

---

### Post by BingHeZhouKe on 2010-10-09
you can try to change your usb mode,such as changed to usb-hdd or usb zip,maybe the desktop doesn't support the mode you are using…

---

### Post by nelliott71 on 2010-10-22
> **HerwigMacho said:**
> Hi I had Similar problem (No DEFAULT od UI directive...)
 
Solved: USB -Stick formatted as FAT, not as FAT32 :):popcorn:
then I could use it as a boot stick for the following 
Hardware: EPATec 3800, 800Mhz, 256RAM, 2GB FlashDisk

THIS! =D>=D>=D>

Thanks, you rock!  :guitar:

---

### Post by magicfab on 2010-11-27
Great tip, I worked around this by formatting to FAT16 and using a 1GB partition to create my bootable USB key.

---

### Post by mrpilot007 on 2011-02-11
> **nelliott71 said:**
> THIS! =D>=D>=D>

Thanks, you rock!  :guitar:

Same issue. This worked for me as well.

On Windows 7 I formatted the USBDrive as FAT instead of FAT32 and this worked. Thanks all.

---

### Post by joao82 on 2011-02-20
> **mrpilot007 said:**
> Same issue. This worked for me as well.

On Windows 7 I formatted the USBDrive as FAT instead of FAT32 and this worked. Thanks all.

The same problem here was also solved by formatting to FAT (I suppose it's FAT16) and not FAT32.
It's impressive how so many errors in other Linux distros can be solved in Ubuntu forums... one would think the distro's own forums would figure it out, but they don't have a clue.
Thanks!

---

### Post by khurtsiya on 2011-02-26
what if the same error appears when I am trying CD?

---

### Post by alaniyonu on 2011-03-12
Hi. I'm having a similar problem that I haven't been able to troubleshoot. 

I installed Ubuntu onto a computer I built a few months ago. The computer doesn't have a CD drive so I booted Ubuntu off of a USB stick. Now I am trying to install Windows 7 but I get a similar error message as the original poster.

The major problem that I'm having is that instead of an ISO, the copy of Windows 7 I have comes in a folder with other folders and files inside so Ubuntu's startup disk creator doesn't work for me.

I've been considering trying some of these **random** folder to ISO programs ive found online but I thought I'd hit up the community before I did.

Best,

THEBBBBEAST

---

### Post by toomanymatts on 2011-04-29
trying to run 11.04 off the USB now, getting the same "no default or ui configuration directive found" error.

I am on a Dell Vostro V13, running 10.10 at the moment.  I installed that from a bootable USB, so set all that up the same way.  The computer does not have a CD drive.

Notice some of the above recommending renaming folders to 'syslinux' - they are already named that way on this version.

Any help greatly appreciated...

---

### Post by Zelei on 2011-04-29
> **toomanymatts said:**
> trying to run 11.04 off the USB now, getting the same "no default or ui configuration directive found" error.

I am on a Dell Vostro V13, running 10.10 at the moment.  I installed that from a bootable USB, so set all that up the same way.  The computer does not have a CD drive.

Notice some of the above recommending renaming folders to 'syslinux' - they are already named that way on this version.

Any help greatly appreciated...

I had this problem after creating a bootable 11.04 USB using the Pendrivelinux installer from within windows - I allowed the installer to format the drive and it picked FAT32

To fix I manually formatted the penkey as FAT16 (just listed as FAT within winXP) - and unchecked format in the installer.

---

### Post by xastxast on 2011-04-29
More ideas appreciated,I have tried all of the ways above with no luck.After passing bios cursor flashing and stays there..Now I am downloading dvd iso.Lastly I will try it.

---

### Post by xastxast on 2011-04-29
I have tried 3 usb sticks without luck before I gave up lastly I tried 4. one and it successfully  boot and install.Strange, a few days ago I installed windows from one of them and I know that others are not faulty.

---

### Post by basthen on 2011-05-08
FAT16 did it for me. Didn't have to rename anything. Thanks!

---

### Post by toomanymatts on 2011-05-09
well this has been a process that has been beyond irritating.

So, as per previous post above, could not get it to start.

Decide to reinstall on to the USB drive...I'm using Ubuntu's start up disk creator.

I get an error that checksums do not match, would i like to retry. I retry, same error.

Eject USB, pass to a colleague on Windows, she reformats for me, and I successfully create a start up disk.

Restart.

Get the Dell splash screen, f12 for boot options, select USB.

Get a screen with a couple of icons at the bottom that indicate that I am starting off the USB and then....back to splash screen and it booted off the HD as always.

Try again.

This time I get past the 2-icons screen, and get language selection screen.  English.  Then another menu asking if i want to install or try without installing etc.

Try without installing.

Enter...some thinking time...back to my Dell splash screen, and boots off the HD.

Try again...same thing, this time when it reverts to splash screen, f12 again, back to the boot options, but...same thing again.

I give up at this point...any advice on how I can test this thing?

---

### Post by tredsyn on 2011-10-10
"no default or ui configuration..."

I encountered this problem after installing Lucid Lynx on my usb drive. I had Natty Narwhal on my usb drive; ran with no problems. I uninstalled Natty and replaced it with Tango Studio (based on Lucid Lynx) for home recording purposes. Then the "no default or ui configuration..." problem started.

> **alord said:**
> just rename folder on flash drive: isolinux -> syslinux, 
 this help me)
 
> **iDonkey said:**
> I also needed to rename the isolinux.bin and  isolinux.cfg files in the syslinux folder to syslinux.bin and  syslinux.cfg and then it works.

Renaming the 3 items (folder + bin file + cfg file) solved the problem. The usb i used was already formatted to fat32 before i used ubuntu natty. :D

---

### Post by Silentzor on 2011-10-11
The fix for me was:

install dosfstools

on the machine used to create the flash drive, format with gparted the flash drive to fat32 and use unetbootin to re-install the image on the flash drive.

Hope this helps.

---

