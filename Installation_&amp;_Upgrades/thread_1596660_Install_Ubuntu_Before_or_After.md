---
title: "Install Ubuntu Before or After?"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Alpha Axl on 2010-10-14
Hi all, happy to be registered!

I just bought a new little PC for Ubuntu (10.10) testing (new to Linux)...

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=A180-0242](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=A180-0242)

...and I was just wondering how to approach the installation when I get home today.  It has Win7 on it, so I'd love to dual-boot, but I wasn't sure if I should go through the Windows installation first, or just plug in my USB drive (already made boot) and just install Ubuntu before anything.  I just figured that installing Ubuntu before anything would make everything run a lot smoother.

I had a friend run me through dual-booting WinXP and Ubuntu on my piece of crap netbook and surprisingly it runs everything in Ubuntu (even the Desktop Cube smoothly), but I just don't want to mess anything up when I go through it solo.

Any help would be greatly appreciated!  Thank you!

---

### Post by Megaptera on 2010-10-14
Hi,
Install Ubuntu after Windows. The Windows boot won't 'see' Ubuntu if you put Windows on second, but Ubuntu 'Grub' will 'see' Windows if you put Ubuntu on second.

You will probably need to make some 'free space' on the partition first by using the disc management tool in Windows.

---

### Post by irv on 2010-10-14
> **Alpha Axl said:**
> Hi all, happy to be registered!

I just bought a new little PC for Ubuntu (10.10) testing (new to Linux)...

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=A180-0242](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=A180-0242)

...and I was just wondering how to approach the installation when I get home today.  It has Win7 on it, so I'd love to dual-boot, but I wasn't sure if I should go through the Windows installation first, or just plug in my USB drive (already made boot) and just install Ubuntu before anything.  I just figured that installing Ubuntu before anything would make everything run a lot smoother.

I had a friend run me through dual-booting WinXP and Ubuntu on my piece of crap netbook and surprisingly it runs everything in Ubuntu (even the Desktop Cube smoothly), but I just don't want to mess anything up when I go through it solo.

Any help would be greatly appreciated!  Thank you!

Neat looking little PC!
The best way to install Ubuntu Linux is to boot the install (I believe in your case would be the USB drive). I have only installed from Live CD's. Just install along side Win7 and chose run side by side with Win7. After you reboot, you will have a grub menu come up and Ubuntu will be the default OS, you can arrow down to Win7 anytime you want to boot into it. If you want Win7 to boot first you can change it by going to: System> Administration> Startup-Manager and change the drop down selection under the boot options.

---

### Post by Alpha Axl on 2010-10-14
Okay, thanks.  My friend mentioned something about using PerfectDisk to arrange everything before as well?  Or would I be okay to just make the partition going through Windows?

---

### Post by irv on 2010-10-14
> **Megaptera said:**
> Hi,
Install Ubuntu after Windows. The Windows boot won't 'see' Ubuntu if you put Windows on second, but Ubuntu 'Grub' will 'see' Windows if you put Ubuntu on second.

You will probably need to make some 'free space' on the partition first by using the disc management tool in Windows.
I would like to make one point to your post, I never freed up space before I installed Ubuntu. I always let the install grab a piece of the hard drive and it always gave me what I needed. Here is a screen shot of my hard drive.
 [ATTACH]172325[/ATTACH]
The 72 Gib is where I keep my data.

---

### Post by Aerodynamic on 2010-10-14
Just boot up the install CD, one of the options in the install process is "run side by side with windows"

You don't need to change the partitions before in windows, because you will have the opportunity to do this in the install process if you want..

---

### Post by Megaptera on 2010-10-14
I agree with Irv too, you can leave it to Ubuntu to do a side-by-side install if Windows is installed.

Useful guide here with screenshots:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

... usually no problems but back up all your docs, pics, vids etc to external media before you start.

---

### Post by perspectoff on 2010-10-14
I am assuming you have a retail boxed version of Windows, then?

A retail boxed version of Windows will install to a pre-created partition.

An OEM version of Windows often installs to the entire hard drive, depending on the vendor (and the agreement between Microsoft and that vendor). This is a ploy to ensure that Windows monopolizes your hard drive. 

If you are using a retail boxed version, I recommend creating your Windows NTFS partition first, using the GParted utility found on the Ubuntu LiveCD (or LiveUSB). Then you can choose the size of the NTFS partition that you want to devote to Windows and not leave it up to chance (mine is 100 Gb, for example).

You can leave the remainder of the hard drive as free space, if you'd like, if you want to devote the rest of the hard drive to Ubuntu. (Alternatively, you can also create an ext4 partition of the size you desire, and then Ubuntu can be manually installed into that partition.) The Ubuntu installer allows you to automatically install to the free space (I think as "install alongisde other OS"), or you can choose a manual install into a partition you have created with GParted. 

Note that you must also have a linuxswap partition (about 2 Gb) for Ubuntu to work, so if you create partitions manually, make sure you create a linuxswap partition as well.

If using the "free space" method, the Ubuntu installer will create both the Ubuntu partition and the linuxswap partition for you in appropriate sizes. 

The reason to install Windows first is not a hard and fast rule, but it avoids a lot of problems. The Windows bootloader does not recognize Ubuntu Linux OSs very well, and during Windows installation the Master Boot Record (MBR) is overwritten so that it indicates the Windows bootloader must be used at startup.

