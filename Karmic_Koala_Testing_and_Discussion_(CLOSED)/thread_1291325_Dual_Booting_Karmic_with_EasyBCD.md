---
title: "Dual Booting Karmic with EasyBCD"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by the.lost.one on 2009-10-14
I installed Karmic (Ubuntu 9.10) and I installed grub on the partition where I installed Karmic so that my Windows mbr is not disturbed. Here's the tutorial I used [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

This worked perfectly with Jaunty 9.04. But because of grub2, I can't boot into Karmic.

Right now I have Vista, Win7 and Karmic installed with Karmic not being able to boot.

**What are the steps to make Karmic dual boot like Jaunty could with Windows?**

---

### Post by sgage on 2009-10-14
You need to a) have the latest beta of EasyBCD and b) have Karmic installed on a primary partition.

I have Karmic on /dev/sda2, and it works fine, just like it used to pre-grub2.

---

### Post by the.lost.one on 2009-10-15
I have EasyBCD 2.0 build 64. It doesn't have Grub2 option.

1. Did you upgrade your earlier distro to Karmic or directly install Karmic?

2. <s>I installed Karmic on the partition where Jaunty was installed (and dual booted perfectly) which was installed on free space (not unallocated tho). Is that primary enough?</s>

I checked from Win 7 disk management, I have installed Karmic on primary partition.

---

### Post by philinux on 2009-10-15
My ubuntu 9.10 on the lappy with ubuntu is installed in a logical partition sda5

Even the beta does not like grub2 or ext4

---

### Post by the.lost.one on 2009-10-15
So I presume there is no way of dual booting Karmic with Windows using Windows boot loader?

---

### Post by null_pointer_us on 2009-10-15
I remember EasyBCD being a totally buggy mess to work with.

Uninstalling/reinstalling that neogrub thing it comes with, along with deleting and re-adding boot entries (instead of just changing their settings) would usually get things working.

Eventually, I just gave it up and installed grub into the MBR, then used trial and error to create a working Windows boot entry in grub. It looks like grub 2 is supposed [to do this automatically]("http://ubuntuforums.org/showthread.php?t=1195275").

Fixing Vista's MBR is [fairly easy]("http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/"). Windows 7 is just [a little more difficult]("http://www.ehow.com/how_4836283_repair-mbr-windows.html") for some reason.

---

### Post by philinux on 2009-10-15
> **the.lost.one said:**
> So I presume there is no way of dual booting Karmic with Windows using Windows boot loader?

I did a jaunty install which of course has legacy grub. I used the ext3 file system, then upgrade to karmic. ```
update-manager -d
```

Home is on it's own partition. Easybcd happy again. 

And I know where you're coming from. I have 5 users of this lappy, not mine by the way, all vista msn messenger addicts, and I did not want grub bootloader. My choice on this machine as I play linux on it when away from home.

---

### Post by volcan_hacker on 2009-10-22
You can solve the problem without EasyBCD, using grub2 only. I had similar problem so posting here how i solved it.

**Problem:**
[I]I had Vista installed on sda1. I installed Karmic Koala 32bit beta on sda8 with ext4 and grub2. grub2 was written on MBR. And my Vista OS was gone, not listed on the the grub2 boot menu as expected. So I had to figure out how to add it there.
[/I]
**Solution:**

Get UUID of /dev/sda1 partition, where the Vista OS resides. Run this command and read the output,

```
sudo blkid
```

Edited /etc/grub.d/40_custom,

```
sudo gedit  /etc/grub.d/40_custom
```

Then added these lines at the end of this file,

```
menuentry 'Windows Vista'{
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set <UUID of my /dev/sda1 partition>
chainloader +1
}
```

saved the file, and run this command to update grub2 config,

```
sudo update-grub
```

Now I can restart and select Windows Vista from the grub2 menu to load Vista.

Hope this helps others. 

Helpful link:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by thecow on 2009-10-22
Will that work with Win 7?  And I assume using ext4 would be irrelevant to that procedure correct?

---

