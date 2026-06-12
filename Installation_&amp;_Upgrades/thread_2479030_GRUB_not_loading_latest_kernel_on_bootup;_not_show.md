---
title: "GRUB not loading latest kernel on bootup; not showing in Advanced Options for Ubuntu"
date: 2022-09-12
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2022-09-12
I recently installed Ubuntu 22.04 LTS, going from 20.04 LTS, and afterwards there are issues with things such as no audio output.
I have an older kernel version (5.13.0-28-generic) being used by GRUB so I installed 5.15.47 using this link as a guide:

[https://www.how2shout.com/linux/how-to-change-default-kernel-in-ubuntu-22-04-20-04-lts/]("https://www.how2shout.com/linux/how-to-change-default-kernel-in-ubuntu-22-04-20-04-lts/")

I am trying to determine why the GRUB is ignoring the newer kernel instance and using the older version instead.
On bootup under 'Advanced Options for Ubuntu' only older kernel versions are displayed, not the recently installed newer version.
Would updating the GRUB Boot Loader in Recovery Mode (F9) have an impact on this problem? Is it
ok/safe to try such a thing?

```

ed@ed-G41MT-S2PT:~$ sudo ubuntu-mainline-kernel.sh -l
[sudo] password for ed: 
v5.15.47-051547
ed@ed-G41MT-S2PT:~$ 

```

But with uname command it shows:

```

ed@ed-G41MT-S2PT:~$ uname -r
5.13.0-28-generic
ed@ed-G41MT-S2PT:~$ 

```

---

### Post by yancek on 2022-09-12
>  Would updating the GRUB Boot Loader in the BIOS have an impact on this problem?  

I'm not sure what you mean by the above statement as there is no Grub in the BIOS firmware.  It is n the drive, the / partition and either the MBR in older Legacy systems or the EFI partition.  If you did not run sudo update-grub, there is not way for Grub to know there is a new kernel.

---

### Post by ozark_hillbilly on 2022-09-12
My bad.
I am referring to after booting up and using the DEL key one option at bottom of screen is Recovery Mode (F9). One of the available options is: "Update GRUB Boot Loader"
I was wondering if this would have any effect on my issue.

---

