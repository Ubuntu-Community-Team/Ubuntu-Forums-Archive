---
title: "Questions about creating good Ubuntu Live USB stick"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by vaul on 2011-09-10
I long wanted to satisfy that geeky itch and create USB live stick, to use  as fallback system and/or in case of emergency. 

I have got 8 Gb SanDisk stick. I did a little research, and it is often said that UNetbootin is the best to do the permanent installation. 

Is it true, or there are better tools? Does it support the 11.10 beta?

I also would not mind being able to sent some files on it from Windows/Mac devices, what file system is best to use in that case — Fat32 or NTFS?

I guess it won't make much sense to make more than one partition for 8 Gb of space, or will it?

Are there any non-trivial aspects to this whole thing?

Thanks.

---

### Post by Pariah819 on 2011-09-10
As far as I know you will only be able to partition your flash drive as FAT32.  I've done many installs of Ubuntu from Flash Drives and love it since most of my computers don't have a CD/DVD drives.  Depending on what you will want to do with the flash drive will kind of correlate to how complicated your customization will be.  I've used UNetbootin and it is probably my favorite.  You also might want to look at PenDriveLinux.com.

---

### Post by oldfred on 2011-09-10
With 8GB you have some more choices.

The standard USB flash drive install is just a reusable replacement for a CD and uses the entire drive. It is a liveCD and installer but not updateable. You then can add persistence which will let you save some files, but you cannot update system. All of these work just fine on smaller flash drives but with a larger one you can do a full install. But then it is not an installer.

With a standard install you have to use manual instal or Something else so you have the choice to install the grub2 boot loader to the MBR of the flash drive. Otherwise it will default to sda (your internal drive).

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

I believe windows will only read the first partition so that needs to be FAT or NTFS. If also a Mac I believe it does not read NTFS so then the only choice is FAT. FAT is ok for small partitions but not recommended for large partitions on hard drives.

---

### Post by vaul on 2011-09-10
Thank you both for the responses.

@Pariah819 I will look into it.

@oldfred Yes, of course I understand that I would have to install boot loader on to the USB, not on my hard drive. 

As far as I was able to understand, I will have to do the full install using the built-in installer, or UNetbootin? 

I actually considered installing 11.10 beta &#8212; would it be any different, speaking of installation and drive partitioning?

P.S. I read some more and it appears there are only two solid options available: either you do a compressed install and won't be able to upgrade, or you do a full install and it depletes the USB stick's read-write cycles pretty quickly. Is this true? Is there compromise?

---

