---
title: "[SOLVED] Dual Boot Vista + Ubuntu"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Dave Crowhurst on 2007-08-30
I'm trying to set up a dual boot Vista + Ubuntu, and i'm following the guide at [apcmag.com]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") site. 

My computer is an Acer Aspire 5710 with an 80gb HDD.

I went in to disk management in Vista and I have...

Hidden volume 9.76 GB (EISA Configuration) - this is some kind of Acer backup/recovery partition?
ACER (C: ) 32.51 GB NTFS (System, Boot, Page File, Active, Crash Dump, Primary Partition)
DATA (D: ) 16.18 GB NTFS (Primary Partition)
16.08 GB Unallocated - this is where I want to install Ubuntu. I created this unallocated space by skrinking down the DATA (D:) partition.

Following the instructions I boot from my Live CD (64bit version)

> Ubuntu will then load the disk partitioner to determine where it's going to be installed. Choose "Manual - use the largest continuous free space". This will automatically select the unpartitioned space we created earlier using the Shrink tool. Click Forward.

I assume that should say Choose "Guided - use the largest continuous free space"

> On the "Ready to install" screen, you'll see that Ubuntu now has enough information to commence the installation. In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". This means that regardless of whether Ubuntu found any user account to migrate, it certainly knows that Windows Vista is installed on the other partition and is aware of it. Click Install.

The problem is that it does NOT know that Vista is installed on the other partition. Under 'Migration Assistant:' it is blank, whereas on the guide it should say Windows Vista/Longhorn (loader) (/dev/sda1)

On the bottom of the screenshot in the guide it says...
> The following partitions are going to be formatted:
partition #2 of SCS|1 (0.0.0) (sda) as ext3
partition #6 of SCS|1 (0.0.0) (sda) as swap

Whereas mine says...

The following partitions are going to be formatted:
partition #5 of SCS|1 (0.0.0) (sda) as ext3
partition #6 of SCS|1 (0.0.0) (sda) as swap

So I go back to Step 4 (prepare disk space) and click manual instead.

/dev/sda
/dev/sda1 ntfs /media/sda1 10478MB 8199MB free
/dev/sda2 ntfs/media/sda2 34911MB 18400MB free
/dev/sda3 ntfs/media/sda3 17371MB 3200MB free
free space 17261MB

So i'm thinking that **sda1** is the hidden recovery partition
**sda 2** is ACER (C: ) where Vista is installed
**sda 3** is DATA (D: )
**free space** is the space i created earlier.

So I need some help please.

Why is "Windows Vista/Longhorn (loader) (/dev/sda2" not being seen?
How do I install Ubuntu in the free space without messing up anything else and so that I can dual boot.

Please keep answers very simple as i'm a complete linux newb.

Many thanks.

---

### Post by Pumalite on 2007-08-30
You cannot partition with Gparted(Live CD); you have to use Vista partitioner first, then install; otherwise Vista will not let you install or run anything in your computer.

[http://sathyasays.wordpress.com/2007/06/12/vista-ubuntu-dual-boot/](http://sathyasays.wordpress.com/2007/06/12/vista-ubuntu-dual-boot/)

---

### Post by Dave Crowhurst on 2007-08-30
I already have Vista installed, I now want to install Ubuntu. The link you provided assumes Ubuntu installed already.

---

### Post by merlinus on 2007-08-30
This may help:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

-merlin

---

### Post by Irihapeti on 2007-08-30
Pumalite:

FYI, I was unable to get more than 4Mb out of trying to use Vista's partitioner, so I used GParted on the liveCD - just let it install automatically (which is very likely NOT recommended, but I did a backup first...). Vista did a great big chkdsk routine and rebooted a time or two, but the whole installation worked fine after that. Was I just lucky?

---

### Post by Pumalite on 2007-08-30
I think yes. First time I hear it. Thank you for the info.

---

### Post by Irihapeti on 2007-08-30
Pumalite:

Maybe it was beginners'' luck, but I had also read this first:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)
[http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/](http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/)

Might be useful to the OP.

Irihapeti

---

### Post by Pumalite on 2007-08-30
> **Irihapeti said:**
> Pumalite:

Maybe it was beginners'' luck, but I had also read this first:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)
[http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/](http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/)

Might be useful to the OP.

Irihapeti

Irihapeti: Thanks.
The first link (XP) was stuff I already had, but the second is pretty interesting stuff.

---

### Post by siralphred on 2007-08-30
the simplest way is to  type: "dskmgmt.msc"  into run (window key+r)  and shrink the vista patition to create a partition for ubuntu. restart with the ubuntu cd and install, where it asks which partition you would like to install ubuntu, remember to choose LARGEST CONTINOUS FREE SPACE that will install ubuntu in the partition u created in vista and will also install a bootloader so u have the option of vista or ubuntu on start up.  this is the easiest way for me since there are nor third party softwares involved

---

### Post by Dave Crowhurst on 2007-08-31
Thank you for the replies so far. [COLOR="Silver"]Can someone please read my original post and answer the specific questions I have asked. That would be very helpful to me as I want to get Ubuntu installed without trashing my Vista install.[/COLOR]

Edit - I'm going to use Wubi to install Ubuntu for me.

---

### Post by Pumalite on 2007-08-31
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by Dave Crowhurst on 2007-08-31
Pumalite, I have quite clearly stated in my original post that that IS the guide I am using. I am asking specific questions because my set up is different to that in the guide (he has one partition, I have multiple partitions).

---

### Post by Irihapeti on 2007-08-31
Dave Crowhurst:
It's been a little while since I've done it, but I seem to recall that when I installed Ubuntu the installer did not specifically note that Vista was there. It just identified that there was an NTFS partition, rather like you have been saying. As far as it was concerned, it could have been any of a number of OSs.

It would seem then that if you formatted the free space to ext3, it would become sda4 (I assume) and you could then install Ubuntu on that.

I agree, though, that the partition editor is a bit difficult to follow when you are totally new to such things. Anyway, if you find that Wubi does the job for you, great. You can always come back to this way of doing things later, if you wish.

Irihapeti

---

### Post by wisse on 2007-09-01
I have got exactly the same problem. And if the migration tool doesn't know that vista is there it will go wrong in the configuration of the grub bootloader won't it? Then why is this marked as SOLVED?

---

### Post by phoenix96 on 2007-09-01
Yup - there's a partition management applet on Vista

---

### Post by Irihapeti on 2007-09-02
Wisse:
Interesting point. I'll stand corrected. The migration assistant does know that Vista is there, now that you mention it, or I would not have ended up with an option in my Grub called "Vista/Longhorn". But when you start the install, it doesn't tell you, the user, "yes, I can see you have Vista there" or anything like that. Or it didn't in my case. But I ended up with a setup that worked straight away.

From what I can make of it, Vista partitions can be resized safely with GParted. I've tweaked the size of mine a couple of times. But if you use GParted, Vista runs a chkdsk on the next boot, which only takes a few minutes. It's no problem if you know what's happening - a bit scary if you don't!

As with any major disk operations, it's a good idea to do a backup beforehand - or at least be willing to live with losing your data. I have an install DVD for Vista - I'd feel a good deal less comfortable if I had to rely on a hidden recovery partition.

Irihapeti

---

### Post by wisse on 2007-09-02
Irihapeti:
Thanks, your reply encouraged me to just go ahead and try it. As mentioned before Vista
was not spotted during the installation. But it grub is configured just fine with the option Vista.
I have working dual boot now.

So it is SOLVED after all.

---

### Post by Irihapeti on 2007-09-02
Wisse:

That's great news. Welcome aboard!

Irihapeti

---

