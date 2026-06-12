---
title: "Kubuntu Edgy: swap failed when awaken from hibernate"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Seva on 2006-10-29
My swap failed on Edgy when latop resumes from hibernate. I got
```
Activate swap:  [fail]
``` 
on boot. After typing
```
sudo swapon -a
```
I got
```
invalid argument: /dev/sda2
```
After "mkswap /dev/sda2" following "swapon -a" it works fine - but it failed after  hibernate again!
I'm using pre-uuid /etc/fstab now.
Strange but /var/log/boot always says:
```
Activating swapfile swap...       
[ ok ]
```

Any advice what happens?

---

### Post by K0LO on 2006-10-29
The resume from hibernation is failing and this leaves the swap partition marked somehow as "corrupt" so that upon rebooting, the swapon fails.

I had to troubleshoot the hibernation problem on my machine to fix this. If I recall correctly, I was using klaptop to do power management and I did not have ACPI turned on. After fixing this (and fixing the swapfile for the umpteenth time) then it started working.

Eventually I removed klaptop and replaced it with the newer power management package, kde-guidance-powermanager, and that works also.

---

### Post by 56phil on 2006-11-17
First you need to restore swap:
```

sudo mkswap /dev/'swap partition'
sudo swapon -va

```
edit your /etc/fstab file
```

gksudo gedit /etc/fstab

```
when you edit your /etc/fstab file make sure that your swap partition has the new UUID.
```

UUID='your correct swap UUID' none swap sw 0 0

```
edit your /etc/initramfs-tools/conf.d/resume file
```

gksudo gedit /etc/initramfs-tools/conf.d/resume

```put this line in your /etc/initramfs.d/resume file
```

RESUME=UUID='your correct swap UUID'

```
and make this entry:
```

sudo update-initramfs -u

```

Now, you should be able to hibernate, resume and keep your swap file intact.

---

### Post by jhkuo on 2006-12-06
The instruction helped me to get hibernate working on my laptop, thanks!

---

### Post by sledhead45 on 2007-02-05
worked for me also on a averatec 3715. . thansk :)

---

### Post by schucki.be on 2007-02-07
Thnx!
Worked for me on a HP/Compaq nx9030 too.:)

---

### Post by mansu on 2007-02-12
Thanks for the solution. My hibernate broke when upgrading to edgy from dapper.

It works for Acer travelmate too except for one caveat.
swapon -va doesn't work right away. It fails wth the following error. /dev/hda10 is my swap partition.

```

sudo mkswap /dev/hda10
<gives a UUID>
sudo swapon -va
swapon on /dev/disk/by-uuid/39526914-4d99-4eb1-8450-c0c66ae257fa
swapon: cannot stat /dev/disk/by-uuid/39526914-4d99-4eb1-8450-c0c66ae257fa: No such file or directory

```

To alleviate the problem you have to manually create the symlink after mkswap and then run swapon -va.

```

suman@mansu:/dev/disk/by-uuid$ sudo ln -s /dev/hda10 ./751d0c53-880f-400f-8c15-a4cd33ed69d1
suman@mansu:/dev/disk/by-uuid$ sudo swapon -va 

```

After this follow the other steps mentioned in the post by 56phil.

More info on this bug [here]("https://launchpad.net/ubuntu/+source/util-linux/+bug/66637").

---

### Post by rosieg on 2007-03-02
Worked for me too - thank you :-)

---

### Post by smokeyd on 2007-04-23
This also was the solution for my Acer TravelMate 2420! Thanks! Boy I love Ubuntu, the very few things that do not work out of the box or with a few gui settings have been described on the fora :)

---

### Post by CyberRaven on 2007-05-24
Had the same issue on my ThinkPad X41, running Kubuntu 7.04 with 2.6.20-15-generic, but I was delighted to find that 56phil's method worked for me as well! Cheers, 56phil!

Btw, I recon this issue is related to/caused by the bug concerning swap partition changing uuid;
[https://bugs.launchpad.net/ubuntu/+bug/105490](https://bugs.launchpad.net/ubuntu/+bug/105490)

See also [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637), especially [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637/comments/23](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637/comments/23) (which more or less describes the same solution as 56phil).

Anyhow, thanks again for learning me something new about, and at the same time renewing my love of, (k)ubuntu/linux! :-)

---

### Post by dskloet on 2007-05-28
This thread has helped me before but recently hibernate stopped working for me again and I can't get it to work anymore. I upgraded to Fiesty recently but I have used hibernate on Fiesty before it broke. I use kernel 2.6.20-16-386 now but I also tried an older kernel again to see if that might work.

Anything else I could try? Or is there maybe a way to start from the beginning (other than a complete reinstall) because I'm not sure if I broke anything while trying all kind of different things in fstab and initramfs and such. Trying to hibernate doesn't always corrupt my swap partition, btw, I just can't return from it (it will just boot).

My laptop is a Fujitsu Siemens Lifebook S6120 and my /etc/fstab looks like this since I tried my pre-uuid version to see if it works:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /media/windows  ntfs    ro,noauto,user,fmask=0111,dmask=0000        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/usb      vfat    user,noauto     0       0

```

Any help would be very much appreciated.

---

### Post by win2456 on 2008-03-25
WOW!  This fixed the issue on my Dell D830 so quickly!  Now I can hibernate easily.  Here are the specs of what I'm running:
-D830 2GB RAM
-Gutsy Gibbon (Ubuntu 7.10)

What was happening was that I would try to hibernate and my system would crash.  The problem here was that the swap partition was smaller than the amount of ram.  This is how I fixed it:
-use LiveCD and run gparted
-resize the swap parition
-after resizing is finished, make sure you change the swap to "on" (you can right click the newly resized swap partition and go "swap on")
-then you have to reboot and modify the UUID in the /etc/fstab file.  Make sure you set the UUID to the one retrieved using the following command:
ls /dev/disk/by-uuid/ -alh
*NOTE: you need to edit the fstab file using SUDO

okay, after you've completed all of this, run the partition editor this time from the normal OS (no need to boot from LiveCD).  Make sure the swap partition is there and it's on.

-REBOOT

after finishing reboot, you can go ahead and replace the UUID in:
gksudo gedit /etc/initramfs-tools/conf.d/resume

don't forge to run:
sudo update-initramfs -u

final step, make sure that the UUID matches in the fstab and resume file.  now shutdown and start up your system.  Go ahead and hibernate!  you'll love it! :)

*another note:  hibernate works flawlessly if I click on the power button from ubuntu and then hibernate.  I have my "close lid" option set to hibernate but it seems to not work sometimes (system stays on) <- but this used to happen in XP as well, so I'm not worried.

Hope this works and thanks a bunch to 56phil for the magic instructions! :)

---

### Post by win2456 on 2008-03-28
i wanted to post an update.  after hibernating several times, i've seen that system still hangs at the blank screen sometimes when preparing to hibernate.  To troubleshoot, I ran this command below before hibernate and i get a perfect hibernate everytime.
sudo update-initramfs -u

any idea on how to automate this everytime i hit the hibernate button?  is there a hibernate script somewhere?

---

