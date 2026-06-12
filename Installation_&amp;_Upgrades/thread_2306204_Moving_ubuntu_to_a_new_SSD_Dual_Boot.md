---
title: "Moving ubuntu to a new SSD Dual Boot"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by tomas34 on 2015-12-13
Hi everybody,

I've been using Ubuntu  for a month, and I'm getting used to it. 
After looking on the forum, i feel like there is no post about my problem:

I have a laptop with a 500go SSD, with Ubuntu and windows on it (Dual boot) and a hard drive that can be used from both OS's. Since Windows takes a lot of space on the SSD ( i use it mostly to play since there isnt that much games on linux) i want to add an extra SSD so Ubuntu can have the space it deserves ( about 10go now, windows is using the rest).
So my question is : how to move ubuntu to the new SSD once installed ( to avoid doing my config all over again, it took me a lot of time)
I'm specially worried about the dual boot. when i turn my pc on, i have that purple  screen (GRUB?) where i choose the OS i want to use. I imagine that by moving ubuntu, there will be an issue when i start the computer ( like it doesnt find ubuntu and automatically starts on windows).

So could someone explain to me ( step by step, i'm neither an Ubuntu expert nor an english native speaker) how could i do that without messing with my pc?

thanks in advance!

---

### Post by Bucky Ball on 2015-12-13
Welcome. 

Well, to clone the Ubuntu partition you can use [fsarchiver]("http://www.fsarchiver.org/Main_Page") or [Clonezilla]("http://clonezilla.org/"). There are probably be others but those two are popular. There is also the very [easy rsync method]("https://frankfzw.wordpress.com/2014/12/23/migrate-ubuntu-14-04-from-hdd-to-ssd/") which you can do from a running install of the Ubuntu you're copying to the SSD, but if you have identical copies, one on the hard drive and one on the SSD, it can become problematic.

I'm guessing, and someone might be able to shed more light, that if you used this method to copy the Ubuntu install to the partition on the SSD, booted to the SSD and:

```
sudo install-grub /dev/sda 
```

... then install and launch Gparted and delete the old Ubuntu on the hard drive and then reboot it may just work. I'd be looking in that direction but more research required. 

I did pretty much exactly what you are doing just yesterday and I used the rsync method. I am currently posting from a Ubuntu install on my SSD which is identical to the one on my hard drive, but of course becoming less so the more I use it. But it is exactly the same. Same apps, settings, symlinks. Everything.

You will need to tweak /etc/fstab to get the partitions on the sda HDD to mount at boot once you are in the SSD install. 

These ideas are just a start. As I say, more research, and opinions from smarter heads than mine, required, but I know the rsync method works if you want to create an identical copy of your hard drive install on an SSD (and fsarchiver and Clonezilla do, to, I simply found the rsync method easier and quicker this time around but have successfully used the other two in the past) . :)

Hope that helps get the ball rolling ...

PS: Regarding the link to the rsync method, install the SSD and create a partition for your Ubuntu install prior to commencing at step 1.

---

### Post by oldfred on 2015-12-13
Is system newer UEFI or older BIOS?

I still suggest a new install, but then copy /home with rsync to new install. 
Your /home includes all your settings and configurations for installed apps. It also includes all your data.
If you have installed lots of apps, you can easily export list of apps and reinstall. List is long as it includes dependencies, but it will not reinstall any of the standard apps default system has.

I just did a test install of 16.04 from ISO on SSD to hard drive and it took 10 minutes including updates from network. I do have high speed Internet.
But that does not include the rsync of /home or install of my apps. Usually I can do the entire configuration in about an hour, but I have done it several times so easier/quicker each time.

With the copy of entire system, you have to be sure not to have duplicate UUIDs as that is not allowed. But grub uses UUID to know what to boot, so you also have to reinstall grub, usually Boot-Repair's full uninstall/reinstall is best. And you have to edit fstab with new UUID also or system will boot but use old install, which then gets new system out of sync and can create even larger issues.

---

