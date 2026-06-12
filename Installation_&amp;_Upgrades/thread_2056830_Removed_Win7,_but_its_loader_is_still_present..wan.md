---
title: "Removed Win7, but its loader is still present..want to remove it"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2012-09-12
Hello everybody,

I removed Win7 when I took the big leap to shift from Windows to GNU/Linux.

In the process of removing, I think Win7's loader remained in the memory and its still present in the memory. :(

Whenever I boot the laptop, it comes as the last option at the booting screen where options have to be chosen among what to select. It says as "**/dev/sda5 Windows 7 Loader**" and is the last option.

Please help somebody in removing the Win7's loader and_ please tell if I remove the loader will it affect my Ubuntu OS or not_??? I think it should not affect but asking as to confirm from experts.  :)

---

### Post by cortman on 2012-09-12
Have you run

```
sudo update-grub
```

---

### Post by Mark Phelps on 2012-09-12
If your PC came with Win7 preloaded, then it had the Win7 boot loader in its own partition -- which you probably did not remove when you removed Win7.  Thus, when you reboot, that partition is still there and the loader is still available.

Running update-grub at this point will only see the same Loader.

You need to remove the Windows boot partition -- that will remove the boot loader.  Then, while still in Ubuntu, THEN do the update-grub command.  When that runs, you should NOT see it find the Windows Loader anymore.

When you reboot, you should be OK.

---

### Post by satyamM on 2012-09-12
> **Mark Phelps said:**
> If your PC came with Win7 preloaded, then it had the Win7 boot loader in its own partition -- which you probably did not remove when you removed Win7.  Thus, when you reboot, that partition is still there and the loader is still available.


Yes I did not remove loader and yes it is in a separate partition. You can see attached screenshot which tells the result of sudo update-grub

> **Mark Phelps said:**
> 
You need to remove the Windows boot partition


How to do that??





Here is the result of sudo update-grub

---

### Post by Ubunterrific on 2012-09-12
There'll be a specific grub file you can omit the windows part out of. 
Would anyone else here simply recommend navigating to /boot (e.g. through the command 'gksu nautilus') and just deleting the windows loader file(s) there?

---

### Post by oldfred on 2012-09-12
That may be the recovery partition. Always best to make the recovery set of DVDs before deleting that partition. But once you have one or two sets so if later you want to reinstall or sell system with Windows you have a way.

Or you can use grub customized to hide the entry.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

---

### Post by satyamM on 2012-09-12
> **oldfred said:**
> That may be the recovery partition. Always best to make the recovery set of DVDs before deleting that partition. But once you have one or two sets so if later you want to reinstall or sell system with Windows you have a way.

So you mean to say that if I I removed this Loader and do not keep its copies then I will never be able to install Windows with a cd of Windows.........unless I get a Win7 loader copy from a friend of mine????
Is that what you mean??

---

### Post by darkod on 2012-09-12
No, you can always install windows with a windows media (cd/dvd).

This looks more like the small system reserved partition, than to a recovery partition. If you look at the size it will tell you more. The system reserved is approx 100MB - 200MB, and the restore partition much larger.

If it's the system reserved, you can delete it right away since without the main win7 partition it's worthless. After that the update-grub will remove the loader entry.

---

### Post by oldfred on 2012-09-12
Vendors do not supply a installer of Windows but an image of the hard drive as purchased. That image will include any special drivers required to run your system. 

If you have a new legal copy of Windows (not your neighbours) you should be able to install that with its serial number, but will still have to download drivers from the vendor & reconfigure system.

If you friend just has an image from his system, it will only work on his system anyway. It is not an install disk.

---

### Post by satyamM on 2012-09-12
> **darkod said:**
> No, you can always install windows with a windows media (cd/dvd). 
But I guess that in this guess, I have to re-install Drivers and all. I think loader is containing all my drivers' installations and other things of Win7.
Correct me if I am wrong.
[/QUOTE]

> 
This looks more like the small system reserved partition, than to a recovery partition. If you look at the size it will tell you more. The system reserved is approx 100MB - 200MB, and the restore partition much larger.
How to check what size it has taken on my Hard Disk? What is the command to see that? Plus if that's a system reserved partition, then will I able to format it or it will remain there?

> 
If it's the system reserved, you can delete it right away since without the main win7 partition it's worthless. After that the update-grub will remove the loader entry.How to delete it right away. Just tell me the process.

