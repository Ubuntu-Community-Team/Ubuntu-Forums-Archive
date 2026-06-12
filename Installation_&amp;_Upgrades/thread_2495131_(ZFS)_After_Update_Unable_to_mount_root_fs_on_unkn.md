---
title: "(ZFS) After Update: Unable to mount root fs on unknown block"
date: 2024-02-07
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2024-02-07
UbuntuStudio v20.04 ... latest upgrade, and on Reboot got the message.

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) Not tainted 5.15.0-94-lowlatency

Tried - boot with Live CD and ran ;
```

sudo dpkg --configure -a

```

Then it did Boot. Ran Update and Upgrade, and Reboot. Same Error!
Any suggestions? Running with SSD and 32 GB Ram and 8 core CPU.

Thanks!

---

### Post by #&amp;thj^% on 2024-02-07
Please see this the post by Tomeu Roig: [https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)

Follow all the steps shown

---

### Post by Rick St. George on 2024-02-07
That's where I got my info. Moreover, there are 12 answers. I chose to boot to LiveCD and (see my first post). Also, as posted on that page;

> 
It's now 11 years later, and 22.04 fails to automatically fix this problem and/or give decent clues of what steps to take !! – 
Rick James May 16, 2022


In addition, Boot Repair may not fix the problem if the problem lies in the Fix being to upgrade to Grub to 2.12!

So, I guess the real question is ... How do Upgrade Grub if I can't boot the computer???

---

### Post by guiverc on 2024-02-07
Ubuntu Studio 20.04 LTS is *end of life* - [https://ubuntustudio.org/2023/04/ubuntu-studio-20-04-has-reached-end-of-life/](https://ubuntustudio.org/2023/04/ubuntu-studio-20-04-has-reached-end-of-life/)

Have you performed file-system checks from the *live* media, and don't forget commands executed (eg. `sudo dpkg --configure -a`) in a *live* environment will impact the *live* environment itself, and not your installed system (*unless you've chroot'd across to the installed system*).

I would still explore your system from the *live* disk, starting with file-system checks, then quick exploration of file-system table (/etc/fstab on the installed system & NOT the *live* system you're running, thus don't forget locations will differ) etc.  If a file-system check detected & fixed any issue; I'd expect normal boot on next try.  Also note the command to perform file-system check varies on file-system involved (ie. `fsck` will just exit for many as per documentation when you attempt to run it on a file-system its not intended to handle; use the appropriate command for your *unstated* file-system(s))

---

### Post by Rick St. George on 2024-02-07
Did the Intel Microcode corrupt Grub? because I'm running on a AMD FX-8320 Vishera, and have Grub 2.04.

According to Symantec .... No Broken Files. And End of Life ... but, 22.04 still has problems - been watching posts.

---

### Post by Rick St. George on 2024-02-07
Ran the following;

```

$ sudo fdisk -l
Disk /dev/sda: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 840 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf8d469ad

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048   1050623   1048576   512M  b W95 FAT32
/dev/sda2       1052670 488396799 487344130 232.4G  5 Extended
/dev/sda5       1052672 488396799 487344128 232.4G 83 Linux


$ sudo dpkg --configure -a

$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-94-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-94-lowlatency
Found linux image: /boot/vmlinuz-5.15.0-94-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-94-lowlatency
Found linux image: /boot/vmlinuz-5.15.0-92-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-92-lowlatency
Found linux image: /boot/vmlinuz-5.15.0-88-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-88-lowlatency
Found linux image: /boot/vmlinuz-5.11.0-27-lowlatency
Found initrd image: /boot/initrd.img-5.11.0-27-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```


Contents of init-select.cfg

```

# Work around a bug in the obsolete init-select package which broke
# grub-mkconfig when init-select was removed but not purged.  This file does
# nothing and will be removed in a later release.
#
# See:
#   https://bugs.debian.org/858528
#   https://bugs.debian.org/863801

```



Contents of Grub:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Any suggestions, because what is in Grub isn't working?!?!?

---

### Post by #&amp;thj^% on 2024-02-07
> **Rick St. George said:**
> Did the Intel Microcode corrupt Grub? because I'm running on a AMD FX-8320 Vishera, and have Grub 2.04.

According to Symantec .... No Broken Files. And End of Life ... but, 22.04 still has problems - been watching posts.

Not here, I thought we have already covered this in previous post.
```
 apt policy intel-microcode
intel-microcode:
  Installed: 3.20231114.1
  Candidate: 3.20231114.1
  Version table:
 *** 3.20231114.1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> apt policy amd64-microcode
amd64-microcode:
  Installed: 3.20231019.1ubuntu1
  Candidate: 3.20231019.1ubuntu1
  Version table:
 *** 3.20231019.1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```
> **Rick St. George said:**
> but, 22.04 still has problems - been watching posts.
What kind of problems are you referring to, If you list those, or better yet search what you think impacts you...then maybe we can debunk or find a work-around. :)

