---
title: "Upgrade Vista/9.04 dual-boot to Win7/10.10"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2010-12-23
I haven't done this in a **long** time, so I probably just need a quick refresher on a few things. I had to revert to Vista as my primary OS for more than a year to do CAD work, but now I finally have the freedom to move back to Ubuntu. I have my Win7 upgrade that I still haven't done (yes, I know I'm late to the party) and I want to update my Ubuntu 9.04 install to 10.10. 

If I remember how to do this correctly, I should upgrade Vista to Win7 **first**, and then install Ubuntu second. I have two separate hard drives, so each OS will go on a separate one. The only issue I had in the past is that the drive with Ubuntu on it must be set as the primary boot device, otherwise GRUB wouldn't load.

Is this all correct? I've been out of the Ubuntu loop for quite a while, are there any caveats to this process that I should be aware of?

---

### Post by sikander3786 on 2010-12-23
Welcome back :-)

Yes you need to upgrade Vista > Win 7 first as that would most likely break Grub.

Yes if Grub is on the Ubuntu HDD, you'll need to set that HDD as master (depending on your Bios) or first boot device.

If you install Grub to the MBR of your Windows HDD, you can use that HDD to boot Ubuntu as well but you'll load the Windows bootloader that way and will need to depend on Grub only. And if you break Grub somehow, you won't be able to boot Windows until you fix Grub. So, if you've got different HDDs, better to install the relative bootloaders to their own drives.

Do you plan to upgrade 9.04 > 10.10 or just want to do a clean install of 10.10?

---

### Post by rainwalker on 2010-12-23
> **sikander3786 said:**
> Welcome back :-)

Yes you need to upgrade Vista > Win 7 first as that would most likely break Grub.

Yes if Grub is on the Ubuntu HDD, you'll need to set that HDD as master (depending on your Bios) or first boot device.

If you install Grub to the MBR of your Windows HDD, you can use that HDD to boot Ubuntu as well but you'll load the Windows bootloader that way and will need to depend on Grub only. And if you break Grub somehow, you won't be able to boot Windows until you fix Grub. So, if you've got different HDDs, better to install the relative bootloaders to their own drives.

Do you plan to upgrade 9.04 > 10.10 or just want to do a clean install of 10.10?

Thank you!

Since I have them installed on separate drives, I believe the bootloaders are separate as well. As I have it right now, when I boot up and get to GRUB I'm given the option of booting into 9.04 or Vista, but the Vista option says "loader" in parenthesis next to it. I'm not quite sure what that means.

I'm going to do a fresh install of 10.10, a nice clean slate :)

---

### Post by sikander3786 on 2010-12-23
Grub just chainloads the Windows bootloader that why it mentions 'loader' there I think.

Yes a clean install would be better. And even, a clean install of Windows would also be better if you can afford that.

So, once you complete the Windows installation/upgrade and boot 10.10 for installation, things to note.

1. You might get a Blank screen with some Nvidia or ATI cards and might need to put in the 'nomodeset' boot parameter from F6 menu.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

2. Your username can't contain a Capital letter or a space or the installer would just stuck there without any errors. And you might be wandering what happened :-)

3. If you plan to change the location of Grub, you need to choose Manual Partitioning. You'll only get the choice there and the "Advanced" button at the last step before installation begins, has been removed.

There are some other changes in the installer but only apply if you plan to dual boot from the same HDD. As you have separate, they are un-necessary here.

Don't remember anything else... Post back if you encounter some problems :-)

---

### Post by rainwalker on 2010-12-23
A clean install would be better, but I can't do that unfortunately. 

Why can't usernames contain a capital letter? I never use them but I didn't know that they **couldn't** be used...

I don't think I'm going to mess with GRUB at all, I don't know enough about it to fix things if I messed something up :P

---

### Post by sikander3786 on 2010-12-23
Don't know why the developers decided not to support Capital Letters in username. But the strange thing is, they missed to include an error message, If the installer doesn't accept anything, it should tell you. Thats not the case here. It instead, just greys out the forward button so you can't click on it and you don't even know what you did wrong. But, that has been fixed in the next release.

So, let us know how your install/upgrade goes.

Good Luck!

---

### Post by rainwalker on 2010-12-23
I will, thank you very much! I forgot how helpful these boards are :)

---

### Post by rainwalker on 2010-12-30
I think I'm finally going to have time to do this upgrade today, but read the upgrade instructions for Win7 and it says "the installation will restart your computer automatically. Enter your product key..."; if my computer restarts, how will it boot into Windows? The hard drive with Ubuntu on it is set as the default, and I assume upgrading to Win7 will break GRUB anyway. How should I handle this?

---

### Post by amit.la on 2010-12-31
Hey.

I'm planning to do the exact same upgrade today. got any pointers for me?

---

### Post by sikander3786 on 2010-12-31
> **rainwalker said:**
> I think I'm finally going to have time to do this upgrade today, but read the upgrade instructions for Win7 and it says "the installation will restart your computer automatically. Enter your product key..."; if my computer restarts, how will it boot into Windows? The hard drive with Ubuntu on it is set as the default, and I assume upgrading to Win7 will break GRUB anyway. How should I handle this?
Let us see the output of boot info script.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Anyways, even if the upgrade breaks Grub, you should be able to upgrade Windows successfully and then you can re-install Grub.

But, if Grub is in the MBR of Ubuntu HDD, Windows shouldn't break it whatsoever.

Boot script can tell us a lot more if you decide to post it.

@**amit.la**:

