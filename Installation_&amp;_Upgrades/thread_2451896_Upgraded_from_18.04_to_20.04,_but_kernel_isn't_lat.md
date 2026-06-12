---
title: "Upgraded from 18.04 to 20.04, but kernel isn't latest"
date: 2020-10-12
forum: Installation &amp; Upgrades
---

### Post by wej2 on 2020-10-12
I recently upgraded my server from 18.04 to 20.04.1 LTS using apt-get upgrade + apt-get dist-upgrade + do-release-upgrade. Everything went fine as far as I can tell, but it is still running the 4.4 kernel. From what I've read online, it looks like I should be running the 5.4 kernel now? I am wondering why when I now run apt-get upgrade/dist-upgrade, it tells me there are no more packages, even though I'm not on the latest kernel.
```
root@proxy:/etc# apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [107 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [111 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [98.3 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [590 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [347 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [150 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu focal-updates/restricted i386 Packages [12.1 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [67.1 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [504 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [669 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu focal-updates/universe Translation-en [125 kB]
Fetched 2,780 kB in 2s (1,225 kB/s)
Reading package lists... Done
root@proxy:/etc# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
When I cat my /etc/os-release file, it looks like I am running 20.04.1:
```

root@proxy:/etc# cat os-release
NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
```
And yet uname -a reports the 4.4 kernel, which appears to belong to xenial:```
root@proxy:/etc# uname -a
Linux proxy.domain.tld 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
I've already rebooted to make sure it loaded the latest kernel. I checked my /boot/grub/grub.cfg file, and it definitely shows the 4.4 kernel image as the only one it will boot into.
```
--snipping irrelevant information--
 echo    'Loading Linux 4.4.0-59-generic ...'
 linux   /boot/vmlinuz-4.4.0-59-generic root=UUID=d451a895-2c74-4806-95ff-1f74b4d31551 ro net.ifnames=0 splash quiet $vt_handoff
 echo    'Loading initial ramdisk ...'
 initrd  /boot/initrd.img-4.4.0-59-generic

```
I do see that I have the 5.4 headers installed in the /usr/src/linux-headers-5.4.0-48 directory.

Can anyone explain what I am missing? Why didn't it update the kernel when the rest of the packages were updated?

Thanks

---

### Post by Bashing-om on 2020-10-12
wej2; Hello -

The package linux-generic installed ?

show us:
```

dpkg -l | grep linux-
ls -al /boot/

```

See what is, and what is set.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by wej2 on 2020-10-12
I just manually ran the install of the latest kernel by doing:
```
apt-get install linux-image-5.4.0-48-generic
```
And a reboot put me in the new kernel, which is good.

I am just curious why the last few release upgrades did not actually upgrade the kernel, but did install the headers. Is that a normal thing for it to do? I'd expect both the image and the headers to be installed together. Should I expect to have to manually update the kernel package on the system each time I do a release upgrade? I am following the LTS release cycle for this server. I started in 2017 with the 16.04 release, which explains why I had the xenial kernel on my system. I never checked to verify that my kernel upgraded when I went to 18.04 a couple of years ago, so I didn't even realize it was still running a kernel from 2016's release cycle. In April 2022, am I going to have to manually install whatever kernel is the latest at that time? Or should do-release-upgrade install the latest kernel? I'm so confused, as apt HAS been installing newer kernels in the same line for security patches, it just didn't upgrade major versions in all that time.

And to answer your specific question, it did not show the linux-image or linux-modules for the 5.4 kernel, it only had the linux-headers packages before I did a manual install of the latest 5.4 kernel.
```

root@proxy:~# dpkg -l | grep linux-
ii  binutils-x86-64-linux-gnu          2.34-6ubuntu1                     amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                         4.5ubuntu3.1                      all          Linux image base package
ii  linux-firmware                     1.187.3                           all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-59             4.4.0-59.80                       all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic     4.4.0-59.80                       amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-48             5.4.0-48.52                       all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-48-generic     5.4.0-48.52                       amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic              5.4.0.48.51                       amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-59-generic       4.4.0-59.80                       amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic 4.4.0-59.80                       amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64               5.4.0-48.52                       amd64        Linux Kernel Headers for development
ii  linux-modules-4.4.0-59-generic     5.4.0-48.52                       amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP

```

---

### Post by Bashing-om on 2020-10-12
wej2; Yup -