Right now your at a semi-vulnerable state. Unless you have ESM in place.
```
ubuntu-security-status
```

---

### Post by Rick St. George on 2024-02-08
What is ESM? Are you referring to Enterprise Service Management?  No I do not. I'm a lone survivor.

And after Booting Computer this morning ... same problem. 
Did my SSD drive go bad???

---

### Post by Rick St. George on 2024-02-08
Got computer up by going back down Grub 3rd previous version (recovery mode). 

lsblk shows sda1 (mount pt) as mounted /mnt/A00D-96E4
blkid shows sda5 UUID (and ID No.)

SDA5 is extended partition on SSD drive.  Not sure what to do next?

---

### Post by #&amp;thj^% on 2024-02-08
> **Rick St. George said:**
> What is ESM? Are you referring to Enterprise Service Management?  No I do not. I'm a lone survivor.


Expanded Security Maintenance (ESM)
Extra security patching for Ubuntu LTS
[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

---

### Post by Rick St. George on 2024-02-08
FYI:

```

$ ubuntu-security-status

This command has been replaced with 'pro security-status'.
3121 packages installed:
     1545 packages from Ubuntu Main/Restricted repository
     1304 packages from Ubuntu Universe/Multiverse repository
     2 packages from third parties
     270 packages no longer available for download

To get more information about the packages, run
    pro security-status --help
for a list of available options.

This machine is receiving security patching for Ubuntu Main/Restricted
repository until 2025.
This machine is NOT attached to an Ubuntu Pro subscription.

Ubuntu Pro with 'esm-infra' enabled provides security updates for
Main/Restricted packages until 2030.

Ubuntu Pro with 'esm-apps' enabled provides security updates for
Universe/Multiverse packages until 2030. There are 55 pending security updates.

Try Ubuntu Pro with a free personal subscription on up to 5 machines.
Learn more at https://ubuntu.com/pro

```

---

### Post by #&amp;thj^% on 2024-02-08
I'm not sure that's for my information, but more so yours. :)
Also I'm sure you noticed this:
```
Ubuntu Pro with 'esm-apps' enabled provides security updates for
Universe/Multiverse packages until 2030. There are 55 pending security updates.
``` 

Any who I can't help with your current problem. Maybe someone else can add some aid.

---

### Post by Rick St. George on 2024-02-08
FYI: 

As the msg from above command states, "v20.04 Good till 2025".

If the fix is in Grub v2.12, then how do I install it, OR how can I update Grub instructions to Boot Up correctly???

---

### Post by #&amp;thj^% on 2024-02-08
> 

    For clarity: This is not a roadblock being put on an existing support stream, it is a new support stream. Previously Ubuntu did not provide security patches for "Universe" repo packages (instead relying on upstream patches to happen when they happen). The Ubuntu security team are now producing in-house security patches for these packages, but only where Pro has been opted into (which is free for personal use).

    If you do not want to opt in to Pro you still have the same level of support you had before (and the same level of support that you have with 99% of other distros).