There are no specific queries in your post. Your case might be totally different. It'd be better to start a new thread. Or at least, please post your current setup.

---

### Post by grahammechanical on 2010-12-31
Speaking as someone who is not an expert may I suggest removing the Ubuntu hard disc, set the Windows hard disc to default, install Windows, then put the Ubuntu hard disc back in, set it to default and reinstall Ubuntu.

As I understand things, Ubuntu is designed to be friendly to other Operating Systems because computers usually come with an OS already installed. But Microsoft does not need to design an OS that is friendly to other operating systems and so they are not friendly.

Regards.

---

### Post by oldironman64 on 2010-12-31
Hi!

I installed Ubuntu 9.10 many times on laptops after Windows XP and had no problems to resize the Windows' partition(s). My laptop has even 2 copies of each.:p
According to common procedures I always installed Windows first and Linux last.

Now I wanted to do the same thing on a Lenovo Ideapad (2Gb main memory+160GB) with Windows 7 already factory installed and got a problem: the Ubuntu CD's partitioner doesn't recognize the existing Windows partitions at all. It looks like if the disk was empty. I also tried to define Linux partitions manually, but no existing partition is displayed. Because the Windows partition is only 100Gb, I guess the rest of the disk contains a hidden recovery partition. :confused:
Are those NTFS partitions any different under Win 7 than under XP?
Is this hidden partition the reason why Ubuntu doesn't see any active partition on the disk?
Could this be the result of some "propriatery" IBM solution?

Thank you for some hints.

---

### Post by rainwalker on 2010-12-31
> **sikander3786 said:**
> Let us see the output of boot info script.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Anyways, even if the upgrade breaks Grub, you should be able to upgrade Windows successfully and then you can re-install Grub.

But, if Grub is in the MBR of Ubuntu HDD, Windows shouldn't break it whatsoever.

Boot script can tell us a lot more if you decide to post it.

Here is my RESULTS.txt: [http://pastebin.com/EhDtT2TU](http://pastebin.com/EhDtT2TU)
(Also attached to this post if a downloadable copy is better)

---

### Post by rainwalker on 2011-01-03
I'm thinking about just going ahead with the upgrade and seeing what happens...

---

### Post by sikander3786 on 2011-01-04
> **rainwalker said:**
> I'm thinking about just going ahead with the upgrade and seeing what happens...
What concerns me is this.

> #
============================= Boot Info Summary: ==============================
#
 
#
 => **ThinkPad** is installed in the MBR of /dev/sda
#
 => **ThinkPad** is installed in the MBR of /dev/sdb

Seems like an IBM specific boot loader. Unfortunately, I don't know much about that so can't be helpful here. I think Thinkpad boot loader chain loads Grub for dual booting but not sure.

Hopefully, the upgrade shouldn't break anything. Or you can wait for some more replies...

---

### Post by rainwalker on 2011-01-04
Crapppp...oh well, it'll be an adventure I guess. Tomorrow will be fun :P

EDIT: Also, I'd "thank" your post but apparently they've gotten rid of the button since I was here forever ago...

---

### Post by sikander3786 on 2011-01-04
You are Welcome.

Let us know how your upgrade goes.

And yes, the "Thank" button was removed for some reasons I don't know about :-)

---

### Post by rainwalker on 2011-01-04
Alright, so I got the Windows 7 part taken care of today. It went surprisingly well, actually, for those in the same situation:

Put in the upgrade disc, it started up and booted the typical full-screen Windows installer. Chose "Upgrade" and the process got started.
It went through "Copying Files" and "Gathering programs/files/settings" before getting to "Expanding Windows files". The computer rebooted at 18% through this step, and I discovered 2 things:
1. The upgrade disc is bootable, remove it at this point so the computer will boot normally.
2. Windows had replaced GRUB with its own bootloader, which loaded and booted Windows 7 successfully.
It booted up and immediately resumed the installation, but the screen was now in a really low resolution and the wifi was off. It finished that step and moved on to "Installing features/updates", which showed the green checkmark next to it almost immediately but the installer continued working. The computer rebooted after this step (the installer disappeared and it took a little while to actually shut down) and then resumed installation, "Transferring files/settings/programs", but at native resolution and with wifi on. The screen blacked out for a second during this step. Rebooted at 62%, picks up again, reboots after the final step finishes (which took a while). Upon rebooting it says "Setup is preparing computer for first use", checks components like video performance. Then you have to enter your product key, and it finishes up. After logging in a window popped up about updating .NET, and there was a whole bunch of stuff in Windows Update. I restarted to apply all that stuff, got bluescreened once but it rebooted automatically and didn't happen again. I had to load Win7-specific versions of a few utilities but that was it. I'll do the Ubuntu part tomorrow, it should be WAY faster (the whole process took about 3 hours, I think).

---

### Post by rainwalker on 2011-01-06
I'm now installing Ubuntu, and I'm unsure onto which drive I should install the bootloader. I'm given the choices:
> /dev/sda ATA HITACHI HTS72201 (160.0 GB)
/dev/sda1 Windows 7 (loader)
/dev/sdb ATA HITACHI HTS72201 (160.0 GB)
/dev/sdb1 Ubuntu 9.04 (9.04)

This is with the advanced partitioning method, I don't know what happens if I just choose "Erase and use the entire disk". I'm pretty sure that's what I did to install 9.04, so I think I might just go with that and let the installer decide what's best...

EDIT: Installation is done, I'm about to restart.

---

### Post by sikander3786 on 2011-01-07
I hope everything was successful and smooth?

---

