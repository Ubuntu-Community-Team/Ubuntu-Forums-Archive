---
title: "Lenovo U410 Problem Install"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by shatteredgear on 2012-07-12
so i bought a lenovo u410 the other day to use with linux along side my windows pc, problem is when i get to the installation screen the hard drives dont show up (500gb hdd or 32gb ssd) i also took off acceleration and put the hard drives in non raid mode but that still didnt work,  i also tried wubi to see if it would run for kicks but that wont work either, can anyone help me out?

---

### Post by irv on 2012-07-12
I'm not sure but you could go to [Ask Ubuntu]("http://askubuntu.com/questions/tagged/lenovo") and see if they have something listed. It looks like others have had problem with the Lenovo.

---

### Post by shatteredgear on 2012-07-12
> **irv said:**
> I'm not sure but you could go to [Ask Ubuntu]("http://askubuntu.com/questions/tagged/lenovo") and see if they have something listed. It looks like others have had problem with the Lenovo.

havent found anything relating to the problem im having, i have a feeling its going to be something minor that im just missing lol

---

### Post by irv on 2012-07-12
I wish I could help further but I don't know that much about the Lenovo U410. Hopefully someone has one out here and can jump in and help.

---

### Post by SvenSvenson on 2012-07-13
Hi,

i also have a Lenovo U410,  I have successfully installed Ubuntu. I was able to use Windows and Ubuntu in Dualboot. But now my Windows doesn't come up anymore.

So my method isn't really good. If you go into your Live System and enter "sudo apt-get remove dmraid" your installer is able to recognize your hard drive(s).

But this is the "dirty way". Because the 500GB HDD and the 32GB SSD are configured as a special RAID0 Volume (for the Intel Smart Response and Intel Rapid Storage Technologies) and you shouldn't access them individually.

---

### Post by shatteredgear on 2012-07-13
> **SvenSvenson said:**
> Hi,

i also have a Lenovo U410,  I have successfully installed Ubuntu. I was able to use Windows and Ubuntu in Dualboot. But now my Windows doesn't come up anymore.

So my method isn't really good. If you go into your Live System and enter "sudo apt-get remove dmraid" your installer is able to recognize your hard drive(s).

