---
title: "Do not need new bootloader"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by donpedrodos on 2011-10-16
First it sounds strange, but this is the case.

I have a system with several partitions and my main partion that i use is a 10.04 LTS version.
Thisone is also in control of the bootloader.

On other partitions i also have have other versions of Ubuntu running.
This installation was done by selecting on the last page during the installation proces for not installing a bootloader anymore.
After that i corrected my fsab file to correct the UUID and i was ready.

But today i wanted to install Ubuntu 11.10 on a different partition, but during the installation proces there is no option anymore to install without bootloader.
I thought i found the solution by the dropdownbox to select on wich partition to put the bootloader on, but no option to skip installing a bootloader.

So my question is, is there any option possible that no bootloader is installed during the installation proces.

This option gave me in the past a lot of help, because i did not have to correct the main bootloader control.

I just want to keep my 10.04 LTS to be in control of the bootloader ... but now i have to pass the control to 11.10 ... obligated?

---

### Post by garvinrick4 on 2011-10-16
> I just want to keep my 10.04 LTS to be in control of the bootloader 
Boot into 10.04 after install of 11.10 and open a terminal and run this:
```
sudo grub-install /dev/sda
```
```
sudo update-grub
```
Now 10.04 is in control of grub.
And no there is no option to not install grub2 (grub-pc) in Ubiquity (Ubuntu installer)

---

### Post by haresear on 2011-10-16
Even though it is generally not recommended, I choose to install the bootloader (grub2) in the new-install partition. Even if it is unreliable, I figure it doesn't matter because I'm not planning on using it anyway. The only downside to this strategy is that you have to boot into the OS that has the controlling bootloader and update the boot menu before you can boot the new install. (Unless you first create an entry to chainload the bootloader in the new-install partition, which introduces the reliability risk).

---

### Post by donpedrodos on 2011-10-17
> **garvinrick4 said:**
> Boot into 10.04 after install of 11.10 and open a terminal and run this:
```
sudo grub-install /dev/sda
```
```
sudo update-grub
```
Now 10.04 is in control of grub.
And no there is no option to not install grub2 (grub-pc) in Ubiquity (Ubuntu installer)

That was the thing i was avoiding before, but it looks i have to go this way now to make the correct partition in control of my bootloader.

> The only downside to this strategy is that you have to boot into the OS that has the controlling bootloader and update the boot menu before you can boot the new install. 
That downside i was always able to avoid, but the way that garvinrick4 advices is the only way to correct it back.

Thanks for looking into in this matter, i was realy thinking i was overlooking an option during the installation, but apperantly not.

---

### Post by garvinrick4 on 2011-10-17
> Thanks for looking into in this matter, i was realy thinking i was  overlooking an option during the installation, but apperantly not. No you were missing nothing but only have to do it once so not to big a deal. Enjoy your Ubuntu donpedrodos.

---

### Post by mechanic on 2011-10-17
> **garvinrick4 said:**
> Boot into 10.04 after install of 11.10 and open a terminal and run this:
```
sudo grub-install /dev/sda
```
```
sudo update-grub
```
Now 10.04 is in control of grub.
And no there is no option to not install grub2 (grub-pc) in Ubiquity (Ubuntu installer)

We know this - the question is why? It's an obvious thing to include and should have been picked up as an omission.

The answer is to use another installer, the command line one on the mini.iso works reasonably well and you can install grub. LILO, or no loader at all.

See my earlier post (about an hour before the OP here) for my rant on the same issue.

---

### Post by haresear on 2011-10-17
> **donpedrodos said:**
> That was the thing i was avoiding before, but it looks i have to go this way now to make the correct partition in control of my bootloader.


That downside i was always able to avoid, but the way that garvinrick4 advices is the only way to correct it back.

Thanks for looking into in this matter, i was realy thinking i was overlooking an option during the installation, but apperantly not.

If you install the new bootloader into the new-install partition, it doesn't disturb the controlling bootloader in the MBR, so it seems to me it would be the same result as not installing a new bootloader.

---

### Post by haresear on 2011-10-17
> **garvinrick4 said:**
> No you were missing nothing but only have to do it once so not to big a deal. Enjoy your Ubuntu donpedrodos.

