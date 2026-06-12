---
title: "Partioning problem!"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by itz_speld_rong on 2011-09-01
I've been called to a friend's house to help him with his Apple Macintosh. Aparently, he was "just watching a video on youtube" when the screen went black with and gave him "some error." ](*,)

It currently boots into the grub menu, but chosing the default (standard boot) only gives me the same error message as the "recovery console." 

My solution? Reinstall.

_The problem?_ I select "Erase and use entire disc." And it detects the HD fine. Then I was just inputting the information (location, name, etc.) and this error popped up and interrupted me:

```
The ext4 file system creation in partition #2 of SCSI (0,1,0) (sda) failed.
```

I'm honestly not sure what to do about this. This drive is fairly new (4 months?), so to think it's a problem with the drive itself seems absurd, but I don't know what else it could be or how to fix this problem.

All of your help is greatly appreciated. Thank you!

---

### Post by dabl on 2011-09-01
This is a pretty good tool kit -- you'd have to boot it and look at the boot sector of the hard drive:  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

If you have a Live CD with Gparted on it, you could try making a new partition table, but that will render all data on the drive inaccessible.

---

### Post by itz_speld_rong on 2011-09-02
> **dabl said:**
> This is a pretty good tool kit -- you'd have to boot it and look at the boot sector of the hard drive:  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

If you have a Live CD with Gparted on it, you could try making a new partition table, but that will render all data on the drive inaccessible.

I honestly don't think there's any valuable data on the disc worth saving. So you'd recommend me using a partitioning tool? I honestly just don't understand why the install can't reformat the disc.

I think I've got it. I actually tried the "Advanced Partitioning" button during the installation process and then deleted the partitions myself.

Thanks for the idea. :P

---