In contrast, the Ubuntu GRUB bootloader is able to recognize the Windows OS, and when it is installed second, both Ubuntu and Windows are able to be booted. By default, the Ubuntu installer also overwrites the MBR to point to the GRUB bootloader, but this is less problematic than allowing the MBR to point to the Windows bootloader.

Personally, I don't allow the MBR to point to either the Windows bootloader or the Ubuntu GRUB2 bootloader, but I create a small independent boot partition with its own master bootloader in it (because I trust neither the Windows bootloader nor the GRUB2 bootloader). But that is an advanced technique for power users only (and is at [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation) or [http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)).

---

### Post by Megaptera on 2010-10-14
> **irv said:**
> I would like to make one point to your post, I never freed up space before I installed Ubuntu. I always let the install grab a piece of the hard drive and it always gave me what I needed. Here is a screen shot of my hard drive.
 [ATTACH]172325[/ATTACH]
The 72 Gib is where I keep my data.

The first time I did a dual boot the guide I followed went that route so I did too, I now know one can do the 'side-by-side' method but like a lot of people I tend to stick to a method that I've been happy with in the past. I wasn't trying to sow confusion I think we posted a couple of minutes apart so we were probably both typing or replies.

---

### Post by perspectoff on 2010-10-14
> **Megaptera said:**
> The first time I did a dual boot the guide I followed went that route so I did too, I now know one can do the 'side-by-side' method but like a lot of people I tend to stick to a method that I've been happy with in the past. I wasn't trying to sow confusion I think we posted a couple of minutes apart so we were probably both typing or replies.

