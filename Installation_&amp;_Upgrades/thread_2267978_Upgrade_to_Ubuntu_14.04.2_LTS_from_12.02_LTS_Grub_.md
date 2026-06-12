---
title: "Upgrade to Ubuntu 14.04.2 LTS from 12.02 LTS Grub broken"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2015-03-05
Hi There,

I am glad i am back here after a long long time...
I had a 12.2 LTS which i last week upgraded to 14.04 LTS.
Its a triple boot with MS XP, Ubuntu and Debian installed on a HDD, then i have another 2 HDD's for data and stuff.

I followed the install guide by clicking "something else" as i wanted to keep my existing /home data and install boot loader on a separate partition.
Everything went without any glitch but after reeboot i am stuck at grub rescue prompt.
Says "file not found" 

I tried reinstallng but still nothing. I tried searching for the /boot files withing grub by the "ls" and "ls (hd0,1)" commands
still not finding the boot.

Please guide me.

---

### Post by Bucky Ball on 2015-03-05
Welcome back. Try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). Use the recommended repair.

---

### Post by richlyn9 on 2015-03-05
I did try this out using both options,
however when i tried to install it did not find the source or something but it was not installed.
and i made a bootable pendrive however on restarting does not boot to it.

---

### Post by dino99 on 2015-03-05
sometimes a clean fresh install is more stable then a dist-upgrade.
actual grub (aka grub2/grub-pc) is way different that grub1 (aka legacy) and is supposed to be installed on the linux MBR partition. (aka /dev/sdx , with x=a -> z)

---

### Post by richlyn9 on 2015-03-05
Should i reinstall again just mentioning my home partition and leaving the rest to itself?

---

### Post by Bucky Ball on 2015-03-05
If you reinstall, it goes without saying, BACKUP any valuable data. 

That is drastic though, and a reinstall if very much the last resort.

> **richlyn9 said:**
> I did try this out using both options,
however when i tried to install it did not find the source or something but it was not installed.
and i made a bootable pendrive however on restarting does not boot to it.

Not sure if I understood this, but I'd perservere with trying to fix grub a bit more first. Perhaps boot into a Live desktop (from install media) and then install Boot Repair using [this]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") option rather than by creating a Boot Repair disk/USB, if that was what you were doing before.

You need to be online for this method. It installs the Boot Repair PPA so all dependencies and software will be there. Nothing should be missing this time. As you've not been able to use Boot Repair yet we don't know if it will fix your issue.

Once you boot to a Live desktop (Try Ubuntu), it is three commands:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

... then run Boot Repair. Hopefully I am not misunderstanding you and this actually helps.

---

### Post by richlyn9 on 2015-03-05
no worries...will try this and revert

---

### Post by Bucky Ball on 2015-03-05
Just a thought: Which OS was running grub? Debian or Ubuntu? It's generally the one that was installed last, unless you manually changed where it was going to install its grub.

---

### Post by richlyn9 on 2015-03-06
Last i installed debian, ao i am guessing debian.

---

### Post by Bucky Ball on 2015-03-06
Okay. Shouldn't matter. Try the instructions in post #6 and report back with your progress.

---

### Post by richlyn9 on 2015-03-07
Thanks guys for your assistance...This issue has been resolved.
I remade a bootable Pendrive from the iso and reinstalled keeping the home partition and directing the boot loader on the Sda drive.
Earlier i wanted the boot-loader to be installed on a separate partition which was causing an issues.
Will have to lookup grub2.
Thanks again and have a good weekend.

---

### Post by Bucky Ball on 2015-03-07
Good news. Enjoy. ;)

---

