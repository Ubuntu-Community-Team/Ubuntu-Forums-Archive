---
title: "&quot;nomodeset&quot; doesn't work after 1 April update"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2010-04-01
Hello??  I've had to use "nomodeset" many times to work around Xorg and/or kernel problems, it worked yesterday, but does not today.  Here's the line out of /boot/grub/grub.cfg

 linux   /boot/vmlinuz-2.6.32-18-generic root=UUID=fcf85719-2242-4b65-a162-a41060902f45 ro   quiet splash nomodeset 

but instead KMS is indeed active!  Ctrl-Alt-F1 gets a command line with little tiny graphics print, not the expected text mode print, and it switches back and forth with Ctrl-Alt-F7 with no mode reset.  Oh yes this is i845 intel video graphics.

Any ideas on how to invoke "nomodeset"?

Well I'll give it a go and see if the "black screen" crash shows up like it did yesterday at 31 March update level....

Thanks, Jerry

---

### Post by tuxx on 2010-04-02
And here I thought I was the only person on earth with that issue!

Same problem here with my Acer Aspire Timeline 4810T and 10.04 Lucid Beta 1.

I really, really depend on nomodeset due to missing brightness-functionality with modeset active.

---

### Post by blueturtl on 2010-04-02
There was a driver spesific way to disable modesetting, though I am not sure if that will work either.

For ATi for example it is radeon.modeset=0

---

### Post by iClouseau88 on 2010-04-02
According to Bug#509273 in Launchpad:

1. Put "nomodeset" or "radeon.modeset=0" in the kernel line just before "quiet splash", to disable DKMS and enable UMS

2. To have DKMS working without crashing gdm and X, use "pci=nomsi" in place of "nomodeset".

Of course one needs to update grub afterwards.

---

### Post by jerrylamos on 2010-04-02
> **iClouseau88 said:**
> According to Bug#509273 in Launchpad:

1. Put "nomodeset" or "radeon.modeset=0" in the kernel line just before "quiet splash", to disable DKMS and enable UMS

2. To have DKMS working without crashing gdm and X, use "pci=nomsi" in place of "nomodeset".

Of course one needs to update grub afterwards.

1. above doesn't work.  "nomodeset" in the kernel line still has KMS on.
And yes, update grub.
Even after 2 April update.

Used to work, doesn't any more.
Not on ati mobility 7500
Not on i845 intel either.

Jerry

---

### Post by iClouseau88 on 2010-04-02
Ya! I share our pain! 

1. April 2 CD does not load even onto an empty partition.

2. Kernel 2.6.32-19 keeps crashing my laptop that has ATI Radeon Xtreme 200M video card, while the same kernel updates fine in my desktop pc that has an Nvidia video card.

---

### Post by tuxx on 2010-04-03
Found a solution here.

Instead of passing 'nomodeset' to GRUB2 I've found that passing 'i915.modeset=0' works!

