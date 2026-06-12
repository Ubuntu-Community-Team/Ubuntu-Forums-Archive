---
title: "Desperate help needed with a super blunder!"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Feilin on 2009-12-18
This is going to sound like a one of those funny stories about a complete idiot trying to use a computer and failed miserably, but please do not laugh and take it seriously knowing that I'm in desperate need of help!

I bought a laptop 6 months ago, and with it came a package of the horrible Windows Vista 32bit, yaddah-yaddah-yaddah... After listening to a friend of mine, I decided to try out Ubuntu 9.04, and downloaded an image file which I burned onto a DVD. I am completely new to Ubuntu, but was hoping it would be nice and easy to install and use it, so I installed it and tried to customise it to make it more comfortable (since I've only used Windows so far). I managed to install Ubuntu next to my Windows system, with a nice little boot loader at start-up and I was still able to choose Vista.

However, as I thought it was unnecessary that Ubuntu had a different "My documents" folder than Vista, I tried to merge them. In the process I managed to change the home directory so I got the error message saying something about my missing home-dir and that I couldn't log in normally and had to use terminal. The loader was still working though, so for a few months or so, I didn't have time to fix the problem, and continued using Vista.

Over time, Vista got so cramped up with viruses and installations, that I my hard drive of 280GB was on 20GB and shrinking by the minute. Whether it was a virus program eating my HDD or Vista downloading updates I didn't want, I don't know, but I decided to try re-install Ubuntu. However, I managed to install it next to the other two installations, and by that time, my drive was full, so Ubuntu was locked due to the lack of space and I was unable to update or install anything.

In the need of a working computer, I used my Ubuntu DVD for a while, but now I've gotten around to solving the problem. My plan was to save my files externally, use my recovery discs that I got with the purchase of the laptop, sweep the disc clean and install one Ubuntu next to Vista (which I would use very little to lower risk of virus infection). When I'd done the recovery however, the old partitions were still there, but it somehow had erased the information, so the boot loader wanted to load Ubuntu which wasn't there.

I the decided to sweep the disk clean with Ubuntu, letting it take the whole disk instead of partitioning it next to everything else, and then try to re-install my hated Vista. What Ubuntu did wasn't quite what I wanted; it removed all the partitions, and when I was done with the installation, my recovery DVD's couldn't find the partitions it needed to install. I thought it's good enough, for now at least, but the problem was my Ubuntu wasn't working either. I don't know if there's supposed to be a swap partition or whatever, but I can't install, update or anything with my computer as it is now, so I'm back to square one again (or even worse since my Vista doesn't work either).

Please help me restore the partitions or whatever action is required so I can install Vista using my recovery DVD's and after that Ubuntu so I have two fully functional systems on my laptop. I have very little time and money, and this matter is getting more and more urgent.

//Feilin

---

### Post by Feilin on 2009-12-18
Oh, and the error message I get when trying to recover with Vista is:
FAIL to get Disk 0 partition 1 drive letter

---

### Post by marshmallow1304 on 2009-12-18
First make sure all your important files are saved externally.  Load up the Ubuntu live CD/DVD and start GParted.  System->Administration->Gparted or System->Administration->Partition Editor (depending on Ubuntu verison).  Format the entire disk to NTFS.  Boot from the Vista install disc and install Vista.  Once done, boot from the Ubuntu disk and install Ubuntu.


Edit:  I don't know if you can do a fresh install with recovery DVDs.  Perhaps the company from which you bought the laptop will send you a Vista installation disc or otherwise assist you.  If not, you might wish to acquire Vista with an *ahem* *alternate* method and use your previously purchased key to validate it.

---

### Post by sgosnell on 2009-12-18
Why can't you install anything to Ubuntu?  It should be straightforward with Synaptic, as long as you enable the necessary repositories there.

You don't say what brand of laptop, so it's not possible to say exactly what partitions the recovery disks expect.  You can repartition however you want with the liveCD, but I have no idea what to put into Google because I don't know the make or model of your laptop.

It will probably be easier to get Ubuntu working, though.  It's not that hard, as long as you can explain your problems more clearly.

---

### Post by themusicalduck on 2009-12-18
If you are certain that you wiped everything with Ubuntu then this is what I would do:

You could check first by running ```
sudo fdisk -l
``` and posting it here. But if you told Ubuntu to use your entire disk, then it will probably all be gone.

If you actually have the recovery discs already made, then I wouldn't think that the recovery partitions would need to still be there. Although it's a bit unfortunate that they were formatted, at least you have some form of recovery disk.

One reason why Vista might not want to install is because Windows doesn't like to install itself onto a hard drive where Ubuntu is already installed. As far as Windows is concerned, if the disk isn't either a windows formatted partition or unallocated then it's not usable.

