---
title: "Floppy disk seek wastes time on boot."
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-08-10
Hi all

I searched for this in the forum but couldnt find it ,i think this was happening early on for alpha1 users too.

Can anyone give some advice on this? Some /dev/fd0 errors.

Can someone point me to a bug report or should i file a new one?




regards
rajeev

---

### Post by phenest on 2009-08-10
I think this is what you're looking for: [bug 404594]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404594")

---

### Post by rajeev1204 on 2009-08-10
THanks phenest.

There is only 1 person who has subscribed to that report,the creator himself.Are any of you not having this problem??

---

### Post by phenest on 2009-08-10
I don't have a floppy disk (whatever that is :wink:)

---

### Post by rajeev1204 on 2009-08-10
> **phenest said:**
> I don't have a floppy disk (whatever that is :wink:)

Well,some users have reported this without a floppy disk.

But i agree, damn ! i wonder why i wasted money on a disk which i never used.

---

### Post by dlmarti on 2009-08-10
> **rajeev1204 said:**
> Well,some users have reported this without a floppy disk.

But i agree, damn ! i wonder why i wasted money on a disk which i never used.

Most people disable it in the BIOS, that I see.

---

### Post by wayne_cat on 2009-08-10
> **rajeev1204 said:**
> Well,some users have reported this without a floppy disk.

But i agree, damn ! i wonder why i wasted money on a disk which i never used.

There are some user with this problem ... somewhere in this threads :

