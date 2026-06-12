---
title: "Trying to duel boot Ubuntu alongside Window 7"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by gadgetgeek on 2011-12-27
Hi all, I currently have windows 7 installed on a 1TB hard drive and i am trying to install Ubuntu 11.10 alongside window 7 duel boot. When i run the ubuntu live cd and select the option to install Ubuntu does not pick up my windows 7 installation.

I have already partitioned my 1TB hard drive in windows and added a partition for Ubuntu.

[IMG]http://i16.photobucket.com/albums/b42/integraledave/Capture-1.png[/IMG]

I only get these 2 options when trying to install ubuntu and not the option to install alongside windows 7. (sorry for bad pics don't know how to take screenshots in ubuntu live cd.) lol

[IMG]http://i16.photobucket.com/albums/b42/integraledave/IMG_0073.jpg[/IMG]

I also went into GParted and took a screenshot. It does not show my partitions, just a lot of unallocated space.

[IMG]http://i16.photobucket.com/albums/b42/integraledave/IMG_0072.jpg[/IMG]

I don't want to kill my windows install so i am stuck at this point and would really like to install Ubuntu. I have read quite a few posts of people with similar problems to mine, but have not found a straight forward answer.

Any help would be much appreciated.

Many Thanks

Gadgetgeek :D

---

### Post by OrangeCrate on 2011-12-27
Check what you did against these instructions...

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu)

---

### Post by darkod on 2011-12-27
Also, go into win7 and delete the partition you created for ubuntu. Ubuntu doesn't install on ntfs. Leave the space as unallocated (unpartitioned).

But this has nothing to do with not recognizing the win7 installation. Gparted usually shows the whole disk as unallocated when there is some error or corruption in the partition table and because of that it can't specify what partitions exist. Windows ignores some of these errors so it might look OK from windows, but linux doesn't.

Programs useful for reading the partitions and recovering partition tables are testdisk and fixparts for example.
But as with any partition tools, BE CAREFUL what you do. Nothing to be scared of, but be careful what you do. Just google testdisk and fixparts and the websites have good tutorials.

---

### Post by gadgetgeek on 2011-12-27
Hi guys thanks for you help.

Ok i've managed to download fixparts windows version.

This is where i get stuck. I click on the fixparts file and i get cmd terminal window open up and i'm stuck what to type in the terminal.

[IMG]http://i16.photobucket.com/albums/b42/integraledave/Capture1-1.png[/IMG]

Does anyone have any idea?

Many thanks

Gadgetgeek

---

### Post by darkod on 2011-12-27
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Look at the Launching Fixparts part. Since you have only one hdd the device is /dev/sda.

In linux you would start in terminal with:
sudo fixparts /dev/sda

but in windows it seems you first start the program and then enter /dev/sda when it asks for device name.

---

### Post by gadgetgeek on 2011-12-27
hmmm fixparts does not seem to want to run correctly in windows GGGRRRAAAAAA

or i'm doing something seriously wrong ? :-(

---

### Post by darkod on 2011-12-27
In win7 instead of double click you might need to use right-click Run As Administrator. But even with that, it might not work properly because you are running windows from the same disk, it's in use.

Another option, I prefer, is booting in live mode with the ubuntu cd (Try Ubuntu option), and install fixparts. Try running it with:
sudo fixparts /dev/sda

In live mode you can literary use:
sudo apt-get install fixparts

it's only temporary until you restart the live session anyway. I think you should be able to install it with apt-get (never needed to use fixparts).

---

### Post by darkomano on 2011-12-27
You should delete the Ubuntu partition you have created from Windows 7 with the help of Disk Management.
 
Then install Ubuntu to this newly unallocated partition. Install Ubuntu with option for GRUB to be installed to partition boot record (PBR) - NOT MBR ! 
 
As you have a "System Reserved" 100 MB partition do not touch it - it has Windows 7 boot loader and config data stored !
 
Then download [Visual BCD Editor]("http://www.boyans.net") - run it and create a "BootSector loader". See on site help how to get partition boot record from Ubuntu with "dd utility for Windows" and attach to created boot sector loader.
 
This way you will have a dual-boot menu controled by Windows boot manager.
 
(Usually GRUB installation is to MBR and the dual-boot menu is controled by GRUB).

---

