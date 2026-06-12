---
title: "Need Advice"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by JimmieC on 2010-06-24
I currently have two hard drives, windows xp on sda and Ubuntu 10.04 on sdb. I would like to take Ubuntu off and do a fresh install on my second hard drive.

I want to avoid a grub issue so, if on reinstall, I choose to install grub2 to mbr on sda will that stop XP from booting normally. I updated my Ubuntu from 9.10 to 10.04 and it caused a problem with my xp booting. That's why I'm asking. If I'm doing this the wrong way please advise. I have read many posts on this issue and I'm still confused.

Thanks,

Jim

---

### Post by varunendra on 2010-06-25
First of all, you don't need to reinstall Lucid if it is working fine.

Second, with both drives connected as they are, run and post the output (result.txt) of boot_info_script which you can download from [here]("http://bootinfoscript.sourceforge.net/").

Third, have you tried updating Grub2 after having difficulty with XP?
```
sudo update-grub
```

---

### Post by JimmieC on 2010-06-25
Sorry for not making myself clear. I fixed the boot issue so I now have a working machine. I want to do a fresh install because of a security reason and I want to avoid any grub problems. If I delete the partitions on my second hard drive and create new partitions do I install grub to the MBR of /dev/sda1 or to another location?

Jim

---

### Post by darkod on 2010-06-25
The grub "problem" comes up when you install it to the windows partition. In most cases, grub never goes to a partition, so that's the first rule you need to know when selecting where to install it. In linux /dev/sda and /dev/sdb are the disks, and if it has a number that's the partition number on that disk. So, never install it to /dev/sda1, or /dev/sdb5, etc.

But to give you more detailed advice, using first disk, second disk, etc is also confusing. Boot ubuntu and in terminal run:

sudo fdisk -l (small L)

That will list all disks and partitions. Post the results here and tell us what you want to do so we have a better picture.

---

### Post by varunendra on 2010-06-25
> **JimmieC said:**
> Sorry for not making myself clear. I fixed the boot issue so I now have a working machine. I want to do a fresh install because of a security reason and I want to avoid any grub problems. If I delete the partitions on my second hard drive and create new partitions do I install grub to the MBR of /dev/sda1 or to another location?

Jim
Quick answer to your question:
Assuming that XP is installed on sda [COLOR=DarkRed](*first hdd*)[/COLOR],  then you install Ubuntu 10.04 (Lucid) on sdb [COLOR=DarkRed](*second  hdd, deleting & recreating all the partitions on it*)[/COLOR]  while both sda and sdb are connected to the computer, then by default,  Grub would be installed on **MBR of sda**.

The MBR of XP would obviously be overwritten & there is nothing  wrong with it. Grub can take good care of it while installing itself.


But it seems that you are too afraid of your XP drive's MBR being overwritten by Grub. No problem! There are safe workarounds for you (although not as convenient as the one above). But, as darko already said, suggesting you a non-standard method without having a clear picture of your drives' current status can make you even more confused.

So if you want anything other than the above suggested quick answer or if you want clear & detailed description of whats & hows, then **please post here the result of the [boot_info_script.]("http://bootinfoscript.sourceforge.net/")**
It not only contains the sudo fdisk -l command suggested by darko, but also a lot more things that will give us a complete & clear picture of your drives & OS status. Run it while both drives are connected & you are logged into Ubuntu (whether from hard disk or a LiveCD session).


@darkod,
I'd suggest you to change the link of boot info script in your sig. to the one I provided above. It links to the page where the short guide about **How To Use Boot_Info_Script** has been provided.

---

### Post by darkod on 2010-06-25
> **varunendra said:**
> 
@darkod,
I'd suggest you to change the link of boot info script in your sig. to the one I provided above. It links to the page where the short guide about **How To Use Boot_Info_Script** has been provided.

Thanks.

---

### Post by JimmieC on 2010-06-26
Thanks for the responses. I've been away from my computer, sorry for the delay in getting back to you. If I can install grub to the MBR of sda without ruining my ability to boot XP then I'm good to go.

Jim

---

### Post by darkod on 2010-06-26
> **JimmieC said:**
> Thanks for the responses. I've been away from my computer, sorry for the delay in getting back to you. If I can install grub to the MBR of sda without ruining my ability to boot XP then I'm good to go.

Jim

You control where to install grub2 by clicking the Advanced button in the last screen of the installer. Make sure you select a MBR, and not a partition, there should not be a number in the device name.

---

### Post by JimmieC on 2010-06-26
Darkod,

Thanks for the help. The tip about the number clears things up for me. I knew that, but it didn't click until you stated it. Again, thanks.

Jim

---

