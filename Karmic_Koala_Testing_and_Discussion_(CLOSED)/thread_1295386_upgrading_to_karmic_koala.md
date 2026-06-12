---
title: "upgrading to karmic koala"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rygar on 2009-10-19
Hi all,

I'm looking forward to upgrading to Karmic Koala (from Jaunty), but I had a few questions about the process.  I'm planning on doing an upgrade, not a fresh install, and I want to know which features of Karmic I will and won't get.

I'm assuming it will upgrade the kernel and GNOME...  Will it replace my current GRUB with GRUB2?

hal is being deprecated for DeviceKit-power.  Will my Ubuntu automatically switch over to DeviceKit-power?  Will it automatically uninstall hal?

The Karmic page says "The Intel video driver has switched from the 'EXA' acceleration method to the new 'UXA'".  Not sure what this is, but I have Intel graphics so I'm assuming this is good; I'll get this?

I'm assuming it WON'T upgrade to ext4...  I know ext4 is better, but is it really practical?  Are there any noticeable differences to ext4 for the average user?

Basically what I want to know is how this upgrade will differ from a fresh install.

Thanks in advance!
Jeff

---

### Post by dearingj on 2009-10-19
I've been using ext4 since Jaunty came out, and all I've noticed compared to ext3 is a slight speed improvement when doing things that involve writing a lot of files, such as installing or upgrading packages. From what I've read online about ext4, it sounds like it's also less likely to have any filesystem-related problems and can be recovered more easily if any problems do happen.

Edit: I forgot about the scheduled fsck :) It happens so fast now that I rarely even notice it.

---

### Post by mcduck on 2009-10-19
> **rygar said:**
> Hi all,

I'm looking forward to upgrading to Karmic Koala (from Jaunty), but I had a few questions about the process.  I'm planning on doing an upgrade, not a fresh install, and I want to know which features of Karmic I will and won't get.

I'm assuming it will upgrade the kernel and GNOME...  Will it replace my current GRUB with GRUB2?

hal is being deprecated for DeviceKit-power.  Will my Ubuntu automatically switch over to DeviceKit-power?  Will it automatically uninstall hal?

The Karmic page says "The Intel video driver has switched from the 'EXA' acceleration method to the new 'UXA'".  Not sure what this is, but I have Intel graphics so I'm assuming this is good; I'll get this?

I'm assuming it WON'T upgrade to ext4...  I know ext4 is better, but is it really practical?  Are there any noticeable differences to ext4 for the average user?

Basically what I want to know is how this upgrade will differ from a fresh install.

Thanks in advance!
Jeff
The upgrade won't change your filesystems, so if you now have Ext3 they will stay Ext3. There's a way to convert Ext3 to Ext4 but that won't actually bring you any of Ext4's benefits for the files that you already have on the filesystem.

Ext4 has clearly better performance than Ext3, this is most noticeable during the scheduled fsck on boot. It only takes a fraction of the time it did on Ext3. :)

As far as I know upgrades won't change you from Grub to Grub2 either. But I could be wrong there, since that's also possible to do (I actually did that already on 9.04).

However the upgrade should indeed move you from HAL to DeviceKit, and uninstall HAL. And you will also get the new Intel driver version, so yes, you will get UXA instead of EXA. And yes, that is good. :)

---

### Post by rygar on 2009-10-19
Thanks guys, this stuff is really helpful!

I do hate those long disk checks...  If I convert my filesystem from ext3 to ext4, will those disk checks be noticeably faster, or will it only make a difference on a fresh install?

Thanks again!

---

### Post by oboedad55 on 2009-10-19
> **rygar said:**
> Thanks guys, this stuff is really helpful!

I do hate those long disk checks...  If I convert my filesystem from ext3 to ext4, will those disk checks be noticeably faster, or will it only make a difference on a fresh install?

Thanks again!

Since karmic is still beta you may want to wait until it's released before you upgrade. As has been pointed out, ext4 does offer some speed improvement, although for me it has been fairly small. I think to get the full benefit of it you'd best do a new install. I keep my home directory backed up so I can get a new install up and fully running very quickly. BTW, it's also true that you'll not get the new grub if you update, not that it's a deal breaker, IMO.

---

### Post by eluminx on 2009-10-19
I dunno how is going to be with your intel graphics, but i just did an upgrade on my HTPC (nvidia chipset and integrated gpu) and the upgrade went flawless.  I mean i have done upgrades before to beta releases and even alpha and i expect errors and actually like dealing with most of the them from time to time.  But this time, i just typed that upgrade command and the upgrade went so good i had to do almost nothing at all.  My HTPC is happily chuggin along with karmic beta and even my HDMI and SPDIF worked, which i managed to get only one working in jaunty.  

So if you are up to fixing some errors you "might" get from upgrading to a beta OS go ahead and do it, my experience with Ubuntu has been great for the past 4 years, even with beta and alpha releases.

---

### Post by autocrosser on 2009-10-19
As far as ext3 to ext4 goes--you would see a change at once with the change as noted above with the start-up file check & as the files in your filesystem slowly get replaced you will see a speed improvement--"almost" all of the bad bugs have been ironed out & the ones that remain are cornercases...so you "should" be good to go.

My Ibex-to-Jaunty updated system that was converted when ext4 first came out is still working well (at least when I boot it up everything works without a problem....) & both of my testing Karmic installs started with ext4 run without any problems at all....

If you upgrade, you will stay with Legacy Grub this time--next time with the Lynx will be Grub2 for all cases...Any new installs get Grub2.

There is lots of "under-the-hood" stuff that makes Karmic a nice move forward---but it's just the preview for what the Lynx will be bringing!!!!

---

