---
title: "no custom hDD setup from 18.04 live server CD?"
date: 2018-06-09
forum: Installation &amp; Upgrades
---

### Post by csynt on 2018-06-09
Hi,

I am trying to do a (fresh) minimal 18.04 setup, installed on the HDD (UEFI) are already Windows 10 and FreeBSD.
issue is that the 'manual' installation of the live-server-18.04 CD does not display the existing partitions like is going to be the only OS
there . Am I using wrong CD image, or is it a bug? I don't want to install from the 'desktop' CD as there is no option for minimal xorg (just the gnome etc crap
that I don't want)

thx in advance.

---

### Post by oldfred on 2018-06-09
Do not know server, and now two server install versions.

Ubuntu will not see NTFS partitions that are hibernated.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Note that Windows on updates will turn fast start up back on. So if issues dual booting or mounting NTFS, check that first.

Some also do not have drives in UEFI settings, set for AHCI, make sure that is the case, but if not add AHCI drivers into Windows first.

---

### Post by csynt on 2018-06-09
thanks I know what you mean...

The installer program can't install  the grub ( some error like grub signed cant installed)

---

### Post by oldfred on 2018-06-09
If installing in UEFI boot mode, you must have an ESP - efi system partition and use gpt partitioning.

I use gparted from desktop as I have not installed with server, but you can use gdisk or gparted. You must set drive to gpt first.
Then create partitions.
Only fdisk in 18.04 supports gpt, older versions will not work, so if 18.04 it also should work.

Are you booting install media with UEFI Secure Boot on.
If you need any proprietary drivers for video or Wi-Fi, you will need Secure Boot off.

       GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[URL="http://www.rodsbooks.com/gdisk/"]http://www.rodsbooks.com/gdisk/


[/URL]

---

### Post by csynt on 2018-06-09
nope the hdd setup is fine, its just a [bug]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1771651") and looks like no-one took care of it so far.

---

### Post by QIII on 2018-06-09
The "bug" in the reports sounds exactly like what many of us went through early on with the advent of UEFI and gpt.

Since I have a single boot Bionic Server running right now that installed without issue (and I set it up with gpt and an EFI partition), it is certain that this is not a universal problem.  Given his long history of dealing with users who have had issues with this in the past and his success in helping them resolve the issue, I am inclined to be in agreement with oldfred vis-a-vis Windows 10.

"Confirmed" as a bug on Launchpad means that others have run into the same issue.  It may very well be that when the issue is triaged and examined, it won't be a bug at all -- but a condition caused by end-user installation.  Not to blame you:  Canonical *could do a lot more* to explain the situation and the messages provided during an attempted installation are vague and not particularly informative.

In any case, you have a problem that you need help with and we are happy to do so.  But please read the reasons your posts have been edited by the Staff.  Keeping a polite attitude and making sure your posts are free of profanity will go a long way toward making people here be willing to help you out.

---

