---
title: "Blank screen after GRUB (64 bit) - cannot install Ubuntu :*("
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by peGGi on 2011-09-12
[SIZE="2"]My laptop's specs:
[LIST]
[*]Lenovo IdeaPad Z570
[*]Intel Core i5-2410M @ 2.3Ghz
[*]6 Gb RAM DDR3
[*]640 Gb ATAPI Hard-disk Drive @ 5,200 RPM
[*]NVIDIA GeForce G520M with Optimus switching technology
[*]Broadcom 802.11n Network Adapter
[*]REALTEK soundcard
[*]Windows 7 Home Premium 64-bit
[/LIST][/SIZE]

I downloaded Ubuntu Studio 11.04 and burned the iso image onto two different DVDs, using two different programs (one DVD is RW, the other is just R).  I verified the hash MD5sum thing.  I get as far as GRUB with the 4 options (install, advanced install, disk verification, system rescue) but no matter which one I select, I get a blank screen and nothing happens.  The DVD drive spins down after about 30 seconds.  Also just before the GRUB screen I get a message saying *Error: "Prefix" is not set*.  I'm not sure if that's relevant. 

I have tried all the options using both DVDs.  Same thing happens.  I have changed the graphics setting in BIOS to UMA or Optimus, but still happens either way.  I've tried booting with the wireless switch turned off, same thing happens.  

I downloaded 'vanilla' Ubuntu 64-bit and burned onto a CD, and the same thing happens.  

I have downloaded Ubuntu 32-bit and I am able to boot from the live CD (interestingly the wireless card won't work, but that's maybe another thread...).

I have searched extensively through these forums and other sites but I can't see anything that will help me.  

I've included a screen-shot of my hard-drive's partitions, in case that's relevant.

Is there something I'm missing?  I'd really appreciate help on this.  The laptop is less than 2 weeks old.  I was so looking forward to getting Ubuntu Studio up and running.  I've gone about as far as my technical abilities will allow.  Would really appreciate any help.

---

### Post by drs305 on 2011-09-12
peGGi,

Welcome to the Ubuntu forums. Sorry you are having difficulties.

Do you end up with a blinking cursor at the top left of your screen? If so, you may be having a video problem. There are certain options you can set *before* the system boots which may help (such as nomodeset). Here is a link to the Community documentation on how to set boot options for the LiveCD.
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

You might also want to consider installing from the Alternate CD. It often works when the normal CD doesn't, as it doesn't rely as much on system drivers.

---

### Post by Quackers on 2011-09-12
I think twin graphics is still a problem for Ubuntu.
With some setups other people have managed to turn off the Nvidia card and get the integrated Intel graphics working, although I think they suffered from poor or no 3D graphics.
Some systems have a switch in bios to turn off the Nvidia card and some don't, it seems. If you can't turn one off I think you will struggle to run Ubuntu until this problem is sorted out.

---

### Post by peGGi on 2011-09-12
Hi drs305 and Quackers,

Thank you both for responding so quickly.  I really appreciate it.

drs05 - I don't see a blinking cursor.  I don't get that far.  Literally as soon as I hit enter on "install Ubuntu" or whatever other option on GRUB, the screen goes blank and that's it.  Installer doesn't start at all.  I looked at the link you provided but I don't think it applies because I can't get the installer to even start.  I tried hitting F6 when GRUB starts but nothing happens.  In grub I can start command line or edit for any of the options - would that help?  I will try the alternate CD.  Hoever I have been trying Ubuntu Studio, which is called 'alternate' in the iso file - so would that amount to the same thing?  If anything occurs to you or if I'm missing something, please let me know!

FTR, I'm using the 'ubuntu studio alternate amd 64' image.  I hope I'm not mixing up the terminology!  When I say GRUB, I'm talking about the black screen with the white writing....  I get 4 options (install ubuntu, expert install, verify disk, and repair broken system).  When I use the non-studio Ubuntu desktop AMD 64 image, I get 3 options at this point.  But it's still a black screen with white writing, I never get as far as purple with F key options or whatever else.

Quackers - there is an option in BIOS to turn off Optimus and just use Intel's graphics.  But the same thing happens when I try and boot in with the live DVD.  I've also tried switching other things on/off in BIOS (wireless, ACHI/IDE).  Also, the 32 bit CD works - would that show that it's possible to have Ubuntu on a switchable system?  

