---
title: "Instructions on how to install Windows XP."
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by Giovanni_Nuo on 2015-11-20
Hi guys, I'm new to the community and I need a little help.

I recently reformatted my computer because I swapped out the old motherboard with a new one, I've just installed Xubuntu 15.10.
I was wondering if there is a way of creating a partition to install XP in it and configuring GRUB to dual boot.

Any tips would be appreciated.

Thanks

---

### Post by yancek on 2015-11-20
First, post some details on your drive/partition which you can do by running the following command from a terminal:

```
sudo fdisk -l
```

That's a lower case Letter L in the command.  Post the output here.  I imagine you are aware that xp is no longer supported in any fashion that I am aware of and that by using it on the internet, you are possibly subjecting the rest of the computer world to a host of problems?

Posting the output suggested above will give info that will allow someone to suggest the next step.  Windows will always overwrite your MBR so you will not be able to boot Xubuntu after installing xp.  You will need the Xubuntu install medium to re-install the Grub bootloader.

---

### Post by holycow131415 on 2015-11-20
Before you do anything, make sure the motherboard has drivers to support XP.

---

### Post by grahammechanical on 2015-11-20
This is how to create partitions using Gparted from a Ubuntu live session.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by Topsiho on 2015-11-21
First: Idon't know why you want to install Windows XP. It is now not supported anymore by MS. No (security) updates. If you are not online that's OK, except for the BSOD's.
Second: Windows should always be installed first. It is very unfriendly to existing OS's.
After the install of Windows, using a partition editor, room must be made for the Ubuntu install. As far as I know, Windows XP permits this to be done by a no-Windows partition editor such as GParted, newer versions have their own partition editors, which should be used to alter partitions.
After partitions are changed, try and boot Windows first, to see that it detects the changes, and can cope with them.

And only after that install the other OS, such as Xubuntu.

I hope that you realize that versions 15.10 are only maintained for 6 months? It is the LTS versions (14.04, 16.04 and so on) that you can safely use during 5 years.

Topsiho

---

### Post by kansasnoob on 2015-11-21
> **Topsiho said:**
> First: Idon't know why you want to install Windows XP. It is now not supported anymore by MS. No (security) updates. If you are not online that's OK, except for the BSOD's.
Second: Windows should always be installed first. It is very unfriendly to existing OS's.
After the install of Windows, using a partition editor, room must be made for the Ubuntu install. As far as I know, Windows XP permits this to be done by a no-Windows partition editor such as GParted, newer versions have their own partition editors, which should be used to alter partitions.
After partitions are changed, try and boot Windows first, to see that it detects the changes, and can cope with them.

And only after that install the other OS, such as Xubuntu.

I hope that you realize that versions 15.10 are only maintained for 6 months? It is the LTS versions (14.04, 16.04 and so on) that you can safely use during 5 years.

Topsiho

Regarding this:

> I hope that you realize that versions 15.10 are only maintained for 6 months? It is the LTS versions (14.04, 16.04 and so on) that you can safely use during 5 years.


That's a bit wrong, errrm considerably so. [Xubuntu]("http://xubuntu.org/") Trusty (14.04) is only supported for 3 years - so since it was released in April 2014 it will reach EOL in April 2017. Xubuntu opted into HWE for Trusty so if someone installs 14.04.2 or 14.04.3 they'll reach [HWE EOL]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support") in August 2016 and based on the Precise HWE EOL upgrade experience they're just as likely to cause problems as a full release upgrade. You can however still install using the archived 14.04.1 images and avoid HWE EOL altogether.

Also 15.10 (aka; Wily) is supported for 9 months rather than just 6, so until July 2016. So support for the aforementioned versions of Xubuntu break down as such:

Xubuntu Trusty installed using the archived 14.04.1 images = EOL April 2017
Xubuntu Trusty installed using the current 14.04.3 images = HWE EOL August 2016
Xubuntu Wily (15.10) = EOL July 2016

So I think if Xubuntu Wily is installed and running OK I'd stick with it until a couple of months after 16.04 (aka; Xenial) is released next April. And Xenial will almost certainly be supported until April 2019 (possibly longer depending on the decision of the Xubuntu maintainers) :D

**Important note**: The aforementioned archived 14.04.1 images were effected by a horrendous bug that require the utmost caution to prevent data loss:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by kansasnoob on 2015-11-21
I discourage doing so for reasons I'll explain later in this post, but it is possible to install Win XP after Ubuntu and this guide shows how to do it:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm/](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm/)

**[COLOR="#FF0000"]But that's incredibly outdated![/COLOR]**

You'd need to completely ignore what's said there about GRUB because Ubuntu now uses GRUB2. There is no need to backup any existing grub files. Instead, after installing Win XP, you'd need to boot the live DVD/USB you used to create space for XP again and run Boot Repair to get both Ubuntu and XP booting from the GRUB2 boot menu:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Now, why do I discourage doing so? 

(1) As previously stated XP is no longer supported. Also you'll notice in that guide it says Windows will see itself as being on Drive F rather than Drive C so some Windows software will complain and possibly not install or work properly.

(2) Since you made major hardware changes Win XP is likely to refuse your Windows COA anyway. In that case it probably would run for only 60 days before needing reinstalled again. I think it's also unlikely that Windows would help you in that regard.

(3) Installing/reinstalling any OS poses risks of data loss, etc.

So I'd first consider other alternatives. Why do you need Windows? 

If the Xubuntu interface is not to your liking maybe you'd prefer another flavor:

[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

If you have Windows software you miss maybe you can find a FOSS alternative or install that Windows software using Wine. Let us know and we'll be glad to help :D

---

### Post by oldos2er on 2015-11-21
As was mentioned, Windows XP is no longer supported and hence not at all safe to install and run. It *might* be feasible to install it to a non-networked computer, but instructions on doing so are beyond the scope of this forum.

Closed.

Thanks everyone who offered help.

---

