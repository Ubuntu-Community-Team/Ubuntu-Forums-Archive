---
title: "Lucid doesn't Boot WinXPs Properly"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jbrice on 2010-03-30
Have installed Lucid Beta 1 on a multiboot system and done all available updates. It works fine and appears to have correctly identified the two WinXP installs on the hard drive, BUT booting either version of WinXP shown on the GRUB menu brings up "Windows XP Other Stuff"

I have tried doing an "update-grub" but the problem remains.

Here is the relevant area of the grub.cfg file:
```
menuentry "Windows XP Work (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 427c3e277c3e165f
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Other Stuff (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 427c3e277c3e165f
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

Any suggestions appreciated as to the best way forward from here.

---

### Post by coffeecat on 2010-03-30
You've got the same UUID in both stanzas. That can't be right. You might want to do a 'sudo blkid' to see what the UUIDs should be for sda2 and sda3.

Were those stanzas generated from /etc/grub.d/30_os-prober, or were you using your own 40_custom for the Windows entries?

---

### Post by jbrice on 2010-03-30
Thanks for the reply. 

> **coffeecat said:**
> You've got the same UUID in both stanzas. That can't be right. You might want to do a 'sudo blkid' to see what the UUIDs should be for sda2 and sda3.


It shouldn't be thus, but often is like this - so I understand - when the Windows multiboot is created with the help of a partition cloning tool, as was the case here.

This set up has worked fine in the past with previous versions of Ubuntu, and has only been fouled up with the arrival of GRUB2 on the machine. 

> Were those stanzas generated from /etc/grub.d/30_os-prober, or were you using your own 40_custom for the Windows entries?

That was auto created by "update-grub" - I haven't got to grips yet with customisation of GRUB2. 

As far as I can see, it either needs the UUID one WinXP partition to be changed (not straightforward I gather) or GRUB2 needs to be persuaded to boot by partition ref. (i.e. (hd0,1)) rather than UUID. However I cannot see how to achieve the latter.

PS - as a temporary fix I have commented-out a couple of lines of the grub.cfg file, and it now boots OK. But obviously not a permanent fix as the commenting will be undone on the next "update-grub":

```

menuentry "Windows XP Work (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
#	search --no-floppy --fs-uuid --set 427c3e277c3e165f
#	drivemap -s (hd0) ${root}
	chainloader +1
}