Thank you both for taking the time to reply.  I'm giving up for tonight (it's 4.35am here...!) but I'd appreciate any further suggestions or advice or sympathy!  All best.

---

### Post by Sef on 2011-09-13
> I have downloaded Ubuntu 32-bit and I am able to boot from the live CD  (interestingly the wireless card won't work, but that's maybe another  thread...).

> [SIZE=2]Broadcom 802.11n Network Adapter[/SIZE]

Broadcom needs some proprietary drivers to make it work.  This is known problem with Dell. Depending on your card, this [sticky]("http://ubuntuforums.org/showthread.php?t=1604868") may have an answer.

---

### Post by peGGi on 2011-09-13
Hi Sef - thank you for that.  I'll try and sort out the network card once I actually get Ubuntu installed.

Just to update - I downloaded Ubuntu Studio 10.04 64 bit, and I can get as far as the installer (I haven't tried installing yet).  I also downloaded Linux Mint 11 64 bit, and the live DVD works (again, haven't tried installing it).   So this makes me think that it is possible to get 64 bit Linux on my system - any ideas why 10.04 64-bit would work (or at least get as far as installer) and 11.04 won't?

---

### Post by peGGi on 2011-09-14
Anyone got any more thoughts on this???  

If not I'll install 10.04 but would love to get 11.04 going....

---

### Post by LinuxTheDragon on 2011-09-14
Hi peGGi,

I just went through the very same issue with my new Z570. After multiple tries, I could not get the 64 bit version of ubuntu 11.04 to get past the grub menu. I was only able to install the 32 bit version, which went through smoothly. I would like to have the 64 bit version, so I will keep an eye on this thread to see if anyone else has suggestions......

