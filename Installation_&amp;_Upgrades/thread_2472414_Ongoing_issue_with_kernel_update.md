---
title: "Ongoing issue with kernel update"
date: 2022-02-26
forum: Installation &amp; Upgrades
---

### Post by daithi_dearg on 2022-02-26
Hello,

Raised this in the past but never got anywhere with it and I guess I'll reinstall if I get nowhere.

More urgency is on this on the back of this:
[https://www.theregister.com/2022/02/23/ubuntu_kernel_updates/](https://www.theregister.com/2022/02/23/ubuntu_kernel_updates/)

I followed the steps in this but since then I'm prompted to run:
sudo apt --fix-broken install

Have following kernels:
```
dpkg --list 'linux-*' | grep -v '^rc\|^un'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-==================================================================
ii  linux-base                                    4.5ubuntu3.7                all          Linux image base package
ii  linux-firmware                                1.187.26                    all          Firmware for Linux kernel drivers
in  linux-headers-5.11.3-051103-generic           <none>                      amd64        (no description available)
iU  linux-headers-5.14.0-1024-oem                 5.14.0-1024.26              amd64        Linux kernel headers for version 5.14.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
iU  linux-headers-oem-20.04d                      5.14.0.1024.22              amd64        OEM Linux kernel headers
iU  linux-image-5.14.0-1024-oem                   5.14.0-1024.26              amd64        Signed kernel image oem
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
iU  linux-image-oem-20.04d                        5.14.0.1024.22              amd64        OEM Linux kernel image
ii  linux-libc-dev:amd64                          5.4.0-100.113               amd64        Linux Kernel Headers for development
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
in  linux-modules-5.14.0-1024-oem                 <none>                      amd64        (no description available)
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-5.6.14-050614-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-65-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-66-generic          <none>                      amd64        (no description available)
iU  linux-oem-20.04b                              5.14.0.1024.22              amd64        Complete OEM Linux kernel and headers (dummy transitional package)
iU  linux-oem-20.04d                              5.14.0.1024.22              amd64        Complete OEM Linux kernel and headers
iU  linux-oem-5.14-headers-5.14.0-1024            5.14.0-1024.26              all          Header files related to Linux kernel version 5.14.0
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5        all          base package for ALSA and OSS sound systems
```

Also:
```
s -ltr /boot/initrd.img*
lrwxrwxrwx 1 root root       27 Mar  4  2021 /boot/initrd.img.old -> initrd.img-5.4.0-42-generic
lrwxrwxrwx 1 root root       27 Sep 19 21:01 /boot/initrd.img -> initrd.img-5.4.0-42-generic
-rw-r--r-- 1 root root 82518823 Feb 15 22:24 /boot/initrd.img-5.4.0-42-generic
```

Hoping someone can shed some light on this.

---

### Post by Impavidus on 2022-02-26
Have you any particular reason to install the 5.14 kernel? It could be useful on bleeding edge hardware, but for most users the 5.4 or 5.13 kernels should be adequate. It appears that installation of the 5.14 kernel failed. The only properly installed kernel is a rather old version of the 5.4 kernel (5.4.0-42). Every supported kernel series is secure and the older ones like 5.4 are actually more secure than the newer ones like 5.13, but you should use the latest version within that series, so that's 5.4.0-100 or 5.13.0-30. So what's your intention? Which kernel must be installed? Then get rid of the others.

---

### Post by daithi_dearg on 2022-02-26
I'd be happy enough to get up to 5.13.030 as 5.4 looks like it was back in 2019:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

My Ubuntu version is Ubuntu 20.04.3 LTS and I see here that this looks to be the kernel on this release:
[https://en.wikipedia.org/wiki/Ubuntu_version_history#Table_of_versions](https://en.wikipedia.org/wiki/Ubuntu_version_history#Table_of_versions)

Rightly or wrongly I thought there would be regular kernel updates offered.

I was applying updates with this syntax:
sudo apt-get update && sudo apt-get dist-upgrade

I also noticed I'm on the latest LTS so maybe I have set options to only upgrade with the LTS.

See in the register in the original post:
The single high severity bug &#8211; CVE-2022-0492 &#8211; is to be found amongst the fixes for OEM 5.14 build of 20.04,

---

### Post by Impavidus on 2022-02-26
Ubuntu 20.04 comes with kernel 5.4 because that was the latest kernel when features were frozen shortly before release early in 2020. To improve stability, no new features are added after that, but bugfixes get backported. If you need the new features, you can get a newer kernel on LTS releases, but you don't need the new kernel for security fixes. Those security fixes get backported to all the old kernel versions still supported on Ubuntu, 5.13, 5.4, 4.15, so those fixes are there too, unless the vulnerability they are supposed to fix isn't present on those older kernels. And that's what's meant by “The single high severity bug – CVE-2022-0492 – is to be found amongst the fixes for OEM 5.14 build of 20.04.” The vulnerabilty fixed by this fix is present in a feature that was recently added to the kernel and is therefore not present in the 5.4 kernel, so need to fix it there.

So abandon the idea that you need the latest kernel for security. The older kernels, but with the latest patches, are actually more secure.

Now for your actual issue. Let's try and get you on the 5.13 kernel, which is the default on fresh installs of Ubuntu 20.04 LTS. It will be upgraded automatically to 5.15 in July, when 21.10 reaches end of life and 20.04 with hwe switches to the kernel used by 22.04. If everything goes well, it can be installed with```
sudo apt update
sudo apt install linux-generic-hwe-20.04
```However, you probably need some cleanup first. Let's see what's actually going wrong:```
sudo apt update
sudo apt install -f
```Hopefully that gives an interesting error message. Just post the whole output here.

---

### Post by MAFoElffen on 2022-02-28
I see a mess, with lots of orphaned packages, that if that was on one of my own machines, or on one of my customers', I would clean up.

Let me show you, your own output, in a different type of perspective from the last thread, and show where you are now. Frankly I don't care about the past, and I wish people would quit focusing on distractions. Lets move forward...

Here are the only images in the packages from your first list:
```

ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
iU  linux-image-oem-20.04d                        5.14.0.1024.22              amd64        OEM Linux kernel image
iU  linux-image-5.14.0-1024-oem                   5.14.0-1024.26              amd64        Signed kernel image oem

```
 
In your boot directory, there is only one version there that it has to boot from:
```

Linux kernel 5.4.0-42

```

Which means everything there that does not have that kernel version, I would purge. That may sound drastic, but look at it, I'll indicate in red and orange: 
```

ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
[COLOR=#ff0000]in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-65-generic          <none>                      amd64        (no description available)[/COLOR]
[COLOR=#ff0000]in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-65-generic          <none>                      amd64        (no description available)
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-66-generic          <none>                      amd64        (no description available)
in  linux-modules-5.6.14-050614-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
in  linux-headers-5.11.3-051103-generic           <none>                      amd64        (no description available)
 in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-66-generic          <none>                      amd64        (no description available)
in  linux-modules-5.6.14-050614-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
in  linux-headers-5.11.3-051103-generic           <none>                      amd64        (no description available)
[/COLOR][COLOR=#ff8c00]iU  linux-headers-5.14.0-1024-oem                 5.14.0-1024.26              amd64        Linux kernel headers for version 5.14.0 on 64 bit x86 SMP
in  linux-modules-5.14.0-1024-oem                 <none>                      amd64        (no description available)
iU  linux-image-5.14.0-1024-oem                   5.14.0-1024.26              amd64        Signed kernel image oem
iU  linux-oem-5.14-headers-5.14.0-1024            5.14.0-1024.26              all          Header files related to Linux kernel version 5.14.0
iU  linux-headers-oem-20.04d                      5.14.0.1024.22              amd64        OEM Linux kernel headers
iU  linux-oem-20.04b                              5.14.0.1024.22              amd64        Complete OEM Linux kernel and headers (dummy transitional package)
iU  linux-oem-20.04d                              5.14.0.1024.22              amd64        Complete OEM Linux kernel and headers
iU  linux-image-oem-20.04d                        5.14.0.1024.22              amd64        OEM Linux kernel image[/COLOR]

```
All those in red above are orphaned. They are orphaned and do no go to any Linux Kernel image you have install, so they are just taking up space and doing nothing. Purge those packages, all of them...

5.14? I don't how it got there. As I remember, you also do not know how it got there. No matters. I know that there would have been problems trying to run 5.14 on 20.04.3. I tested this about 5-6 months ago. As far as I could go without problems was up into the 5.13 range, and there were still challenges. That is probably why there is no intramfs image of it in /boot. Purge that.

Once you get it cleaned up, there will still be some dependency challenges, and a problem where your kernel was not upgrading properly right? It still has a broken system that is not upgrading kernels in a series. So once the cleanup is done, we need to move forward to try to fix that. There is a way to get the apt-system to work that out 'for you'. For both of those problems. But we need to check something first...

First, run this:
```

which ubuntu-drivers
# if it comes back with something like /usr/bin/ubuntu-drivers, go on. 
# If blank output, then install package package 'ubuntu-drivers-common'.

ubuntu-drivers list-oem
# if no output, then this is true: "Ubuntu Certified Hardware Platform. Safe to install the Hardware Enablement Stack (HWE)." || \
# if output, then "Hardware meta packages were listed. Please refrain from manually changing the kernel flavors. The Hardware Enablement Stack (HWE) should not be installed on this platform. "

```
This is something that you, or anyone else **should run** on their own computers before blindly upgrading kernels or installing the HWE... It will tell them (as per the Ubuntu Wiki) "if it is safe to install on their hardware." I'm just going by the doc's... I have this code in the UbuntuForums 'system-info' script, especially for that purpose.

If it says your hardware is compatible with HWE, then you should, even if it is just temporarily. I know with me saying that, you are "saying what the heck?" Your greatest chance of success is for apt to install all the packages necessary to get a different kernel series working again on your computer (even if that is only a part of HWE). Does that sound reasonable and logical now? You can always go back back... And I will post the commands for both...

If safe, then the command to install the HWE is
```

sudo apt install --install-recommends linux-generic-hwe-20.04

```
When it displays what packages it is going to install, copy the terminal output of that into a text file in an editor to save a record of that...

You should have a working kernel series upgrade system now, but you may or may not want to be on that series. That is a personal decision you have to make on your own... If you wanted to downgrade via
```

sudo apt install --install-recommends linux-generic

```

If the verification test above said your hardware was not safe to install the HWE or to upgrade kernels... Then do this
```

sudo apt install --reinstall --install-recommends linux-generic

```
Tell me how it goes...

P.S.: Notice there is not path between HWE or normal except to upgrade to HWE or downgrade to Generic. If someone tries to purge or uninstall either package, bad JuJu...

EDIT2:
If you want to verify that, or see what was (in some point of time) manually installed, run the 'system-info" script in my signature line and let it upload to a pastebin somewhere, then post the link to it. That report will show what we are recommending a solution for, and fill in some blanks in information..

---

### Post by daithi_dearg on 2022-02-28
Ok sounds like I was worrying unnneccesarily.

I came across and I suppose I look under package "linux" and high priority and released I see that CVE-2022-0185 is only one released this year:
[https://ubuntu.com/security/CVE-2022-0185](https://ubuntu.com/security/CVE-2022-0185)

This seems to be fixed with this release:
Released (5.4.0-96.109) 

I thought with Apache I could check the releases backported into a release and I wonder is there something similar.

I was able to clean up this more recent kernel with synaptic.

I know there's an newer LTS due in the next couple of months and I can wait for that. I was more concerned that the kernel I was on had Vulnerabilities.

Much appreciated for the education.

---

### Post by Impavidus on 2022-02-28
Now that you have cleaned up the orphaned packages, make sure you get all security patches for your currently installed kernel. The way to do that is by installing the kernel metapackage. For kernel 5.4, that's```
sudo apt install linux-generic
```
Alternatively, for kernel 5.13, it's```
sudo apt install linux-generic-hwe-20.04
```

---

### Post by MAFoElffen on 2022-02-28
@Impavidus - Exactly, with one more caveat...

@daithi_dearg
Look at my post... Please do not forget the "--install-recommends" flag. And run the two lines of code I posted before making a decision to install HWE, for the just in cases.

The reason I am recommending that flag, is your system is broke in how it is upgrading kernels and keeping "In Series"... It needs that extra help there to get back to where it should be. Either of those should "fix" your system.

Once it get's that gong again, then the security patch upgrades should start working again. The goal is to get the "Kernel Series Upgrades" system working again for you.

I apologize that i didn't take a more active participation on your last thread. I thought it was being handled.

---

### Post by daithi_dearg on 2022-02-28
Is there some syntax missing here:
```
[ ! -z "$(which ubuntu-drivers)" ] && echo -e "Please install package 'ubuntu-drivers-extra' before continuing." || echo -e "Safe to go on with next command."
[ -z "$(ubuntu-drivers list-oem 2> /dev/null )" ] && echo "Ubuntu Certified Hardware Platform. Safe to install the Hardware Enablement Stack (HWE)."" || echo "Hardware meta packages were listed. Please refrain from manually changing the kernel flavours. The Hardware Enablement Stack (HWE) should not be installed on this platform. "
```

Do I need to create a script off this?

Also in regards to the cleanup I was going on this being the list I needed to cleanup but no joy
```
david@david-N7x0WU:~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'|grep -v ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-===============================================================
iU  linux-generic                                 5.4.0.100.104               amd64        Complete Generic Linux kernel and headers
iU  linux-image-generic                           5.4.0.100.104               amd64        Generic Linux kernel image
in  linux-modules-5.10.12-051012-generic          <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-5.6.14-050614-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-100-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-65-generic          <none>                      amd64        (no description available)

david@david-N7x0WU:~$ sudo dpkg --purge linux-modules-5.10.12-051012-generic
[sudo] password for david: 
dpkg: warning: ignoring request to remove linux-modules-5.10.12-051012-generic which isn't installed
```

Was trying to stick on the 5.4.0 kernel but get these errors:
```
david@david-N7x0WU:~$ sudo apt install --install-recommends linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version (5.4.0.100.104).
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-modules-extra-5.4.0-100-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
david@david-N7x0WU:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.4.0-100-generic
The following NEW packages will be installed:
  linux-modules-extra-5.4.0-100-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/39.4 MB of archives.
After this operation, 202 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 191762 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-100-generic_5.4.0-100.113_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-100-generic (5.4.0-100.113) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-100-generic_5.4.0-100.113_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-100-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.4.0-100-generic_5.4.0-100.113_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Seems like this is pretty corrupted so probably best to go with with hwe kernel so if you share the syntax on whether my hardware is compatible with this I can attempt this.

---

### Post by ActionParsnip on 2022-02-28
what is the output of
```

df -h

```

---

### Post by MAFoElffen on 2022-02-28
Sorry. I had a typo up above...

It comes out to two commands. Instead of trying to make them one-lines, I'll just explain each:
```

which ubuntu-drivers

```
This checks if the command is actually there. If it comes back with something like' /usr/bin/ubuntu-drivers', it's installed, go on.
 
If blank output, then install package package 'ubuntu-drivers-common', which includes the 'ubuntu-drivers' utility.

Once there:
```

ubuntu-drivers list-oem

```
If this commands returns no output, then the Ubuntu Wiki says that the hardware tested is: "...an Ubuntu Certified Hardware Platform. It is safe to install the Hardware Enablement Stack (HWE)." 

If that command does show any output, then the Ubuntu Wiki warns that "if Hardware meta packages were listed. Please refrain  from manually changing the kernel flavors. The Hardware Enablement Stack  (HWE) should not be installed on this platform. "

I'm not sure of the outcomes if you go against that, but thought if they took the time to say that, instead of just going ahead and installing it, that there must have been "something" that happened that prompted them to say that. I mean, I test a lot of DEV things. Not all goes well, and I get lots of practice finding work-arounds and fixes. But for them to say that, using that wording in their Doc's, after all the other things I have tested without warnings from them... Just saying.

---

### Post by daithi_dearg on 2022-03-01
Command ran fine:
```
david@david-N7x0WU:~$ which ubuntu-drivers
/usr/bin/ubuntu-drivers
david@david-N7x0WU:~$ ubuntu-drivers list-oem

```

Someone else suggested doing a "df -h":
```
david@david-N7x0WU:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.8G     0  3.8G   0% /dev
tmpfs                        784M  2.0M  783M   1% /run
/dev/mapper/ubuntu--vg-root  456G  179G  254G  42% /
tmpfs                        3.9G   20K  3.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop1                   128K  128K     0 100% /snap/bare/5
/dev/loop2                   111M  111M     0 100% /snap/core/12725
/dev/loop0                   9.2M  9.2M     0 100% /snap/canonical-livepatch/119
/dev/loop3                   136M  136M     0 100% /snap/chromium/1912
/dev/loop4                   135M  135M     0 100% /snap/chromium/1899
/dev/loop6                    62M   62M     0 100% /snap/core20/1328
/dev/loop7                    56M   56M     0 100% /snap/core18/2253
/dev/loop5                   163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop9                   219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop8                   248M  248M     0 100% /snap/gnome-3-38-2004/87
/dev/loop10                  141M  141M     0 100% /snap/gnome-3-26-1604/102
/dev/loop12                   62M   62M     0 100% /snap/core20/1361
/dev/loop11                  9.2M  9.2M     0 100% /snap/canonical-livepatch/126
/dev/loop13                  141M  141M     0 100% /snap/gnome-3-26-1604/104
/dev/loop14                  2.7M  2.7M     0 100% /snap/gnome-system-monitor/174
/dev/loop15                  135M  135M     0 100% /snap/skype/200
/dev/loop16                  2.5M  2.5M     0 100% /snap/gnome-system-monitor/163
/dev/loop17                   55M   55M     0 100% /snap/snap-store/558
/dev/loop18                   56M   56M     0 100% /snap/core18/2284
/dev/loop22                   66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop19                   66M   66M     0 100% /snap/gtk-common-themes/1519
/dev/loop20                  323M  323M     0 100% /snap/wine-platform-6-stable/14
/dev/loop21                  617M  617M     0 100% /snap/libreoffice/242
/dev/loop24                  604M  604M     0 100% /snap/libreoffice/239
/dev/loop25                  165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop26                  250M  250M     0 100% /snap/zoom-client/167
/dev/loop23                  347M  347M     0 100% /snap/wine-platform-runtime/286
/dev/loop27                  347M  347M     0 100% /snap/wine-platform-runtime/285
/dev/loop28                   51M   51M     0 100% /snap/snap-store/547
/dev/loop29                  323M  323M     0 100% /snap/wine-platform-6-stable/8
/dev/loop31                  6.0M  6.0M     0 100% /snap/notepad-plus-plus/346
/dev/loop30                  6.0M  6.0M     0 100% /snap/notepad-plus-plus/343
/dev/loop32                  304M  304M     0 100% /snap/wine-platform-5-stable/16
/dev/loop34                  219M  219M     0 100% /snap/gnome-3-34-1804/77
/dev/loop35                  153M  153M     0 100% /snap/skype/203
/dev/loop33                  304M  304M     0 100% /snap/wine-platform-5-stable/18
/dev/loop36                  250M  250M     0 100% /snap/zoom-client/168
/dev/loop37                  249M  249M     0 100% /snap/gnome-3-38-2004/99
/dev/sda2                    705M  182M  472M  28% /boot
/dev/sda1                    511M  5.3M  506M   2% /boot/efi
tmpfs                        784M   36K  784M   1% /run/user/1000

```

Upgrade failed with following:
```
david@david-N7x0WU:~$ sudo apt install --install-recommends linux-generic-hwe-20.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-generic
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  linux-headers-5.13.0-30-generic linux-headers-generic-hwe-20.04
  linux-hwe-5.13-headers-5.13.0-30 linux-image-5.13.0-30-generic
  linux-image-generic-hwe-20.04 linux-modules-5.13.0-30-generic
  linux-modules-extra-5.13.0-30-generic
Suggested packages:
  fdutils linux-doc | linux-hwe-5.13-source-5.13.0 linux-hwe-5.13-tools
The following NEW packages will be installed:
  linux-generic-hwe-20.04 linux-headers-5.13.0-30-generic
  linux-headers-generic-hwe-20.04 linux-hwe-5.13-headers-5.13.0-30
  linux-image-5.13.0-30-generic linux-image-generic-hwe-20.04
  linux-modules-5.13.0-30-generic linux-modules-extra-5.13.0-30-generic
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 93.8 MB of archives.
After this operation, 508 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-5.13.0-30-generic amd64 5.13.0-30.33~20.04.1 [18.3 MB]
Get:2 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.13.0-30-generic amd64 5.13.0-30.33~20.04.1 [10.0 MB]
Get:3 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-extra-5.13.0-30-generic amd64 5.13.0-30.33~20.04.1 [51.1 MB]
Get:4 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-generic-hwe-20.04 amd64 5.13.0.30.33~20.04.17 [2,616 B]
Get:5 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-hwe-5.13-headers-5.13.0-30 all 5.13.0-30.33~20.04.1 [11.8 MB]
Get:6 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.13.0-30-generic amd64 5.13.0-30.33~20.04.1 [2,567 kB]
Get:7 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-generic-hwe-20.04 amd64 5.13.0.30.33~20.04.17 [2,508 B]
Get:8 http://ie.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-generic-hwe-20.04 amd64 5.13.0.30.33~20.04.17 [1,932 B]
Fetched 93.8 MB in 4s (22.9 MB/s)
Selecting previously unselected package linux-modules-5.13.0-30-generic.
(Reading database ... 191763 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-5.13.0-30-generic_5.13.0-30.33~20.04.1_a
md64.deb ...
Unpacking linux-modules-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
Selecting previously unselected package linux-image-5.13.0-30-generic.
Preparing to unpack .../1-linux-image-5.13.0-30-generic_5.13.0-30.33~20.04.1_amd
64.deb ...
Unpacking linux-image-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
Selecting previously unselected package linux-modules-extra-5.13.0-30-generic.
Preparing to unpack .../2-linux-modules-extra-5.13.0-30-generic_5.13.0-30.33~20.
04.1_amd64.deb ...
Unpacking linux-modules-extra-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-ck3jKi/2-linux-modules-extr
a-5.13.0-30-generic_5.13.0-30.33~20.04.1_amd64.deb (--unpack):
 unable to open '/lib/modules/5.13.0-30-generic/kernel/drivers/media/usb/dvb-usb
/dvb-usb-gp8psk.ko.dpkg-new': Operation not permitted
Selecting previously unselected package linux-image-generic-hwe-20.04.
Preparing to unpack .../3-linux-image-generic-hwe-20.04_5.13.0.30.33~20.04.17_am
d64.deb ...
Unpacking linux-image-generic-hwe-20.04 (5.13.0.30.33~20.04.17) ...
Selecting previously unselected package linux-hwe-5.13-headers-5.13.0-30.
Preparing to unpack .../4-linux-hwe-5.13-headers-5.13.0-30_5.13.0-30.33~20.04.1_
all.deb ...
Unpacking linux-hwe-5.13-headers-5.13.0-30 (5.13.0-30.33~20.04.1) ...
Selecting previously unselected package linux-headers-5.13.0-30-generic.
Preparing to unpack .../5-linux-headers-5.13.0-30-generic_5.13.0-30.33~20.04.1_a
md64.deb ...
Unpacking linux-headers-5.13.0-30-generic (5.13.0-30.33~20.04.1) ...
Selecting previously unselected package linux-headers-generic-hwe-20.04.
Preparing to unpack .../6-linux-headers-generic-hwe-20.04_5.13.0.30.33~20.04.17_
amd64.deb ...
Unpacking linux-headers-generic-hwe-20.04 (5.13.0.30.33~20.04.17) ...
Selecting previously unselected package linux-generic-hwe-20.04.
Preparing to unpack .../7-linux-generic-hwe-20.04_5.13.0.30.33~20.04.17_amd64.de
b ...
Unpacking linux-generic-hwe-20.04 (5.13.0.30.33~20.04.17) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-ck3jKi/2-linux-modules-extra-5.13.0-30-generic_5.13.0-30.
33~20.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by daithi_dearg on 2022-03-05
Not quite sure what resolved this and whether an update was released for this.

Last commands I ran were and I'm not sure did this have an impact:
```
1219  sudo dpkg --purge linux-headers-5.4.0-100 linux-headers-5.4.0-100-generic linux-image-5.4.0-100-generic inux-modules-5.4.0-100-generic
 1220  sudo apt-get update && sudo apt-get dist-upgrade
 1221  sudo apt --fix-broken install
 1222  dpkg --list 'linux-*' | grep -v '^rc\|^un'|grep ii
 1223  sudo dpkg --purge linux-modules-5.4.0-100-generic
 1224  sudo apt --fix-broken install
 1225  sudo apt-get update && sudo apt-get dist-upgrade
```

Had issues powering down and could see there was a 5.13 kernel that wasn't working and went back in to purge. Think command 1223.

Working now on the new kernel. Seems slower booting up but hopefully we're good now.

Also have remaining versions and wonder do I need to do a cleanup here for the in packages:
```
david@david-N7x0WU:~$ dpkg --list 'linux-*' | grep -v '^rc\|^un'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture Description
+++-=============================================-===========================-============-===============================================================
ii  linux-base                                    4.5ubuntu3.7                all          Linux image base package
ii  linux-firmware                                1.187.27                    all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                       5.13.0.30.33~20.04.17       amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.13.0-30-generic               5.13.0-30.33~20.04.1        amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-42                        5.4.0-42.46                 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04               5.13.0.30.33~20.04.17       amd64        Generic Linux kernel headers
ii  linux-hwe-5.13-headers-5.13.0-30              5.13.0-30.33~20.04.1        all          Header files related to Linux kernel version 5.13.0
ii  linux-image-5.13.0-30-generic                 5.13.0-30.33~20.04.1        amd64        Signed kernel image generic
ii  linux-image-5.4.0-42-generic                  5.4.0-42.46                 amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                 5.13.0.30.33~20.04.17       amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.4.0-100.113               amd64        Linux Kernel Headers for development
in  linux-modules-5.10.6-051006-generic           <none>                      amd64        (no description available)
in  linux-modules-5.10.6-051006-lowlatency        <none>                      amd64        (no description available)
in  linux-modules-5.11.0-051100-generic           <none>                      amd64        (no description available)
ii  linux-modules-5.13.0-30-generic               5.13.0-30.33~20.04.1        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-42-generic                5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-5.4.65-050465-generic           <none>                      amd64        (no description available)
in  linux-modules-5.6.14-050614-generic           <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-43-generic         <none>                      amd64        (no description available)
in  linux-modules-extra-4.15.0-45-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.13.0-30-generic         5.13.0-30.33~20.04.1        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-100-generic         <none>                      amd64        (no description available)
ii  linux-modules-extra-5.4.0-42-generic          5.4.0-42.46                 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
in  linux-modules-extra-5.4.0-45-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-51-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-52-generic          <none>                      amd64        (no description available)
in  linux-modules-extra-5.4.0-65-generic          <none>                      amd64        (no description available)

```

---

### Post by MAFoElffen on 2022-03-05
Which Kernel version is it booting on now? 
```

uname -a

```
On --fix-broken, did it install the missing dependencies and resolve everything?

---

### Post by daithi_dearg on 2022-03-11
```
david@david-N7x0WU:~$ uname -a
Linux david-N7x0WU 5.13.0-30-generic #33~20.04.1-Ubuntu SMP Mon Feb 7 14:25:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

Think I had to run this before it got upgraded:
sudo apt-get update && sudo apt-get dist-upgrade

Thanks for the assistance.

Can I mark this as resolved or does an admin do that?

---

### Post by tea for one on 2022-03-11
> **daithi_dearg said:**
> Can I mark this as resolved or does an admin do that?

The OP marks the thread as solved. Info here [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

