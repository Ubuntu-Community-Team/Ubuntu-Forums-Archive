---
title: "Grub menu does not point to latest kernel"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by virgil_machine on 2012-12-25
Running Precise, 12.04.1 64-bit, I apply updates whenever update manager tell me there are some.

sudo update-grub shows me I have kernels 3.2.0.30 through 35 installed, but uname -r shows that I am running 3.2.0.29, which it what the startup messages tell me.

gksudo gedit /boot/grub/menu.lst shows 3.2.0.29 as the latest, plus several 2,6.blah.blah versions

Any idea what's going on?

My vms running under virtualbox boot 3.2.0.35...

---

### Post by oldfred on 2012-12-25
I do not know about virturalbox.

But you should not really have menu.lst. That is from grub legacy and Ubuntu has used grub2 since 9.10. Only if you upgraded from 9.04 or forced the install of old grub would you have it.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by virgil_machine on 2012-12-26
Thank you.  It will take me some time to get to this.  I will post the report here when I'm done.  

I assume that you mean to create the summary and post that, not do the recommend repair--correct?

---

### Post by darkod on 2012-12-26
I suggest you simply remove both grub1 and grub2, and install grub2 again. You seem to have a mix up of grub1 and grub2, so it's not using grub2 fully as it should.

If you want to do this, we can post the commands to run.

---

### Post by grahammechanical on 2012-12-26
If we upgrade from a version of Ubuntu that is using Grub legacy to a version of Ubuntu that is using Grub 2, then the menu.lst is still in /boot/grub with all the references to the kernels that were there before the upgrade. To put it another way, the change-over to Grub 2 does not delete menu.lst. Onlt a fresh install with a format will delete menu.lst.

You may be looking at an obsolete script. When you are at the Grub menu with Ubuntu selected press E. That will put Grub into edit mode. see, what kernel is actually being booted. Pressing Esc will back out of edit mode. Pressing F10 will boot the kernel being examined.

Also you can run System Monitor. That will tell you the actual kernel that is loaded.

Regards.

---

### Post by virgil_machine on 2012-12-26
Darkod and grahammechanical, thanks.

Yes, this was a distribution upgrade from lucid, and yes I figured there was some grub confusion.  It's possible that the initial upgrade got me to the .29 kernel and the others were added with update manager after the upgrade but not recognized by grub.

So, deleting both grub versions and installing grub2 makes sense to me.

I'll investigate that. 

However, I'll also do the Boot Repair thing oldfred suggested (may get me to the same place).  This is a learning experience.

---

### Post by virgil_machine on 2012-12-26
OK.  I ran boot-info, results here: [http://paste.ubuntu.com/1468525/]("http://paste.ubuntu.com/1468525/")

Looks like old grub is there.  Not sure what to do with most of the info, but the recommended repair sounds like what you guys think.

One question:  what are the risks of trashing my system by doing this?  I normally use clonezilla to create a backup image on a spare hard drive before major updates.  Sounds like that's a good idea here...am I off base?

Thanks again for the help.

---

### Post by darkod on 2012-12-27
I don't think the default recommended repair will sort it, because that's only a repair when it's not working. You need to purge the old grub and reinstall the new one. The is a purge option in the advanced settings of boot-repair, but I think it's better to do all this in terminal. Your system boots fine, and you know what you need to do.

I see boot-repair more as a tool for users dependent on GUI programs and not sure what to do or what is going on.

The chance to mess up the system is almost non-existent, having said that, something can always go wrong with technology. :) There is no 100% never. :)

I would boot the machine, and in terminal remove all grub, then reinstall grub2 and recreate the config files:
```
sudo apt-get remove --purge grub grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```

That should sort it out.

Just in case, have your ubuntu live cd at hand if things go wrong so you can boot with it in live mode. You can do repairs in live mode too, but since your system is booting right now, it's easier to do it from the running installation with the above commands.

You are free to try boot-repair if you want to. The above is only my recommendation.

---

### Post by virgil_machine on 2012-12-27
Thank you.  The boot-info also said:
> =================== Final advice in case of recommended repair
The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Is this something I need to do?

---

### Post by darkod on 2012-12-27
On older boards the BIOS couldn't boot the boot files if they are beyond 137GB on the disk. With a combination of a disk bigger than 137GB and an older board, you can hit this problem.

Boot-repair is only advising you of this potential issue, but since your BIOS currently boots the files just fine even when they are far from the beginning of the disk, I don't think you need to worry about it.

Otherwise, if this problem hits you, there is no easy fix. You will need to create one small /boot partition at the front of the disk to make sure the boot files always stay at front. Creating this partition means repartitioning the disk, which carries its own risk.

I wouldn't try this unless you really start having problems.

---

### Post by virgil_machine on 2012-12-27
Sounds good. I'll let you know how this works out (probably tomorrow--I will clone the system 1st and need time to do that).

---

### Post by virgil_machine on 2012-12-28
I clone the system from time to time to make sure I have a functioning image.  My existing backup was 4 months old (taken before I upgraded from lucid to precise), so it was time.

[BTW, I was reminded NOT to use a USB 2.0 drive (I have a n HD dock) as the target for clonezilla--takes twice as long--but I didn't feel like opening the case to hook up my spare drive and I didn't have an eSATA cable--doesn't pay to be lazy.]

Anyway, after cloning, I rebooted and followed darkod's instructions:
```
sudo apt-get remove --purge grub grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```


Went smoothly, and rebooted.  All the noise I was getting at startup went away--lots of messages about VMWARE (which I do not use) and something about the SCO Timer (or something). Now it just boots..takes me from the Ubuntu logo screen to the password screen to my desktop. ```
 uname -r
``` shows I'm now on kernmel version 3.2.0-35...so this is now done.

Thanks you all!

---

### Post by virgil_machine on 2012-12-28
One other thing:

I got rid of all the dpkg errors that showed up in the boot-repair log by
```
sudo dpkg --clear-avail
sudo aptitude purge virtualbox-2.0 virtualbox-2.1 virtualbox-3.0 virtualbox-3.1 
```

and for good measure
```
sudo apt-get autoremove
```

System *should* be cleaner

---