A better way to install Vista might be to delete all partitions again provided you can make a backup, and then when you try to install Vista it should be successful. After installing Vista you can then reinstall Ubuntu onto a second partition.

You can delete your partitions if you boot into a live Ubuntu CD and run the partition editor under System > Administration > Gparted (or it might be listed as Partition Editor).

You can either format the partition as ntfs from gparted, or just delete all the partitions so that the hard drive space is listed as unallocated then the Vista installer can make its own partition.

Also the latest version of Ubuntu is 9.10, if you're having problems with 9.04 then 9.10 might work better.

---

### Post by Feilin on 2009-12-19
I don't know why, but every time I tried to update or use Add/Remove... it just gave me a red round sign with a white thick line saying it couldn't install. Now I'm running from the Ubuntu DVD.



When I run the command in terminal I get this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadad1f1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37785   303507981   83  Linux
/dev/sda2           37786       38913     9060660    5  Extended
/dev/sda5           37786       38913     9060628+  82  Linux swap / Solaris


(which btw reminded me that my HDD was supposed to be 320 GiB, not 280 as I was led to believe by Vista...)



I didn't think it would need the partitions either, that's why I tried this method; because everything was ****** up anyways. There's another solution to more specifically my problem and a similar laptop model, but I don't quite understand it. It goes:
"I defined the first partition with an id of hex "27"(unknown). I also made a second partition with an id of hex "07"(ntfs) and made it the boot partition"

I think I'll follow that one first, as it is more specific, but how do I try that? How do I "define" the partitions with "id of hex"?

---

### Post by jocko on 2009-12-19
> **Feilin said:**
> 
When I run the command in terminal I get this:

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

That's because you used an option that doesn't exist. it should be -l (lower case letter L) not -1 (number one).
```
sudo fdisk -l
```

---

### Post by Feilin on 2009-12-19
Using GParted, I made it all unallocated, ran the recovery and I think it all worked. Now however, it doesn't load the boot loader, but gives me the following error message instead:



GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17



How do I correct this error? Would installing Ubuntu replace whatever boot loader it tries to install or can I just delete it?



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadad1f1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

---

### Post by darkod on 2009-12-19
When you say you ran the recovery, do you mean you installed vista from your recovery dvd? That should also overwrite grub on the MBR with the vista bootloader.
And yes, installing ubuntu next to your vista now (provided you do have vista restored on the computer) will write new grub bootloader on the MBR and it should work fine.

---

### Post by Bartender on 2009-12-19
> **Feilin said:**
> Using GParted, I made it all unallocated, ran the recovery and I think it all worked. Now however, it doesn't load the boot loader, but gives me the following error message instead:



GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17



How do I correct this error? Would installing Ubuntu replace whatever boot loader it tries to install or can I just delete it?



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadad1f1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

If you're seeing a GRUB Loading Stage 1.5, that tells us that GRUB Stage 1 is still on the MBR.  I know that you're confused right now, but it makes perfect sense.  The MBR is not erased when you go in and make the HDD unallocated.  

GRUB Stage 1 is going to sit there in the MBR until you reinstall Vista or root GRUB out via some other tool.  Maybe a Super GRUB Disc would do it, I don't know.  Or command line if you knew how.

But there's no need to root out GRUB.  

You were instructed to format to NTFS, not unallocated, and use your Vista recovery disc.  If you make an NTFS partition with GParted, then install Vista to that partition, Vista will go in and overwrite the MBR for you with it's data.

So go back and format to NTFS so that the Vista installer sees a partition that it can use.  If you're planning on reinstalling Ubuntu, here's an idea - decide how much space you want to give to Vista - let's say 50GB - create a 50GB NTFS partition, apply the change, get out of GParted and reboot with the Vista recovery disc in the tray.  The Vista recovery disc will recognize the NTFS partition and you can install to just that area.  Installing Ubuntu later will be much easier.  No screwing around with trying to shrink Vista.

EDIT:  Well, I'm not sure this all makes **perfect** sense.  If you reinstalled Vista, then the MBR should have been re-written with Vista's data.  Your fdisk -l indicates that the drive is all NTFS now, which is what we should see if you reinstalled Vista.  But the GRUB message is indicating that Vista didn't install correctly.  At least not what we would have expected.

If you think Vista is on there now, but it didn't rewrite the MBR for some reason, you could try repairing the MBR with [this]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").  But it might be just as easy to try installing Vista again.  Vista **should** re-write the MBR.

---

### Post by darkod on 2009-12-19
> **Bartender said:**
> 
So go back and format to NTFS so that the Vista installer sees a partition that it can use.  If you're planning on reinstalling Ubuntu, here's an idea - decide how much space you want to give to Vista - let's say 50GB - create a 50GB NTFS partition, apply the change, get out of GParted and reboot with the Vista recovery disc in the tray.  The Vista recovery disc will recognize the NTFS partition and you can install to just that area.  Installing Ubuntu later will be much easier.  No screwing around with trying to shrink Vista.