```

---

### Post by coffeecat on 2010-03-30
> **jbrice said:**
> It shouldn't be thus, but often is like this - so I understand - when the Windows multiboot is created with the help of a partition cloning tool, as was the case here.

Oh, I see. A clone/image of a partition would include the UUID. I did a bit of googling and came up with these:

[http://ubuntuforums.org/showthread.php?t=1240146](http://ubuntuforums.org/showthread.php?t=1240146)
[https://answers.launchpad.net/ubuntu/+question/47564](https://answers.launchpad.net/ubuntu/+question/47564)

However, a note of caution from a Microsoft page which has a downloadable Windows utility:

[http://technet.microsoft.com/en-us/sysinternals/bb897436.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897436.aspx)

> NT may become confused and think that the media (disk) has changed after a FAT volume id has changed and pop up messages indicating that you should reinsert the original disk (!). It may then fail the disk requests of applications using those drives."Windows **may** become confused..." :lol: I'd interpret that as saying that it might go into a fit of terminal sulks if you changed the UUID on the C:\ partition. Or perhaps not, but I thought I'd point that out.

> **jbrice said:**
>  or GRUB2 needs to be persuaded to boot by partition ref. (i.e. (hd0,1)) rather than UUID. However I cannot see how to achieve the latter.

I hope that's possible but atm I don't know how. You certainly had the option of either with legacy grub. If I find something I'll post back.

---

### Post by jbrice on 2010-03-30
> **coffeecat said:**
> 
"Windows **may** become confused..." :lol: I'd interpret that as saying that it might go into a fit of terminal sulks if you changed the UUID on the C:\ partition. Or perhaps not, but I thought I'd point that out. 
I'm very reluctant to change the UUID of the WINXP partitions as one of the curses of getting dual-boot windows to work is just that sort of confusion. Part of WinXP seems to use the DOS path to identify partions, and other parts use the UUID. So you can imagine the consequences that could arise from having two NTFS partitions and two instances of WinXp, and then changing an NTFS UUID on one of them!

> I hope that's possible but atm I don't know how. You certainly had the option of either with legacy grub. If I find something I'll post back.

Thanks again. Note that I have found a temporay fix - see my previous posting - but would like to get it sorted out properly.

---

### Post by kansasnoob on 2010-03-30
That is interesting. You see the older "legacy grub" did not use UUID's to identify Windows partitions.

I don't know if a person could write Windows boot entries for grub2 that did not include the UUID?????????

I may have to puzzle over this a bit.

---

### Post by coffeecat on 2010-03-30
> **jbrice said:**
> Thanks again. Note that I have found a temporay fix - see my previous posting - but would like to get it sorted out properly.

I *think* I've come up with a permanent fix for you based on your solution. I didn't realise that if you commented out the 'search....' line that the stanza would still work.

Anyway, make the 30_os-prober file inactive by:

```
sudo chmod -x /etc/grub.d/30_os-prober
```Then it will be ignored when update-grub is next run. Then add your custom stanzas to /etc/grub.d/40_custom and make it executable. Then run sudo update-grub.

The disadvantage of that is that you will need to add all other OS entries to your 40_custom file. If you were multibooting other Linux flavours/versions as well as Windows that gets to be a bit tedious.

More information here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by QLee on 2010-03-30
[QUOTE=kansasnoob]I don't know if a person could write Windows boot entries for grub2 that did not include the UUID?????????[/QUOTE]

Yes, you can also write device node or LABEL for that but I'm not sure if there is any way of making it persistant through a grub upgrade other than writing your own static entries and disabling OSprobe for the update. I'm not sure what disabling passing UUID to the system (in etc/default/grub) does, that might work.

---

### Post by kansasnoob on 2010-03-30
I posted the following query here:

[http://ubuntuforums.org/showpost.php?p=9049578&postcount=394](http://ubuntuforums.org/showpost.php?p=9049578&postcount=394)

> I ran into something interesting. Of course you know that grub2 now uses UUID's even for Windows partitions, whereas legacy grub only used the device name, eg: root (hd0,0).

Well here's someone that's cloned an XP and has two Win partitions with the same UUID:

[http://ubuntuforums.org/showthread.php?t=1442606](http://ubuntuforums.org/showthread.php?t=1442606)

I'm wondering if /etc/grub.d/30_os-prober can be edited in some manner to not use UUID's only for Windows????????????

I'll bet either Dave or Meierfra will know if /etc/grub.d/30_os-prober can be edited to not use UUID's for Win entries.

My thought is to keep grub2 as functional as possible, that is have it still look for UUID's for other Linux OS's and have it not use UUID's only for Win.

---

### Post by jbrice on 2010-03-30
Thanks all for your interest and support - will wait and see what comes of kansasnoob's posting in "grub2 basics".

---

### Post by QLee on 2010-03-30
[QUOTE=kansasnoob]
I'll bet either Dave or Meierfra will know if /etc/grub.d/30_os-prober can be edited to not use UUID's for Win entries.

My thought is to keep grub2 as functional as possible, that is have it still look for UUID's for other Linux OS's and have it not use UUID's only for Win.[/QUOTE]

Sure, one could make a change to that effect, however, then one would have a non-standard prober and would have to monitor that some upgrade did not revert to standard behaviour.

---

### Post by jbrice on 2010-03-31
At least for now, I am going to use a custom boot entry added to /etc/grub.d/40_custom  like this:
```
menuentry "Windows XP Work (USE THIS ONE)" {
	insmod ntfs
	set root='(hd0,2)'
	chainloader +1
}
```

It's possibly not the prettiest solution, but will suffice for this PC as I'm the only user.

---

