---
title: "Kernel upgrade switched from generic to oracle"
date: 2022-03-22
forum: Installation &amp; Upgrades
---

### Post by dag-ybeweb on 2022-03-22
Hi,

Yesterday my xubuntu started an upgrade of the kernel and switching from the regular generic 64-bit kernel it has always used it suddenly decided to install "linux-image-5.13.0-1021-oracle". My dpkg --list contains a bunch of generic images and one oracle version.
Is there an explanation for this? Perhaps a fix?
And in any case, how do I remove this strange entry? I've tried removing the package, but it then demands to install some unsigned oracle kernel version.

I can boot into a working environment by selecting a different entry in grub, but clearly something isn't as it should be.

This is a completely new problem for me and any help would be fantastic.

-ED

---

### Post by dag-ybeweb on 2022-03-22
So can anyone tell me why that oracle entry suddenly appears there and why it's the first option for GRUB?

rc  linux-image-5.11.0-16-generic               5.11.0-16.17                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-22-generic               5.11.0-22.23                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-25-generic               5.11.0-25.27                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-31-generic               5.11.0-31.33                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-34-generic               5.11.0-34.36                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-36-generic               5.11.0-36.40                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-37-generic               5.11.0-37.41                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-38-generic               5.11.0-38.42                        amd64        Signed kernel image generic
[COLOR=#ff0000]ii  linux-image-5.13.0-1021-oracle              5.13.0-1021.26                      amd64        Signed kernel image oracle[/COLOR]
rc  linux-image-5.13.0-20-generic               5.13.0-20.20                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-21-generic               5.13.0-21.21                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-22-generic               5.13.0-22.22                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-23-generic               5.13.0-23.23                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-25-generic               5.13.0-25.26                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-27-generic               5.13.0-27.29                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-28-generic               5.13.0-28.31                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-30-generic               5.13.0-30.33                        amd64        Signed kernel image generic
ii  linux-image-5.13.0-35-generic               5.13.0-35.40                        amd64        Signed kernel image generic
ii  linux-image-5.13.0-37-generic               5.13.0-37.42                        amd64        Signed kernel image generic
ii  linux-image-generic                         5.13.0.37.46                        amd64        Generic Linux kernel image

No changes has been made to the computer or settings. It was just a normal day with a normal kernel update and then this happened.

---

### Post by deadflowr on 2022-03-22
> And in any case, how do I remove this strange entry? I've tried removing the package, but it then demands to install some unsigned oracle kernel version.
Your output is missing packages.
it only listed the specific kernel images but not the meta-packages
Show what
```
dpkg -l | grep linux-image 
```
shows

From the output I would guess you have at least the linux-image-oracle meta-package.
And maybe the linux-image-generic-hwe-20.04 meta-package.

*Note that I use the term meta-package loosely here, as I think the kernel packages may use a different term for what they are.

---

### Post by dag-ybeweb on 2022-03-22
No, this was it in it's entirety and the oracle one sticks out like a sore thumb. I have never had any oracle version in my grub or anywhere else in this computer. And now it demands to boot with it.

```
 ed@EDcom:~$ **dpkg -l | grep linux-image**
rc  linux-image-5.11.0-16-generic               5.11.0-16.17                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-22-generic               5.11.0-22.23                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-25-generic               5.11.0-25.27                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-31-generic               5.11.0-31.33                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-34-generic               5.11.0-34.36                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-36-generic               5.11.0-36.40                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-37-generic               5.11.0-37.41                        amd64        Signed kernel image generic
rc  linux-image-5.11.0-38-generic               5.11.0-38.42                        amd64        Signed kernel image generic
ii  linux-image-5.13.0-1021-oracle              5.13.0-1021.26                      amd64        Signed kernel image oracle
rc  linux-image-5.13.0-20-generic               5.13.0-20.20                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-21-generic               5.13.0-21.21                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-22-generic               5.13.0-22.22                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-23-generic               5.13.0-23.23                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-25-generic               5.13.0-25.26                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-27-generic               5.13.0-27.29                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-28-generic               5.13.0-28.31                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-30-generic               5.13.0-30.33                        amd64        Signed kernel image generic
rc  linux-image-5.13.0-35-generic               5.13.0-35.40                        amd64        Signed kernel image generic
ii  linux-image-5.13.0-37-generic               5.13.0-37.42                        amd64        Signed kernel image generic
ii  linux-image-generic                         5.13.0.37.46                        amd64        Generic Linux kernel image
ed@EDcom:~$
```

---

### Post by dag-ybeweb on 2022-03-22
So my guess is that I can "simply" remove it, but when I try that it demands to install another version like so:

```

ed@EDcom:~$ **sudo apt-get remove linux-image-5.13.0-1021-oracle**
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfwupdplugin1 linux-headers-5.13.0-35 linux-headers-5.13.0-35-generic linux-image-5.13.0-35-generic linux-modules-5.13.0-35-generic
  linux-modules-extra-5.13.0-35-generic
Use 'sudo apt autoremove' to remove them.
[B]The following additional packages will be installed:
  linux-image-unsigned-5.13.0-1021-oracle[/B]
Suggested packages:
  fdutils linux-oracle-doc-5.13.0 | linux-oracle-source-5.13.0 linux-oracle-tools linux-headers-5.13.0-1021-oracle
The following packages will be REMOVED:
  linux-image-5.13.0-1021-oracle
The following NEW packages will be installed:
  linux-image-unsigned-5.13.0-1021-oracle
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 10,9 MB of archives.
After this operation, 1&#8239;011 kB of additional disk space will be used.
Do you want to continue? [Y/n] n

```
As you can see from the suggested packages I have nothing of what would be normal to have should oracle have been what was normally in use. It's like the update system glitched and did this and forgot about that it did it.

---

### Post by ajgreeny on 2022-03-22
What output do you see from command 
**dpkg -l linux-generic***

---

### Post by dag-ybeweb on 2022-03-22
Actually, I think I found the problem which for some reason didn't enter my mind that could be an issue.
Yesterday there was an nVidia update and that seems to have added this to my system.

I tried to purge the unwanted kernel with ```
dpkg --purge linux-image-5.13.0-1021-oracle
```instead of using apt and it then complained about this:```
dpkg: dependency problems prevent removal of linux-image-5.13.0-1021-oracle:
 **linux-signatures-nvidia-5.13.0-1021-oracle** depends on linux-image-5.13.0-1021-oracle | linux-image-unsigned-5.13.0-1021-oracle; however:
  Package linux-image-5.13.0-1021-oracle is to be removed.
  Package linux-image-unsigned-5.13.0-1021-oracle is not installed.
 linux-modules-5.13.0-1021-oracle depends on linux-image-5.13.0-1021-oracle | linux-image-unsigned-5.13.0-1021-oracle; however:
  Package linux-image-5.13.0-1021-oracle is to be removed.
  Package linux-image-unsigned-5.13.0-1021-oracle is not installed.
```
So I reverted the nVidia driver to an earlier version and purged the kernel and dependencies with dpkg, and now it's seems to be gone.

I still must say that I have never seen kernel issues caused by gfx driver. The offending driver seems to be nvidia-driver-510 while the one I reverted to is nvidia-driver-470.
It was a little baffling that this in any way could impact the choice of kernel, and how it could add it without telling me about it.

Thank you for trying to dig into the matter for me as I am more than a little inexperienced when it comes to working with kernels. Still, I haven't had the opportunity to test proper reboots yet so ... fingers crossed.

---

### Post by ajgreeny on 2022-03-24
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by ActionParsnip on 2022-03-25
You can clean up your output with:
```

sudo dpkg -P `dpkg -l | grep linux-image-5 | grep ^rc | awk {'print $2'}`

```

The lines starting with "rc" will then be cleaned up for you

---

### Post by gholst on 2023-01-19
Hello,
First, thank you! You save my day! :)

I know is Closed and it can be an old discussion, but I was with the same problem and found an easier or quicker solution:
   [FONT=monospace][COLOR=#000000]sudo apt purge linux-image-5.19.0-1015-oracle lin[/COLOR]ux-modules-5.19.0-1015-oracle linux-objects-nvidia-525-5.19.0-1015-oracle linux-signatures-nvidia-5.19.0-1015-oracle

Remove the linux-image and also the nvidia that links to the "oracle" flavour.

Regards
[/FONT]

---

### Post by ActionParsnip on 2023-01-19
Can this please be marked as solved if there is no more issue...

---

