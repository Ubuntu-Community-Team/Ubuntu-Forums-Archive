---
title: "[SOLVED] Usplash problems"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scottuss on 2008-10-14
Hi guys,

Just done a clean install of Intrepid, there were a few problems (my computer's internal speaker was beeping like crazy at boot up and shut down!) but that seems to be fixed after a few updates.

The main problem I have now is that on booting, there is no Ubuntu logo displayed with the progress bar (usplash?)

I am using quiet splash options in my menu.lst

Sometimes I see the kernel messages and bootup text but sometimes I get a red screen with characters flying down it.

Any ideas?

Thanks so much in advance!

---

### Post by WiFi Ed on 2008-10-14
No ideas or answers unfortunately, but I had/have similar symptoms. Like you, the manic beeping seems to have gone away for me, but I sometimes got the normal progress bar/logo screen, sometimes not. Since I like to see the bootup messages I turned off the quiet splash option so I don't know if the problem still exists.

---

### Post by kansasnoob on 2008-10-14
The only thing I can think of, and there's no reason it should happen on a clean install, is if the uuid's don't match between:

```
sudo blkid -c /dev/null
```

and:

```
cat /etc/fstab
```

Easy to check. Sample:

> lance@lance-desktop:~$ sudo blkid -c /dev/null
[sudo] password for lance: 
----I cut out some garbage here because it's a test drive-----
/dev/sda8: UUID="838a51e6-9e03-4a74-a861-e18983366fb0" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="9e452f2d-b79b-4f6a-818d-3a60f6aaf9bc" 
lance@lance-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=838a51e6-9e03-4a74-a861-e18983366fb0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=9e452f2d-b79b-4f6a-818d-3a60f6aaf9bc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
lance@lance-desktop:~$ 


---

### Post by autocrosser on 2008-10-14
I'm at work right now, but there is a on-going bug report about this--When I get home in about 4~5 hours from now I'll shoot you the link--there is a "fix"--requires some configure work & downloading v86d from Synaptic.

---

### Post by FuturePilot on 2008-10-14
This bug
[https://bugs.launchpad.net/bugs/279187]("https://bugs.launchpad.net/bugs/279187")

---

### Post by WiFi Ed on 2008-10-14
> **autocrosser said:**
> I'm at work right now, but there is a on-going bug report about this--When I get home in about 4~5 hours from now I'll shoot you the link--there is a "fix"--requires some configure work & downloading v86d from Synaptic.


Please post the link here in the thread:) I might want to try the fix...

Thanks

---

### Post by chuckyp on 2008-10-14
Confirmed your bug, I had the same issues when I upgraded to ibex today.

---

### Post by yakumo9275 on 2008-10-14
they are using an old v86d, I have same issue.

I pulled v86d from git and built latest sources, here is it attached. this fixes my bug.

unzip and put both files into /sbin (will need to sudo it). make sure they are executable.

I think intrepid is using v1.5, the git repo is at 1.9...

---

### Post by autocrosser on 2008-10-14
The main report is at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

Futurepilot---that report is almost the same as one I reported back in June: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

Both of these have relevance on the issue--the devs are working on it fairly hard....


> **WiFi Ed said:**
> Please post the link here in the thread:) I might want to try the fix...

Thanks

---

### Post by scottuss on 2008-10-16
Recent updates seem to have fixed this. Thanks everyone for your input! Intrepid has turned out to be awesome so far! :guitar:

---

### Post by Megatog615 on 2008-10-28
I just had this issue when upgrading to Intrepid(to beat the upgrade frenzy on the 30th). I still was required to install v86d. When I boot however, my box loses connection to my monitor(monitor goes into standby from no connection), and I hear one beep later in the boot process. The only way to boot is to actually disable usplash in GRUB, so I do not know if v86d actually fixed the problem I was having.

Possibly unrelated, but I was also getting buffer I/O errors on /dev/sr1(which is my DVD drive and I confirm a CD was inside when I got the errors). Why would something want to write to a read-only storage medium such as a CDROM during the boot process?

---

