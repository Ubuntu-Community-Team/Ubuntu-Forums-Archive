---
title: "one too many ubuntus"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by brook adams on 2010-02-09
Hi There,

I needed to install windows for some classes I'm taking. I used the partition editor to clear some space on the disk and installed windows 7.
This worked fine except that I could no longer boot ubuntu. So... I started ubuntu from a thumb drive and chose an option that would put grub back in place.

This also worked except that I unintentionally installed another ubuntu (an older version from the thumb drive). This version had just partitioned  enough space for itself and nothing else, so it runs out of disk space when it runs. It's boot loader however is the one my bios sees when I turn on the machine. 

I reconfigured the grub from this extra ubuntu to default to loading my original version and this works fine. I can load windows and either of the two ubuntus installed on my computer. But of course I don't need the second ubuntu, I just don't know how to get rid of it.

My question is... How do I get rid of the extra ubuntu and free up its 2.5 gig of space and get the boot loader for the original ubuntu to be the default when I turn on the machine?

Thanks folks

---

### Post by raymondh on 2010-02-09
> **brook adams said:**
> Hi There,

I needed to install windows for some classes I'm taking. I used the partition editor to clear some space on the disk and installed windows 7.
This worked fine except that I could no longer boot ubuntu. So... I started ubuntu from a thumb drive and chose an option that would put grub back in place.

This also worked except that I unintentionally installed another ubuntu (an older version from the thumb drive). This version had just partitioned  enough space for itself and nothing else, so it runs out of disk space when it runs. It's boot loader however is the one my bios sees when I turn on the machine. 

I reconfigured the grub from this extra ubuntu to default to loading my original version and this works fine. I can load windows and either of the two ubuntus installed on my computer. But of course I don't need the second ubuntu, I just don't know how to get rid of it.

My question is... How do I get rid of the extra ubuntu and free up its 2.5 gig of space and get the boot loader for the original ubuntu to be the default when I turn on the machine?

Thanks folks

Back-up your good/wanted ubuntu.

Try using gparted from a live session (thumb drive) to delete the unwanted ubuntu and put that space into the remaining ubuntu.  Afterwards, boot into the remaining Ubuntu and run

```
sudo update-grub2
```  (if using GRUB2, to reflect the changes)

If not using GRUB2 (and using grub-legacy) we may have to manually edit the menu.lst to delete the unwanted ubuntu from grub and then  'sudo update-grub' (no quotes).

References:

[http://ubuntuforums.org/showpost.php?p=7505203&postcount=1](http://ubuntuforums.org/showpost.php?p=7505203&postcount=1)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) 

Raymond

---

### Post by darkod on 2010-02-09
What Raymond said is generally true, but watch out for this:
If the unwanted install was the latest, the grub2 on the MBR is using the config files from there. When you delete the partition, don't expect grub2 to work and boot. But you can still reinstall grub2 on your MBR that will use the files from your wanted ubuntu. Either before or after you delete the unwanted partitions. Just follow the instructions from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

And next time you want to reinstall the grub bootloader use instructions how to reinstall just the bootloader. Don't install another ubuntu because of a new bootloader (grub2). It would have saved you a lot of hassle.

---

### Post by raymondh on 2010-02-09
> **darkod said:**
> What Raymond said is generally true, but watch out for this:
If the unwanted install was the latest, the grub2 on the MBR is using the config files from there. 

+ 1.  Thanks Darkod ... 'forgot about that scenario :)  Thanks.

Raymond

---

### Post by brook adams on 2010-02-09
Thanks darkod and Raymond

I'll try these steps and then add to this thread.

Brook Adams

---

### Post by brook adams on 2010-02-10
Success!

Thanks guys.

That was an interesting exercise. I read a lot of material about grub and was able to alter my menu.lst file and it works.

Of course when I upgrade I'll have to learn the new grub 2 stuff but I won't worry about that now.

Brook Adams

---

### Post by raymondh on 2010-02-10
> **brook adams said:**
> Success!

Thanks guys.

That was an interesting exercise. I read a lot of material about grub and was able to alter my menu.lst file and it works.

Of course when I upgrade I'll have to learn the new grub 2 stuff but I won't worry about that now.

Brook Adams

congratulations.  Glad you have that working out :)

GRUB2 is interesting.  I will admmit that I am still learning the syntax and 'flow' of grub2 .... having been accustomed to legacy .... but, it is interesting.  Seems less editing is required and, is more automated.

Raymond

---