What your failing to see is this " There are 55 pending security updates."

---

### Post by Rick St. George on 2024-02-08
Fail to see how this will fix GRUB 2.04 on my computer, but will try anyway.

Attempting ... but installng SNAP, which I previously went out of my way to REMOVE from my computer.

Will Update ....

---

### Post by #&amp;thj^% on 2024-02-08
Most likely won't fix grub.

I keep getting what you want me to hear but nothing shown to help you.
Try this:
```
sudo grub-install /dev/sda
```
Then run "update-grub"

---

### Post by Rick St. George on 2024-02-09
Upon Startup this morning, same problem, but hitting Enter after "Press any key to continue" it booted up!
Afterwards, a Popup - System program problem detected, Do you want to report the problem now?"  Yes

Ran Fallen's suggestion;

```

~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.

~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-94-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-94-lowlatency
Found linux image: /boot/vmlinuz-5.15.0-94-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-94-lowlatency
Found linux image: /boot/vmlinuz-5.15.0-88-lowlatency
Found initrd image: /boot/initrd.img-5.15.0-88-lowlatency
Found linux image: /boot/vmlinuz-5.11.0-27-lowlatency
Found initrd image: /boot/initrd.img-5.11.0-27-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

Will ReBoot and report back!  .... Same problem, but again hitting Enter upon "Press any key to cont." and it boots up. 
However, this is what it did before, after the last Update/Upgrade  and it didn't work any more. Maybe this is the best I can hope for? 
Feel there must be something I should add to Grub???

FYI - Looking at Disks shows 91GB Free on 250 GB SSD.

---

### Post by Rick St. George on 2024-02-09
I wonder if these instructions [https://www.gnu.org/software/grub/manual/grub/html_node/Environment-block.html]("https://www.gnu.org/software/grub/manual/grub/html_node/Environment-block.html")  can help in setting or resetting the Environment Variables?  Note the CAUTION on "skip-sig" on this page [https://www.gnu.org/software/grub/manual/grub/html_node/load_005fenv.html#load_005fenv]("https://www.gnu.org/software/grub/manual/grub/html_node/load_005fenv.html#load_005fenv"). Followed the links on that page but too complicated for me!

Any suggestions?  
Thanks!

---

### Post by #&amp;thj^% on 2024-02-09
When's the last time you ran "autoremove"?
```
sudo apt autoremove
```
and please show this:
```
sudo du /boot -h -s

```

---

### Post by Rick St. George on 2024-02-09
> **1fallen said:**
> When's the last time you ran "autoremove"?
```
sudo apt autoremove
```


After last upgrade (last week).

[QUOTE}
and please show this:
```
sudo du /boot -h -s

```[/QUOTE]

Result:

```

$ sudo du /boot -h -s
258M	/boot

```

---

### Post by #&amp;thj^% on 2024-02-09
Rick can you now run the system-info script found in my signature. but run it with "--details" added to the end of the script.
Post the url back here so we see it. It will save time in asking for a bunch more questions.
The script is just this, copy and paste:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details
```

---

### Post by Rick St. George on 2024-02-09
Here you go ...

```

~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
> chmod +x system-info && \ ./system-info --details
--2024-02-09 12:42:25--  https://github.com/UbuntuForums/system-info/raw/main/system-info
Resolving github.com (github.com)... 140.82.114.4
Connecting to github.com (github.com)|140.82.114.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info [following]
--2024-02-09 12:42:25--  https://raw.githubusercontent.com/UbuntuForums/system-info/main/system-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.110.133, 185.199.111.133, 185.199.108.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 87660 (86K) [text/plain]
Saving to: &#8216;system-info&#8217;

system-info                  100%[===========================================>]  85.61K  --.-KB/s    in 0.02s   

Last-modified header missing -- time-stamps turned off.
2024-02-09 12:42:26 (3.91 MB/s) - &#8216;system-info&#8217; saved [87660/87660]

bash:  ./system-info: No such file or directory


```