It makes perfect sense except hte OP is calling the vista dvd recovery disc, not install disc. Depending whether it's just bad wording, a recovery dvd will probably wipe the hdd and create "factory setup". And shrinking would be necessary.
In case you do have vista dvd definitely do as Bartender says, much better for you.

---

### Post by Bartender on 2009-12-19
darkod -
I haven't seen it with my own eyes, but pretty sure this works even with a recovery disc.  The recovery disc still looks for NTFS, and the way it was described to me by the guy who did it, the recovery disc ignored the rest of the HDD.

I guess I should try to find out for sure but I don't have a Vista PC handy for this experiment!!

I could try it with my Acer laptop recovery discs on a test PC...  I'm sure it wouldn't install correctly but I might be able to get to the partitioning part.

---

### Post by Feilin on 2009-12-19
Now I got everything working; I created an ntfs disk of 70 GiB, recovered it with my Vista recovery disks, and then installed Ubuntu on the remaining part. But Ubuntu still wont let me install things... I'm really confused; when I try to update, install or even remove program, I get this message:



E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



...along with:



Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.



...and another message saying it's not genuine or something (this only happened once, for some reason, as a crash file). Why is it doing this to me even though it's a mint installation? Though, more importantly, what should I do?

---

### Post by sgosnell on 2009-12-19
Do what it says.  Type ```
sudo dpkg --configure -a
``` into a terminal.  First, make sure no other instance of apt-get is running.  This includes update manager, synaptic package manager, gdebi package installer, add/remove programs, and anything else that might download and/or install packages.  Only one can run at the same time, and they're all gui front-ends for apt-get.

---

### Post by Feilin on 2009-12-20
It gives me this:



dpkg: dependency problems prevent configuration of konquest:
 konquest depends on libkdegames5; however:
  Package libkdegames5 is not installed.
dpkg: error processing konquest (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 konquest




Also, before I got this when surfing and firefox wanted me to install flash:



Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by sgosnell on 2009-12-20
Konquest is the KDE file browser.  Why do you want that, unless you're installing the KDE desktop?

As for the rest, do what they ask - run those commands in a terminal, exactly as given.  Make sure your /etc/apt/sources.list file is sane, and run Synaptic and have it fix broken packages.  You've tried to install something that went wrong, either because of trying to install through two different package installers, or because the installer crashed or was interrupted.  That's no mint installation.

---

### Post by Feilin on 2009-12-20
Actually, Konquest is supposed to be a game... Well, I admit shining greener than a glow-the-dark light stick, but at least I'm learning now.

Anyhow, I did what you said, and yes, to experienced Linux users, that might be obvious to just follow the instructions the messages gives you (as it's actually on the user's side, in contrast to Windows where every day is a struggle against the hardware doing things you don't want it to). I have managed to install and updated stuff now, so I'm gonna try and update to 9.10, but unfortunately I've come to realise Chinese internet connections are somwhat... slow at best, unstable or nonexistent at worst. So far so good, and I'll see in a few hours if it manages to patch me with the latest stuff.

No matter how it goes, I've learned a lot and thanks everybody who contributed to that! I'd like to repay it, but I suppose the best way of doing so is just using Ubuntu in the future.

---

### Post by jocko on 2009-12-20
> **sgosnell said:**
> Konquest is the KDE file browser.  Why do you want that, unless you're installing the KDE desktop?

As for the rest, do what they ask - run those commands in a terminal, exactly as given.  Make sure your /etc/apt/sources.list file is sane, and run Synaptic and have it fix broken packages.  You've tried to install something that went wrong, either because of trying to install through two different package installers, or because the installer crashed or was interrupted.  That's no mint installation.
Konqueror is the kde file manager, konquest is a game for kde.

---

### Post by Bartender on 2009-12-20
That capital "K" threw me too.  I knew it didn't sound quite right but I was thinking KDE package also.

To the OP - I wouldn't be in a big rush to upgrade to 9.10.  I think you'd be happier with 9.04.  I was excited to install 9.10 over 9.04 but 9.04 is working fine for us and I keep hearing about things that worked in .04 and aren't working in .10.

In other words, if it ain't broke don't fix it.  You can have plenty of fun with .04 while the devs work on making sure that the next release of Ubuntu is as trouble-free as possible.  There's extra motivation to do that since the next version will be long-term release.

Glad to hear that you tried the NTFS partition thing.  I needed someone to verify that's a legitimate procedure!  :)

---

### Post by jimpr13 on 2009-12-20
> **jocko said:**
> Konqueror is the kde file manager, konquest is a game for kde.

yes i agree but only in kde environments.for example at xfce it doesnt run

---

### Post by sgosnell on 2009-12-20
> konqueror is the kde file manager, konquest is a game for kde.duh!!

---

