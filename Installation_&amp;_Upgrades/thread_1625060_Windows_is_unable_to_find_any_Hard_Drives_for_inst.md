---
title: "Windows is unable to find any Hard Drives for installation!"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by zap_xlib on 2010-11-18
I had installed windows XP and then Ubuntu a few months ago. I was mostly using Ubuntu only. My Ubuntu is up to date. Windows XP got the blue screen and i had to re-install it. So, i used the Disk Utility and formatted my C-drive as NTFS with a boot flag. 

After that, when i attempted to install windows XP on my C-Drive that i just formatted, Windows Setup is unable to recognize any drives! :(

I really don`t want to uninstall Ubuntu or format my whole HDD, just to install windows XP. But i also want to install windows XP as i have to run some applications in it!. 

Any help is anticipated and appreciated!.

Thank you!.

---

### Post by sikander3786 on 2010-11-18
Please boot into Ubuntu and post the output of,

```
sudo fdisk -lu
```

And also note that after installing Windows, you'll need to re-install Grub in order to boot Ubuntu.

---

### Post by zap_xlib on 2010-11-18
> **sikander3786 said:**
> Please boot into Ubuntu and post the output of,

```
sudo fdisk -lu
```

And also note that after installing Windows, you'll need to re-install Grub in order to boot Ubuntu.

Hi!. Thanks for your reply... The output i got is below:


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5040503f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62910539    31455238+   7  HPFS/NTFS
/dev/sda2        62910540   125821079    31455270    7  HPFS/NTFS
/dev/sda3       125821080   167766794    20972857+   7  HPFS/NTFS
/dev/sda4       167768062   312580095    72406017    5  Extended
/dev/sda5       167768064   306589695    69410816   83  Linux
/dev/sda6       306591744   312580095     2994176   82  Linux swap / Solaris

```

---

### Post by sikander3786 on 2010-11-18
There seems to be a little problem regarding cylinder boundaries (??) but that should not be causing any problems to Windows.

Are you sure that drive doesn't need any extra drivers to be loaded for Windows? I have seen a few drives like that...

Might be some members comes up with some better answer. Wait and see. And in the mean while, it'd be better to post your query on some Windows forums as well as it seems to be a Windows specific problem to me.

Good Luck!

---

### Post by zap_xlib on 2010-11-18
> **sikander3786 said:**
> There seems to be a little problem regarding cylinder boundaries (??) but that should not be causing any problems to Windows.

Are you sure that drive doesn't need any extra drivers to be loaded for Windows? I have seen a few drives like that...

Might be some members comes up with some better answer. Wait and see. And in the mean while, it'd be better to post your query on some Windows forums as well as it seems to be a Windows specific problem to me.

Good Luck!

I don`t think there is any need for extra drivers to be loaded for windows. Yes, i would love to get a solution, or i might have to waste lot of time trying to remember what all packages i installed in UBUNTU, if i really have no other choice but to format the whole drive and re-install windows and then linux... 

Thank you for your time!.

---

### Post by coffeecat on 2010-11-18
@zap_xlib, are you using a Microsoft XP install disc or an OEM manufacturer's Windows restore/install disc? I calculate your NTFS partitions to be approximately sda1 - 30GiB, sda2 - 30GiB and sda3 - 20GiB. The Microsoft install disc should detect all three NTFS partitions and should be happy to install to a 30GiB one. But an OEM disc may have a minimal size constraint and may not be coded to give you a sensible error message if your NTFS partitions are too small for it.

---

### Post by zap_xlib on 2010-11-18
> **coffeecat said:**
> @zap_xlib, are you using a Microsoft XP install disc or an OEM manufacturer's Windows restore/install disc? I calculate your NTFS partitions to be approximately sda1 - 30GiB, sda2 - 30GiB and sda3 - 20GiB. The Microsoft install disc should detect all three NTFS partitions and should be happy to install to a 30GiB one. But an OEM disc may have a minimal size constraint and may not be coded to give you a sensible error message if your NTFS partitions are too small for it.

Yes, that is right!. 32, 32, 21. It is a restore/install disc as it does not detect any disc and all i get is some message like "Setup could not find any hard drives on this computer, please press F3 to reboot". From that point, i have no other option but to reboot.

---

### Post by coffeecat on 2010-11-18
> **zap_xlib said:**
> It is a restore/install disc 

I thought it might be. I've seen threads like this before. It must be that some restore discs will only work if the hard drive is in a certain configuration. Which is really very unprofessional work on the part of the responsible software engineers. You'd think at the very worst it would offer to reformat the whole disc for you. Not that that would help you.

The only thing I can suggest is to make one much larger NTFS partition, perhaps sda1, 2 and 3 combined to make ~80GB. If the restore disc is happy to use that you could then shrink the reinstalled XP down to 30GB again and re-create your sda2 and sda3.

Other than that, I don't know what to suggest - sorry.

**Edit:** one further thought. What make/model of computer is it? A google search might bring up things from people using the restore disc. That might give you some idea of how big a NTFS partition it needs - if indeed that is the problem.

---

### Post by zap_xlib on 2010-11-18
Oops... just forgot to attach an image, and made a double post. So, i`m editing this post...

---

### Post by zap_xlib on 2010-11-18
> **coffeecat said:**
> The only thing I can suggest is to make one much larger NTFS partition, perhaps sda1, 2 and 3 combined to make ~80GB. If the restore disc is happy to use that you could then shrink the reinstalled XP down to 30GB again and re-create your sda2 and sda3.

Hey, that`s a good idea!. I`ll certainly try it!.

Thank you very much!.

---

### Post by coffeecat on 2010-11-18
> **zap_xlib said:**
> Oops... just forgot to attach an image, and made a double post. So, i`m editing this post...

I see that the SMART status is reporting a few bad sectors. You might want to keep an eye on that and/or view all the SMART data in Disk Utility. This might mean the drive is on the way out and/or the bad sectors may be confusing the restore disc.

---