---

### Post by satyamM on 2012-09-12
> **oldfred said:**
> Vendors do not supply a installer of Windows but an image of the hard drive as purchased. That image will include any special drivers required to run your system. 

If you have a new legal copy of Windows (not your neighbours) you should be able to install that with its serial number, but will still have to download drivers from the vendor & reconfigure system.

If you friend just has an image from his system, it will only work on his system anyway. It is not an install disk.


I am in no mood to install windows again in my system. So better remove its loader too, plus if by chance, I have to install it, I will install drivers from internet. Am in right on this? 

Next, how to remove this loader, just tell me the process, as it may be occupying large memory....OR first tell me the command to see what amount of memory is this occupying, if not more than 100MB or 150MB then I can bear to keep it in my system.....

So 2 things::
1. command to see size of it..or size of each partition as it's also a partition (right?)
2. removal process of it.

.

---

### Post by oldfred on 2012-09-12
From Ubuntu to see sizes:

sudo fdisk -lu

But visual from gparted is usually better. And often you need to run gparted from a liveCD as some partitions are mounted and with liveCD then most are not mounted. But with liveCD the swap partition is often mounted and you still have to click on it in gparted and right clip swap-off. The you can edit partitions at will.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by darkod on 2012-09-12
Like oldfed says, best way to check partition sizes is running in terminal something like (I like the parted option better):
```
sudo parted -l
sudo fdisk -lu
```

If parted shows that the sda1 partition is very small, that would be the win7 system reserved partition. And yes, you can delete it even when it says system reserved, because that title is from win7 point of view, and you don't even have the OS any more.

If you prefer working with GUI tools, you can open Gparted and delete it, or do it with parted in terminal. Under the assumption that the partition is sda1, the parted procedure would be something like:
```
sudo parted /dev/sda
rm 1
quit
```

Be CAREFUL, since that WILL delete partition #1 on disk /dev/sda. Do it only if you are sure!

---

### Post by satyamM on 2012-09-12
Okay..I am attaching screenshot of result of   "" sudo parted -l ""  ...and tell what do ....
I think ** #1 is the one which you are referring to**.....
..
..

---

### Post by darkod on 2012-09-12
Yeah, that's only the win7 system reserved. You are OK deleting it.

You can use the command above or Gparted if you want GUI.

---

### Post by satyamM on 2012-09-12
> **darkod said:**
> Yeah, that's only the win7 system reserved. You are OK deleting it.

You can use the command above or Gparted if you want GUI.

How are you sure that it is the #1 is the one containing Win7 loader.....is it the name of file system which tells that it's Win7's or anything else?

---

### Post by darkod on 2012-09-12
Look at your screenshot in post #4. It says Found Windows 7 loader on /dev/sda1. It tells you the exact partition.

The only dilemma was whether it's the small win7 boot partition or the larger restore partition which also has boot files (loader). Being only 105MB it's definitely the small win7 boot partition.

---

### Post by satyamM on 2012-09-12
> **darkod said:**
> Look at your screenshot in post #4. It says Found Windows 7 loader on /dev/sda1. It tells you the exact partition.

The only dilemma was whether it's the small win7 boot partition or the larger restore partition which also has boot files (loader). Being only 105MB it's definitely the small win7 boot partition.


OK. Yeah, now it makes sense. Thanks for helping darkod.
Anyways, if it's just 105M, I am in no mood to remove it. Because it won't make much effect, so better keep it.

Plus, one more query :: Can this Win7 loader be helpful in  installing Windows again if I decide to install Windows again ? I mean does it contain drivers for Windows or what? OR is it useless?

---

### Post by darkod on 2012-09-12
No drivers, pretty much useless. It contains few boot files that would install new with the new install anyway.

You can keep it, as long as you know that the win7 present in the boot menu doesn't work. :)

You can even disable the os-prober in ubuntu, so that it doesn't report the win7 loader files. In that case the grub2 boot menu won't even show since you have only ubuntu. Right now it thinks win7 is there too:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

---

### Post by satyamM on 2012-09-12
Okay...that solves my problem.

I am gonna keep it for some days....and later when I change my mind I will remove it...

Thanks again for the help. =D>=D>=D>

Thread Solved.  :guitar:

Bye. ):P

---

