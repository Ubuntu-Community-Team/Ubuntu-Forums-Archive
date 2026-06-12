---
title: "Problems Booting 20.04.4 on a Dell Latitude 7400"
date: 2021-03-17
forum: Installation &amp; Upgrades
---

### Post by Martin_Kuemmel on 2021-03-17
Actually this is kind of an update to this issue from a year ago:
[https://ubuntuforums.org/showthread.php?t=2443622](https://ubuntuforums.org/showthread.php?t=2443622)

Then the solution was to upgrade to 20.0.4. However, over the course of the last year the situation got gradually worse. I *only* re-boot when suggested after a kernel update, but I needed more and more tries to get the boot started. As of now I need ca.20 tries ending up on a dark, slightly illuminated screen before I get a normal boot. I can boot from safe mode, but then some stuff like my docking station does not work properly. 

The machine is a 1-year-old Latitude 7400 laptop which had 18.0.4 as OEM from Dell when I bought it. The 18.0.4 still exists on another partition but does not boot (as a year ago). Then I created an issue on a Dell forum which was pushed around and eventually died out.

Right now I am kind of afraid to re-boot, since I don't know whether it gets up.

Any ideas?

---

### Post by kansasnoob on 2021-03-19
I read that old thread to get up to speed and suspect the kernel jump from the 5.4 series to the later "hwe" series kernels may be the culprit. But first lets gather a bit of info. 

Please post the output of these commands:

```
ls /boot
```

```
uname -r
```

```
apt policy linux-generic*
```

```
ubuntu-drivers list-oem
```

Note: the last one of those will take a while to complete and may well display nothing at all once the terminal prompt appears again.

---

### Post by Martin_Kuemmel on 2021-03-22
Sorry, just realized that post.
```

mkuemmel@bruce-2:~$ ls /boot/
config-5.8.0-44-generic      memtest86+.elf
config-5.8.0-45-generic      memtest86+_multiboot.bin
efi                          System.map-5.8.0-44-generic
grub                         System.map-5.8.0-45-generic
initrd.img                   vmlinuz
initrd.img-5.8.0-44-generic  vmlinuz-5.8.0-44-generic
initrd.img-5.8.0-45-generic  vmlinuz-5.8.0-45-generic
initrd.img.old               vmlinuz.old
memtest86+.bin
```

```

mkuemmel@bruce-2:~$ uname -r
5.8.0-45-generic
```

```

mkuemmel@bruce-2:~$ apt policy linux-generic*
linux-generic-hwe-18.04-edge:
  Installed: (none)
  Candidate: 5.4.0.67.70
  Version table:
     5.4.0.67.70 500
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     5.4.0.26.32 500
        500 http://de.archive.ubuntu.com/ubuntu focal/main amd64 Packages
linux-generic-hwe-20.04-edge:
  Installed: (none)
  Candidate: 5.8.0.45.51~20.04.31
  Version table:
     5.8.0.45.51~20.04.31 500
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
linux-generic-hwe-20.04:
  Installed: 5.8.0.45.51~20.04.31
  Candidate: 5.8.0.45.51~20.04.31
  Version table:
 *** 5.8.0.45.51~20.04.31 500
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.4.0.26.32 500
        500 http://de.archive.ubuntu.com/ubuntu focal/main amd64 Packages
linux-generic-hwe-18.04:
  Installed: (none)
  Candidate: 5.4.0.67.70
  Version table:
     5.4.0.67.70 500
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     5.4.0.26.32 500
        500 http://de.archive.ubuntu.com/ubuntu focal/main amd64 Packages
linux-generic:
  Installed: (none)
  Candidate: 5.4.0.67.70
  Version table:
     5.4.0.67.70 500
        500 http://de.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     5.4.0.26.32 500
        500 http://de.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```

That one gives nothing:
```
mkuemmel@bruce-2:~$ ubuntu-drivers list-oem
mkuemmel@bruce-2:~$ 

```

One bit of information, the last two successful boots were **both** with the USB-C cable of the docking station plugged in. There might be something in it and I can make some tests to see whether this is significant.

---

### Post by ajgreeny on 2021-03-22
Try installing the older 5.4.0-67 kernel, boot to it from grub and see if that helps as kansasnoob suspects it might.

I don't think there is any problem installingbthat older kernel even though you must now have linux-generic-20.04-hwe installed in order to get those 5.8.0 kernels.

I have never used the hwe system for any of my LTS installs so I'm not certain about these kernel version additions when moving back to older series but see what happens and then come back again.

---

### Post by Martin_Kuemmel on 2021-03-23
So the sequence of events was:
[LIST=1]
[*]I install a 5.4.0-67 kernel as suggested;
[*]I boot into that kernel, it works! Happy, but other things (dockingstation, internet, ...) don't, which maybe was to be expected.
[*]I boot into 5.8.0-45 just for fun, it works! Interesting.
[*]I boot several times into 5.8.0-45  with/without USB keyboard with/without dockingstation, it always works!
[*]I boot into 5.4.0-67, it does not work.
[/LIST]


At the end ~half of the boots into 5.4.0-67  do work, and most/all of the 5.8.0-45 boots work when they happen** after **after a 5.4.0-67. Should I go back to 5.4.0-67? I guess I would have to adjust many other packages (which of course is doable). Or get used to boot into 5.4.0-67 and then go for 5.8.0-45 afterwards?

---

### Post by ajgreeny on 2021-03-23
How very strange, and I'm afraid I have no idea where to suggest you go, or what  to try from here on.

Perhaps others will have more ideas; I certainly hope so!

---

### Post by Martin_Kuemmel on 2021-03-23
Okay while waiting for (hopefully) many other ideas, what's the strange part:
[LIST]
[*]that 5.4.0-67 is not fully functional; 
[*]that 5.4.0-67 does not always boot; 
[*]that 5.8.0-45 boots after a 5.4.0-67 boot? 
[/LIST]
Just curious.

---

### Post by ajgreeny on 2021-03-23
Can you check that you have all the packages that normally are installed with the linux-image packages, ie, the linux-headers, linux-modules packages of the exact same version as the linux-image package.  If they're missing install them and see if that makes any difference.

Linux-modules are a dependency of the linux-image so should be installed already but linux-headers are merely suggested packages so could be missing.
I honestly do not have any idea if that will make any difference to your problem but it is easy enough to install if missing so worth doing.

---

### Post by kansasnoob on 2021-03-23
> **Martin_Kuemmel said:**
> So the sequence of events was:
[LIST=1]
[*]I install a 5.4.0-67 kernel as suggested;
[*]I boot into that kernel, it works! Happy, but other things (dockingstation, internet, ...) don't, which maybe was to be expected.
[*]I boot into 5.8.0-45 just for fun, it works! Interesting.
[*]I boot several times into 5.8.0-45  with/without USB keyboard with/without dockingstation, it always works!
[*]I boot into 5.4.0-67, it does not work.
[/LIST]


At the end ~half of the boots into 5.4.0-67  do work, and most/all of the 5.8.0-45 boots work when they happen** after **after a 5.4.0-67. Should I go back to 5.4.0-67? I guess I would have to adjust many other packages (which of course is doable). Or get used to boot into 5.4.0-67 and then go for 5.8.0-45 afterwards?

What method did you use to install the 5.4 series kernel? The proper way would have been:

```
sudo apt install --install-recommends linux-generic
```

If already installed may help to run:

```
sudo apt-get reinstall --install-recommends linux-generic
```

Sometimes if just using "apt" fails the old "apt-get" command sorts things out.

This may be helpful:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop)

