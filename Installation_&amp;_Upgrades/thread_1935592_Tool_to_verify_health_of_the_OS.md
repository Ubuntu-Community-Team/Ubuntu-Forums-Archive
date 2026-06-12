---
title: "Tool to verify health of the OS"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by williepabon on 2012-03-04
Is there a tool or a command that I can use to verify that my Linux installation is healthy? I want to know if there is a tool that compares the system files installed in my hard drive with the standard distribution files for my version (that may be located either on a CD or online) to check if there are corrupted, missing or wrong version files, and offers the option to repair and/or replace the files that are at fault. Such a thing exists? Thanks.

---

### Post by Lasall on 2012-03-04
Hi williepabon,

you can try debsums - a tool to "check the MD5 sums of installed Debian packages".

---

### Post by Frogs Hair on 2012-03-04
The disk utility will give a green light if the disk is healthy . You will see the drives listed on the left pane .

---

### Post by williepabon on 2012-03-04
> **Lasall said:**
> Hi williepabon,

you can try debsums - a tool to "check the MD5 sums of installed Debian packages".

Lasall:
Thanks for answering. Need some help in the use of the tool. I installed it from the  repositories, but not sure how to write the command to check the integrity of the OS. My OS is Ubuntu 10.04. Thanks for the help.
wp

---

### Post by Lasall on 2012-03-04
You have to initialize it first (generate missing md5sums), then check all files installed over dpkg (with config files):
```

sudo debsums_init
sudo debsums -ca

```
You get a list of files which md5sums differ from original installation. In the majority of cases (or even always) that are changed configuration files.

On your system there are some files that are not tracked by dpkg, so they will not be checked with debsums.

---

### Post by williepabon on 2012-03-07
> **Lasall said:**
> You have to initialize it first (generate missing md5sums), then check all files installed over dpkg (with config files):
```

sudo debsums_init
sudo debsums -ca

```
You get a list of files which md5sums differ from original installation. In the majority of cases (or even always) that are changed configuration files.

On your system there are some files that are not tracked by dpkg, so they will not be checked with debsums.

Lasall:

Thanks for the info. I used the command to check specifically my Ubuntu kernel version (2.6.32-38-generic and all the files reported OK. What else should I be doing? Thanks.

---

### Post by CharlesA on 2012-03-07
Are you checking files because you think your machine may have been compromised?

---

### Post by williepabon on 2012-03-07
> **CharlesA said:**
> Are you checking files because you think your machine may have been compromised?

Charles:
Thanks for answering. First, I have been running Ubuntu 10.04 from an external drive (connected via a USB port) for the past two years without any problem whatsoever. A few weeks ago, I increased the RAM on my pc (could be coincidental) and now the USB ports all run excessively slow. Obviously, since my OS run from the external drive, now everything slows down to a crawl. I also have Ubuntu 10.10 on a memory stick (USB). If I boot up with it, everything is fine an normal. So, I suspected that some driver within the kernel of 10.04 might be corrupted or changed for some unknown reason. That's why I did the debsums command to verify the integrity of the files on the OS, but everything there checked OK. Now, I don't know what else to do. Any suggestions? Thanks.

---

### Post by ajgreeny on 2012-03-07
Just as a test, try booting to an earlier kernel from the grub menu, and see if it makes any difference to your USB transfer speed.

I suggest this as I did try a different kernel several months back from the ppa repository available just for more recent kernel versions;  I think it was a 2.6.38 version but can't remember in detail.  Using it my USB transfer speeds were appallingly slow; just a few KB/sec, so it was useless for many activities including regular backups to USB hard-drive, and I quickly uninstalled it.

I am using 10.04 like you, but now run a 2.6.35-32 kernel from the proposed repos, which I have enabled in the update tab of software-sources.

---

### Post by williepabon on 2012-03-07
> **ajgreeny said:**
> Just as a test, try booting to an earlier kernel from the grub menu, and see if it makes any difference to your USB transfer speed.

I am using 10.04 like you, but now run a 2.6.35-32 kernel from the proposed repos, which I have enabled in the update tab of software-sources.

ajgreeny:
Your suggestion, I already did. I tried the last two previous kernels bu I got the same problem.

---

### Post by grahammechanical on 2012-03-07
When you increased the RAM did the BIOS get reset to factory defaults or something?

I found that in my BIOS I did not get options to adjust USB speeds until I disabled legacy floppy disk support. Then USB options turn up and I then got two speed settings for the USB ports which were not available before.

Finding out which one was the fastest setting made running from USB a lot faster than before.

So, in your case I am wondering if somehow the BIOS settings got reverted or changed when more RAM was added.

Regards.

---

### Post by williepabon on 2012-03-12
> **grahammechanical said:**
> When you increased the RAM did the BIOS get reset to factory defaults or something?

I found that in my BIOS I did not get options to adjust USB speeds until I disabled legacy floppy disk support. Then USB options turn up and I then got two speed settings for the USB ports which were not available before.

Finding out which one was the fastest setting made running from USB a lot faster than before.

So, in your case I am wondering if somehow the BIOS settings got reverted or changed when more RAM was added.

Regards.


Thanks for answering. My situation is not like you describe. I found out that the problem manifests itself when the pc has 3 Gigs of RAM. I documented the whole situation on Question #190306 at Ubuntu Launchpad, but still I haven't received a solution for my problem. I am wishing an Ubuntu nerd that figures out my problem. Or, is it a bug?

---

