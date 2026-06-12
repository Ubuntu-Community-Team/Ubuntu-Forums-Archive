---
title: "No option to load ubuntu after duel boot windows install"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by sdschutter on 2008-08-22
Alright, I'm fairly new to Ubuntu, but not exactly a newbie.

I have one HD with two partitions: one for WinXp and all my media, the other for Ubuntu.  Anyway, I set them up a few months ago when I first started using Ubuntu.  After not booting into windows for 2 months I decided it was taking up too much space on my HD and deleted it manually while browsing it on the Ubuntu side.  I did this because I had no way of backing up my media and just wanted to clean the biggest windows out of there to make room for downloads.  Sloppy, I know.

Today I got a program that didn't work so great under Wine and was essential to my life; therefore, I decided to bite the bullet and reinstall windows on the old partition.  WinXP works fine; however, when I boot my computer it goes right into XP, no longer providing me with a prompt with both Ubuntu and WinXP as options.  

Please help, I am going through withdraw here.

---

### Post by SkonesMickLoud on 2008-08-22
Boot to the Ubuntu LiveCD, fire up a terminal and enter the following:

```
sudo grub
```

```
find /boot/grub/stage1
```

Which should return something along the lines of:

```
(hdx,x)
```

Then enter:

```
root (hdx,x)
```

```
setup (hd0)
```

Reboot and you've got grub back.

---

### Post by sdschutter on 2008-08-23
Thanks, that worked. 

Cheers.

---

### Post by realGaurab on 2008-12-09
I am having the same problem. I had ubuntu but decided to do make a dual boot and installed XP. Now I can't boot in ubuntu, there is no option at boot. 

I tried to do what SkonesMickLoud said but I got an error. My *find /boot/grub/stage1* displays *(hd0,6)*. 
[[IMG]http://img242.imageshack.us/img242/9659/screenshoteb8.th.png[/IMG]](http://img242.imageshack.us/my.php?image=screenshoteb8.png)

And when I restart, it will directly take me to windows.

One weird thing you can see in this screenshot is the partition editor says the entire hard disk is unallocated. Under places, however, all the partitions are available and all my data is in there too.

Thanks for help.

---

### Post by meierfra. on 2008-12-12
Please post the output of 

```
sudo fdisk -lu

sudo sfdisk -d /dev/sda
```

---

