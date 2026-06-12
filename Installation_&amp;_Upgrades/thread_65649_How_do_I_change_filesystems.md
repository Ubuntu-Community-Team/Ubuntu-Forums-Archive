---
title: "How do I change filesystems?"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by agm642 on 2005-09-14
I'm not sure this is the correct place to post this, but I didn't find another place... Anyway, during the installation, I am only allowed to choose between ext2 and XFS. Is there a way to use another filesystem? Also, can I change my ext2 filesystem to another one without having to format the partition?

---

### Post by Juergen on 2005-09-14
You can enable the logging, making it an ext3-fs.
Other than that, changing the filesystem **is** formatting...

---

### Post by mchatel on 2005-09-14
[QUOTE=agm642]I'm not sure this is the correct place to post this, but I didn't find another place... Anyway, during the installation, I am only allowed to choose between ext2 and XFS. Is there a way to use another filesystem? Also, can I change my ext2 filesystem to another one without having to format the partition?[/QUOTE]

Hey there.
Might need more info, to give a useful answer.

So, do you mean you are going through the Ubuntu installation process, and setting up your partitioning and filesystem locations?  Are you referring to any particular directory or mount location (ex. home, /, etc...).

I know that when I was going through the Ubuntu installation, and setting up my partitions, I had a number of filesystem choices that I could choose.  I chose to use ReiserFS for all of my mount locations... except boot.  I stuck with ext3 for that.  

And of course, when you setup the swap space, there is no filesystem choice.

---

### Post by agm642 on 2005-09-14
Well, I simply chose disk partitioning from the installation menu, and I only got ext2 and XFS. It was a test system, so I only set up root and swap, therefore I don't know what it would do to other partitions.

---

### Post by mlomker on 2005-09-14
[QUOTE=agm642]I'm not sure this is the correct place to post this, but I didn't find another place... Anyway, during the installation, I am only allowed to choose between ext2 and XFS. Is there a way to use another filesystem? Also, can I change my ext2 filesystem to another one without having to format the partition?[/QUOTE]

The default is ext3, not ext2.  If you select the manual partitioning option then you can use any filesystem type that you want.  I'd recommend have /home separate from /.  That'll allow you to reinstall the operating system without losing everything valuable.  I run the Reiser3 filesystem, btw.

---

### Post by agm642 on 2005-09-15
OK, thanks a lot! I do have a seperate /home on my primary PC, that was just  a test one. I dunno why I couldn't get ext3... :confused: Anyway, how can I enable logging as Juergen said? Also, slightly off topic, but AFAIK Reiser and XFS are both quicker than ext3, is that true?

---

### Post by mlomker on 2005-09-16
[QUOTE=agm642]OK, thanks a lot! I do have a seperate /home on my primary PC, that was just  a test one. I dunno why I couldn't get ext3... :confused: Anyway, how can I enable logging as Juergen said? Also, slightly off topic, but AFAIK Reiser and XFS are both quicker than ext3, is that true?[/QUOTE]

You know what, I installed the Breezy version of Ubuntu at one point and I must have used that installer to uprade to reiser.  After a bit I had reinstalled Hoary and it was happy to use the reiser filesystem once it was there.  I think that's the deal...there are more options with the Breezy installer.

You can add a journal to an existing ext2 filesystem using the **tune2fs -j /dev/hd?** command.  You'll actually have to reformat to get to reiser, though.  For reiser it is **	mkreiserfs /dev/hd?**.

I really dig reiser--I've read some articles written by the company and they seem really cool.  It was also the default filesystem in Linspire and that's where I came from before Kubuntu.

---

### Post by agm642 on 2005-09-16
I won't risk installing a pre-release version of Breezy, so I will probably create a Reiser partition through Knoppix. I like Reiser very much too. Still, I hope we will soon see write support to it from Windows. Not that it really matters to me, but it would be useful, since I can't bring myself to abandon Windows completely. Thanks very much anyway.

---

### Post by mlomker on 2005-09-16
[QUOTE=agm642]Not that it really matters to me, but it would be useful, since I can't bring myself to abandon Windows completely.[/QUOTE]

I can't either...I'm actually an MCSE.  I run WinXP in a VMWare session on my Kubuntu box for the tools that I need in Windows.

---