Even though nVidia may not be in play I'd still check for drivers using:

```
ubuntu-drivers list
```

That may display what wifi drivers are needed?

I'm uncertain about the docking station but let's do one thing at a time. Just happened to think - if not already doing so begin with:

```
sudo apt update
```

```
sudo apt dist-upgrade
```

We may also be able to spot any missing parts by running:

```
sudo apt-get -f install
```

Pay close attention though - under some circumstances that may recommend removing stuff we don't want to remove!

---

### Post by kansasnoob on 2021-03-24
Just thought to add - a reboot is needed after every change. For example if you're missing any "modules" for the 5.4 series 'linux-generic' kernel they won't load after installation until you reboot. If no progress after trying the above post the output of:

```
dpkg --list | grep 5.4.0-67
```

---

### Post by Martin_Kuemmel on 2021-03-24
Okay usually to whatever the "Software Updater" recommends and that's how I ended up with the 5.8 kernel that had the issues on boot.

To follow the suggestion to got back to 5.4.0.67 I followed a webpage I googled and did:
```
sudo apt-get install linux-image-5.4.0.67-generic linux-headers-5.4.0.67-generic
```

The kernel showed up in grub, I booted into it and it showed the behaviour above. My did not re-install any other dependent libraries and applications. So in the end I find it understandable that not everything works when using this "old" kernel.

I guess the two last posts would lead to a clean, working installation based on 5.4.0.67. Since I experience already now the failures to boot into 5.4.0.67 described above I am somehow afraid to end up with a 5.4.0.67 based laptop that has the same problems I am having right now with 5.8.x.

So, is there still hope that I'll be able reliably boot my laptop once turning everything back to 5.4.0.67?

