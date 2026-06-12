---
title: "i386 support"
date: 2021-06-14
forum: Installation &amp; Upgrades
---

### Post by axet2 on 2021-06-14
Hello!

I tried to install Ubuntu on i386, and suprized linux-image-generic is no longer available! Strange, even old LTS releases has no i386 support any longer.

Package info has no i386 links:

[https://packages.ubuntu.com/focal/linux-image-generic](https://packages.ubuntu.com/focal/linux-image-generic)

Or just direct link:

[http://archive.ubuntu.com/ubuntu/dists/focal/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/focal/main/binary-i386/Packages.gz)

has no linux-image at whole! Yet amd64 has it:

[http://archive.ubuntu.com/ubuntu/dists/focal/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/focal/main/binary-amd64/Packages.gz)

Ubuntu no longer support i386 even for old releases?

---

### Post by Holger_Gehrke on 2021-06-14
That's not an old LTS, it's the current LTS published in April 2020. AFAIK the last LTS which supported 32 bit processors was 18.04 (bionic beaver). For main line Ubuntu that has slightly less than two years of support left but for the other flavours it's partially EOL. By "partially" I mean that the stuff it has in common with main line Ubuntu still gets updates, but the packages which are specific to the flavour don't.

Holger

---

### Post by Impavidus on 2021-06-14
Not in Ubuntu 20.04, which never had any 32 bit support, but the 32 bit kernels are still available for Ubuntu 18.04.

I remember that the Ubuntu 18.04 live disk only came as 64 bit, but the Lubuntu and Xubuntu live disks for 18.04 were still available as 32 bit.

---

### Post by guiverc on 2021-06-14
Most *flavors* (*if not al*l) provided i386 ISOs for Ubuntu 18.04 LTS.

Lubuntu & Xubuntu released & provided 18.10 ISOs, and even continued building  them into the *disco* (19.04) cycle, the package build infrastructure remained on for the entire *disco* cycle so installs of Lubuntu/Xubuntu 19.04 received updated packages though neither flavor actually produced an *official* released ISO (only the *dailies* until Dec 2018).

(*technically the building of eoan i386 packages continued in the alpha stage, even into beta, but that was disabled prior to official launch so on release day any i386 installs was two kernel updates behind the official released kernel found on amd64 ISOs, falling further behind too as time ticked on).*

---

### Post by ActionParsnip on 2021-06-14
Does the system have a make and model?

---

### Post by TheFu on 2021-06-14
> **Impavidus said:**
> Not in Ubuntu 20.04, which never had any 32 bit support, but the 32 bit kernels are still available for Ubuntu 18.04.

I remember that the Ubuntu 18.04 live disk only came as 64 bit, but the Lubuntu and Xubuntu live disks for 18.04 were still available as 32 bit.

I'm fairly certain that Ubuntu moved to i686 with Intel instructions a long time ago.  I've had a number of Via i686 clone CPUs that were missing all the necessary i686 instructions that Ubuntu (and many other) Linux required since 2012 when Intel 80386 was dropped from the 3.8 kernel. Here's the commit
[https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=743aa456c1834f76982af44e8b71d1a0b2a82e21](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=743aa456c1834f76982af44e8b71d1a0b2a82e21)

> Pull "Nuke 386-DX/SX support" from Ingo Molnar:
 "This tree removes ancient-386-CPUs support and thus zaps quite a bit
  of complexity

32-bit != i386.  The file name convention hasn't been honest for some time. The same can be said for amd64 in the filenames.  It is for all x86-64 CPUs, not just those from AMD.

32-bit == i686 for a long time.  I think somewhere around 19.10, Canonical decided to drop i686 support. 
Arch Linux dropped i686 support in 2017. 
Fedora dropped it in 2019 (F-31) too. Prior to then, there was a community version with 32-bit i686 support, but there wasn't enough volunteers to keep that effort going.

Debian retains i686 support, if that is a possibility for the OP's needs.  I suspect MX-Linux has i686 support too. A friend who likes to run really old hardware uses it, plus it is systemd free, which can make many people happy.

---

### Post by oldfred on 2021-06-14
Users often think they need 32 bit as they have 32 bit Windows.
May be 64 bit hardware and 64 bit Ubuntu or more likely a lightweight flavor of Ubuntu will work just fine.

Almost all UEFI systems are 64 bit. 

Microsoft required vendors to install in UEFI boot mode using gpt partitioning with release of Windows 8 in 2012. A few tablet type systems were 32 bit UEFI boot, but 64 bit systems.

Many systems since 2006 were 64 bit. My laptop & desktop from 2006 were core2 duo or 64 bit. Some Pentium systems were 32 bit & some were 64 bit from back then.

Advantages and Disadvantages of 64bit. (Plus install Guides) from 2008
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by rsteinmetz70112 on 2021-06-14
It's a little confusing since Ubuntu calls some of the 32 bit packages i386, even though the kernels won't run on a real 386.

---

### Post by deadflowr on 2021-06-14
32-bit is a mixed bag on 20.04 and newer versions of Ubuntu.
On the one hand, The dropped support refers to the host architectures, like no more 32-bit kernels. Making running a 32-bit system impossible.
But on the other hand, a lot of packages are 32-bit only or require 32-bit libraries that they have to keep maintaining those or else [s]major[/s] issues can happen.
Ubuntu has been keeping a tracking list of these which you can read about here:
See: [https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598/1]("https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598/1")

Unfortunately the options for running 32-bit are slowly dwindling as more and more distros move in the same direction as Ubuntu.

---

### Post by grahammechanical on 2021-06-14
Wine is a package/application that requires 32 bit (i386) libraries. There is a 64 bit version of Wine but if we want to run a 32 bit Windows application through Wine we will need lots of i386 libraries installed as well.

The 64 bit CPU architecture (AMD64) is backwards compatible with 32 bit CPU architecture (i386). So, 32 bit applications will run on a 64 bit OS. A lot of Windows applications were 32 bit. And so to use Wine to run them requires 32 bit libraries which are still available in the Ubuntu repositories.

Ubuntu no longer supports a 32 bit (i386) operating system. This is noted above. But it does support some 32 bit (i386) libraries. You will most likely need to activate the universe repository.

Regards

---

### Post by guiverc on 2021-06-14
> **grahammechanical said:**
> 
Ubuntu no longer supports a 32 bit (i386) operating system.

Ubuntu 18.04 is not EOL yet for *main* Ubuntu.

Ubuntu in i386 (*technically i686 but Debian/Ubuntu call them x86 32-bit i386*) still offers support for Ubuntu Server to be installed in i386 which has slightly less than two years of supported life remaining  (if I recall correctly, it may *not* have ESM support though just like i386 isn't mentioned in *xenial* ESM notices).

ISOs for download still exist though are limited - ie. [https://cdimage.ubuntu.com/netboot/18.04/](https://cdimage.ubuntu.com/netboot/18.04/) or [http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-i386/current/images/netboot/) as no *live* installers were created in i386 for Ubuntu, only *flavors*.

---

### Post by MAFoElffen on 2021-06-14
My question to the OP is what CPU is it? 

I can well remember trying to run Linux on older Pentium 32 bit procs and comparable early AMD's that (in time) needed older or special kernels to keep running. Biggest was whether they had PAE support or not. It was a pain to try to install non-PAE kernels, which as I remember, the last Ubuntu flavor to support that was Lubuntu, (many years back)... Then installing other Desktops to it.

As for the future of Linux now and future support of i386: [https://lwn.net/Articles/838807/](https://lwn.net/Articles/838807/)

Quote from that historical note:
> ***"It is well understood that many 32-bit systems will stop working in the year 2038 when the 32-bit time_t overflows."***

Just saying...

---