I tried nomodeset and the alternate CD install also to no avail. :(

My factory install had the same partition setup - I used windows to shrink its own partition as small as it could (around 200GB I think), and then put ubuntu in that new free space. I was hesitant to use the ubuntu installer to resize the partition since I thought windows might not like it :P I did a windows backup as well prior to in case I needed to restore. Just my two cents if you were thinking the same way.

---

### Post by peGGi on 2011-09-14
Hey LinuxTheDragon,

Thanks for sharing.  Think I'll opt for old 64bit than new 32bit.  Pity.  I might wait a while then try upgrading to 11.04; maybe in a few months the problem will miraculously be sorted! 

How did you get on with wireless and graphics?  I hear that they can be troublesome with Broadcom cards/ NVIDIA Optimus systems respectively.

Yeah have been mulling over the partition thing.  Ideally what I want is to have a partition for windows, a partition for ubuntu, a partition for data that windows and ubuntu can share (with movies, music, etc.) and then whatever other partitions the Lenovo system needs...  It's a little confusing - I know that a hard-drive can only have 4 primary partitions, and it already has three...  I'm backing everything up, partions and all, twice (with Lenovo's one-touch backup and EaseUs Todo backup).  Then I'm going to take a chance and merge the Lenovo D: with the Windows C:....  I hope that won't hinder the Lenovo programs.  Then I'll be able to create two more partitions for Ubuntu and the data partition...  I hope I'm not being crazy!  If anyone has advice about this partition business I'd appreciate hearing it. :)

---

### Post by staticd on 2011-09-16
Same prob.
Acer 4755. i3-23330M, Linpus preinstalled.
Posted solution at.
[http://ubuntuforums.org/showthread.php?t=1841496](http://ubuntuforums.org/showthread.php?t=1841496)

Tell me if it works

---

### Post by LinuxTheDragon on 2011-09-16
staticd: thanks for the post - I will try that method shortly.

peGGi: Agreed. I would prefer 64 bit myself, and will be trying staticd's method - hopeully it will work. I was able to get my wireless working, but I have an intel wireless card, not broadcom. I believe sef's post above looks promising. Just an fyi, FN + F5 is a toggle switch for me to enable/disable the wireless card. I also used the info in this thread [http://ubuntuforums.org/showthread.php?t=1761472](http://ubuntuforums.org/showthread.php?t=1761472) to help get my wireless working. might prove useful after you get the broadcom drivers installed.
Haven't gotten to the nvidia drivers yet. Next on the list :) My graphics is working, but not utilizing the nvidia drivers yet.
Good luck!

---

### Post by peGGi on 2011-12-06
Ok I got it sorted... I think.

Before that, just to mention that Ubuntu Studio is only available as an alternate image, so you can't boot it as a Live CD/USB.  I did not know this.  But I couldn't even get to the install menu anyway in 64-bit.

I kind of managed to figure it out based on staticd's solution:[http://ubuntuforums.org/showthread.php?p=11497240#post11497240](http://ubuntuforums.org/showthread.php?p=11497240#post11497240)  I couldn't fully use this solution because he/she appears to be starting from Ubuntu, whereas I'm still on Windows.  So my method is for creating a Live USB from a Windows machine.

Oh - I'm trying 11.10 now as opposed to 11.04, but I had the exact same problem with the Live CD for 11.10.  

I downloaded Ubuntu 64-bit 10.04.  I also downloaded Ubuntu 64-bit 11.10.  

I then created a Live USB for 10.04 using UNetBootIn.  

I extracted Ubuntu 64-bit 11.10 to a normal Windows folder using WinRAR.  

I opened up the folder for the Live USB in Windows Explorer.  I deleted the following folders from the 10.04 Live USB: .disk,  casper, dists, install, pics, pool, preseed (i.e. everything apart from the isolinux folder).

I then copied all items from the 11.10 folder (so that's everything except for boot, efi and isolinux folders) into the Live USB folder.  Replace any files that have the same name.  

I was then able to boot into the Live USB and into a live Ubuntu 64-bit session.  This method also worked to allow me to get as far as the installation menu in Ubuntu Studio 64-bit.

Word of caution: this method worked to allow me to try a live session.  However, I don't know (because it's beyond my technical understanding) if messing with the .iso image like this will cause problems for an actual installation...

---

### Post by MAFoElffen on 2011-12-06
> **peGGi said:**
> Ok I got it sorted... I think.

Before that, just to mention that Ubuntu Studio is only available as an alternate image, so you can't boot it as a Live CD/USB.  I did not know this.  But I couldn't even get to the install menu anyway in 64-bit.

I kind of managed to figure it out based on staticd's solution:[http://ubuntuforums.org/showthread.php?p=11497240#post11497240](http://ubuntuforums.org/showthread.php?p=11497240#post11497240)  I couldn't fully use this solution because he/she appears to be starting from Ubuntu, whereas I'm still on Windows.  So my method is for creating a Live USB from a Windows machine.

Oh - I'm trying 11.10 now as opposed to 11.04, but I had the exact same problem with the Live CD for 11.10.  

I downloaded Ubuntu 64-bit 10.04.  I also downloaded Ubuntu 64-bit 11.10.  

I then created a Live USB for 10.04 using UNetBootIn.  

I extracted Ubuntu 64-bit 11.10 to a normal Windows folder using WinRAR.  

I opened up the folder for the Live USB in Windows Explorer.  I deleted the following folders from the 10.04 Live USB: .disk,  casper, dists, install, pics, pool, preseed (i.e. everything apart from the isolinux folder).

I then copied all items from the 11.10 folder (so that's everything except for boot, efi and isolinux folders) into the Live USB folder.  Replace any files that have the same name.  

I was then able to boot into the Live USB and into a live Ubuntu 64-bit session.  This method also worked to allow me to get as far as the installation menu in Ubuntu Studio 64-bit.

Word of caution: this method worked to allow me to try a live session.  However, I don't know (because it's beyond my technical understanding) if messing with the .iso image like this will cause problems for an actual installation...
The main graphics problem is the hybred / switched graphics...  If you have a BIOS option to switch between the GPU's, then you can turn on the NVidia chip and leave it ON... and use an NVidia driver.... Power consumption sucks. If you switch off the nvidia GPU, then you also have to rename the xorg.conf so that it can use the xserver.xorg.video.intel driver for the Intel GPU. Otherwise you'll end up at the "Purple Screen of Death."

If you don't have that BIOS Option, then you need to use Bumblebee or Ironhide to switch on the Nvidia GPU.  The plus on this option is that it also switches the drivers between the intel and nvidia when it does it.  It's still not automatic, but it works.

Third option is leave the Nvidia GPU off and settle for the Intel GPU and the lower res graphics.

---

