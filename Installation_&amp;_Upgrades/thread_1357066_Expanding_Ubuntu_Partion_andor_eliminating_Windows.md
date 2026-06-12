---
title: "Expanding Ubuntu Partion and/or eliminating Windows Partition"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by bdws1975 on 2009-12-16
hi all,

Currently, I've got a 320GB hd and it's partitioned thus:

185 Windows partition
121 Ubuntu partition

I'm wanting to do one of the following 1.  expand the ubuntu partition and minimize the windows or 2.  eliminate the windows and expand the ubuntu to encompass the rest of the hd.

I'm looking for advice on:

1.  which is easier
2.  how do i accomplish 1 (direction to where to find instructions, etc).

Thanks for your help,

Brett

---

### Post by raymondh on 2009-12-16
> **bdws1975 said:**
> hi all,

Currently, I've got a 320GB hd and it's partitioned thus:

185 Windows partition
121 Ubuntu partition

I'm wanting to do one of the following 1.  expand the ubuntu partition and minimize the windows or 2.  eliminate the windows and expand the ubuntu to encompass the rest of the hd.

I'm looking for advice on:

1.  which is easier
2.  how do i accomplish 1 (direction to where to find instructions, etc).

Thanks for your help,

Brett

Brett,

You could use gparted to do either of the above options.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

-  back-up your personal files and make sure/test that the back-ups are working
-  If you plan to take space away from windows .... defrag windows first.  2X if you have the time (it's worth it)
-  did I mention .... back-up your files as there are no guarantees when working with partitions?  ;)

If you need a mini guide, kindly (in ubuntu) access gparted (system > admin > partition editor) and post a screenshot of what it outputs.  That'll help us visualize.

Which is easier?  Both are.  It really depends on whether you plan to keep on 2-booting.  In case you decide now to erase windows but later on decide you need it back .... better have a windows install disk ready.

Regards,

---

### Post by bdws1975 on 2009-12-16
Thanks Raymond.  Can I assume that it's better to run from livecd than from my linux os?

I appreciate the help.  I'll need to read up to figure it out, but this is a great start.

No rush, so I can take my time to do it right.

Thanks,
brett

---

### Post by raymondh on 2009-12-16
> **bdws1975 said:**
> Thanks Raymond.  Can I assume that it's better to run from livecd than from my linux os?

I appreciate the help.  I'll need to read up to figure it out, but this is a great start.

No rush, so I can take my time to do it right.

Thanks,
brett

Yes on liveCD.  To do partition work ... the partitions have to be UNMOUNTED.  The liveCD (and in live session ... known as TRY UBUNTU WITHOUT ANY CHANGES) will unmount the partitions.  You can also double check that the partitions are unmounted by right clicking on the intended partition and if given the option to unmount, do so.  For swap, select SWAPOFF.

If you wish, download and burn to cd the latest gparted.  That (a gparted liveCD) is a valuable and powerful tool to have in your bag.

When you're ready, post a screenshot.

Regards,

---

### Post by bdws1975 on 2009-12-16
Hi Raymond,

I took a screenshot of what I see in gparted.

I'd like to eliminate the 172gb ntfs and the 13.04gb ntfs and incorporate the space into the linux partition.

Thanks!
Brett

---

### Post by bdws1975 on 2009-12-16
sorry to post so soon, but let me make sure I'm getting this right:

1.  download gparted to cd or thumb drive
2.  shut down computer
3.  boot from cd or thumbdrive
4.  the follow instructions on web page

Thanks!
Brett

---

### Post by raymondh on 2009-12-16
> **bdws1975 said:**
> Hi Raymond,

I took a screenshot of what I see in gparted.

I'd like to eliminate the 172gb ntfs and the 13.04gb ntfs and incorporate the space into the linux partition.

Thanks!
Brett

Brett, you attached a text file.

-In ubuntu, access gparted thru system > admin > partition editor.
-When it outputs, press the PrtScr key (top right of keyboard) and save to desktop
-Go back to this thread and in the tools (beside the smiley face above), click attach
-a window pops up.  Browse to your desktop, click on the .png file you save and upload.

