---
title: "Partioning My Harddrive"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by NobleRooster on 2007-12-02
I have Windows Vista already installed on my laptop, but I want to install Ubuntu on here as a second partition as well. 

The only problem is I'm not sure what to choose when it opens up the partition editor. (That is when I run the live cd, then choose to install, it asks how to partition the drive)

I would like to set aside say 30-40gb of my 160gb harddrive.

Help is appreciated.

Edit: I included a screen shot to show what I'm talking about.

[Screenshot]("http://i81.photobucket.com/albums/j229/JBennett89/Screenshot.png")

---

### Post by curtis1552 on 2007-12-02
The fist option is what you want to do, but you first need to make sure that you have all you important information on the HDD backed up onto a CD, DVD, or external HDD. 
What the option should do is resize the Vista partition and make one for Ubuntu (actually 2)
However, sometimes things can happen and your partition can become corrupted, making it unusable; hence the backup. 

During the linux install it may ask you if you want to over write the master boot record (MBR) select no, you can load Linux in a variety of ways, but windows can be a real pain if there is no MBR -- you will modify the MBR later. I can't remember if ubuntu uses lilo or GRUB, but IMO GRUB is better.

I would also recommend installing SuperGRUB after the Ubuntu installation (you can find ISO online) SuperGRUB automates the GRUB installation and recognizes Linix Partitions as they are installed. (I am currently multi-booting XP, ubuntu 7.10, edubuntu 7.10, and slackware.) It detected my edubuntu (the last one i installed) without any input from me.