But this is the "dirty way". Because the 500GB HDD and the 32GB SSD are configured as a special RAID0 Volume (for the Intel Smart Response and Intel Rapid Storage Technologies) and you shouldn't access them individually.
kinda wish this laptop would just stop giving me problems and just work lol :( damn this "special" hard drive

---

### Post by lx3r on 2012-07-13
same issue here with the u410. 
Weird thing is that the file manager does actually recognize the disks after a while, but the installer doesnt.
haven't been able to solve it yet.
(also, wireless doesnt work, probably just the wrong driver loaded.)

---

### Post by shatteredgear on 2012-07-13
> **lx3r said:**
> same issue here with the u410. 
Weird thing is that the file manager does actually recognize the disks after a while, but the installer doesnt.
haven't been able to solve it yet.
(also, wireless doesnt work, probably just the wrong driver loaded.)

if you manage to get everything working as they should let me know, i couldn't figure it out at all

---

### Post by SvenSvenson on 2012-07-13
You could completely delete windows, and set up the drives normally. (Deactivate the Raid mode in BIOS)
After that you install windows and ubuntu like on any other pc. You could partition the SSD and move directories like /boot to the SSD to speed up your Ubuntu.

But then you loose this "ultra cool Intel Cache Technology" for the working with windows lool
I don't know if this cache technology is so damn good. But your boot time will increase from 30 to 60 seconds in windows, but i think this is manageable. I didn't use Windows on the u410 long enough to say what for other speed benefits this Cache Technology brings.

If you mainly use Ubuntu you get speed-benefits with this solution i think.

---

### Post by SvenSvenson on 2012-07-13
It seems the package mdadm is helpful.

Google for "ubuntu installer intel rapid storage raid"
At first glance some results looks promising.

---

### Post by lx3r on 2012-07-13
hmmm.. this might be interesting:
[http://board.issociate.de/thread/509721/Does-Linux-support-Intel-Smart-Response-Technology.html](http://board.issociate.de/thread/509721/Does-Linux-support-Intel-Smart-Response-Technology.html)

I think i'll try this next week. Then no rapid-intel-blabla on windows anymore, but really, i dont care...

---

### Post by godgough on 2012-07-21
I have found a solution that works for me:   [http://ubuntuforums.org/showthread.php?p=12121677#post12121677]("http://ubuntuforums.org/showthread.php?p=12121677#post12121677")
The key for me was disabling RST for a restart of the computer.

---

### Post by nemesys571 on 2012-08-07
> **SvenSvenson said:**
> You could completely delete windows, and set up the drives normally. (Deactivate the Raid mode in BIOS)
After that you install windows and ubuntu like on any other pc. You could partition the SSD and move directories like /boot to the SSD to speed up your Ubuntu...

SvenSvenson, I guess you did this already. Where did you install Windows from? From the hidden recovery partition? I'm planning to buy one of these soon. And speaking of recovery partition, is there a way to return it to factory state in case I need to send it for a warranty-covered repair? Since it doesn't have an optical drive, I wonder what kind of recovery options the machine comes with.

---

### Post by SvenSvenson on 2012-08-08
I installed Windows from a USB Stick from the scratch. Because I'm a student I can purchase Win7 (with key) as ISO for free from Microsoft MSDNAA.
(I have completely formatted both disks)

But I think It will work with every downloaded Win7 ISO and bootable USB Stick. Then you could use your product key from the backside of the laptop. Otherwise write the Lenovo Support to send you a Recovery CD (But then you need a external drive).

Out of the box, there was a Windows Recovery Partition and a Lenovo "One Key Recovery" Partition I think. But as I said, I completely formatted everything

For everyone who finds this Posting. I found a solution to install Ubuntu.
**Just go into the Live-System and execute a "dmraid -ay"** ... After that the RAID is activated. Then start the Installation from the Desktop Link and, wow look at this, the Installer recognizes all disks and partitions.

(If you first configure the Intel Smart Response with the GUI in Windows to use just 18,6 GB of the SSD, the Ubuntu Installer even recognizes the Rest of the SSD as dedicated Partition and you can use this partition too, to speed up your ubuntu system)

---

### Post by brianfast on 2012-09-10
SvenSvenson, thanks for your tips. Did you figure out how to make a full linux install with the cache raid? Or do you just use the SSD to mount something like /boot and not as RAID cache?

How do you get to the Windows GUI you are talking about?

---

### Post by SvenSvenson on 2012-09-10
You have to search after "Intel matrix storage manager" and Download it. The GUI looks like this: [http://imageshack.us/photo/my-images/842/intelsmartresponse.png/](http://imageshack.us/photo/my-images/842/intelsmartresponse.png/)

If you configure the Intel RST with just 16,6 GB the SSD gets split into two partitions (see the picture).

In the Ubuntu Live System you must run the "sudo dmraid -ay" command. Then start the installation from the Desktop icon, your installer should recocnize the RAID volume.

Meanwhile I have ubuntu installed, but I didn't get grub to work.

---

### Post by killtroubles on 2012-09-10
did you use install alongside windows 7 ??

---

### Post by ceesiebo on 2012-10-10
I got it working as a dual boot. I had to do a bit of research though. First of all, the RAID volume is basically worthless and not really a real raid. The intel software is used to make the SSD usable as a cache-volume. I removed the acceleration (which slows the Windows boot) and made the SSD available to the system using the software SvenSvenson noted. You don't have to download it, it's available on the hard drive in Windows.

After that I rebooted with Ubuntu 12.04 from a stick. I chose to try out Ubuntu first. Then I chose install from the desktop and it saw the volumes and also the Windows OS. I got the option to install as a dual boot. I installed Ubuntu on the SSD (which now boots lightning fast!). Since you can choose the volume to boot from via the BIOS you can boot from the SSD so GRUB is also on the SSD. The MBR on the hard drive is still there but not altered so Windows can still boot without a problem if you choose to boot directly from the hard drive. GRUB has also recognised the Windows OS, so when booting from the SSD I still get the option to start Windows instead.

When booting Ubuntu I got the GRUB in a terminal first, so I had to install GRUB again (I used Boot-Repair by the way).

I also got an extra problem by the way. The right button of the touchpad didn't work properly. But I solved that by following another instruction on the Ubuntu forums where someone provided a package and it works great. I even got multi gesture support now! So I'm happy with my dual boot and a lightning fast booting Ubuntu. Windows booting slowly now is not a problem for me since I only use it for running a PC game once in a while.

---

### Post by irv on 2012-10-11
ceesiebo very good post. I know it will help other down the road. Isn't it great how fast SSD's boot. I also install one this past year and I don't even go into suspend mode any more when I am on the road, because it boots so fast. And this was on an older laptop. Maybe you can mark this one solved.
[ATTACH]225413[/ATTACH]

EDIT: Sorry about that, I see shatteredgear started this thead.

---

