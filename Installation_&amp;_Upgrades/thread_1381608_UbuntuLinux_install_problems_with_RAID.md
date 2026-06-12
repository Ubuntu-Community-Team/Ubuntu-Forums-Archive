---
title: "Ubuntu/Linux install problems with RAID"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by xiainx on 2010-01-15
The story: I've tried to install Ubuntu / Kubuntu several times now (at least 10), and everytime I've had a problem. Here's the situation, I have Windows 7 installed on my machine right now, and I don't want to remove it for a couple of reasons: I play games sometimes, there are still some things in Windows that I do need (yes, NEED). That said, I want to use a linux distro on my machine (I'm a software engineering student, so I kind of need it...). Ubuntu seems like a good distro, and I might also try Fedora or something in the future.

The problem: When I try to install Ubuntu/Kubuntu, I arrive at the partition screen (after shrinking my Windows partition by a generous amount), and the installer does not see that I have Windows 7 installed. It gives me the choice to either: install on the entire disk, or specify my partitions manually. So, I said alright, not a problem, I'll just use Wubi. Well, I got it to install alright, and was really excited to start using it. I rebooted my machine into Ubuntu. The screen showed black with the lights blinking (to indicate it was powered on). I waited a while, still black. I tried restarting it, I tried waiting 2 hours, it wouldn't move past this black screen. Looks like Wubi doesn't work either. What could possibly be the problem???

The machine: Dell XPS M1730, Intel T9300 (I've been trying to get 64 bit thus far, as it works fine for Windows), NVidia GFX card, 4 GB RAM, 320 GB drive. 

The potential problem: I bought a RAID drive with the computer, it was 160 GB. When I upgraded from Windows Vista to 7 a few months ago, I decided to decouple it, and make it one 320 GB drive (I think this is called RAID 0, correct?). I'm wondering if, when I run the installer, the windows 7 partition is on the other physical disc, and the installer cannot see it. Could this be a problem? Right now, I'm thinking the only solution is to re-install 7 on a RAID 1, with 160 GB, and then try to squeeze another OS onto that (it would be much more comfortable with 320 GB, as I have about 100 GB of personal stuff...).

Please, please, please help me! I will do anything (within reason), if you will help me! Thank you.
Iain

---

### Post by xiainx on 2010-01-15
Can anyone help me out with this??

---

### Post by darkod on 2010-01-15
> **xiainx said:**
> Can anyone help me out with this??

Yes, we can. But to make sure we give you right advice, I have a question. When you say you decoupled the raid1, do you mean:

1. Two separate drives of 160GB each, NOT in raid array of any kind.
2. Two 160GB drives in raid0 array, total usable space 320GB.

If you completely decoupled the raid and removed the array, the problem is ubuntu 9.10 can see raid settings traces on your drives and giving you headaches. In this case, with the raid array already gone, do:

1. Go into BIOS and MAKE SURE all raid settings are disabled. Just to make sure.
2. Boot with ubuntu cd, Try Ubuntu option, and in terminal execute:

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

That will remove all raid settings from both drives, which should be named /dev/sda and /dev/sdb (you might want to check that before executing above commands to make sure). You can check with:
sudo fdisk -l

After the above, your disks are free of raid settings and just reboot again with ubuntu cd, select Install Ubuntu and do as you want depending how you want ubuntu set up (where, how much space, etc).

PS. If you just chaged the raid1 into raid0, the above is not what you should do. There is different procedure if using raid0. That's why it's very important whether you completely removed the raid array or you just changed it to raid0.

---

### Post by xiainx on 2010-01-15
I believe it's in RAID 0 right now, as I still have an array matrix manager running it. In my BIOS, I have a few options for managing the RAID, I will restart my computer, and tell you what they are in a minute.
Thanks for your help so far!

Edit: Okay, I think I know how to disable the RAID now, but let me ask... Should I do this, and reinstall 7, then Ubuntu, or is there someway to keep the RAID 0, and install Ubuntu with 7 as is? If not, can I keep the RAID 0, and do a fresh install of 7, then Ubuntu with the RAID still enabled?

---

### Post by darkod on 2010-01-15
> **xiainx said:**
> I believe it's in RAID 0 right now, as I still have an array matrix manager running it. In my BIOS, I have a few options for managing the RAID, I will restart my computer, and tell you what they are in a minute.
Thanks for your help so far!

For fakeraid (motherboard raid) read here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I have no hands on experience with fakeraid so not much I can help you with. I only know you need to use Alternate Install CD, not the standard Desktop CD.

---

### Post by xiainx on 2010-01-15
Alright, looks like it will be easier to do this on a non-RAID drive, so I am going to go ahead and reinstall 7 on a non-RAID configuration, and then give Fedora a try. With me luck!!! Thanks for the help.

---

### Post by xiainx on 2010-01-15
For future reference, for those who are wondering how I resolved this problem...

1) Prepare all your stuff (backup data, etc. etc.) for a full OS reinstall.

2) Boot your PC, with the Ubuntu install disc in (don't worry, we will install 7 first...). When you see the RAID configuration manager boot screen, hit CTRL + I to enter configuration. Now, disable all the raid settings, this will setup your machine with two drives, in a non RAID configuration.

3) Boot into Ubuntu, and choose to try it without changing your computer. We need to do this to reformat the drives before we can install 7. Basically, the problem I found out is that if you have two drives, and you try to install 7 on one of them, but there is a filesystem on the other (when we deleted the RAID, we didn't delete the filesystem), it freaks out and won't let you install.

4) Start GParted, I think it's in preferences -> system -> partition manager.

5) Partition your two drives however you please. For me, I chose to setup one drive as one partition, NTFS for my data, and the other with two partitions, one NTFS, and one unspecified.

6) Turn off the computer and put in the Windows 7 install disc.

7) Boot up, and install Windows 7 onto the correct partition (if you follow the scheme above, it is the smaller partition).

8) Now, setup your data drive by opening the drive manager. (open windows explorer, right click on computer, click Manage, choose Disk Management). Right click on the data drive, and choose change drive letter and path. This will mount it so that Windows 7 can see it and use it.

9) Now it's time for your other OS. Turn off the computer, and put the Ubuntu (or whatever) install disc in.

10) Boot up, and install the new OS to the unallocated space on the non-data drive. I just let my OS do the formatting, it was pretty easy. You need to make sure to let the OS booter boot the linux OS primarily. If you tell it to boot Windows primarily, you won't be able to boot into linux! It is much easier to boot into windows from a primary linux.

11) Now, you're done! You can setup Ubuntu (or your Linux OS) to see the NTFS data drive by following the instructions [here]("http://ubuntuforums.org/showthread.php?t=217009"), or Googling the problem.


Best of luck, and enjoy your dual boot!

---

