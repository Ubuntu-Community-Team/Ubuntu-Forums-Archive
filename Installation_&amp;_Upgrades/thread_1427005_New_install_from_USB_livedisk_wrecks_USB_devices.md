---
title: "New install from USB livedisk wrecks USB devices?"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by BastardNamban on 2010-03-11
I had a working 8.04 install a week ago, totally updated. I used a remastersys .iso to make a unetbootin usb key custom live cd to install my build of linux with all settings on a new hard drive.

I have since added XP SP3 to it to start, for using a 3D CAD program, and just finished updating that, and installed Ubuntu from the live USB key on it with 1 / partition and 1 swap partition. I type this now from that. I did this twice- as te first time, I thought it would fix the problem. It didn't- since putting Ubuntu on with that 2x, I can no longer read my 2 external HDDs (1PATA, 1SATA) in USB external enclosures. In either XP or Ubuntu!

I'm freaking out. My data should be there- but nothing I try reads them! They come on, with no scratching- I know they work fine, and haven't crashed. But nothing I try lets me see and use the files on them.

Why? I don't know- I do know I'm seeing a lot of os boot choices at the boot menu- all with their own kernal number and safe mode. Then "memtest xxxkernal" or something, then XP.

Can someone please help? I will check again in morning EST.

---

### Post by garvinrick4 on 2010-03-11
> **BastardNamban said:**
> I had a working 8.04 install a week ago, totally updated. I used a remastersys .iso to make a unetbootin usb key custom live cd to install my build of linux with all settings on a new hard drive.

I have since added XP SP3 to it to start, for using a 3D CAD program, and just finished updating that, and installed Ubuntu from the live USB key on it with 1 / partition and 1 swap partition. I type this now from that. I did this twice- as te first time, I thought it would fix the problem. It didn't- since putting Ubuntu on with that 2x, I can no longer read my 2 external HDDs (1PATA, 1SATA) in USB external enclosures. In either XP or Ubuntu!

I'm freaking out. My data should be there- but nothing I try reads them! They come on, with no scratching- I know they work fine, and haven't crashed. But nothing I try lets me see and use the files on them.

Why? I don't know- I do know I'm seeing a lot of os boot choices at the boot menu- all with their own kernal number and safe mode. Then "memtest xxxkernal" or something, then XP.

Can someone please help? I will check again in morning EST.
Is your USB a Live USB does it give you the choice of using without changing? If so use it. If not use a Live CD and go into
the program gparted under System/ADmin.  Use drop down menu in gparted to devices pick one of your USB devices, Label it.
Lets say you name it info.

sudo mkdir /media/info

sudo mount /dev/sdb1 /media/info

sudo umount /media/info

1: to make a directory
2: to mount space after sdb1 or whatever your # is in 
sudo fdisk -l (small L) or what it says in gparted your # is.
3: to unmount and umount is right.

Being mounted in a live CD can they now be read?

---

### Post by BastardNamban on 2010-03-11
No, it's a Live USB, like I stated. The problem was no one in my house has a working optical burning drive, myself included- my laptop's Sony dvd burning drive was having problems, and burning me coasters, so I can't use it either- that's why I went and figured out how to make the live USB stick to install from- I had no live disk I could make!

The live USB stick had, per unetbootin's menu, first an option for "Default", whatever that was, and next, "Live", and a bunch more options. After installing from it with a 2 GB swap partition and a 12 GB / partition in ext3 (temporary fix to get files off the drives into windows).

The whole point of making the live USB was to install from it. It worked, but only the external USB devices don't read. The problem is neither drive will read in a perfectly good XP SP3 install EITHER!
They don't sound like they've crashed, seem to work fine- but neither OS can read them. I thought maybe since I used them in linux, reinstalling a temporary linux install might work, but no.
Also, I still have an install drive icon on my desktop after fully installed.

Can anyone tell me what to do? Is it a driver I don't have? An option I haven't enabled? If Windows XP can't mount them either, what's going on????

---

### Post by BastardNamban on 2010-03-11
I just tried one of the external drives on another computer- a Win XP machine. Nothing happened- it never mounted there either.

I'm not hearing loud scratches from the drive, so it hasn't crashed. I hear a small seeking sound, going back and forth, probably because the drive can't mount, it just seeks.

I tried opening gparted in Ubuntu from the new install, and turning on the external SATA drive- it doesn't even show up, not even in the drop-down menu. What the hell is going on here???