And --- ya still need the linux-generic package.
> 
ii  linux-base                           4.5ubuntu3.1                        all          Linux image base package
ii  linux-firmware                       1.187.3                             all          Firmware for Linux kernel drivers
ii[color=red] linux-generic[/color]                        5.4.0.48.51                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.4.0-47               5.4.0-47.51                         all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-47-generic       5.4.0-47.51                         amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-48               5.4.0-48.52                         all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-48-generic       5.4.0-48.52                         amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                5.4.0.48.51                         amd64        Generic Linux kernel headers
ii  linux-image-5.4.0-47-generic         5.4.0-47.51                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-48-generic         5.4.0-48.52                         amd64        Signed kernel image generic
ii  linux-image-generic                  5.4.0.48.51                         amd64        Generic Linux kernel image
ii  linux-modules-5.4.0-47-generic       5.4.0-47.51                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-48-generic       5.4.0-48.52                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-47-generic 5.4.0-47.51                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-48-generic 5.4.0-48.52                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-sound-base                     1.0.25+dfsg-0ubuntu5                all          base package for ALSA and OSS sound systems
sysop@2004x-c:~$ 


see:
```

apt show linux-generic

```
to get an idea of what is not going on here.

[INDENT]all in the process
[/INDENT]

---

### Post by garvinrick4 on 2020-10-13
#This is link to all kernels already built in .deb that Ubuntu uses short for debian.
[URL="https://kernel.ubuntu.com/~kernel-ppa/mainline/"]https://kernel.ubuntu.com/~kernel-ppa/mainline/
[/URL]
#scroll down to kernel wanted (latest on bottom v5.9/)
#select and open and save to Downloads or where you choose I will use Downloads i already chose them for you below
#notice the four you need to build kernel are amd64. You can choose low latency if that is what you are using instead of full build of Ubuntu
#both versions use the the all.deb 
# Will always use the headers for amd64, the all.deb, the image and the  modules if using Ubuntu light version choose the lowlatency and the  all.deb
#now select each one of these at a time and download to Downloads or use the links below for first time if you choose to do so. 
##edit these are for full Ubuntu not LTS again use the 3 low latency and the all.deb four packages for LTS install. 

[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-headers-5.9.0-050900-generic_5.9.0-050900.202010112230_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-headers-5.9.0-050900-generic_5.9.0-050900.202010112230_amd64.deb)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-headers-5.9.0-050900_5.9.0-050900.202010112230_all.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-headers-5.9.0-050900_5.9.0-050900.202010112230_all.deb)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-image-unsigned-5.9.0-050900-generic_5.9.0-050900.202010112230_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-image-unsigned-5.9.0-050900-generic_5.9.0-050900.202010112230_amd64.deb)
[URL="https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-modules-5.9.0-050900-generic_5.9.0-050900.202010112230_amd64.deb"]https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.9/amd64/linux-modules-5.9.0-050900-generic_5.9.0-050900.202010112230_amd64.deb
[/URL]
#open a terminal
> cd Downloads
> ls
#Make sure only 4 .deb packages in Downloads if more move them to other location for time being so as to install all .deb packages at one time with next line of code
   or use Desktop for instance as location of and just cd Desktop instead of cd Downloads if Downloads full of .deb files. Can install one at a time but pain in the rear.
> sudo dpkg -i *.deb
#That is a lower case I not an lower case L
#Done, now reboot
> sudo shutdown -r now

## save link of all kernels so as to install any kernel you wish in future always keep old one so can boot with it if any problems with a new kernel.
# Will always use the headers for amd64, the all.deb, the image and the modules if using Ubuntu light version choose the lowlatency and the all.deb

## Hope this helps those who are new to Ubuntu and command line this will work with all packages already built in into .deb to install

---

### Post by deadflowr on 2020-10-13
As Bashing-om sort of pointed to, the OP doesn't have the linux-generic, nor linux-image/[s]headers-generic[/s], packages.
Those are needed in order to get the updated kernels for the current releases.
Just install linux-generic and it will pull in the linux-image and linux-headers generic packages,
which in turn will install the latest stable kernel for the release in question.

Edit: scratch that, they do have the linux-headers-generic package installed.
But they still seem to be missing the linux-image-generic package which is the actual kernel package required.

---

### Post by garvinrick4 on 2020-10-13
Hi Deadflowr was just giving the 4 packages needed to install a new kernel in case others needed to understand and install in future using
the link provided should have stated that at beginning.

---

### Post by deadflowr on 2020-10-13
> **garvinrick4 said:**
> Hi Deadflowr was just giving the 4 packages needed to install a new kernel in case others needed to understand and install in future using
the link provided should have stated that at beginning.

I guess if they want to run mainline kernels they can do that.
I'm just saying they would need the generic packages if they want to run the current kernels for the particular release they are on.
Either that or they can manually install the updated kernels whenever it is needed.
Easier to just install the generic packages and let the system automatically bring in the new kernels when available.

Edit: It's nice to have options

---