### Post by darkod on 2011-12-28
> **darkomano said:**
> You should delete the Ubuntu partition you have created from Windows 7 with the help of Disk Management.
 
Then install Ubuntu to this newly unallocated partition. Install Ubuntu with option for GRUB to be installed to partition boot record (PBR) - NOT MBR ! 
 
As you have a "System Reserved" 100 MB partition do not touch it - it has Windows 7 boot loader and config data stored !
 
Then download [Visual BCD Editor]("http://www.boyans.net") - run it and create a "BootSector loader". See on site help how to get partition boot record from Ubuntu with "dd utility for Windows" and attach to created boot sector loader.
 
This way you will have a dual-boot menu controled by Windows boot manager.
 
(Usually GRUB installation is to MBR and the dual-boot menu is controled by GRUB).

And the reason for all of this is? Simply not to use grub and instead use a bootloader which by default (without third party software) can't boot any other OS?

---

### Post by gadgetgeek on 2011-12-28
Thanks for you input guys :-) If i get time today i will try and boot ubuntu live cd and try and run fix parts from there.

---

### Post by darkomano on 2011-12-28
> **darkod said:**
> And the reason for all of this is? Simply not to use grub and instead use a bootloader which by default (without third party software) can't boot any other OS?
 
1. It is not correct that GRUB is not used. 
2. Windows 7 boot manager can boot any OS.
3. There is no third party software involved in the booting.
4. **Third party software only configures BCD** (Boot Configuration Data)
 
The proposed booting goes like this:
 
**(This is standard**) Windows MBR -> Windows PBR -> bootmgr (Windows 7 boot manager -> 
PBR of Ubuntu (GRUB2 first stage) -> 
(**This is standard**) Ubuntu bootsequence as usual after first stage.
 
It is really strange that Windows 7 boot capabilities are not widely known.
 
Windows holds **only** 90% of OS market and is de facto standard - I am not responsible for the design and implementation of Windows or any other Microsoft product :)
 
GRUB based OS's are more flexible in boot requirements so it is better to let Windows be in control. This is only a private opinion based on experience from both worlds (Windows and Linux).

---

### Post by darkod on 2011-12-28
> **darkomano said:**
> 1. It is not correct that GRUB is not used. 
2. Windows 7 boot manager can boot any OS.
3. There is no third party software involved in the booting.
4. **Third party software only configures BCD** (Boot Configuration Data)
 
The proposed booting goes like this:
 
**(This is standard**) Windows MBR -> Windows PBR -> bootmgr (Windows 7 boot manager -> 
PBR of Ubuntu (GRUB2 first stage) -> 
(**This is standard**) Ubuntu bootsequence as usual after first stage.
 
It is really strange that Windows 7 boot capabilities are not widely known.
 
Windows holds **only** 90% of OS market and is de facto standard - I am not responsible for the design and implementation of Windows or any other Microsoft product :)
 
GRUB based OS's are more flexible in boot requirements so it is better to let Windows be in control. This is only a private opinion based on experience from both worlds (Windows and Linux).

I don't want to get into any large argument. I am aware how the boot process goes. The point is that the OP has a problem with the partition table, and not with the bootloader. Your post doesn't help him at all solving the partition table issue, instead just giving instructions how to use windows bootloader chainloaded to grub2 that he didn't even ask for.

---

### Post by gadgetgeek on 2011-12-28
Many thanks darkod, I am now successfully duel booting win7 64bit and ubuntu 64bit.

Incase anyone has the same problem as me, this is what i did to fix my problem:

I booted from the ubuntu live cd.
Downloaded fixparts from website [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/) using firefox.
Installed by double clicking on the downloaded file.
Opened up terminal and typed "sudo fixparts /dev/sda" which ran the file.
And was greeted with this:

NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):

I simply typed "y" then hit enter.
Then typed "q" to exit.

I then restarted my pc to see if windows still booted and it did no problem :-)

So i popped in my ubuntu live cd and clicked "Install Ubuntu" and was greeted with 3 options now.

I chose to "install alongside window 7" and ubuntu did its own thing and installed ubuntu alongside windows all very easy 
:-) 

Now the fun begins :-)

Thanks

gadgetgeek

---

### Post by darkod on 2011-12-28
Glad you got it working. Please mark the thread as SOLVED, you can do that in Thread Tools above the first post.

---