Raymond

---

### Post by bdws1975 on 2009-12-16
> **raymondh said:**
> Brett, you attached a text file.

-In ubuntu, access gparted thru system > admin > partition editor.
-When it outputs, press the PrtScr key (top right of keyboard) and save to desktop
-Go back to this thread and in the tools (beside the smiley face above), click attach
-a window pops up.  Browse to your desktop, click on the .png file you save and upload.

Raymond

crap.  sorry about that.  I chose the wrong file.

Here you go.

Brett

---

### Post by raymondh on 2009-12-17
> **bdws1975 said:**
> crap.  sorry about that.  I chose the wrong file.

Here you go.

Brett

No worries.

So, we're taking out windows ... from your previous post

**I'd like to eliminate the 172gb ntfs and the 13.04gb ntfs and incorporate the space into the linux partition.**

Yes, the main idea is to first delete the unwanted partitions (one at a time) ... then enlarge the EXTENDED partition ... and then enlarge (or move swap) the ubuntu partition.

-  delete the 13gb sda2
-  enlarge extended (sda3) to the right
-  move swap (sda6) to the right
-  enlarge the right side of ubuntu (sda5) to bump up to the newly moved swap
-  delete the 172gb (sda1)
-  enlarge the extended (sda3) to the left
-  enlarge the left side of ubuntu (sda5) to the left
-  edit the grub.cfg file or, re-install GRUB.

At any action, you can review and apply.  You can also do each action and click apply after everything is done (that will be frustratingly long so have your favorite drink ready).

Also, post back if you need assistance in manually editing the grub.cfg file or re-installing/updating grub to reflect the changes.  If you don't edit, you may/will still see a windows entry in your boot-up ... which of course when you select, will lead to an error.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Back-up.  Defrag first (to give ubuntu a chance to have a defragged space/blocks)

Regards,

---

### Post by raymondh on 2009-12-17
Brett,

will catch/follow this thread tomorrow. early work day tomorrow.

'Take your time to read up on gparted and grub2.  When ready, the forum can/will assist you should you run into stumbling blocks.

Regards,

---

### Post by bdws1975 on 2009-12-17
Thanks Raymond.  I'll make this my last post also as I too have an early day.

I want to make sure I have the first steps right:

1.  shut down comp 
2.  boot from cd into gparted
3.  complete actions above
4.  reboot into ubuntu
voila!

Is that basically correct?

This is all so new to me but I'm loving it.

I'm backing up all files right now and will do the resizing tomorrow night.

Thanks!
Brett

---

### Post by bdws1975 on 2009-12-17
> **raymondh said:**
> No worries.

So, we're taking out windows ... from your previous post

**I'd like to eliminate the 172gb ntfs and the 13.04gb ntfs and incorporate the space into the linux partition.**

Yes, the main idea is to first delete the unwanted partitions (one at a time) ... then enlarge the EXTENDED partition ... and then enlarge (or move swap) the ubuntu partition.

-  delete the 13gb
-  enlarge extended to the right
-  move swap to the right
-  enlarge the right side of ubuntu to bump up to the newly moved swap
-  delete the 172gb
-  enlarge the extended to the left
-  enlarge the left side of ubuntu to the left
-  edit the grub.cfg file or, re-install GRUB.

At any action, you can review and apply.  You can also do each action and click apply after everything is done (that will be frustratingly long so have your favorite drink ready).

Also, post back if you need assistance in manually editing the grub.cfg file or re-installing/updating grub to reflect the changes.  If you don't edit, you may/will still see a windows entry in your boot-up ... which of course when you select, will lead to an error.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Back-up.  Defrag first (to give ubuntu a chance to have a defragged space/blocks)

Regards,

to be clear:  when you say enlarge 'ubuntu' you mean the ext3 correct?

thanks,
Brett

---

### Post by raymondh on 2009-12-17
> **bdws1975 said:**
> to be clear:  when you say enlarge 'ubuntu' you mean the ext3 correct?

thanks,
Brett

