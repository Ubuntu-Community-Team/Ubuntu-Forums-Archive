---
title: "Reassurance sought on dual boot upgrade"
date: 2022-07-25
forum: Installation &amp; Upgrades
---

### Post by col48 on 2022-07-25
I have a dual-boot system with two Ubuntu in partitions on a single HD.  The active one runs Xenial and the other is Lucid.  No Windows.  I think the Grub version is nominally 1.98.

Since Xenial is out of support it is time to install Jammy and I want to do that over the Lucid, retaining the ability to boot to Xenial -- there are things which will take some time to transfer and I don't want to lose continuity during the period of transition.

I've seen some reports that installing Jammy inhibits the other side of a dual boot because of what the new version of Grub does.
**Is this true?**
If so, is there a simple workaround?

I've tried Jammy from a live USB so I am confident Jammy would itself be fine on the machine, but I need reassurance that I won't have any problems with booting to Xenial whenever I need to once I go ahead with the installation of Jammy.

---

### Post by yancek on 2022-07-25
>   I've seen some reports that installing Jammy inhibits the other side of a dual boot because of what the new version of Grub does

What exactly are you referring to here.  If you want to install over lucid, you would need to know which partition(s) it is on so you install to that partition or partitions.  Also, you would need to know which partition(s) Xenial is on so you do not overwrite it.  After installing Jammy, the installer should install Grub and also update Grub to include Xenial in the Grub menu.  Are you planning to install Jammy in UEFI or Legacy?  Is Xenial installed Legacy or UEFI?

---

### Post by oldfred on 2022-07-25
With grub 2.06 they want to turn off os-prober.
The scan of all your partitions looking for other installs may be a security issue.

You can run os-prober once & then turn it off.
I prefer not to use os-prober anyway & have always turned it off. 
I then add my own boot stanzas to 40_custom. 
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
This is now a mega thread, summerized in the help.ubuntu.com link above. May want to start at end.
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

You can also use configfile to load the other install's grub.cfg file.
Configfile example
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by col48 on 2022-07-25
Thanks yancek.

I know which partition I want to overwrite and that it is big enough.  Xenial was installed Legacy (there is no /sys/firmware/efi for instance).  I'm assuming Jammy would be happy in a Legacy partnership.

Some weeks ago, not long after Jammy was released (life gets in the way!), I did an internet search on dual boot and Jammy and found several articles which talked about problems with trying to boot the non-Jammy OS after the installation because of what was said to be a then-unresolved issue with the version of Grub.  But in each case the non-Jammy OS was a Windows version. I know that in the past if you wanted to set up a dual-boot machine *from scratch* you had to be careful how you went about it if you wanted to mix Windows with Linux, although Linux with Linux was no problem.  I just want to be sure it's still no problem.

I hope you can understand my caution - if all goes well that's fine, but if it doesn't, I will have no means of accessing the internet.

---

### Post by oldfred on 2022-07-25
You do have to make sure both systems are in same boot mode. Both UEFI or both BIOS.
But Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012.
So most systems are UEFI.

And if system is over 10 years old Ubuntu is usually not the best choice. A lighter weight flavor often works better on old systems.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

### Post by tea for one on 2022-07-26
> **col48 said:**
> I hope you can understand my caution - if all goes well that's fine, but if it doesn't, I will have no means of accessing the internet.
Yes, caution is understandable and not to be dismissed. There are many threads in these forum pages where more foresight should have been practised.
You mentioned that you have already explored Ubuntu 22.04 (Jammy), therefore you hopefully accessed the internet in a live session?

---

### Post by col48 on 2022-07-26
@teaforone  Good point, I did try Firefox in the live Jammy USB session, so access to this forum would be possible - although if I had to write down any critical information a problem would be that I struggle to read my own handwriting these days!

@oldfred  Thanks for your input.  My understanding of this kind of thing is pretty rudimentary, which is one reason I am cautious.  I just missed seeing your post #3 before posting my #4 but was both alarmed and reassured (if that's possible) by the links you gave.  I owe the stability of my present setup to you in that you guided me through the process of setting up the initial dual boot on this system about 12 years ago for which I am still very grateful.  It's the same system, but only in the way that a brush may be called the same brush even when its handle and its head have each been replaced more than once.  So although in some ways this is an old system, in terms of what makes it fly it is only about 4 years old.

So....

Legacy booting has served me fine - I have no strong reason to change it.....  (is this unwise?)
.... so I would need to ensure installing Jammy respects this (would it do so automatically?)
My system only has Ubuntu at present - no Mint, Windows etc.
Changing Grub config files can be left until after the initial Jammy install.  (I'm not sure of the what os_prober does after the intial install?)
I must be sure I tell the installation process to install to the correct (Lucid) partition.
I must remember to backup my Xenial partition to my offline resource just before taking the plunge.
Although there is a swap partition on the HD from way back, I think a swap file is the current style, so would not tell Jammy about it (is this possible?)
What other questions will the installation process ask that I will need to prepare answers for before I start?


Thanks ahead of time for any help you give - it is much appreciated.

---

### Post by oldfred on 2022-07-26
I have gone back to using a swap partition of 4GB.
If using swap file & you have a swap partition it automatically uses it. You have to explicitly click on swap partition and change to do not use. Only available with something else install option.

If system is 12 years old, it probably is BIOS only. Or if very early UEFI, that often was buggy. Both vendor updates to UEFI and Linux had to do many work arounds to get early UEFI to work.

Ubuntu has changed a lot in 12 years. I started back with gnome2. Did not like Unity so used fallback which was lighterweight. Then when they changed back to gnome, it became a much heavier but full functional system. It now is really meant for newer systems or systems with more RAM and faster drives. My old 2006 1.5GB RAM laptop would not load Ubuntu. I was able to install server & fallback.  But I have converted to Kubuntu which is more middleweight on my newer desktops and was a bit surprised that Kubuntu installed on that old laptop and with very limited test seemed functional. Just now compared to newer system with SSD was slow.

The os-prober script searchs every partition for other installs and then adds a boot stanza for those installs. I have many partitions and many test and old installs. Many are obsolete, just have not yet reused that partition. I do not want most of those in my grub anyway, so turn os-prober off.

---

### Post by col48 on 2022-07-26
@oldfred
Yes, its pure BIOS.  Well, at times I delude myself that I almost understand what it is doing!!!

The two or three times the swap partition has been invoked the system has almost ground to a halt.  It isn't SSD, and the operation (was it a whole-spreadsheet sort on a big spreadsheet?) would have been very slow even if it was wholly in memory, if which there is a nominal 16Gb.  So I avoid using the swap space.  Otherwise, the system is fast enough for me - I'm not into Gaming in any way.

It sounds as though os_prober can safely be ignored with my small number of OS.  When I started with Hardy and then early on with Lucid I used to retain three levels of kernel so that if an upgrade failed and corrupted its predecessor there was still the grandfather available.  It never happened, of course, and I think kernel upgrades for a long time have routinely removed 'grandpa'.

I feel reassured about proceeding - thanks.

But I must pick a day when I am unlikely to be distracted, which won't be for a week or two.

---

