---
title: "HOWTO reinstall Ubuntu without loosing configs (even if /home not separate)"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2012-03-16
Reinstalling Ubuntu may sometimes be the quickest way to solve a problem (eg. if you broke your graphic driver).

Few people know it, but since Hardy it's possible to reinstall Ubuntu without loosing the content of the /home folder (which contains program settings, internet bookmarks, emails... and all the documents, music, videos that you have put in it). _**Even if /home is not a on separated partition.**_ (which is the case by default if you did not manually separate it).

Here is HOWTO do it simply:

1) by security, backup your documents and settings (including /home hidden files) on external disk or DVDs. Remark: some special applications settings may be in system folders, eg LAMP, see below in the thread.
2) run Ubuntu installer
3) go until the "Installation type" (or "Allocate disk space") menu
4) If you are using **Ubuntu 11.10 or newer**, you just need to select the "Upgrade 11.10 to 11.10" option of Ubuntu installer :

[[img]http://pix.toile-libre.org/upload/img/1331906258.png[/img]](http://pix.toile-libre.org/?img=1331906258.png)

5) If your are using **Ubuntu 11.04 or previous**, you need to choose manual partitioning ("Something-else" entry), then select Ubuntu system partition, set its mount point as "/" (keep the same format type, the same size, and untick the "Format" checkbox).

After reinstall, user accounts must be re-created with same login/password.

(I also created a wiki page in order to improve this HOWTO collaboratively: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation))

---

### Post by iamronen on 2012-04-03
I am trying to fix an 11.10 installation ... but the upgrade 11.10 to 11.10 option is disabled. 


Why is that?

Can I use the "something else" option safely to get around this?

---

### Post by OliverHaslam on 2012-04-03
I could really do with a way to do a clean install but not lose all my installed services and their settings. I've set the machine up as an AFP, web and SFTP server and don't want to have to do it all again.

---

### Post by YannBuntu on 2012-04-03
@iamronen: sorry i don't know why you don't have the option. Maybe we could find an explanation in your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1"). Please could you indicate it?

---

### Post by iamronen on 2012-04-03
Hello Yann,