Found the idea here: [http://www.phoronix.com/scan.php?page=article&item=intel_kms_ums&num=2](http://www.phoronix.com/scan.php?page=article&item=intel_kms_ums&num=2)

YMMV.

---

### Post by iClouseau88 on 2010-04-03
The article in the link you give only compares KMS to UMS in Ubuntu 10.04.

How did you arrive at "passing "i915.modeset=0" to grub2 works?

---

### Post by tuxx on 2010-04-03
It's mentioned in the article how to disable KMS :-)

---

### Post by jerrylamos on 2010-04-03
> **tuxx said:**
> Found a solution here.

Instead of passing 'nomodeset' to GRUB2 I've found that passing 'i915.modeset=0' works!

Found the idea here: [http://www.phoronix.com/scan.php?page=article&item=intel_kms_ums&num=2](http://www.phoronix.com/scan.php?page=article&item=intel_kms_ums&num=2)

YMMV.

Thanks!  Works for me.  nomodeset does not work.  modeset=0 does not work.  On this intel i845 video graphics i915.modeset=0 does work.

Now on ati nomodeset does not work, modeset=0 does not work, somewhere I saw a note that says radeon.modeset=0 might work....will try that after working on the ati Thinkpad T40 which Lucid Beta updated to date lasts about 2 minutes on AOL mail before firefox crashes, gdm crashes, X crashes back to login...Alpha 3 had no such problem.

Thanks!  Jerry

---

### Post by psyke83 on 2010-04-03
> **jerrylamos said:**
> Thanks!  Works for me.  nomodeset does not work.  modeset=0 does not work.  On this intel i845 video graphics i915.modeset=0 does work.

Now on ati nomodeset does not work, modeset=0 does not work, somewhere I saw a note that says radeon.modeset=0 might work....will try that after working on the ati Thinkpad T40 which Lucid Beta updated to date lasts about 2 minutes on AOL mail before firefox crashes, gdm crashes, X crashes back to login...Alpha 3 had no such problem.

Thanks!  Jerry

The kernel boot parameters may be overridden by /etc/modprobe.d/radeon-kms.conf. Try making modifications within that file rather than on the GRUB boot line.

---

### Post by iClouseau88 on 2010-04-04
OK.  See it now.  I guess this also applies to older Intel chipset like i815, i.e. "i815.modeset=0".

---

### Post by iClouseau88 on 2010-04-04
How can one make modification to the file /etc/modprobe.d/radeon-kms.conf from within it, instead of on the GRUB menu kernel line item if the monitor is black or blank and frozen?

---

### Post by zika on 2010-04-04
> **iClouseau88 said:**
> How can one make modification to the file /etc/modprobe.d/radeon-kms.conf from within it, instead of on the GRUB menu kernel line item if the monitor is black or blank and frozen?Use "text" or "single" option (kernel-line) in GRUB, and, then, remove/edit /etc/modprobe.d/radeon-kms.conf...?

---

### Post by gibbylinks on 2010-04-04
> **psyke83 said:**
> The kernel boot parameters may be overridden by /etc/modprobe.d/radeon-kms.conf. Try making modifications within that file rather than on the GRUB boot line.

Will this "stick" after a kernel upgrade ? And is there somewhere I can go to see what parameters are available ?

Also is "nomodeset" not working a bug ? or has this been phased out for something else ?

It's not good when you get a black screen at boot-up !! very disconcerting !! ;0)

Cheers

---

### Post by jerrylamos on 2010-04-04
> **zika said:**
> Use "text" or "single" option (kernel-line) in GRUB, and, then, remove/edit /etc/modprobe.d/radeon-kms.conf...?

That's just the point! With this update, "single" mode DID NOT WORK. KMS WAS STILL ACTIVE, AND THE "RECOVERY" SCREEN DID NOT SHOW.  ONLY BLACK.

Only thing that worked was to ssh in from another pc on the net, change /etc/default/grub from nomodeset to i915.modeset=0, update-grub all from ssh since "recovery" mode didn't work.

For over a year it must be, Ubuntu development has been pushing KMS as default even though many bugs are in launchpad on intel and even ati graphics.  We'd have lost much less time if "no KMS" were the default and have an option in Preferences to try "KMS" if you wanted to.

Jerry

---

### Post by iClouseau88 on 2010-04-04
I guess for stand-alone machines with legacy ati/radeon/intel video drivers, one can verify the presence of and un-install "dkms" prior to upgrading to or downloading fresh Lucid beta 1.

Please correct me if I am mistaken.

---

### Post by jerrylamos on 2010-04-04
> **iClouseau88 said:**
> I guess for stand-alone machines with legacy ati/radeon/intel video drivers, one can verify the presence of and un-install "dkms" prior to upgrading to or downloading fresh Lucid beta 1.

Please correct me if I am mistaken.

?  This is from ati radeon express 200 which runs KMS fine.  At least lately it does on Lucid Beta.  If I check Synaptic, "dkms" is not installed.

Jerry

---

### Post by iClouseau88 on 2010-04-05
Hi,

Last night I re-installed Ubuntu 9.10 because a few days ago I accidentally hosed my multi-boot system by messing up Grub.  Anyway I had tried to avoid the black screen problem by installing 9.10 instead of 10.04 beta 1. When inserting the Ubuntu CD, I hit F6 to select acpi=off and noapic. Even with these precaution steps being taken, I still booted into a black screen.  Following a forced reboot, I added these items to the end of the kernel line in Grub menu: acpi=off, noapic, radeon.modeset=0. I was then able to boot and log in to Ubuntu 9.10. Synaptic showed there's no "dkms", but I removed "compiz-gnome". I then became root to edit /etc/modprobe.d/radeon-kms.conf.  Since this file is empty, I added "radeon.modeset=0" to it and saved the file. After restart, I checked the kernel line in Grub menu and since it showed no parameters other than "quiet splash", I added the above 3 parameters.  This resulted in booting into a black screen. So I restarted and left the kernel line alone and succeeded in logging into 9.10. When I did an aptitude update I saw the warning to ignore bad line "radeon.modeset=0" in /etc.modprobe.d/radeon-kms.conf".  Checking this file again, to find that the line is not there anymore.

I did check into /etc/default/grub but was afraid to change this odd-looking Grub2 configuration menu that only has "quiet splash" in the kernel line, so I left it alone and backed out.

I apologize for this seemingly unrelated post but it points to the problem of black screen even dating back to October 2009 when Ubuntu 9.10 was released. I hope this post helps others who are experiencing same problem with installing Ubuntu 9.10 and 10.04 beta 1.

---

### Post by zika on 2010-04-05
> **iClouseau88 said:**
> Hi,

Last night I re-installed Ubuntu 9.10 because a few days ago I accidentally hosed my multi-boot system by messing up Grub.  Anyway I had tried to avoid the black screen problem by installing 9.10 instead of 10.04 beta 1. When inserting the Ubuntu CD, I hit F6 to select acpi=off and noapic. Even with these precaution steps being taken, I still booted into a black screen.  Following a forced reboot, I added these items to the end of the kernel line in Grub menu: acpi=off, noapic, radeon.modeset=0. I was then able to boot and log in to Ubuntu 9.10. Synaptic showed there's no "dkms", but I removed "compiz-gnome". I then became root to edit /etc/modprob.d/radeon-kms.conf.  Since this file is empty, I added "radeon.modeset=0" to it and saved the file. After restart, I checked the kernel line in Grub menu and since it showed no parameters other than "quiet splash", I added the above 3 parameters.  This resulted in booting into a black screen. So I restarted and left the kernel line alone and succeeded in logging into 9.10. When I did an aptitude update I saw the warning to ignore bad line "radeon.modeset=0" in /etc.modprob.d/radeon-kms.conf".  Checking this file again, to find that the line is not there anymore.

I did check into /etc/default/grub but was afraid to change this odd-looking Grub2 configuration menu that only has "quiet splash" in the kernel line, so I left it alone and backed out.

I apologize for this seemingly unrelated post but it points to the problem of black screen even dating back to October 2009 when Ubuntu 9.10 was released. I hope this post helps others who are experiencing same problem with installing Ubuntu 9.10 and 10.04 beta 1.**/etc/modprob[SIZE="7"]e[/SIZE].d/radeon-kms.conf**

---

### Post by iClouseau88 on 2010-04-05
Hi zika,

Sorry for the typo.  I did actually type "modprob**e**" with an "**e**" in the /etc/modprobe.d/radeon-kms.conf file.

By the way, I just looked into /etc/modprob.d/radeon-kms.conf file and saw "radeon.modeset=0".

Ubuntu 9.10 is working fine in my machine now!

---

### Post by Ubuntiac on 2010-04-11
Anyone have any *other* ideas for turning off KMS?

I've tried with bothe nomodeset and radeon.modeset=0 in both the kernel line (with "splash" removed) and in etc/modprobe.d/radeon-kms.conf

Still though I'm seeing in Xorg.0.log that KMS is enabled and that DRI is reporting that KMS is not supported. This is crashing KDM with a squillion plymouth errors.

Oh and, yes, I'm on an ATI card. ;)

---

### Post by dino99 on 2010-04-11
a quick search in nautilus about kms could give you some ideas where to go. But not sure to find a disable setting anyway, as i remember its part of kernel.

---

### Post by Lollerke on 2010-04-11
nomodeset doesn't ,but radeon.modeset=0 works for me.

---