to answer your last 2 posts .... yes and yes.... I edited post 9 to include the specific sda numbers.

EXTENDED is **sda3**
Ubuntu (referring to root / , where your system files are) is on **sda5**

Those are the 2 partitions that you will need to enlarge.

**Sda1** and **sda2** are the window system files and recovery partitions.  Those are the 2 partitions that you have to delete.

**sda6** is the linux SWAP.  That is the partition that you have to move.

----------------------------------------------------------------------------

Hey Brett, since you have backed-up your files and this seems to be a fairly new Ubuntu install .... and considering the time it would take you/gparted to do all those actions ..... it would seem better and faster to do a fresh, re-install of Ubuntu.

- You can choose USE ENTIRE DISK in step 4 of the install process or;
- You can create the partitions beforehand, as well as separating /home from root, and do a manual install.

Your choice.  Either way (resizing and moving or re-install or manual install) would be a good learning experience.

---

### Post by bdws1975 on 2009-12-17
> **raymondh said:**
> to answer your last 2 posts .... yes and yes.... I edited post 9 to include the specific sda numbers.

EXTENDED is **sda3**
Ubuntu (referring to root / , where your system files are) is on **sda5**

Those are the 2 partitions that you will need to enlarge.

**Sda1** and **sda2** are the window system files and recovery partitions.  Those are the 2 partitions that you have to delete.

**sda6** is the linux SWAP.  That is the partition that you have to move.

----------------------------------------------------------------------------

Hey Brett, since you have backed-up your files and this seems to be a fairly new Ubuntu install .... and considering the time it would take you/gparted to do all those actions ..... it would seem better and faster to do a fresh, re-install of Ubuntu.

- You can choose USE ENTIRE DISK in step 4 of the install process or;
- You can create the partitions beforehand, as well as separating /home from root, and do a manual install.

Your choice.  Either way (resizing and moving or re-install or manual install) would be a good learning experience.

Hi Ray

I've given it some thought and think that reinstalling fresh is the best way.  i DO need some practice and right now is the easiest time to do it.

I'm interested in segregating my root/ from the rest.  Is there a tutorial that can help me with that?  Can I assume that segregating the root is for security reasons?

I greatly appreciate your help.  I'm so new to linux, etc but am having a great time.

Brett

---

### Post by raymondh on 2009-12-17
> **bdws1975 said:**
> Hi Ray

I've given it some thought and think that reinstalling fresh is the best way.  i DO need some practice and right now is the easiest time to do it.

I'm interested in segregating my root/ from the rest.  Is there a tutorial that can help me with that?  Can I assume that segregating the root is for security reasons?

I greatly appreciate your help.  I'm so new to linux, etc but am having a great time.

Brett

Do you want to segregate / from /home with Ubuntu already installed .... [see this link]("http://www.psychocats.net/ubuntu/separatehome")

Do you want to separate the partitions (/ and /home) before installing ... [see this link]("http://www.psychocats.net/ubuntu/installseparatehome")

The biggest advantage of separating your personal configurations, files, settings (which reside in /home) from the system files (which reside in root /) is should you need to re-install Ubuntu, you only need to re-install over the borked root ... and just mount the existing /home to it.

Since you are ready to do a fresh install, go ahead and practice moving, resizing, creating partitions with gparted.  See what happens when you check/uncheck the 'round to cylinder' box .... and all those different permutations.

Here's a link on [how to restore GRUB2]("http://ubuntuforums.org/showthread.php?t=1014708") should you require it.

Have fun ... happy ubuntu-ing :)

---

### Post by bdws1975 on 2009-12-17
thanks so much Ray.

I couldn't wait so I successfully reinstalled ubuntu and now have all 320gb's clicking!  I'm thankful for your help.

Take care,
Brett

---

### Post by raymondh on 2009-12-17
> **bdws1975 said:**
> thanks so much Ray.

I couldn't wait so I successfully reinstalled ubuntu and now have all 320gb's clicking!  I'm thankful for your help.

Take care,
Brett

You're welcome.  Happy holidays.

---