If the (new-install) grub2 is updated, you'll have to restore the controlling bootloader again.

---

### Post by donpedrodos on 2011-10-17
> **haresear said:**
> If the (new-install) grub2 is updated, you'll have to restore the controlling bootloader again.

This was happening to me in the past, but with the option of not installing a bootloader, i found out you do not need a repair.

I use Ubuntu as from 7.04 and have several partitions with the latest final and/or the newest beta.
I did not do this for a while, thats why the new installer supprised me a littlebit with failing this option.

But like garvinrick4 said, one day i just must to put this back in action.

Thanks again everybody for the responce.

---

### Post by oldfred on 2011-10-17
If a new boot loader takes over, it should include the option to boot your old system. From the old system you can easily reinstall its boot loader.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You can also add a boot stanza in 40_custom from your old install to always boot the most current kernel on an update without having to reboot into the older/controlling install. Ubuntu includes an updated link in root that you can use to boot.

Boot most up2date kernel on sda7
menuentry "Install on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}

---

### Post by haresear on 2011-10-17
> **donpedrodos said:**
> This was happening to me in the past, but with the option of not installing a bootloader, i found out you do not need a repair.

I use Ubuntu as from 7.04 and have several partitions with the latest final and/or the newest beta.
I did not do this for a while, thats why the new installer supprised me a littlebit with failing this option.

But like garvinrick4 said, one day i just must to put this back in action.

Thanks again everybody for the responce.

Perhaps my comments were not clear. If the new bootloader is installed in the new-install partition rather than the MBR, for example /dev/sda3 instead of /dev/sda, then the original bootloader in the MBR will not be disturbed and will remain in control without any need to repair it. On the other hand, if you allow the new bootloader to be installed in the MBR (e.g. /dev/sda) then you will have to reinstall the original bootloader as garvinrick4 said. However, it is not just a one-time thing because whenever grub2 for the new OS is updated (and for 11.10 it has been updated once already since the October 13 release) it will over-write the MBR again, and you will have to reinstall the original bootloader again. This may not seem like a big deal, but when you have a half-dozen different Linux installs all wanting to rewrite the MBR, it can get to be annoying.

---

### Post by oldfred on 2011-10-17
You stop it from updating this way.

To see where dpkg sees grub:
sudo debconf-show grub-pc

To reset
sudo dpkg-reconfigure grub-pc

more /var/cache/debconf/config.dat  | grep /dev/disk

run dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally rerun manually grub-install /dev/sdXY after grub-pc package updates to keep stage1 install in sync.

---

### Post by haresear on 2011-10-17
@oldfred:
Great -- thanks for the insight and solution.

---

### Post by mechanic on 2011-10-18
With no bootloader on a particular partition, every time you install a new distro to it the UUID will change so the 'master' grub needs to run anyway. 

If you have grub on a partition generating its own grub.cfg file, the version of grub you use to boot the system reads that grub.cfg file rather than just going on the vmlinuz files it can find in the /boot directory. This can cause confusion!

Stage1 in grub-pc/grub2??

---

### Post by haresear on 2011-10-18
> **mechanic said:**
> If you have grub on a partition generating its own grub.cfg file, the version of grub you use to boot the system reads that grub.cfg file rather than just going on the vmlinuz files it can find in the /boot directory. This can cause confusion!

Interesting -- didn't know one grub would read another grub's grub.cfg file. So far I haven't experienced any boot problems with multiple grub.cfg files. With multiple *buntu installs that insist on installing their own bootloader somewhere, there doesn't seem to be any way to avoid having a grub.cfg created in each partition. I suppose you could just delete them manually whenever they get regenerated.

---

### Post by oldfred on 2011-10-18
I turn off os-prober as it finds too many when you have many systems installed. Then I just use the partition boot stanza posted above and put it into 40_custom. But I have 4 drives with 4 MBRs so I can boot different systems that way also. But when you get too many like I think I have it is difficult to keep track. Or maybe it is the first part of my id name kicking in. :)

@mechanic
Yes it is not stage1. That was a quote from back when we did not understand how grub2 even worked. But idea is still correct.

---