Don't know what it is, but Hope this helps!

---

### Post by #&amp;thj^% on 2024-02-09
LOL That's not it, you need to let it run, then after it completes it will give you a URL from paste.bin
Just follow the prompts it gives you.
```
+x system-info && ./system-info --details
--2024-02-09 12:03:17--  https://github.com/UbuntuForums/system-info/raw/main/system-info
Loaded CA certificate '/etc/ssl/certs/ca-certificates.crt'
Resolving github.com (github.com)... 140.82.113.4
Connecting to github.com (github.com)|140.82.113.4|:443... connected.
This script needs some parts of it to run with elevated permissions.

Please enter your password for that to happen.
[sudo] password for me: 

```
To' be clear don't paste that content here but just the URL

I'm going to be away for a couple hours just a heads up.

EDIT: This is what it dose: View at: [https://termbin.com/o8ft](https://termbin.com/o8ft)

---

### Post by Rick St. George on 2024-02-09
Posted to PasteBin at  [https://paste.ubuntu.com/p/tc8y9x5YdW/]("https://paste.ubuntu.com/p/tc8y9x5YdW/")
I too will be out for several hours. Will check back later today ... Thanks!

---

### Post by #&amp;thj^% on 2024-02-09
This is what your booted to currently
```

linux-headers-5.11.0-27-lowlatency
linux-hwe-5.11-headers-5.11.0-27
linux-image-5.11.0-27-lowlatency
linux-modules-5.11.0-27-lowlatency
```
In previous posts you show this kernel "5.15.0-94-lowlatency" as installed.
will you paste this back, it's a dry run so nothing will take place until you remove the safety flag
```
sudo apt-get install linux-buildinfo-5.15.0-94-lowlatency -s
```

I now know why you don't want to upgrade to 22.04. :)

---

### Post by #&amp;thj^% on 2024-02-09
Rick, You seem to have a kernel from proposed ie:
```
linux-image-5.15.0-94-lowlatency | 5.15.0-94.104~20.04.1 |** focal-proposed** | amd64, arm64
 linux-image-5.15.0-94-lowlatency | 5.15.0-94.104         | jammy-proposed | amd64, arm64

```
And I doubt it's installed fully. Nothing else is jumping out at me.
Include this as well please
```
dpkg --list | grep linux-image

```
And this:
```
ls -l /lib/modules/

```

---

### Post by #&amp;thj^% on 2024-02-10
Well I stand corrected, I guess they pushed that kernel through now. It's been years since I've used 20.4, so i installed in a KVM to test some unrelated to this thread.
rmadison still shows as proposed:
```
rmadison linux-image-5.15.0-94-lowlatency
 linux-image-5.15.0-94-lowlatency | 5.15.0-94.104~20.04.1 | focal-proposed | amd64, arm64
 linux-image-5.15.0-94-lowlatency | 5.15.0-94.104         | jammy-proposed | amd64, arm64

```
But I'm now booted to:
```
 uname -a
Linux me-Standard-PC-Q35-ICH9-2009 5.15.0-94-lowlatency #104~20.04.1-Ubuntu SMP PREEMPT Wed Jan 17 16:34:00 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

```
fully updated, and I'm no help on your grub issue....mine boots just fine:
```
 pro security-status
1789 packages installed:
     1529 packages from Ubuntu Main/Restricted repository
     260 packages from Ubuntu Universe/Multiverse repository

To get more information about the packages, run
    pro security-status --help
for a list of available options.

This machine is attached to an Ubuntu Pro subscription.

Main/Restricted packages are receiving security updates from
Ubuntu Pro with 'esm-infra' enabled until 2030.

Universe/Multiverse packages are receiving security updates from
Ubuntu Pro with 'esm-apps' enabled until 2030. You have received 18 security
updates.

```
All modules are present:
```
 ls -l /lib/modules/
total 12
drwxr-xr-x 5 root root 4096 Mar 16  2023 5.15.0-67-generic
drwxr-xr-x 5 root root 4096 Feb 10 09:25 5.15.0-94-generic
drwxr-xr-x 5 root root 4096 Feb 10 09:43 5.15.0-94-lowlatency

```
I'm still curios about what I've ask to see though.
My grub is nothing special:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


```

---

### Post by Rick St. George on 2024-02-10
1fallen: At your Request;

```

~$ sudo apt-get install linux-buildinfo-5.15.0-94-lowlatency -s
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-buildinfo-5.15.0-94-lowlatency
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Inst linux-buildinfo-5.15.0-94-lowlatency (5.15.0-94.104~20.04.1 Ubuntu:20.04/focal-security, Ubuntu:20.04/focal-updates [amd64])
Conf linux-buildinfo-5.15.0-94-lowlatency (5.15.0-94.104~20.04.1 Ubuntu:20.04/focal-security, Ubuntu:20.04/focal-updates [amd64])

~$ dpkg --list | grep linux-image
rc  linux-image-5.11.0-25-lowlatency              5.11.0-25.27~20.04.1                        amd64        Signed kernel image lowlatency
ii  linux-image-5.11.0-27-lowlatency              5.11.0-27.29~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-34-lowlatency              5.11.0-34.36~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-36-lowlatency              5.11.0-36.40~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-37-lowlatency              5.11.0-37.41~20.04.2                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-38-lowlatency              5.11.0-38.42~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-40-lowlatency              5.11.0-40.44~20.04.2                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-41-lowlatency              5.11.0-41.45~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-43-lowlatency              5.11.0-43.47~20.04.2                        amd64        Signed kernel image lowlatency
rc  linux-image-5.11.0-46-lowlatency              5.11.0-46.51~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-25-lowlatency              5.13.0-25.26~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-27-lowlatency              5.13.0-27.29~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-28-lowlatency              5.13.0-28.31~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-30-lowlatency              5.13.0-30.33~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-35-lowlatency              5.13.0-35.40~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-37-lowlatency              5.13.0-37.42~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-39-lowlatency              5.13.0-39.44~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-40-lowlatency              5.13.0-40.45~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-41-lowlatency              5.13.0-41.46~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-51-lowlatency              5.13.0-51.58~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.13.0-52-lowlatency              5.13.0-52.59~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-42-lowlatency              5.15.0-42.45~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-43-lowlatency              5.15.0-43.46~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-46-lowlatency              5.15.0-46.49~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-48-lowlatency              5.15.0-48.54~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-50-lowlatency              5.15.0-50.56~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-52-lowlatency              5.15.0-52.58~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-53-lowlatency              5.15.0-53.59~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-56-lowlatency              5.15.0-56.62~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-60-lowlatency              5.15.0-60.66~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-67-lowlatency              5.15.0-67.74~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-69-lowlatency              5.15.0-69.76~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-70-lowlatency              5.15.0-70.77~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-71-lowlatency              5.15.0-71.78~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-72-lowlatency              5.15.0-72.79~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-73-lowlatency              5.15.0-73.80~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-75-lowlatency              5.15.0-75.82~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-76-lowlatency              5.15.0-76.83~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-78-lowlatency              5.15.0-78.85~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-79-lowlatency              5.15.0-79.88~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-82-lowlatency              5.15.0-82.91~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-83-lowlatency              5.15.0-83.92~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-84-lowlatency              5.15.0-84.93~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-86-lowlatency              5.15.0-86.95~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-87-lowlatency              5.15.0-87.96~20.04.1                        amd64        Signed kernel image lowlatency
ii  linux-image-5.15.0-88-lowlatency              5.15.0-88.98~20.04.1                        amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-92-lowlatency              5.15.0-92.102~20.04.1                       amd64        Signed kernel image lowlatency
ii  linux-image-5.15.0-94-lowlatency              5.15.0-94.104~20.04.1                       amd64        Signed kernel image lowlatency
rc  linux-image-5.4.0-64-generic                  5.4.0-64.72                                 amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-lowlatency               5.8.0-43.49~20.04.1                         amd64        Signed kernel image lowlatency
rc  linux-image-5.8.0-63-generic                  5.8.0-63.71~20.04.1                         amd64        Signed kernel image generic
rc  linux-image-5.8.0-63-lowlatency               5.8.0-63.71~20.04.1                         amd64        Signed kernel image lowlatency
rc  linux-image-5.8.0-64-lowlatency               5.8.0-64.72                                 amd64        Signed kernel image lowlatency
ii  linux-image-lowlatency-hwe-20.04              5.15.0.94.104~20.04.47                      amd64        lowlatency Linux kernel image

:~$ ls -l /lib/modules/
total 216
drwxr-xr-x 2 root root 4096 Sep 15  2021 5.11.0-25-lowlatency
drwxr-xr-x 5 root root 4096 Apr 21  2022 5.11.0-27-lowlatency
drwxr-xr-x 2 root root 4096 Oct  4  2021 5.11.0-34-lowlatency
drwxr-xr-x 2 root root 4096 Oct 22  2021 5.11.0-36-lowlatency
drwxr-xr-x 2 root root 4096 Nov 11  2021 5.11.0-37-lowlatency
drwxr-xr-x 2 root root 4096 Dec  9  2021 5.11.0-38-lowlatency
drwxr-xr-x 2 root root 4096 Dec 22  2021 5.11.0-40-lowlatency
drwxr-xr-x 2 root root 4096 Jan 10  2022 5.11.0-41-lowlatency
drwxr-xr-x 2 root root 4096 Jan 26  2022 5.11.0-43-lowlatency
drwxr-xr-x 2 root root 4096 Jan 26  2022 5.11.0-46-lowlatency
drwxr-xr-x 2 root root 4096 Feb  8  2022 5.13.0-25-lowlatency
drwxr-xr-x 2 root root 4096 Feb 20  2022 5.13.0-27-lowlatency
drwxr-xr-x 2 root root 4096 Mar 15  2022 5.13.0-28-lowlatency
drwxr-xr-x 2 root root 4096 Mar 23  2022 5.13.0-30-lowlatency
drwxr-xr-x 2 root root 4096 Apr  2  2022 5.13.0-35-lowlatency
drwxr-xr-x 2 root root 4096 Apr 21  2022 5.13.0-37-lowlatency
drwxr-xr-x 2 root root 4096 May 11  2022 5.13.0-39-lowlatency
drwxr-xr-x 2 root root 4096 Jun 16  2022 5.13.0-40-lowlatency
drwxr-xr-x 2 root root 4096 Jul  5  2022 5.13.0-41-lowlatency
drwxr-xr-x 2 root root 4096 Jul 15  2022 5.13.0-51-lowlatency
drwxr-xr-x 2 root root 4096 Aug  5  2022 5.13.0-52-lowlatency
drwxr-xr-x 2 root root 4096 Aug 15  2022 5.15.0-42-lowlatency
drwxr-xr-x 2 root root 4096 Sep 22  2022 5.15.0-43-lowlatency
drwxr-xr-x 2 root root 4096 Oct 15  2022 5.15.0-46-lowlatency
drwxr-xr-x 2 root root 4096 Oct 19  2022 5.15.0-48-lowlatency
drwxr-xr-x 2 root root 4096 Nov 15  2022 5.15.0-50-lowlatency
drwxr-xr-x 2 root root 4096 Dec  1  2022 5.15.0-52-lowlatency
drwxr-xr-x 2 root root 4096 Feb 22  2023 5.15.0-53-lowlatency
drwxr-xr-x 2 root root 4096 Mar 13  2023 5.15.0-56-lowlatency
drwxr-xr-x 2 root root 4096 Mar 28  2023 5.15.0-60-lowlatency
drwxr-xr-x 2 root root 4096 Apr 18  2023 5.15.0-67-lowlatency
drwxr-xr-x 2 root root 4096 Apr 25  2023 5.15.0-69-lowlatency
drwxr-xr-x 2 root root 4096 May 16  2023 5.15.0-70-lowlatency
drwxr-xr-x 2 root root 4096 Jun  2  2023 5.15.0-71-lowlatency
drwxr-xr-x 2 root root 4096 Jun 23  2023 5.15.0-72-lowlatency
drwxr-xr-x 2 root root 4096 Jul  9  2023 5.15.0-73-lowlatency
drwxr-xr-x 2 root root 4096 Jul 29  2023 5.15.0-75-lowlatency
drwxr-xr-x 2 root root 4096 Aug 16 13:12 5.15.0-76-lowlatency
drwxr-xr-x 2 root root 4096 Aug 31 10:33 5.15.0-78-lowlatency
drwxr-xr-x 2 root root 4096 Sep  8 13:52 5.15.0-79-lowlatency
drwxr-xr-x 2 root root 4096 Sep 22 11:38 5.15.0-82-lowlatency
drwxr-xr-x 2 root root 4096 Oct  5 13:29 5.15.0-83-lowlatency
drwxr-xr-x 2 root root 4096 Oct 19 19:11 5.15.0-84-lowlatency
drwxr-xr-x 2 root root 4096 Oct 31 15:22 5.15.0-86-lowlatency
drwxr-xr-x 2 root root 4096 Feb  6 15:21 5.15.0-87-lowlatency
drwxr-xr-x 6 root root 4096 Feb  8 15:16 5.15.0-88-lowlatency
drwxr-xr-x 2 root root 4096 Feb  8 14:37 5.15.0-92-lowlatency
drwxr-xr-x 6 root root 4096 Feb  8 15:16 5.15.0-94-lowlatency
drwxr-xr-x 5 root root 4096 Feb 10  2021 5.4.0-26-lowlatency
drwxr-xr-x 2 root root 4096 Jul 26  2021 5.4.0-64-generic
drwxr-xr-x 2 root root 4096 Jul 26  2021 5.8.0-43-lowlatency
drwxr-xr-x 2 root root 4096 Aug 19  2021 5.8.0-63-generic
drwxr-xr-x 2 root root 4096 Apr 21  2022 5.8.0-63-lowlatency
drwxr-xr-x 2 root root 4096 Aug 19  2021 5.8.0-64-lowlatency


```

---

### Post by #&amp;thj^% on 2024-02-10
Wow you have a lot of cruft, we need to clean most of that up....and i can see the possibility on why grub is confused.

Give me a beat to come up with something please.

EDIT for now please run this:
```
sudo apt --purge autoremove
```

---

### Post by Rick St. George on 2024-02-10
Somewhere I saw where UbuntuStudio places a Script to run Lowlatency by Defualt.
Using Grub Customizer, this is what is in the Default setting - Ubuntu Lowlatency;

```

recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  7426e742-ddf2-4ade-98a8-ad444dda2e5b
else
  search --no-floppy --fs-uuid --set=root 7426e742-ddf2-4ade-98a8-ad444dda2e5b
fi
linux	/boot/vmlinuz-5.15.0-94-lowlatency root=UUID=7426e742-ddf2-4ade-98a8-ad444dda2e5b ro  
initrd	/boot/initrd.img-5.15.0-94-lowlatency


```

Does this  help?

---

### Post by #&amp;thj^% on 2024-02-10
No please tell me you didn't install>>> Grub Customizer....if so there is the problem.
```
 apt policy  grub-customizer

```

---

### Post by Rick St. George on 2024-02-10
Yes, Thought we would have to make changes ... What's the problem?

```

~$ apt policy  grub-customizer
grub-customizer:
  Installed: 5.1.0-2
  Candidate: 5.1.0-2
  Version table:
 *** 5.1.0-2 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Rick St. George on 2024-02-10
> **1fallen said:**
> Wow you have a lot of cruft, we need to clean most of that up....and i can see the possibility on why grub is confused.

Give me a beat to come up with something please.

EDIT for now please run this:
```
sudo apt --purge autoremove
```

Done! and all this time I thought "autoremove" would remove them!?!?! How many other people thought this as well ... Hhmmm!!!

---

### Post by #&amp;thj^% on 2024-02-10
If you do a search in our Forums you will see many many issues with Grub-Customizer.

Did you just now install it? Or has it been installed for a while?

---

### Post by #&amp;thj^% on 2024-02-10
> **Rick St. George said:**
> Done! and all this time I thought "autoremove" would remove them!?!?! How many other people thought this as well ... Hhmmm!!!

Unfortunately a Lot still do.
Are you now able to boot properly?

---

### Post by Rick St. George on 2024-02-10
> **1fallen said:**
> 

Did you just now install it? Or has it been installed for a while?


Installed after having problems and reading a bunch of posts and forums, in anticipation of modifying Grub.
And don't know after Removing with Purge if Reboot is Ok!  Will try now and report back. Thanks!

Nope ... same problem. Envronment Block too small.  Also, think I mentioned previously a Popup Msg - > "System program problem detected". I keep reporting them.

Obviously there is still a problem. 

1Fallen: Do you suggest I run the install buildinfo 5.15.0-94 without the Flag ? ? ?

---

### Post by tea for one on 2024-02-10
> **Rick St. George said:**
>  Envronment Block too small.  
Is this problem similar to your previous Solved thread?
[https://ubuntuforums.org/showthread.php?t=2484308&highlight=environment+block](https://ubuntuforums.org/showthread.php?t=2484308&highlight=environment+block)

---

### Post by Rick St. George on 2024-02-10
YES, and that's where I found it (mentioned earlier that UbuntuStudio had a script that changed Grub) ... note in post #15 regarding installing "ubuntustudio-lowlatency-settings". 

> 
Adds lowlatency kernel as boot default if available
 This package makes the lowlatency kernel the default kernel in GRUB.
 Also adds a second entry for the generic kernel if available.


I thought I  had previously posted this problem. An update always modify Grub file. Anyway, followed MafoElfen's suggestion in post #35 at that link. Will Reboot and see if fixed ... Again!


HOOORAY !!! No Msg -> "Environment Block too small" ... Booted Up OK!  Here is what worked;

```


sudo rm /boot/grub/grubenv
sudo grub-editenv /boot/grub/grubenv create


```

I should've looked under ALL my previous post instead of general search.  Thanks Guys for all you do.

---

### Post by MAFoElffen on 2024-02-11
I hear a "rumor" that I am looking into, trying to confirm and what it really means to us.... That rumor is that the 6.8.0 (which is not yet done) lowlatency kernel will be the default for all Noble Ubuntu LTS kernel series.

I apologize, I am working on a new work-around to a different PPA. I haven't got to that part of my prioritized list. Still working on something higher up in priorities this morning...

---

### Post by #&amp;thj^% on 2024-02-11
If you want to read about it: [https://www.omgubuntu.co.uk/2024/02/ubuntu-24-04-linux-kernel-6-8-likely](https://www.omgubuntu.co.uk/2024/02/ubuntu-24-04-linux-kernel-6-8-likely)
And a must read: [https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2023007](https://bugs.launchpad.net/ubuntu/+source/linux-lowlatency/+bug/2023007)

---

### Post by Rick St. George on 2024-04-25
As an additional NOTE to help ... I believe the problem was due to a failing SSD drive. Due to the fact more recently i received this Error after nogo on boot --- "Failed to Read or Write outside HD0". 
I looked up when I installed this SSD and it had been 10 years. So if it can't read the drive .... Replace it! I did, and did a fresh install of v22.04. It worked flawlessly ... for one day!
See [https://ubuntuforums.org/showthread.php?t=2497163]("https://ubuntuforums.org/showthread.php?t=2497163")

---