I believe we communicated in email (I've been having boot problems for quite some time).. and after reviewing my logs you suggested I try to recovery installation ... only to find it disabled :(

I've generated an up-to-date summary:
[http://paste.ubuntu.com/913516]("http://paste.ubuntu.com/913516")

All Things Good
:)
Ronen

---

### Post by iamronen on 2012-04-04
Hello Again Yann,

I am trying to use the "Something Else" option and when I choose the "sda1" partition and click install now I get an error message saying that "No root file system is defined". 

Could this be an indicator about the problem I am experiencing?

All Things Good
Ronen

---

### Post by YannBuntu on 2012-04-05
Hi Ronen,
"No root file system is defined" means that you forgot to set the "/" mount point to your system partition (sda1).
Reminder: don't forget to untick the "Format" checkbox for sda1 if you want to preserve your configurations.

---

### Post by iamronen on 2012-04-06
Helly Yann,

Thank you. I am happy to report that my Ubuntu now (after many months) boots from the hard drive. However the installation was somewhat destructive.

I've had to restore the user accounts (the files were on the hard drive but the accounts were not created) ... I found a way to do that. It seems I have a lot of more installation to do. 

Amongst other things it seems I've lost my LAMP stack installation. Does this mean I've also lost any databases I had? If I install MySQL will the databases themeselves be restored? is there something I can/should do before installing the LAMP stack?

Gratefully Yours
Ronen

---

### Post by YannBuntu on 2012-04-06
After reinstall, user accounts must be re-created with same login /password, i will add this to the 1st post.
Concerning LAMP, sorry i don't know.

---

### Post by iamronen on 2012-04-06
Thank you Yann.

In the backup instructions I would a warning to people using a LAMP stack to backup anything in the var/www folder and MySQL databases.

I don't know what else resides in the var folder ... but it seems like a vulnerable space that is both a system folder and a potentially data-containing folder.

After installation I also had to resinstall some packages that are not in the Ubuntu core installation. Settings and data for these application were kept safely in the user home folder ... however applications were missing.

I wonder if the Reinstall option was available if it would have done a better job.

All Things Good
Ronen

---

### Post by YannBuntu on 2012-04-07
Thanks, i added a warning in the 1st post.

---

### Post by bwanamarko on 2012-09-16
Hi,

Thanks for this post.
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
I decided to wait until 12.10. My issues are not showstoppers, I can boot fine, just too frequent "Ubuntu has encountered an error" messages and "partial upgrades" since upgrading to 12.04LTS.

It would be very helpful if your post had a screenshot of the manual partitioning setup screen. My screen did not allow me to set the mount point of my ubuntu partition, nor did it have a checkbox under format. Also there were two other partitions, but I didn't know how to modify them. The directions in your post say, "Also set other partitions (/boot/efi, /boot...) if needed." but it wasn't clear to me what that means (n00b that I am) since I didn't have a /boot or /boot/efi partition, and to "what" should the other partitions be set? What mount points? Should they be formatted? Also, I know that my ubuntu install is on /dev/sda1, but how would another n00b know? Obviously this reinstallation method is not for complete n00bs, but I think just a little more detail on the partition screen would help vastly.

Also have a look at this thread:
[http://askubuntu.com/q/56051](http://askubuntu.com/q/56051)
in which many suggest creating a separate /home partition on your machine. This is the way my android is set up, and really appreciate how easy it is to reinstall my os, which I do quite frequently.

--Mark

---

### Post by YannBuntu on 2012-09-16
> **bwanamarko said:**
> I decided to wait until 12.10.

ok

> **bwanamarko said:**
> It would be very helpful if your post had a screenshot of the manual partitioning setup screen. 

I added a link to [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) which I updated recently (please look at it), but screenshots would be too much in this page.

Screenshots would be much more useful in this page: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

> **bwanamarko said:**
> My screen did not allow me to set the mount point of my ubuntu partition

This is not normal.

---

### Post by FabioJBCarneiro on 2012-10-27
Hello Yann,

I'm new to Ubuntu and in fact I have most of the questions bwanamarko has talked about.

I have separate /boot, /root, /home and EFI partitions. None of them have specified mount points and none of them are marked for formatting.

So, should I just mount the root partition on "/"? Should I do this to any of the others? Do I need to format any of them? 

Also, when asked the device for bootloader installation should I select the specific /boot partition or can I just select /dev/sda?

Sorry for the very basic questions, but I really am out of my element here. Thanks!

---

### Post by hans12345 on 2012-10-27
I'm planning to upgrade 12.04 to 12.10

I have a NAS (Network attached storage, in this case a Zyxel 310 using Samba) used by Ubuntu, Lubuntu and WIN XP machines. It's been tricky getting all my files accessible on the NAS.

Can I just upgrade, or will the accessing / using the NAS cause problems?

---

### Post by YannBuntu on 2012-10-28
> **FabioJBCarneiro said:**
> I have separate /boot, /root, /home and EFI partitions. None of them have specified mount points and none of them are marked for formatting.

So, should I just mount the root partition on "/"? Should I do this to any of the others? Do I need to format any of them? 


- if your /boot partition was already used by another system, create another /boot partition for your new system or you may get problems
- if your /home partition was already used by another system, you must use a different username or you will get problems
- you need to tick the "format" checkbox for / and /boot partitions. Tick the "format" checkbox for /home only if it is not already used by another system.
- you need to select the mount point for / , /boot and /home. Not for the EFI partition.
- as you use UEFI, please follow: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


> **FabioJBCarneiro said:**
> Also, when asked the device for bootloader installation should I select the specific /boot partition or can I just select /dev/sda?

Always leave /dev/sda.

---

### Post by keithpickering on 2012-12-03
> **YannBuntu said:**
> Reinstalling Ubuntu may sometimes be the quickest way to solve a problem (eg. if you broke your graphic driver).

1) by security, backup your documents and settings (including /home hidden files) on external disk or DVDs. Remark: some special applications settings may be in system folders, eg LAMP, see below in the thread.
2) run Ubuntu installer


And how do you invoke the Ubuntu installer??

---

### Post by YannBuntu on 2012-12-03
> **keithpickering said:**
> And how do you invoke the Ubuntu installer??

by clicking the "Install Ubuntu" button. [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Endolith on 2013-01-16
I tried to upgrade to 12.10 and now the boot is broken and it won't get past the Ubuntu loading screen.  Will the Reinstall option destroy any customized system files I have?  Or will it be smart and offer to keep/replace/show diff of them like the upgrade tool does?

The instructions on [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) seem incomplete.  Can you explain or link to *how *one recreates user accounts?

> **keithpickering said:**
> And how do you invoke the Ubuntu installer??

From a USB install disk?

---

### Post by gkampou on 2013-12-26
Will all configuration files remain unchanged (e.g. fstab, vim settings, etc)?

---