When you install ubuntu you will need to make at least 2 partitions (giving a total of 3).
One for the file system, and one called swap. The swap should be 2x the size of your memory (but most people don't make it over 1 gig indifferent of memory).

Also remember that Linux distros have a harder time with NTFS than windows, and windows can't use the Linux file system - you might want to have a shared partition with fat32 on it. This would mean a total of 4 partitions - windows/swap/shared/linux.

---

### Post by NobleRooster on 2007-12-02
> **curtis1552 said:**
> The fist option is what you want to do, but you first need to make sure that you have all you important information on the HDD backed up onto a CD, DVD, or external HDD. 
What the option should do is resize the Vista partition and make one for Ubuntu (actually 2)
However, sometimes things can happen and your partition can become corrupted, making it unusable; hence the backup. 

During the linux install it may ask you if you want to over write the master boot record (MBR) select no, you can load Linux in a variety of ways, but windows can be a real pain if there is no MBR -- you will modify the MBR later. I can't remember if ubuntu uses lilo or GRUB, but IMO GRUB is better.

I would also recommend installing SuperGRUB after the Ubuntu installation (you can find ISO online) SuperGRUB automates the GRUB installation and recognizes Linix Partitions as they are installed. (I am currently multi-booting XP, ubuntu 7.10, edubuntu 7.10, and slackware.) It detected my edubuntu (the last one i installed) without any input from me.

When you install ubuntu you will need to make at least 2 partitions (giving a total of 3).
One for the file system, and one called swap. The swap should be 2x the size of your memory (but most people don't make it over 1 gig indifferent of memory).

Also remember that Linux distros have a harder time with NTFS than windows, and windows can't use the Linux file system - you might want to have a shared partition with fat32 on it. This would mean a total of 4 partitions - windows/swap/shared/linux.

Wow, all this is practically greek to me.

Ok, so when I start the install, I just slide that bar to a size I want the new Ubuntu partition to be?
And then it should create a new partition and install Ubuntu to it, right?
Do I have to create the swap partition later, or can I do it right there in that partition editor?  If so, how?

Sorry to ask so many questions, but I'm extremely new to Ubuntu and dual booting stuff.

---

### Post by logos34 on 2007-12-02
have a look at this page:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Defrag windows and then use vista's disk management tool to shrink the vista partition. Use guided install to put ubuntu on remaining disk space (it will create the swap for you). 

There is a slight chance you will have trouble booting vista with grub.  Read [this first]("https://help.ubuntu.com/community/WindowsDualBoot").  Personally, I would try grub on the mbr but be prepared to use EasyBCD to edit vista boot manager to boot linux in case of problems.

---

### Post by meindian523 on 2007-12-02
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

I guess that's what you need.....

---

### Post by Multi-Booter on 2007-12-02
I think Vista boots better through Grub than it does through it's own bootloader.
I have never had a problem with it.

However, I am fortunate enough to have two SATA drives... so Vista resides on it's own hard drive as it was originally. So Grub is on the other drive... which means when I restart, I have 2 ways of booting Vista, depending on which disk I choose to boot.

With all this said, this is only the case because I was unable to shrink the Vista partition. The drive is 250GB with 195GB free, but it tells me there is not enough space for this action. I have no idea why and I have not probed any deeper yet. But the tool did work for shrinking other windows partitions just fine.

Finally, I think Vista differs from other versions of windows in how it boots. I think it has a different bootloader / process for booting. But I have no conformation of that... just general observation... and again I have not probed any deeper into it yet. I only have time for so much and so far I have not had the need to know more about Vista's boot process. I've had no issues personally, and so far.... debunking popular belief, I have had almost no incoming Vista service calls. The 32-bit versions of XP & XP Pro still generate almost all...

In the end, if you are installing on a partition on the same physical drive as Vista, it might not hurt for you to research Vista's bootloader. You might want to go an alternate route installing ubuntu and use Vista's bootloader instead of Grub so that your Vista is left alone...

---

### Post by Griff on 2007-12-02
I'm not new to dual booting and whatnot, but the partition editor on the gutsy cd isn't allowing me to shrink the vista partition.  I was able to clear off the recovery partion (new laptop) so it isn't a permission thing.  Any idea why?

---

### Post by Pumalite on 2007-12-02
It's not supposed to. With Vista, you have to use Vista partitioner to allocate space for Ubuntu first; otherwise, no go.

---

### Post by Pumalite on 2007-12-02
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Multi-Booter on 2007-12-02
Yes... Vista has it's own tool... and I find with stuff like this it's best not to buck the system, and instead use what is 'native' to the OS to work on it's partition if possible.

The tool in Vista works... I've used it to change partition sizes... it just didn't work for me on my Vista partition for whatever unknown reason.

To use it graphically...

Click start
Click control panel
Click computer management
Select Disk Management

In the list, right click on the partition Vista is on.
Select Shrink Volume and let it do it's thing.

---

### Post by Pumalite on 2007-12-02
Beats me. Never used Vista. Never want to.

---

### Post by Griff on 2007-12-02
> **Pumalite said:**
> Beats me. Never used Vista. Never want to.
Ah.  Didn't realize that other partition progs wouldn't work.  I used the one in windows and it worked fine.  Only problem is it wouldn't let me get the partition smaller than 60GB.  Not sure why.  I never wanted vista but they all come installed now.  I'm keeping it around in case I ever have anything from the school that I can't get running in linux.

And so far I am extremely disappointed with vista.  A brand new install shouldn't lag on a dual core 64 bit AMD Turion with a gig of ram.

---

### Post by Multi-Booter on 2007-12-02
> **Griff said:**
> 
And so far I am extremely disappointed with vista.  A brand new install shouldn't lag on a dual core 64 bit AMD Turion with a gig of ram.

For a Microsoft OS it's not bad... not bad at all actually... but it is a resource hog.

You don't have the hardware to support it properly is the reason it lags.
You're no doubt thrashing your system running it.... which really burns me up.
To sell a system like that is not moral in my opinion... but I have seen Vista installed and sold on less.

In the end though, it is what it is... and if you don't have the hardware, you are better off replacing it with something else. So bottom line... get yourself at least another GB of ram, else there is not as much point in having Vista.

---

### Post by GoldenH on 2007-12-02
Installing ubuntu with vista is super-easy. here's how i did it.

1) download alternate 7.10 installation disc (since the normal one won't boot on all computers!) 

2) use vista drive manager to Shrink the vista partition (as low as you can go, really)

3) reboot, go with install. choose "guided - empty space" in the partition manager. just take whatever it says.

4) after it installs all the stuff from your disk, it'll ask you to install grub to the mbr, say no, install it to the linux partition instead.

5) finish and reboot into vista.

6) download and install EasyBCD

7) tell EasyBCD where your linux partition is, tell it to add it to the boot menu.

8) reboot into ubuntu


very easy, no thinking required!

why not use grub? cuz linux doesn't care and vista does.


As for vista being slow, i was dissapointed also with 1 GB ram. until i stuck in my flash drive and decided to see what ReadyBoost is.

holy cow!
 
ReadyBoost is incredible, i've never had such a performance boost in an upgrade in my life. never mind one so unexpected!

---