Yours is a good partition scheme at [http://ubuntuforums.org/attachment.php?attachmentid=172325](http://ubuntuforums.org/attachment.php?attachmentid=172325).

You have 3 primary partitions, each with NTFS. Your fourth partition is an extended partition, in which you have created two logical partitions. (An almost unlimited number of logical partitions can be created in the extended partition). One of those two logical partitions is the linuxswap partition, and the other is the ext4 partition for Ubuntu.

I think that is an excellent configuration.

I generally put my extended partition as the last partition (whereas you have put it as your third partition), but that is my personal choice so that I can manipulate the extended partition more easily.

For years I have advocated a boot partition. It amuses me that in your configuration, the partition designated /dev/sda1 is actually a boot partition that a recent version of Windows has created. (Older versions of Windows did not create their own boot partition.) It appears, therefore, that Windows is now also putting its bootloader in its own boot partition. When Windows installs, the MBR is overwritten, then, so that it points to the Windows bootloader in /dev/sda1.

Ubuntu keeps its won GRUB2 bootloader within its own partition. It does not install a separate boot partition by default. It then overwrites the MBR again to point to its own partition.

MBR wars, in effect.

The bottom line is that if you already have a Windows installation with a Windows boot partition (in the example /dev/sda1) and a Windows OS partition (in the example /dev/sda2), you had better leave both of them alone. You shouldn't place your own bootloader into the Windows boot partition. Windows is finicky that way.

If you want your own boot partition, create it as the third primary partition. You can always use a logical partition of the extended partition as your data partition (instead of wasting one of the three primary partitions for your data partition).

Remember, it is the MBR that determines which bootloader will be started, and it is the MBR that records where the first bootloader is located.

---

### Post by Cavsfan on 2010-10-14
I have some experience installing Ubuntu with Windows 7 and I would advise you to just use windows 7 disk manager to free up some space for your Ubuntu.
Just type this in the little search area above the start button "**disk man**" and it should show up. Click on it and it will show you your partitions. You will see your 
windows 7 partition and just right click on it and then click on "shrink" and after a few it will tell you how much room you can free up. If it is enough just plug the 
CD/DVD in and reboot (Hopefully your bios is setup to install from CD/DVD first and if not change it. Then click the bottom option (manual I believe) 
and you will see your unused free space. Make 2024 MB of that swap and the rest ext4 with the '/" and let it install. I did a clean install 2 days ago and 
it went pretty fast. I would make both Physical partitions unless that will make more than 4 (max) if so, just make the swap file a logical partition.

You only have 160GB to work with so choose wisely grasshopper LOL.

Then if you want you can check out the tutorial in my signature as it is really good for dual booting.
I was wanting Windows to be the default for my wife and son and had to change the default line every time a new kernel was added. The tutorial alleviates the need for that. 
It make it maintenance free and you can have a nice boot up splash screen too.

---

### Post by perspectoff on 2010-10-14
> **Cavsfan said:**
> I have some experience installing Ubuntu with Windows 7 and I would advise you to just use windows 7 disk manager to free up some space for your Ubuntu.
Just type this in the little search area above the start button "**disk man**" and it should show up. Click on it and it will show you your partitions. You will see your 
windows 7 partition and just right click on it and then click on "shrink" and after a few it will tell you how much room you can free up. If it is enough just plug the 
CD/DVD in and reboot (Hopefully your bios is setup to install from CD/DVD first and if not change it. Then click the bottom option (manual I believe) 
and you will see your unused free space. Make 2024 MB of that swap and the rest ext4 with the '/" and let it install. I did a clean install 2 days ago and 
it went pretty fast. I would make both Physical partitions unless that will make more than 4 (max) if so, just make the swap file a logical partition.

You only have 160GB to work with so choose wisely grasshopper LOL.

Then if you want you can check out the tutorial in my signature as it is really good for dual booting.
I was wanting Windows to be the default for my wife and son and had to change the default line every time a new kernel was added. The tutorial alleviates the need for that. 
It make it maintenance free and you can have a nice boot up splash screen too.

I agree with shrinking the partition (on which a pre-installed version of Windows is installed) from within Windows itself, as you described. However, you can only get so much free space with this method, due to the MFT (Master File Table) problem in Windows. On my system, I could only get about 50 Gb free with this method. To move the MFT, I had to use PerfectDisk (which is able to move the MFT) so I could get over 200 Gb free. 

However, when Windows is installed into an already created partition, it fits itself into that partition automatically, no matter what size it is. There is no worrying about the MFT placement. If this user has that option, I would therefore do that rather than installing Windows (to the whole disk, for example) with the intention of shrinking it later.

(However, looking at his link for the eMachines desktop, it says Windows 7 is pre-installed, so that my advice appears moot. The user likely does have to shrink his windows partition to make free space available, despite the implication of his OP. Further, it looks like he has an OEM copy of Windows 7, which does not generally allow installling to a new partition but usually automatically installs to the entire hard drive, again requiring the Windows partition to later be shrunk to free up space.)

As for your dual-booting tutorial, that is enough to scare a newbie away from Ubuntu forever, lol!

In general, it is not necessary anyway. As long as you don't remove Ubuntu from your computer, Grub2 is fairly self-maintaining. Of course, the inherent problem with relying on Grub2 (installed in the Ubuntu partition) is that if a user ever decides to remove Ubuntu, their computer will no longer boot until the MBR is again changed to point to the Windows boot partition. 

MBR wars, indeed.

---

### Post by Megaptera on 2010-10-14
Hi perspectoff,
That screenshot is that of irv's set up not mine.

I don't have dual boot, my set up is:


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             5.5G  2.9G  2.4G  56% /
none                  982M  316K  981M   1% /dev
none                  989M 1020K  988M   1% /dev/shm
none                  989M   96K  989M   1% /var/run
none                  989M     0  989M   0% /var/lock
none                  989M     0  989M   0% /lib/init/rw
/dev/sda7             140G  951M  132G   1% /home
/dev/sda1              92M   30M   57M  35% /boot

---

### Post by Alpha Axl on 2010-10-14
My Windows installation will be pre-installed on the PC most likely, with no disc.

My friend mentioned PerfectDisk, but is there a well known tutorial out there for doing something like this with it?

Sorry for all the questions...just wanna make sure my Linux experience is off to a good start! >_<

---

### Post by Megaptera on 2010-10-14
This talks about Ubuntu 9.10 but the system is the same for 10.04

[http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/](http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/)

no need for 'Perfect Disc' with this guide.

---

### Post by Alpha Axl on 2010-10-14
> **Megaptera said:**
> This talks about Ubuntu 9.10 but the system is the same for 10.04

[http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/](http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/)

no need for 'Perfect Disc' with this guide.
10.10 as well?  That's the one I'll be installing.

---

### Post by irv on 2010-10-14
There were some great post in this thread, I just read them all. I did something yesterday I thought I would never try, and it worked great. See this [thread]("http://ubuntuforums.org/showthread.php?t=1595534").
I deleted Peppermint OS off my HD and move things around and made my HD look like the screen shot I posted earlier. I got a lot of help from plucky on this forum. I did it all with gparted off the live CD. I never touched the windows partition but I did move the complete Ubuntu OS to another part of the partition so I could get at the unallocated space and recover it for my data storage. I keep all my data on a NTFS partition so I can get to it from Linux or Windows. I also keep data in Dropbox and Ubuntuone on the Internet.
By the way what I did I wouldn't recommend a new user try.

---

### Post by Cavsfan on 2010-10-14
> **perspectoff said:**
> I agree with shrinking the partition (on which a pre-installed version of Windows is installed) from within Windows itself, as you described. However, you can only get so much free space with this method, due to the MFT (Master File Table) problem in Windows. On my system, I could only get about 50 Gb free with this method. To move the MFT, I had to use PerfectDisk (which is able to move the MFT) so I could get over 200 Gb free. 

However, when Windows is installed into an already created partition, it fits itself into that partition automatically, no matter what size it is. There is no worrying about the MFT placement. If this user has that option, I would therefore do that rather than installing Windows (to the whole disk, for example) with the intention of shrinking it later.

(However, looking at his link for the eMachines desktop, it says Windows 7 is pre-installed, so that my advice appears moot. The user likely does have to shrink his windows partition to make free space available, despite the implication of his OP. Further, it looks like he has an OEM copy of Windows 7, which does not generally allow installling to a new partition but usually automatically installs to the entire hard drive, again requiring the Windows partition to later be shrunk to free up space.)

As for your dual-booting tutorial, that is enough to scare a newbie away from Ubuntu forever, lol!

In general, it is not necessary anyway. As long as you don't remove Ubuntu from your computer, Grub2 is fairly self-maintaining. Of course, the inherent problem with relying on Grub2 (installed in the Ubuntu partition) is that if a user ever decides to remove Ubuntu, their computer will no longer boot until the MBR is again changed to point to the Windows boot partition. 

MBR wars, indeed.

The MFT is a lot better in Windows 7 than it was in Vista. I just had to delete the $usnjrnl file which is a huge file that doesn't defragment
and it is at the end of the drive making it impossible to "shrink" the drive". I defragmented it as much as I could with Defraggler (which 
is better than windows defrag method) and then deleted the $usnjrnl file with this command (in Windows 7 of course).  ```
FSUTIL USN DELETEJOURNAL /D C:
```It is a re-generating file so no real harm is done, but after I did that I was able to free up 100+GB for Ubuntu.
You loose all restore points, but that is not an issue on a new PC and I didn't care either.

This will make it to where he can shrink the windows partition.

And as for my tutorial, if you can read and follow instructions, I don't see a problem. I was a bit intimidated myself at first, but made the changes 
with a fellow forum member **Ranch Hand'**s help. And yes it does make a difference if you want to have windows as the default.  I have a son 
who plays some games that depend on Directx 10, which cannot be run under wine and my wife is used to windows also. Plus I like to stay fresh 
on Windows in order to help friends with their issues.

So, if you dual boot and have something other than the top option Ubuntu as your default, my tutorial makes it maintenance free. As I stated earlier I 
had to change the default line for Windows every time a new kernel was added and that got tiresome pretty quickly.

---

### Post by Cavsfan on 2010-10-14
> **Alpha Axl said:**
> 10.10 as well?  That's the one I'll be installing.

Alpha Axl, you should be able to free up enough space with Disk Management in windows with the info. from my first post and if you cannot shrink
the partition enough, just use the command in a DOS window from my 2nd post. It will do no harm and should allow Disk Management in Windows 
to be able to "shrink" your Windows partition and allow you to install Ubuntu 10.10.

!0.10 is a little bit different than 9.10, just choose the bottom option "specify partitions Manually (advanced).
Here is exactly what 10.10 looks like to install - I did it 2 days ago.

[[COLOR=blue]_Installing Ubuntu 10.10_[/COLOR]]("http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml")

---

### Post by perspectoff on 2010-10-14
> **Megaptera said:**
> This talks about Ubuntu 9.10 but the system is the same for 10.04

[http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/](http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/)

no need for 'Perfect Disc' with this guide.

That's not a very transparent method. What is exactly happening? Is Wubi being installed within Windows? In that case, Ubuntu will not be stored in its own partition but within the Windows partition as a giant file.

That can cause problems for advanced users who might want other OS's, multiple installations, and other situations as well.

In a Wubi installation, is the Master File Table not a limitation?

I mean, if the hard drive is 100 Gb, and the MFT lives at 70 Gb on the hard drive, can you create a Wubi file greater than 30 Gb or can the maximum Wubi file size still only be 30 Gb (same limitation as with a new partition if the MFT is not moved)?

I would like to point out that the best tutorial for shrinking the Windows partition (and moving the MFT) is also from this site:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by perspectoff on 2010-10-14
> **Cavsfan said:**
> The MFT is a lot better in Windows 7 than it was in Vista. I just had to delete the $usnjrnl file which is a huge file that doesn't defragment
and it is at the end of the drive making it impossible to "shrink" the drive". I defragmented it as much as I could with Defraggler (which 
is better than windows defrag method) and then deleted the $usnjrnl file with this command (in Windows 7 of course).  ```
FSUTIL USN DELETEJOURNAL /D C:
```It is a re-generating file so no real harm is done, but after I did that I was able to free up 100+GB for Ubuntu.
You loose all restore points, but that is not an issue on a new PC and I didn't care either.

This will make it to where he can shrink the windows partition.

And as for my tutorial, if you can read and follow instructions, I don't see a problem. I was a bit intimidated myself at first, but made the changes 
with a fellow forum member **Ranch Hand'**s help. And yes it does make a difference if you want to have windows as the default.  I have a son 
who plays some games that depend on Directx 10, which cannot be run under wine and my wife is used to windows also. Plus I like to stay fresh 
on Windows in order to help friends with their issues.

So, if you dual boot and have something other than the top option Ubuntu as your default, my tutorial makes it maintenance free. As I stated earlier I 
had to change the default line for Windows every time a new kernel was added and that got tiresome pretty quickly.

Wow! Cool. I hadn't realized that MS had changed their MFT methodology. Time to go experimenting...

---

### Post by perspectoff on 2010-10-14
> **Cavsfan said:**
> 

And as for my tutorial, if you can read and follow instructions, I don't see a problem. I was a bit intimidated myself at first, but made the changes 
with a fellow forum member **Ranch Hand'**s help. And yes it does make a difference if you want to have windows as the default.  I have a son 
who plays some games that depend on Directx 10, which cannot be run under wine and my wife is used to windows also. Plus I like to stay fresh 
on Windows in order to help friends with their issues.

So, if you dual boot and have something other than the top option Ubuntu as your default, my tutorial makes it maintenance free. As I stated earlier I 
had to change the default line for Windows every time a new kernel was added and that got tiresome pretty quickly.

I stand corrected. I see your point. I forget because I use Grub legacy as my master bootloader (in a boot partition) which is so much simpler to work with that I had forgotten how difficult GRUB2 is to customize. My Grub Legacy bootloader just chainloads Grub2, so I never have to fiddle with Grub2 (thank dog) and leave it as a self-maintaining module.

But I do see the problem if you rely on Grub2 and want Windows as the default OS.

---

### Post by Alpha Axl on 2010-10-14
I'm heading home now to try things out... I'll let you all know how it goes!  Thanks so much for all the valuable input.

Seems like a great community here!

---

### Post by Cavsfan on 2010-10-14
> **perspectoff said:**
> I stand corrected. I see your point. I forget because I use Grub legacy as my master bootloader (in a boot partition) which is so much simpler to work with that I had forgotten how difficult GRUB2 is to customize. My Grub Legacy bootloader just chainloads Grub2, so I never have to fiddle with Grub2 (thank dog) and leave it as a self-maintaining module.

But I do see the problem if you rely on Grub2 and want Windows as the default OS.

You should drop legacy Grub as Grub2 has made huge improvements and it was very easy to modify as I went by my own tutorial after a clean install.
All you have to do is copy and paste the commands, except that you have to get that UUID right for Windows or you won't be getting back into Windows 
until you do.  And it doesn't matter which Windows, it will work for XP, Vista, and 7; I wouldn't go as far as to say ME or 98, but hopefully there are no more of those around.
But everything you need is provided to have a nice background for your bootup screen in addition to not have to maintain it every time a kernel is installed. I may have 
gotten a bit wordy, but I thought everything in there was necessary.

Here is a tutorial that could help you get rid of your legacy Grub that was written by **drs305** and he is one of the Grub authorities around here. He knows his stuff!
[[COLOR=blue]_drs305 GRUB2 Tutorial_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

> **Alpha Axl said:**
> I'm heading home now to try things out... I'll let you all know how it goes!  Thanks so much for all the valuable input.

Seems like a great community here!

Good luck! If you have any trouble there are always people willing to help in this forum. Sometimes we end up stepping on each others toes trying to help. LOL!

---

### Post by Alpha Axl on 2010-10-14
Partitioned, installed, and everything is running perfectly fine, except one thing.

Whenever I go to restart or shut off the computer (in Ubuntu obviously), it looks like it's going to shut off, shows the Ubuntu logo, and then it stops at a blank purple screen.  At that point I'm forced to hold the power button for 5 seconds to actually turn the computer.

Anyone else ever have this problem?  Other than just that everything seems perfect.  Thanks so much for all the help everyone!  Really means a lot. =P

---

### Post by Alpha Axl on 2010-10-15
Sorry to double post, but here's the message (or part of) that I get every time I log in and out now...

[http://img686.imageshack.us/img686/6793/imag0211r.jpg](http://img686.imageshack.us/img686/6793/imag0211r.jpg)

...also sorry for the quality. >_<   Any ideas?  =/

---

### Post by Megaptera on 2010-10-15
> **perspectoff said:**
> That's not a very transparent method. What is exactly happening? Is Wubi being installed within Windows? In that case, Ubuntu will not be stored in its own partition but within the Windows partition as a giant file.

That can cause problems for advanced users who might want other OS's, multiple installations, and other situations as well.

In a Wubi installation, is the Master File Table not a limitation?



Perspectoff please read the link I gave .... it is nothing to to with Wubi.

Please can we keep in mind that the o/p does not appear to be very experienced and some of the replies here are very tech and raise interesting points and personal achievements that may be a bit too complex for this thread? :)

---

### Post by Alpha Axl on 2010-10-15
Yeah, at this point I just want Ubuntu 10.10 to run smoothly without login/logout errors like I posted above.  From there I'll start to dig deeper. =P

---

### Post by Megaptera on 2010-10-15
Hi,
The link I gave in answer #5 of this thread might help:

[http://ubuntuforums.org/showthread.php?t=1596567](http://ubuntuforums.org/showthread.php?t=1596567)

Here's that link:  [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Alpha Axl on 2010-10-15
Oh okay thanks.  Would that apply to the shutting down part as well?  It pressed Esc on shutdown to see what's going on and I saw Checking update something before the text went away. >_<

---

### Post by Cavsfan on 2010-10-15
The last 2 or 3 times I installed Ubuntu at the end when it said it was restarting, it never did. I sat there for a long time with just a purple 
screen and eventually pressed the reset button to restart it. But, after that first time it works every time. Is that your issue? 
Or did you restart it a few times with the same situation?

On a brand new install, I doubt you would need to mess with Plymouth. 

Did you install the desktop version 32 bit or 64 bit? Hopefully it was just like my issue - the 1st reboot after installing.

---

### Post by Alpha Axl on 2010-10-15
I've restarted plenty of times and it happens each time.  When I installed Ubuntu I did the 3rd party software and download updates options...should I try not doing that and just going step by step to identify the problem?  I'm also not sure if I restarted before I went ahead and did update manager and got all the kernels...I'll probably just do a fresh install again when I get home and take my time with each step.

Oh and I installed the i386 version even though I have an amd64, but I've been told countless times that it wouldn't be a problem and it might help it run more efficiently that way.

---

### Post by Cavsfan on 2010-10-15
> **Alpha Axl said:**
> I've restarted plenty of times and it happens each time.  When I installed Ubuntu I did the 3rd party software and download updates options...should I try not doing that and just going step by step to identify the problem?  I'm also not sure if I restarted before I went ahead and did update manager and got all the kernels...I'll probably just do a fresh install again when I get home and take my time with each step.

Oh and I installed the i386 version even though I have an amd64, but I've been told countless times that it wouldn't be a problem and it might help it run more efficiently that way.

Oh, I have been using the 64 bit version ever since I got my PC almost 2 years ago and there is no problem with it. The talk about it is way 
overblown! I would go for the 64bit version and I definitely would reinstall it since it is so new. I did not click "download updates while installing" 
as I didn't feel comfortable with it. Like I said I sat there for about 10 minutes after it said it was going to restart after it finished installing and 
nothing happened so I hit the reset button and everything was OK after that. And occasionally I see messages like the one you posted 
come across the screen, but they are not there long enough for me to read them and they go away. Hopefully all will be good on your 2nd try!
Just go by the manual option and delete your swap and ext4 and re-create them and it should be fine.

---

### Post by Alpha Axl on 2010-10-15
As far as the correct swap, drives, etc...does this look right?

[http://img508.imageshack.us/img508/4301/ubuntu1010installationl.jpg](http://img508.imageshack.us/img508/4301/ubuntu1010installationl.jpg)

...that's what I followed from How-To Geek.  I honestly had no idea what I was doing (complete n00bie), and just made the sda2 and sda5 drive spaces the same space and type, with my Ubuntu install on the rest of my free space.

Does it matter if they weren't exactly sda2 and sda5?  I know I had a different number on mine due to the amount of recovery disks included with the new PC.

Thanks so much for the continued help!  =)

---

### Post by Cavsfan on 2010-10-15
> **Alpha Axl said:**
> As far as the correct swap, drives, etc...does this look right?

[http://img508.imageshack.us/img508/4301/ubuntu1010installationl.jpg](http://img508.imageshack.us/img508/4301/ubuntu1010installationl.jpg)

...that's what I followed from How-To Geek.  I honestly had no idea what I was doing (complete n00bie), and just made the sda2 and sda5 drive spaces the same space and type, with my Ubuntu install on the rest of my free space.

Does it matter if they weren't exactly sda2 and sda5?  I know I had a different number on mine due to the amount of recovery disks included with the new PC.

Thanks so much for the continued help!  =)

I would take out the home and increase the swap to 2024 MG and leave the rest for / ext4.
Other than that it looks good, but the fact that it's only 14GB might be an issue.
I have a 2024MB swap and almost 100,000MB (100GB) for my / ext4. And I have run pretty close to out of room!
Luckily I have a 1TB USB drive I backup to.
You might want to go with the netbook edition, but I am not familiar with that.

I myself, don't know if you can pull this off with 14GB.
Perhaps someone with more experience with netbooks or small drives could help out here.

---

### Post by Alpha Axl on 2010-10-15
What exactly is the /home for anyway?  Just a custom setting they have?

I actually have 40GB dedicated, that's just a image from the site.

---

### Post by Cavsfan on 2010-10-15
> **Alpha Axl said:**
> What exactly is the /home for anyway?  Just a custom setting they have?

I actually have 40GB dedicated, that's just a image from the site.

/home is just your user location for storing stuff - documents, music, videos, etc. and I have heard it is good to have a separate partition for it 
because then when you do another clean install, it will not touch your /home partition. I don't do that myself and if you do that you may have 
some old stuff left over from a previous installation. I would get confused myself. 

I have my 500GB disk setup like this 2MB (2048K) as swap and the rest of about 100GB as / ext4 and that is all you really need unless you get a lot 
more sophisticated than I am! LOL!
Here is what my disk looks like with Windows 7 and Maverick Meerkat:
(and the sizes changed on their own a bit after I set it up and installed)

[[IMG]http://ompldr.org/tNXRxbA[/IMG]]("http://ompldr.org/vNXRxbA")

Bottom line is 40GB aught to be enough if you have other disks to store media, etc. on.
I can't figure out how to recoup that 1MB that is shown as unused, but what's 1MB now days? Not much.

---

### Post by Alpha Axl on 2010-10-15
Just re-installed everything doing it offline and it still seems to hang =(

If it helps I have a NVIDIA GeForce 9200.

---

### Post by Alpha Axl on 2010-10-15
Sorry again for the double-post, but I just tried the 64-bit install for the hell of it, and everything turns on/shuts down perfectly fine, but my wireless doesn't seem to be working.

Are there any files I could maybe copy over to a USB and load after installing to fix it?  I'm almost there! XD

---

### Post by irv on 2010-10-16
> **Alpha Axl said:**
> Sorry again for the double-post, but I just tried the 64-bit install for the hell of it, and everything turns on/shuts down perfectly fine, but my wireless doesn't seem to be working.

Are there any files I could maybe copy over to a USB and load after installing to fix it?  I'm almost there! XD

Plug in a network cable to get connected to the Internet then go to System>Administration> Additional Drivers, It should fine the driver for your wifi card. Just select it. Then you should be able to unplug the cable and the wifi should work.

---

### Post by Cavsfan on 2010-10-16
> **Alpha Axl said:**
> Sorry again for the double-post, but I just tried the 64-bit install for the hell of it, and everything turns on/shuts down perfectly fine, but my wireless doesn't seem to be working.

Are there any files I could maybe copy over to a USB and load after installing to fix it?  I'm almost there! XD

Good! Must have been because you were trying to install a 32 bit OS on a 64 bit box! :)
I always go for the 64 bit myself.

> **irv said:**
> Plug in a network cable to get connected to the Internet then go to System>Administration> Additional Drivers, It should fine the driver for your wifi card. Just select it. Then you should be able to unplug the cable and the wifi should work.

I am glad you know what to do as I am clueless. My Internet worked as soon as I installed, but I am plugged into my router, so there is no wireless. :) 
My son's PS3 is the only thing wireless around here.

---

### Post by Alpha Axl on 2010-10-16
Tried everything to get wireless working on he 64-bit, no go. ;_;

I apparently have a Ralink WLAN RT3090 module in my PC and there are Linux drivers for it, but no matter what I do I can't seem to get it to work.  When I turn the computer on it shows my nearby wireless points for a second, and then says disconnected, so it's obviously working.

About to try to Netbook edition as much as I don't want to.

---

### Post by irv on 2010-10-16
> **Alpha Axl said:**
> Tried everything to get wireless working on he 64-bit, no go. ;_;

I apparently have a Ralink WLAN RT3090 module in my PC and there are Linux drivers for it, but no matter what I do I can't seem to get it to work.  When I turn the computer on it shows my nearby wireless points for a second, and then says disconnected, so it's obviously working.

About to try to Netbook edition as much as I don't want to.

It is sounding more and more like a firewall or security issue? Maybe someone could add some input on this. The reason I say this is because you said it "shows wireless points for a second and then says disconnected."

---

### Post by Alpha Axl on 2010-10-16
Since the topic title and situation has changed (I'm sticking with the 32-bit Desktop install that just has a shutdown problem), I'm going to start a new thread on that specifically so other members don't get confused on what the actual issue is.

Mainly because I've been bouncing around trying everything lol

---

### Post by Cavsfan on 2010-10-16
I'd stick with what you got and this thread. We'll figure it out. Never load a 32 bit OS on  a 64 bit box. :(

---

### Post by Cavsfan on 2010-10-16
See if this post doesn't help it is marked as solved. It doesn't appear to be your exact situation but, same wifi.

[[COLOR=blue]_MSI WInd U210 AMD Ralink WiFi Card HELP!!!_[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1274886&page=7")

You just need to add some sources to your sources list apparently.

---

### Post by Cavsfan on 2010-10-16
That last post might not be what you need as this PPAs are missing.
But, apparently all you need to do is install the Linux driver for your Ralink WLAN RT3090 router.

Finding the driver is another story, unless you have it on CD or something,
This is the manufacturer's website link and it goes no where.

[http://web.ralinktech.com/ralink/Home/Support/Linux.html ]("http://web.ralinktech.com/ralink/Home/Support/Linux.html")

---

### Post by Cavsfan on 2010-10-16
Found it! Here is the ppa you need to add to your sources directory:

Edit your edit software source list, enter this into terminal: **gksu gedit /etc/apt/sources.list**
Then copy and paste these 2 lines into the bottom of the file:

```
deb http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu Maverick main 
deb-src http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu Maverick main 

```And save the file and close it.

Now add the key for the ppa by entering this into terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 86F4C28E
```Then enter in terminal **sudo apt-get update && sudo apt-get upgrade**
Install the packages it finds and reboot and see if it works.

If not, I found another possible way: open this link. 
[[COLOR=blue]_PPA for Ralink RT 3090_[/COLOR]]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")

If it wants to open it with Ubuntu Software Center, let it. It should install the PPA and the driver should be available.
Enter in terminal **sudo apt-get update && sudo apt-get upgrade** and it should install the driver and you'll have to reboot, but one of these methods should work.

---

### Post by Alpha Axl on 2010-10-16
Just tried everything you listed (thanks so much for the idiot step-by-step instructions...I need them! XD) and I got this after doing the terminal update...

[I][B]Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick Release.gpg                   
Ign [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/) Maverick/main Translation-en
Ign [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/) Maverick/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick/main Sources                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick/main amd64 Packages                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick/main Sources                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick/main Sources
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) Maverick/main amd64 Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/Maverick/main/source/Sources.gz](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/Maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [/B][B][http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/Maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/dists/Maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.[/B][/I]  

...you can see that the RT3090 packages aren't found =(

---

### Post by Alpha Axl on 2010-10-16
Anyone know if this would work?

[http://www.bestbuy.com/site/Lenovo+-+Ideacentre+Q150+Desktop+/+Intel%26%23174;+Atom%26%23153;+Processor+/+2GB+Memory+/+250GB+Hard+Drive/1287497.p?id=1218247187038&skuId=1287497](http://www.bestbuy.com/site/Lenovo+-+Ideacentre+Q150+Desktop+/+Intel%26%23174;+Atom%26%23153;+Processor+/+2GB+Memory+/+250GB+Hard+Drive/1287497.p?id=1218247187038&skuId=1287497)

...just looking for a nettop type PC that will **work**. >_<

---

### Post by stockham on 2010-10-16
I expect you can make just about any PC work with dual boot...

I liked this approach: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) 
Although the actually tasks are slightly different than shown, it was a great aid..

---

### Post by Alpha Axl on 2010-10-17
I'm forced to run completely wireless as I live upstairs from the actual network area, and people are very stubborn about doing any hardwire stuff unfortunately.

I have an older desktop PC I'd love to try out and see if I can get that running good, but it doesn't have built-in wireless.  If I got one of the linksys USB wireless receivers ( [http://www.amazon.com/Wireless-USB-Network-Adapter-WUSB11/dp/B0013VH73I/ref=sr_1_5?s=electronics&ie=UTF8&qid=1287294460&sr=1-5](http://www.amazon.com/Wireless-USB-Network-Adapter-WUSB11/dp/B0013VH73I/ref=sr_1_5?s=electronics&ie=UTF8&qid=1287294460&sr=1-5) ), would those work seamlessly with Ubuntu as well?  If so, I'll run out an get one in the morning and test it on the other two PCs I have floating around. =P

---

### Post by irv on 2010-10-17
> **Alpha Axl said:**
> I'm forced to run completely wireless as I live upstairs from the actual network area, and people are very stubborn about doing any hardwire stuff unfortunately.

I have an older desktop PC I'd love to try out and see if I can get that running good, but it doesn't have built-in wireless.  If I got one of the linksys USB wireless receivers ( [http://www.amazon.com/Wireless-USB-Network-Adapter-WUSB11/dp/B0013VH73I/ref=sr_1_5?s=electronics&ie=UTF8&qid=1287294460&sr=1-5](http://www.amazon.com/Wireless-USB-Network-Adapter-WUSB11/dp/B0013VH73I/ref=sr_1_5?s=electronics&ie=UTF8&qid=1287294460&sr=1-5) ), would those work seamlessly with Ubuntu as well?  If so, I'll run out an get one in the morning and test it on the other two PCs I have floating around. =P

I went wireless at the church. I just bought some of these card and put them in all the desktops. [http://www.newegg.com/Product/Product.aspx?Item=N82E16833340009]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833340009").
It worked for me.

---

### Post by Cavsfan on 2010-10-17
Edit you sources and remove those last 2 lines I told you to add above. There is no PPA for Maverick and I don't really know how to 
tell it to us Lucid, which is the latest on that PPA. 

After you have deleted those 2 lines, enter **sudo apt-get update && sudo apt-get upgrade**
and the errors should be gone.

You might need to open up a new thread with Ralink WLAN RT3090 driver in the title.

This is kind of out of my league.
Some one will be able to figure this out. There are a lot of knowledgeable people on here.

And that bestbuy link didn't go anywhere.

---

### Post by Alpha Axl on 2010-10-19
So yesterday I gave up and decided to try it on my main PC, which I originally didn't want to do (as I'm a n00bie and didn't want to mess my main up by any chance).  This is my main...

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=G180-15634](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=G180-15634)

...I threw the 32-bit 10.10 Desktop on a USB stick, installed it, wireless worked, and all I needed was a proper shutdown...and I got it!  Ubuntu 10.10 is successfully installed on my system.  YAY.

Now I have my laptop and my 22" monitor side by side and I'm extending them. =P

The problem may have not been resolved, but I figured I'd let everyone know that I've come up with a different solution.  I actually like it a lot better this way too because my laptop runs it a hell of a lot better than that crappy nettop I got.  My friend's birthday is coming up and he still has a 512MB RAM PC with XP Home...so I'll give him the one I got. XD

Thanks again all!

---

### Post by Cavsfan on 2010-10-19
> **Alpha Axl said:**
> So yesterday I gave up and decided to try it on my main PC, which I originally didn't want to do (as I'm a n00bie and didn't want to mess my main up by any chance).  This is my main...

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=G180-15634](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=G180-15634)

...I threw the 32-bit 10.10 Desktop on a USB stick, installed it, wireless worked, and all I needed was a proper shutdown...and I got it!  Ubuntu 10.10 is successfully installed on my system.  YAY.

Now I have my laptop and my 22" monitor side by side and I'm extending them. =P

The problem may have not been resolved, but I figured I'd let everyone know that I've come up with a different solution.  I actually like it a lot better this way too because my laptop runs it a hell of a lot better than that crappy nettop I got.  My friend's birthday is coming up and he still has a 512MB RAM PC with XP Home...so I'll give him the one I got. XD

Thanks again all!

Glad you got something working well! You should mark this thread as resolved by clicking on Thread Tools at the top right and then Mark this thread as solved at the bottom of the pull down list.

Woot! Now begins the learning process! Congratulations and welcome to Ubuntu! :popcorn:

---

### Post by DougieFresh4U on 2010-10-19
> **Cavsfan said:**
> Edit you sources and remove those last 2 lines I told you to add above. There is no PPA for Maverick and I don't really know how to 
tell it to us Lucid, which is the latest on that PPA. 


You can change 'Maverick' to 'Lucid' on those 2 lines, save then 
sudo apt-get update
sudo apt-get upgrade

---

### Post by Alpha Axl on 2010-10-19
> **DougieFresh4U said:**
> You can change 'Maverick' to 'Lucid' on those 2 lines, save then 
sudo apt-get update
sudo apt-get upgrade
Tried that too actually and nothing.  =/

---

### Post by DougieFresh4U on 2010-10-19
> **Alpha Axl said:**
> Tried that too actually and nothing.  =/
 Ok, just curious what does it list in Synaptic>Settings>Repositories>Software Sources>Other Software

EDIT - I don't think the ppa is functioning at this time.

---