### Post by Blasphemist on 2011-09-10
I saw this thread a few minutes ago. [http://ubuntuforums.org/showthread.php?t=1842121](http://ubuntuforums.org/showthread.php?t=1842121)

Jerry has an interesting process in post  2. I do think you'll have to work that geeky itch to use it but it is an interesting approach.

---

### Post by Herman on 2011-09-10
> P.S. I read some  more and it appears there are only two solid options available: either  you do a compressed install and won't be able to upgrade, or you do a  full install and it depletes the USB stick's read-write cycles pretty  quickly. Is this true? Is there compromise?It depends mainly on kind of flash memory you're talking about but generally speaking the average USB flash memory stick you can buy off the shelf these days should be able to run Ubuntu in it for a very long time before it eventually wears out.

Flash memory has improved with time and GNU/Linux operating systems have become more flash friendly too, which ext4's delayed allocation and the new sector 2048 partition alignment.

There are exceptions.
Camera cards don't seem to last very long compared with USB sticks and there was one particular make and model of USB flash memory stick I had to  return to the store for replacement three times. After the third time I  left it formatted FAT32 and used it for other purposes, so it seems like  some kinds of flash memory might not be suitable. I'm not  sure, it maybe it was a bad day at the flash memory factory the day the  box that was sent to my local electrical/electronic store was  manufactured, the quality control person must have been asleep or something, and the third time I was lucky. 

Another time I bought ten of some other brand and got one dud.

Most of the better USB flash memory sticks now have controllers like SSD drives do which feature wear leveling to rotate the erase blocks. Some work better than others.
Larger capacity drives with a little empty space left empty for the flash memory controller to rotate will generally last dis-proportionally longer than a small drive that's full all the time, so at least an 8GB drive is recommended over a 4 GB drive.
Some makes and models are fast and some are slow, with annoying pauses while erase blocks are emptied before being written to. Other USB drives will give you smoother, more seamless performance, they have a cache memory to temporarily store disc writes in like a HDD does. (No reason why not if it improves performance and customers will pay for it). I have read they can swap out bad erase blocks too, like hard disks can. I think some also might write to more than one flash 
There is at least one kind of USB flash memory stick you can buy that's guaranteed for life even when running Ubuntu and is reputed to be also one of the fastest on the market as well. 

There are a number of settings you can modify after Ubuntu is installed  to improve the speed and reduce wear in flash memory at the same time.

I have an EeePC 4G that has been running Ubuntu for a few years now and is still working fine. It only has a 4GB SSD for /, so right now I'm using the camera card for /boot and /home. I have worn out a few camera cards over the years, I guess camera cards just aren't made for this kind of use.

Hard disks wear out too, they lose their magnetic properties over time, or an electronic component on the hard disk drive's controller card can fail gradually, or they can suffer a bearing failure.

Flash memory drives don't usually suffer from bearing failures and are generally more durable, they are much more resistant to shock and other kinds of environmental factors and accidents.
My EeePC still functions just fine when my car is running over washboard dirt roads that make it bounce six inches off the dash and slam back down again while it's running my USB GPS to record my travels. It also fell off a table in the back yard experimenting with GPS programs when the wind blew a table over while it was running and I was in the house for something.
If it had a HDD instead of an SSD it would have died several times over by now.

The USB interface is limited to a data transfer speed of about 60 MB/sec  compared with about 600 MB/sec for USB3 and Sata-600, while the fastest  IDE interfaces can do about 133 MB/Sec or more. So even if you install in an USB external HDD, which would be a little faster than the average flash drive, don't be too  surprised if your Ubuntu in a USB isn't as fast as some other OS in an  internal HDD or SSD.

To sum up I like both kinds of flash memory installation.
The persistence kind is useful for installing Ubuntu with. That's about all I use them for.
A full Ubuntu installation in a flash memory makes a great auxilliary or 'support' installation since it has GRUB2 in it and is updatable. Those are the kind I use a lot and I seem to be getting quite acceptable mileage.
I'm typing to you from Ubuntu in a 64GB SSD. (OCZ Vertex). It's guaranteed for life.

 I really think the fear of wearing out the flash is an anachronism, (especially if you buy at least average quality or better).

---

### Post by vaul on 2011-09-11
@Blasphemist An interesting point, thanks. I will look into it.

@Herman Many thanks for detailed and comprehensive reply.

I bought [this]("http://www.google.com/products/catalog?q=cruzer+slice+8gb&um=1&ie=UTF-8&tbm=shop&cid=7119902826904102704&sa=X&ei=31VsTvL8N86o8APhnsWuDQ&ved=0CD4Q8wIwAQ") SanDisk flash drive for something like $17. I think either I have gotten an exceptionally bad deal, or it is at least average.

Ok, so to sum it up, your advice is: a use good disk, format to ext4, do a full install.

P.S. I admit, that fear most likely is an anachronism, since I heard that years ago, quoting the other, even older source. But you know, fears are picked up all right.

---

### Post by mrcoolinux on 2011-09-11
> **vaul said:**
> I long wanted to satisfy that geeky itch and create USB live stick, to use  as fallback system and/or in case of emergency. 

I have got 8 Gb SanDisk stick. I did a little research, and it is often said that UNetbootin is the best to do the permanent installation. 

Is it true, or there are better tools? Does it support the 11.10 beta?

I also would not mind being able to sent some files on it from Windows/Mac devices, what file system is best to use in that case — Fat32 or NTFS?

I guess it won't make much sense to make more than one partition for 8 Gb of space, or will it?

Are there any non-trivial aspects to this whole thing?

Thanks.
Hi, you might want to check this site out! 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
this is how i did my live-cd

---

### Post by vaul on 2011-09-11
@mrcoolinux That is quite interesting, but is there a way to do the opposite thing?

That would be more useful in my case &#8212; I plan to buy a laptop in the following year, and would like to move system from the USB stick I am trying to create now to the laptop's hard drive.

There is one more thing I would like to ask &#8212; most howtos I came across advised that main hard drive should be disconnected during the process of installation for safety reasons. My desktop's tower is still on warranty and I prefer not to void it unless absolutely necessary. Is there a way to safely do a full install on USB stick without disconnecting main hard drive?

---

### Post by vaul on 2011-09-14
The absence of replies must indicate that when you follow forums writing style and common sense and *do update your last post instead of creating a new one*, the update is not sent to the people subscribed to the thread.

Can anyone please answer the question that I edit-added to the previous post?

---

### Post by jroa on 2011-09-14
Of course you can do it with out disconnecting the main drive.  However, you do run the risk of accidentally installing to the wrong drive when you do this.  Just make sure that you choose the correct drive when you do the install.

I don't think that disconnecting the drive would in any way void the warranty, though.  Unless there are stickers on the tower that prevent you from opening it up, there is no way for them to know it was tampered with.

Another option for you is to temporarily disable the main drive in the CMOS/BIOS, if your motherboard allows this.

---

### Post by oldfred on 2011-09-14
The main issue that those that suggest disconnecting drive is to avoid installing the grub2 boot loader to the MBR of the internal drive. If you do manual install as the instructions posted before and select sdb or whatever the external flash is called in the combo box at the bottom of the install screen. 

If you use the graphical install, you can follow this for a second drive but should add the settings to reduce writes to reduce wear and speed up system somewhat.
Heman's install to second drive:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[FONT=Arial][SIZE=1]**p24/041.png**
**Where Do You Want To Install GNU/GRUB?**[/SIZE][/FONT]       
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by vaul on 2011-09-15
Okay, thanks for the info.

I however have one more question left &#8212; when I do the install and manually specify partitioning, should I allocate all space there is on the drive for system partition?

For example, if I used 16 Gb USB stick instead, should I make 8 Gb system and the 8 Gb home? Is there need for swap in this case?

---

### Post by Herman on 2011-09-15
> when I do the install and manually specify partitioning, should I allocate all space there is on the drive for system partition?
For example, if I used 16 Gb USB stick instead, should I make 8 Gb  system and the 8 Gb home? Is there need for swap in this case?It's very much a matter for personal preference, but personally I (almost) always just allocate all space there is on the drive for system partition and install with no swap area, (especially for USB stick installations). I ignore the warning messages from the installer complaining that I didn't make a swap area and after the installation is over I install a program called  [Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/"). That saves me space in my flash memory stick because the dynamic swap manager only makes swap files for the amount of swap area that is needed at any time. That's better than making an excessively large swap area, most of which will probably never be used and will just be a waste of the already limited space in a USB stick.
If you want you can install swap space manager from Ubuntu's Software Center or if you're in a hurry,
```
sudo apt-get install swapspace
```It's up to you whether or not to make a separate /home. I almost never do that, but some people love it, it's up to you. :)

---

### Post by Herman on 2011-09-15
After the installation is complete I also recommend setting swappiness to 10, the default is 60 I believe.  By setting the swappiness value down to 10 you will cause the operating  system to prefer using the RAM a lot more heavily and since RAM is  generally very fast to read and write to compared with flash memory you  will boost the performance of your operating system while at the same  time minimizing wear in the flash memory.

You can do that (set swappiness to a lower value) regardless of whether you created a separate swap area or if you have a swap file or you decided to use dynamic swap manager like I do.

Just open your /etc/sysctl.conf with the gedit text editor,          
```
gksudo gedit /etc/sysctl.conf
```
 Add the line 'vm.swappiness=10' to the end of the file,
         ```
vm.swappiness=10
```
Save and close the file.

You might notice a slight improvement in performance. :)

---

### Post by vaul on 2011-09-15
Thanks, I believe that is all I wanted to know about this.

---