[http://ubuntuforums.org/showthread.php?t=1229741&highlight=fd0](http://ubuntuforums.org/showthread.php?t=1229741&highlight=fd0)

[http://ubuntuforums.org/showthread.php?t=1223118&highlight=fd0](http://ubuntuforums.org/showthread.php?t=1223118&highlight=fd0)

[http://ubuntuforums.org/showthread.php?t=1181968&highlight=fd0](http://ubuntuforums.org/showthread.php?t=1181968&highlight=fd0)

[http://ubuntuforums.org/showthread.php?t=1180436&highlight=fd0](http://ubuntuforums.org/showthread.php?t=1180436&highlight=fd0)

---

### Post by jerrylamos on 2009-08-10
> **phenest said:**
> I don't have a floppy disk (whatever that is :wink:)

My IBM Thinkpad T40 doesn't have a floppy disk either.  On that machine choose between CD or floppy.  I've got the CD.  No floppy controller or hardware anywhere.

Even with no floppy disk installed karmic wastes 6 lines timing out on each attempted access to /dev/fd0 before continuing boot.  Yes, grub.cfg says no floppy but boot tries anyway.  Seems to almost double boot time.

Yes, latest grub2 & karmic are installed.

Jerry

---

### Post by phenest on 2009-08-11
> **rajeev1204 said:**
> Well,some users have reported this without a floppy disk.

But i agree, damn ! i wonder why i wasted money on a disk which i never used.

My Dell Precision M90 was not designed to have a floppy disk drive at all. I have no messages on my system to suggest an error regarding fd0.

---

### Post by rajeev1204 on 2009-08-11
> **phenest said:**
> My Dell Precision M90 was not designed to have a floppy disk drive at all. I have no messages on my system to suggest an error regarding fd0.


I guess its having a floppy controller on the board which craps out the kernel.

This is a valid bug and i have subscribed to it.


My boot takes 2 minutes to complete.

---

### Post by Hairy_Palms on 2009-08-11
another way to fix it is to blacklist the floppy kernel module in blacklist.conf under /etc/modprobe.d

---

### Post by ssam on 2009-08-11
this is the bug report you are really after. i duped the old one.
[https://bugs.launchpad.net/linux/+bug/384579](https://bugs.launchpad.net/linux/+bug/384579)

---

### Post by ronacc on 2009-08-11
my test box does not have a floppy and I was getting those errors on boot , disabling the the floppy in bios cured the problem foe me .

---

### Post by rajeev1204 on 2009-08-11
> **ronacc said:**
> my test box does not have a floppy and I was getting those errors on boot , disabling the the floppy in bios cured the problem foe me .

How to disable a floppy in bios? Also, if we do that , how do the devs know enough users are having that problem or not? Anyways,i guess ill disable or search for that option in bios.

---

### Post by phenest on 2009-08-11
To be quite honest, why does Linux support floppy drives? Who the hell uses them, and why? I hardly use the CD/DVD drive much! ;)

---

### Post by wayne_cat on 2009-08-11
> **phenest said:**
> To be quite honest, why does Linux support floppy drives? Who the hell uses them, and why? I hardly use the CD/DVD drive much! ;)

A lot of servers still have floppy drives ... and they still need them ... try to update the firmware of an older IBM Xseries without a floppy.

---

### Post by phenest on 2009-08-11
> **wayne_cat said:**
> A lot of servers still have floppy drives ... and they still need them ... try to update the firmware of an older IBM Xseries without a floppy.

I've just discovered there is a BIOS update for my laptop. You can either run it from Windows (whatever that is), or from a floppy disk (whatever that is). Ok. I'm joking. I do know what both are, but this is something I got round once before. It's possible to create a bootable CD with PC-DOS (I think) with the firmware/BIOS upgrade on.

Got me a project! :D

---

### Post by novafluxx on 2009-08-11
This is why I like having a Dell laptop! They support BIOS updates in Linux, and have easy instructions on their Linux wiki for Ubuntu!

Sorry for the seemingly shameless plug, but I know some manufacturers are very...sparse...with their NON-Windows support.

---

### Post by wayne_cat on 2009-08-11
> **phenest said:**
> I've just discovered there is a BIOS update for my laptop. You can either run it from Windows (whatever that is), or from a floppy disk (whatever that is). Ok. I'm joking. I do know what both are, but this is something I got round once before. It's possible to create a bootable CD with PC-DOS (I think) with the firmware/BIOS upgrade on.

Got me a project! :D

This is maybe interesting:

[http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom)

Under Linux you can:

- Flash a running system
- Flash a remote system over SSH. No physical access required
- No need for a boot floopy or bootable CD to flash a system.

---

### Post by wayne_cat on 2009-08-11
> **novafluxx said:**
> This is why I like having a Dell laptop! They support BIOS updates in Linux, and have easy instructions on their Linux wiki for Ubuntu!

Sorry for the seemingly shameless plug, but I know some manufacturers are very...sparse...with their NON-Windows support.

It is not a sin to mention a company that cares for linux

---

### Post by phenest on 2009-08-11
I have successfully upgraded the BIOS on my laptop with an EXE I got from Dell, without a floppy drive nor access to Windows.

So again, any other reasons for a floppy drive?

---

### Post by ronacc on 2009-08-11
> **rajeev1204 said:**
> How to disable a floppy in bios? Also, if we do that , how do the devs know enough users are having that problem or not? Anyways,i guess ill disable or search for that option in bios.

check your bios boot order and set it up so that floppy is not listed in the boot order . You can still file a bug or subscribe to an existing one , disabling floppy in bios just saves you the annoyance of the seek on boots .

---

### Post by ronacc on 2009-08-11
> **phenest said:**
> I have successfully upgraded the BIOS on my laptop with an EXE I got from Dell, without a floppy drive nor access to Windows.

So again, any other reasons for a floppy drive?

legacy hardware that still has a floppy . I build all my own boxes and haven't used a floppy in years but they still do exist .

---

### Post by wayne_cat on 2009-08-11
> **ronacc said:**
> legacy hardware that still has a floppy . I build all my own boxes and haven't used a floppy in years but they still do exist .

not only legacy hardware ... new systems (i.e. Dell Inspiron) still have floppy 
drives (in the 19-in-1 media card reader)

---

### Post by phenest on 2009-08-11
> **ronacc said:**
> legacy hardware that still has a floppy . I build all my own boxes and haven't used a floppy in years but they still do exist .

On new m/b's? No one makes floppy disks, drives, and I'm guessing controllers too.

---

### Post by phenest on 2009-08-11
> **wayne_cat said:**
> not only legacy hardware ... new systems (i.e. Dell Inspiron) still have floppy 
drives (in the 19-in-1 media card reader)

It doesn't matter whether some systems have a drive, what would you use it for that you can't do with a CD?

---

### Post by wayne_cat on 2009-08-11
> **phenest said:**
> It doesn't matter whether some systems have a drive, what would you use it for that you can't do with a CD?

Grub legacy and Grub2 are typical GNU tools ... and GNU does not drop support for 
hardware that is still used by many people. 

See the grub-devel mailing list ... You will find a lot of Grub2 users who still use floppy
drives to boot systems (with special scsi or raid controllers). Try to boot from a CD if
your controller does not support it. Floppy drives are rare today, but they are not dead.

---

### Post by phenest on 2009-08-11
> **wayne_cat said:**
> Floppy drives are rare today, but they are not dead.

They're as dead as the Vic 20. You might have one, but is it really worth hanging on to?

---

### Post by rajeev1204 on 2009-08-11
Drop the arguments both of you.Its important for those who need it.

Stick to original thread title please.Thanks.\

---

### Post by phenest on 2009-08-11
> **rajeev1204 said:**
> Drop the arguments both of you.Its important for those who need it.

Stick to original thread title please.Thanks.\

Who's arguing? I was just saying, that's all. :roll:

---

### Post by rajeev1204 on 2009-08-12
> **phenest said:**
> Who's arguing? I was just saying, that's all. :roll:

Got repetitive <gulp is that correct spelling?> .No problems folks,Lets move on now.:)

---

### Post by rajeev1204 on 2009-08-14
THis is still not fixed for me.Keeps probing for /dev/fd0.Also,i dont have an option to disable floppy in bios.

---

### Post by Grenage on 2009-08-14
There should be an option under 'Floppy drive type' e.g.

Disabled
720k
1.4MB

I've not seen a BIOS without this option (I'm not calling you a liar, I've just not seen one myself!).

---

### Post by dlmarti on 2009-08-14
Even if you don't own a floppy drive, the chips that support one may still be present.
Disable the floppy drive in the BIOS, and the kernel will not try to find the drive.

---

### Post by edujose on 2009-08-14
Hi rajeev1204, I had the same problem till a few days ago.

I installed Karmic alpha 3 and observed the delay you say at booting. It's around 2 min. where the kernel is trying to detect a floppy drive and giving errors about not finding it. Went to BIOS but option "FLoppy A" was set to "Not Installed" (system has no floppy drive, I removed it when changin case some moths ago). So what was wrong?

Then saw another BIOS option under Advanced, Diskette Configuration called "Diskette Controller". Changed it from "Enabled" to "Disabled" and after rebooting the detection delay was gone.

It seems on some motherboards (mine is Intel, though an ancient one) it's not enough to tell the BIOS there is no floppy drive (floppy not installed): the diskette controller (the hardware that deals with floppy drives) must also be set to "Disabled".

Maybe your motherboard has an equivalent setting to disable the floppy disk controller.

Anyway I had no such big delays in Hardy: Seems the Karmic kernel tries harder when detecting floppy units :-)

Edit: I forgot, all this is the same dlmarti said in above post, but expanded :P

---

### Post by amano on 2009-08-14
There is no need to still comment on the issue: [https://bugs.freedesktop.org/show_bug.cgi?id=23309](https://bugs.freedesktop.org/show_bug.cgi?id=23309) , [http://cgit.freedesktop.org/DeviceKit/DeviceKit-disks/commit/?id=dacee202cc8ea79540983be547e2b7b05fbd81a2](http://cgit.freedesktop.org/DeviceKit/DeviceKit-disks/commit/?id=dacee202cc8ea79540983be547e2b7b05fbd81a2)

As you can read above, David Zeuthen has fixed the issue upstream. Let's wait until the fix within Devicekit-Disks hits the Ubuntu repos...

---

### Post by rajeev1204 on 2009-08-14
> **amano said:**
> There is no need to still comment on the issue: [https://bugs.freedesktop.org/show_bug.cgi?id=23309](https://bugs.freedesktop.org/show_bug.cgi?id=23309) , [http://cgit.freedesktop.org/DeviceKit/DeviceKit-disks/commit/?id=dacee202cc8ea79540983be547e2b7b05fbd81a2](http://cgit.freedesktop.org/DeviceKit/DeviceKit-disks/commit/?id=dacee202cc8ea79540983be547e2b7b05fbd81a2)

As you can read above, David Zeuthen has fixed the issue upstream. Let's wait until the fix within Devicekit-Disks hits the Ubuntu repos...

Thats good news.

---

### Post by amano on 2009-08-21
This should be fixed for good now. Can everybody enable the floppy controllers in the BIOS again and test it out?

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006862.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006862.html)

---

### Post by amano on 2009-08-22
No comments?

---

### Post by rudenko_ruslan on 2009-08-22
> **amano said:**
> Can everybody enable the floppy controllers in the BIOS again and test it out?
Everything seems OK to me. Before and after update.

---

### Post by rajeev1204 on 2009-08-22
> **amano said:**
> No comments?

Yes,its been fixed with the updates a few days ago.

---

### Post by ezsit on 2009-08-22
> How to disable a floppy in bios? Also, if we do that , how do the devs know enough users are having that problem or not? Anyways,i guess ill disable or search for that option in bios.

If your BIOS has an option to enable or disable the floppy drive AND you have the setting to ENABLE, then there is NO BUG when Linux searches for the nonexistent floppy your BIOS is reporting. This is what you want Linux to do, search for hardware that the BIOS reports is there.

---

