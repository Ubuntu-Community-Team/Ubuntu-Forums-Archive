---
title: "Can't Install 11.04 from disc at all"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by Throne777 on 2011-05-06
I've tried two discs now trying to fresh install 11.04 and the only thing it's done is crash. 
I can't 'Try Ubuntu' (it just crashes). And I can't install it either. Starts to copy files (if it manages to get to that point without crashing), after I've set up partitions and told it to wipe the partition where / is being installed, but I get an Input/Output error after about 25% of the way in the status bar. Like I said, I've tried two frshly burned discs and get the same thing each time.
I had got Unity working from upgrading from 10.10, so it's not like my hardware isn't supported.
So currently I have no working OS & can't even install a new one :s
Is it possible that I've got two dodgy discs?
I doubt it's because of a faulty hard drive. I ran a memtest using an opensuse CD and it passed with no errors.
Help!

---

### Post by Quackers on 2011-05-06
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok when booting from the cd and at the first purple screen (with the little stickman icon at the bottom) press any key. Choose your language and on the next screen you should see an option to check the cd for errors. Try that. If any error is reported the disc is no good. If the md5sum checks out ok but the disc is bad, try burning the image again at the slowest possible speed.

---

### Post by Dutch70 on 2011-05-06
<double post>

---

### Post by Dutch70 on 2011-05-06
I've seen people have trouble with certain types or brands of cd's, no idea why. I'm sure you are burning it at the slowest speed possible & checking it for defects after you burn it, right?

Your hard drive would not cause it to crash when running it from the cd in live mode.

Also, if you have a usb stick, it's much easier & faster.

Other than that, you may want to try downloading the "Alternate cd install" & give that a shot.

---

### Post by jramshu on 2011-05-06
I had a problem with a livecd in 11.04. I just re-burned it at a slower speed and that seemed to work for me. Also, I ran a lense cleaner disk too, just in case the lens was dirty. (I smoke so.....)

---

### Post by cpmman on 2011-05-06
Maybe no help for current situation but for future I always download any iso and then zsync it which not only does the MD5SUM check automatically but also downloads and corrects any discrepancy.  Starting with a known good file enables you to verify the disc burn.

A good method is also to install to an external disc first (they are so cheap nowadays) and gives you more confidence than a live disc does that it will work with your hardware - or at least point to where it needs tweaking - before committing to internal fixed disc.

---

### Post by Throne777 on 2011-05-06
Ran MD5Checksum; no errors.
Checked the CD; no errors.

And my computer's too old to be able to boot from USB.

---

### Post by cpmman on 2011-05-06
> **Throne777 said:**
> 
And my computer's too old to be able to boot from USB.

Try the Plop boot manager in my sig. it worked on my 9 year old Acer Travelmate.

---

### Post by dozycat on 2011-05-06
Try with another version, 10.04 is long service. or the netbook version. Or try damn small linux to see if it is a problem with your machine or memory.

---

### Post by Throne777 on 2011-05-06
> **dozycat said:**
> Try with another version, 10.04 is long service. or the netbook version. Or try damn small linux to see if it is a problem with your machine or memory.

Had to install 10.04, which installed without a hitch (as did openSuse a few days ago -like I said, I performed a memtest before installing opensuse which it passed). So there's nothing wrong with my hardware.

One of the times on the 11.04 it actually realised it had crashed and told me to 'file a bug report', which lead to much 'I CAN'T BECAUSE I DON'T HAVE A £$&*ING OPERATING SYSTEM!!' type rants, etc etc.

So the 11.04 has a fairly critical installation bug, it would seem.

---

### Post by Quackers on 2011-05-06
What is your current partition layout?
Please post the output of ```
 sudo fdisk -lu
``` in a terminal.

Or alternatively go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cpmman on 2011-05-06
> **Throne777 said:**
> Had to install 10.04, which installed without a hitch (as did openSuse a few days ago -like I said, I performed a memtest before installing opensuse which it passed). So there's nothing wrong with my hardware.