Someone, anyone, PLEASE, I don't mean to sound frantic, but ALL of my data, my life, pictures, programs, resume, tax data, everything I moved to those 2 external hard drives (internal ones in enclosures) before I replaced my hard drive. They worked fine then. I NEED that data to continue setting up my computer! I have never had such a helpless issue with linux- this is the first time I can't seem to see any way to fix something, no matter where I look for options.

:cry:

---

### Post by BastardNamban on 2010-03-11
Another update- in XP, a normal USB stick with FAT32 format opens and reads fine. In Ubuntu, the same FAT32 format USB stick doesn't open- BUT it does register under the places menu. Clicking on it doesn't let me open it, and I get an error message. See attached image for the screenshot of the error.

Now I know it's something wrong with Ubuntu. I figured XP wouldn't even detect an Ext3 format external drive, which they must have somehow become- because a FAT32 USB key works in XP. Neither work in Ubuntu, but the FAT32 USB stick shows up- it's just unacessable.

Does this help towards finding a solution?

EDIT: I have also tried burning a brand new standard live disk .iso in XP to a CD, but the computer refuses to boot from the CD even with boot order proper- it keeps scanning back and forth, unable to read it, as had the other coasters I burned to start with. So live disk CD is a no-go option. ARGHHHH!

---

### Post by julianb on 2010-03-11
Things i would consider trying:

1. plug one or both of the "external" drives in as an internal drive instead, see if anything works correctly
2. save any needed data, then wipe the main (internal) hard drive, install Windows XP; install Ubuntu if you want to.
3. use a different machine (borrow from a friend?) to see whether you can access the external drives
4. if nothing above works, consider getting someone who does data recovery ($$$) to retreive whatever you have on your external drives. 


Some more-obscure things you could try out are:
make a tiny core linux liveCD (if your computer doesn't boot from USB) or "liveUSB flash drive"... see if you can access your external drives from there.

PS-- if you have not already... try command line tools where GUI tools fail. When dealing with mount/unmount operations I like to try the terminal (mount/umount). Whenever "mount" fails i try to "umount" the device and then try to "mount" it again, paying attention to any error message that come up.

---

### Post by BastardNamban on 2010-03-11
Ok, thanks for the reply...

1. The 2 external drives (1 PATA, 1 SATA) are BOTH 3.5" drives. This is a laptop 120GB hard drive. As such, what you sugguest is impossible. They won't fit in the laptop.

2. I did. Or rather, it was a blank HDD from the beginning- it's brand new! I already installed XP on it, about 25 GB partition. I also already put Ubuntu on it (2 GB swap, 12 GB / partitions). I intended the ubuntu install I type from now to be temporary (a more detailed install later on)- just to get the data off the 2 drives. It hasn't worked.

3. Again, as written above- I tried that. No go.

4. No- I'm pretty sure they haven't physically crashed. Because that FAT32 USB thumb drive reads and writes in XP, and displays but is inaccessable in Ubuntu, I know something is wrong in Ubuntu...

***Neither external USB HDD will even show up in either system, but the odds of both having physically crashed and not working without making the load scratching sounds that should make are extremely low. This has to be some kind of driver issue?

Can anyone with vast knowledge of Ubuntu comment? Can someone tell me what's going on? I am going to try putting in my old laptop HDD tommorrow with the old Ubuntu install still on it- if the drives mount there, I know they aren't bad. If they don't mount on that, I'm up the crick as they say.

---

### Post by BastardNamban on 2010-03-12
I FIXED IT!!! :o

I had a stroke of insight- I know what a bad drive sounds like, and so the drives should have been fine- but when the old HDD ubuntu install wouldn't read them (I switched in the old drive this morning, typing from it now), I knew it wasn't the OS or the computer.

Something with the enclosure itself had to be wrong.

Then I realized- what if the power cable had gone bad? Perhaps that blinking green to red on the PATA enclosure was hinting at that, and I just didn't know the error code.

I found the spare enclosure cable I keep away- I usually use 1 cable and switch it between drives. Less wires.

Lo and behold- the drive spins up fine, and opens in this old install!

IT WAS THE POWER CABLE, NOT THE DRIVE!

I'm surprised no one recommended that one. In hindsight, it's so obvious. I haven't tested it on the new Ubuntu install, but it should read and write fine now on the new HDD.

I'm marking this solved- and consider this an endorsement for Venus DS3 enclosures- I've taken the things between the US and Japan 6 times in the last 5 years, and only now does anything go wrong with them. A simple power cord failure- but the enclosure works fine. The things are built like a tank, with their own fans, but they're lightweight, and survived this long.

---