---

### Post by kansasnoob on 2021-03-25
> **Martin_Kuemmel said:**
> Okay usually to whatever the "Software Updater" recommends and that's how I ended up with the 5.8 kernel that had the issues on boot.

To follow the suggestion to got back to 5.4.0.67 I followed a webpage I googled and did:
```
sudo apt-get install linux-image-5.4.0.67-generic linux-headers-5.4.0.67-generic
```

The kernel showed up in grub, I booted into it and it showed the behaviour above. My did not re-install any other dependent libraries and applications. So in the end I find it understandable that not everything works when using this "old" kernel.

I guess the two last posts would lead to a clean, working installation based on 5.4.0.67. Since I experience already now the failures to boot into 5.4.0.67 described above I am somehow afraid to end up with a 5.4.0.67 based laptop that has the same problems I am having right now with 5.8.x.

So, is there still hope that I'll be able reliably boot my laptop once turning everything back to 5.4.0.67?

I'm trying to get you back to the state you were in May 2020 with 20.04:

[https://ubuntuforums.org/showthread.php?t=2443622&page=2](https://ubuntuforums.org/showthread.php?t=2443622&page=2)

At that time 20.04 would have been running the 5.4 series kernel and you said all was well. What I'm recommending now should not create any new problems, but I would avoid removing any kernels until we have a 5.4 series kernel working properly. I suspect you may be missing something like the appropriate "linux-modules-extra" packages.

Just installing a specific kernel can create problems that's why we need to install 'linux-generic' with all of its "depends" and "recommends" so we know we're working with a complete kernel. Installing 'linux-generic' may well remove 'linux-generic-hwe' but right now we don't care about that. Those are just meta-packages to ensure we're not missing any dependencies and also to ensure proper updates to the series kernel we use so we're getting all the proper security updates. Like just yesterday most of my machines got the update to 5.4.0.70.73 just through the software-updater.

---

### Post by Martin_Kuemmel on 2021-03-26
Thanks for the explanation. This all makes sense, and I will tackle that during the weekend after generating the necessary backups and so on.
I'll post the result, of course!

---

### Post by Martin_Kuemmel on 2021-03-27
I did as suggested in #10. After a reboot everything works, which is great!
The newest kernel is -70, and #11 applied to that gives:
```
mkuemmel@bruce-2:~$ dpkg --list | grep 5.4.0-70
ii  linux-headers-5.4.0-70                     5.4.0-70.78                           all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-70-generic             5.4.0-70.78                           amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-5.4.0-70-generic               5.4.0-70.78                           amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                       5.4.0-70.78                           amd64        Linux Kernel Headers for development
ii  linux-modules-5.4.0-70-generic             5.4.0-70.78                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-70-generic       5.4.0-70.78                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP

```

I rebooted a couple of times (maybe 4), which for me is "Power off" and then switch on again. I did that with and without the dockingstation plugged in, and it worked.

Then I tried "Reboot". The mechanics is as with "Power off", I go the grub menu and select the -70 kernel. But it did not reboot. I tried a couple of times in various kernels, no way.

I tried in recovery mode, and it works (but my dockingstation not). I try with the dockingstation plugged in, and it works (including the dockingstation).

As kind of a summary:
[LIST]
[*]my laptop works with kernel 5.4.0-70.78 
[*]one reliable way to boot is to go for the recovery mode 
[*]the other reliable way to boot is with the dockingstation plugged in 
[*]when hitting "Reboot" the laptop does not boot 
[/LIST]

The situation is not so bad, but also not much different than it was with the 5.8 kernel. I'll consolidate the systematics on when I can boot and when not with a few tries. Apart from  that I am still happy for suggestions to improve the situation. The problem is not straight forward, but it is not straight forward since a year, and the fact that the Dell'ies could not find a solution might confirm that as well.

---

### Post by Martin_Kuemmel on 2021-04-16
Okay, the software update wants do install **both **new 5.4 and 5.8 kernels. I think it is time to get rid of the 5.8 kernels that are still on my system.

Could someone help me and tel me ho to de-install the 5.8 kernels?

Thanks.

---

### Post by deadflowr on 2021-04-16
> Could someone help me and tel me ho to de-install the 5.8 kernels?

You can remove the linux-generic-hwe-20.04 meta-package.
(Also check that removing that also removes both the linux-image-generic-hwe-20.04 and linux-headers-generic-hwe-20.04 meta-packages,
if it doesn't also remove those then mark those for removal too)
Removing those will stop it from trying installing the newer 5.8 kernels.

After that you might want to try manually removing any 5.8 kernels that are installed.

---