One of the times on the 11.04 it actually realised it had crashed and told me to 'file a bug report', which lead to much 'I CAN'T BECAUSE I DON'T HAVE A £$&*ING OPERATING SYSTEM!!' type rants, etc etc.

So the 11.04 has a fairly critical installation bug, it would seem.

So how are you posting?

Live CD?

Both upgrade and clean install have worked for me.

---

### Post by Throne777 on 2011-05-06
> **Quackers said:**
> What is your current partition layout?
Please post the output of ```
 sudo fdisk -lu
``` in a terminal.


```

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e017e01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        41947134   315643903   136848385    5  Extended
/dev/sda2   *        2048    41945087    20971520   83  Linux
/dev/sda3       315645120   321669494     3012187+  82  Linux swap / Solaris
/dev/sda5        41947136   315643903   136848384   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eabf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953519615   976758784    7  HPFS/NTFS

```

---

### Post by Throne777 on 2011-05-06
> **cpmman said:**
> So how are you posting?

Live CD?

Both upgrade and clean install have worked for me.

I was using my friend's PC to post at the time (he wasn't pleased because it meant tearing him away from EVE for half an hour :p). I'm now running 10.04.

---

### Post by Quackers on 2011-05-06
Thanks for the output.
I can't see anything from that that would lead to the installer crashing.
As you have checked the md5sum and the cd for errors the only thing that I can think of is that you could be getting a bad read from the cd. As was suggested earlier you could clean the laser on the cd drive. Even a dry lint-free cloth may do some good.
I notice that your sda2 partition is physically before the sda1 partition on the disc. I don't know that it could be a problem, but it is a little unusual.

---

### Post by dozycat on 2011-05-07
if do you have an usb memory around, create live ubuntu useb 11.04 with the iso 11.04 from ubuntu 10.04. Usually I keep 9.04 and 10.04 in usb around for testing and repairs, they can save your head.

---

### Post by linuxftw3 on 2011-05-07
> **Throne777 said:**
> Had to install 10.04, which installed without a hitch (as did openSuse a few days ago -like I said, I performed a memtest before installing opensuse which it passed). So there's nothing wrong with my hardware.

One of the times on the 11.04 it actually realised it had crashed and told me to 'file a bug report', which lead to much 'I CAN'T BECAUSE I DON'T HAVE A £$&*ING OPERATING SYSTEM!!' type rants, etc etc.

So the 11.04 has a fairly critical installation bug, it would seem.


11.04 has many, many, many, bugs.. downgrade to maverick it's much better :D

---

### Post by mörgæs on 2011-05-07
> **dozycat said:**
> Or try damn small linux ...

Damn Small Linux has been abandoned several years ago. Whatever you do to solve the problem, don't use obsolete software.

As you can see in post 7, this machine can not boot from USB.

---

### Post by dozycat on 2011-05-07
I still keep a copy around. too bad it is finished.

---

### Post by mörgæs on 2011-05-07
Throne777, did you try the alternate ISO as suggested earlier? 

Besides this, 10.04 is a great release. Except for the eyecandy, I do not see any reason for preferring 11.04 to 10.04.

---

### Post by mörgæs on 2011-05-07
> **dozycat said:**
> I still keep a copy around. too bad it is finished.

If you want something light, best is to pick from this list:

[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by dozycat on 2011-05-07
Thanks I will look, but you know in that list is  damn small linux.
But you are right we never must be afraid of trying something new only because we know something and we are already familiar with it.
That´s why I am going to give an opportunity to unity and to Gnome 3.0 if I can I have the opportunity.

---

### Post by Throne777 on 2011-05-07
> **mörgæs said:**
> Throne777, did you try the alternate ISO as suggested earlier? 

Besides this, 10.04 is a great release. Except for the eyecandy, I do not see any reason for preferring 11.04 to 10.04.

No I didn't. I'm sticking with 10.04 until 11.10 comes out. Think I'm going to wait for a lot of the Unity bugs to get ironed out.

10.04 is a great setup, like you said. Does everything I want it to do (except I can't get the latest VLC to compile :( ), it's lightning fast & it's really stable.

---

