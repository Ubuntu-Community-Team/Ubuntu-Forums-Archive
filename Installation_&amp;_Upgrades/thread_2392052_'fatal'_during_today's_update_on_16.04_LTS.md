---
title: "'fatal' during today's update on 16.04 LTS"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by harfin on 2018-05-16
[SIZE=2]Was advised of upgrade / update this morning, but it appears something may have gone wrong! 

 The updating steps were:
[/SIZE]
[SIZE=1]```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libpoppler-glib8 libpoppler58 linux-firmware poppler-utils
4 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 50.5 MB of archives.
After this operation, 16.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpoppler58 amd64 0.41.0-0ubuntu1.7 [758 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpoppler-glib8 amd64 0.41.0-0ubuntu1.7 [104 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-firmware all 1.157.18 [49.5 MB]
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 poppler-utils amd64 0.41.0-0ubuntu1.7 [130 kB]
Fetched 50.5 MB in 26s (1,920 kB/s)                                            
(Reading database ... 267136 files and directories currently installed.)
Preparing to unpack .../libpoppler58_0.41.0-0ubuntu1.7_amd64.deb ...
Unpacking libpoppler58:amd64 (0.41.0-0ubuntu1.7) over (0.41.0-0ubuntu1.6) ...
Preparing to unpack .../libpoppler-glib8_0.41.0-0ubuntu1.7_amd64.deb ...
Unpacking libpoppler-glib8:amd64 (0.41.0-0ubuntu1.7) over (0.41.0-0ubuntu1.6) ...
Preparing to unpack .../linux-firmware_1.157.18_all.deb ...
Unpacking linux-firmware (1.157.18) over (1.157.17) ...
Preparing to unpack .../poppler-utils_0.41.0-0ubuntu1.7_amd64.deb ...
Unpacking poppler-utils (0.41.0-0ubuntu1.7) over (0.41.0-0ubuntu1.6) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpoppler58:amd64 (0.41.0-0ubuntu1.7) ...
Setting up libpoppler-glib8:amd64 (0.41.0-0ubuntu1.7) ...
Setting up linux-firmware (1.157.18) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-124-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-122-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic
WARNING: missing /lib/modules/4.4.0-81-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-81-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_F4fpZx/lib/modules/4.4.0-81-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_F4fpZx/lib/modules/4.4.0-81-generic/modules.builtin: No such file or directory
Setting up poppler-utils (0.41.0-0ubuntu1.7) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...

```[/SIZE]
[SIZE=2]
Post the update, I ran Update again, and was advised that all was up to date.

[/SIZE][SIZE=2]Confused!
Alan[/SIZE]

---

### Post by Autodave on 2018-05-16
What went wrong? No idea. Something hiccuped?  Since you ran the update again and it was OK, I would not be worried a lot about it.

---

### Post by harfin on 2018-05-16
Thanks for that Dave. I'll follow your advice.
Alan

---

### Post by harfin on 2018-05-20
Since my initial reply and whether or not it is related,  I was given during the next update a message which said that there "had been an internal error, and would I like to report it"; to which I agreed. 

The details the message report listed was "/usr/lib/x86_64-gnu/unity/compiz-config-profile-setter"

When I attempt to boot up as normal, the system hangs at the point where the desktop image screen is showing plus the few icons I have as items on my desktop. I have no mouse or key access to the side toolbar and thus the system at al (other than being able to right-click and select the terminal). At that time I have no option other than turning off the laptop, and rebooting. I then click the escape key at the appropriate stage and chose ubuntu advanced. I then select the latest version and the system goes into a safe mode. At that point after the system system says my computer is all up to date, and I then select return to normal boot. When that completes my tool bar is then revealed and the system purports to act / react as normal.

It isnt of course, and on next boot-up I go through the same rigmarole as before!

Help!

Alan

---

### Post by harfin on 2018-05-20
Attempted this afternoon to log on, and this time as it boot was running and had got to the welcome screen, the same message appeared i.e. "Ubuntu has experienced an internal error. Would you like to report it"; I agreed, the details as before were again :
> /usr/lib/x86_64-gnu/unity/compiz-config-profile-setter

The system hung (mouse pointer has become a **X**, and cannot see side toolbar), and the only way forward is to power off, reboot using the esc key during the boot process, select the current version and selecting go to grub boot loader.

Surely there is a way to avoid this convoluted process prior to the publishing of a fix for this "internal Ubuntu error"?

Alan

---

### Post by harfin on 2018-05-22
[SIZE=2]It's now **SIX** days now since I submitted my problem with Ubuntu 16.04 LTS

I have had only one comment from a forum member

I continue to have the same unresolved issue, namely I am unable to log onto my laptop as it goes into some sort of limbo state after revealing the Desktop screen; no toolbar, no ability to progress, and with the mouse pointer replaced by a [/SIZE][B][SIZE=2]X[/SIZE]
[/B]
[SIZE=2]Is there no-one on this forum who can offer me any suggestions/recommendations?
[/SIZE]
[SIZE=2]&#8203;Alan A Hart[/SIZE]

---

### Post by deadflowr on 2018-05-22
What does
```
dpkg -l | grep linux
```
show?
seems like an issue with the 4.4.0-81 kernel.
Should be redeemable by either reinstalling that kernel or removing that kernel.
Or reinstall it and then remove it cleanly.

---

### Post by harfin on 2018-05-22
[SIZE=2]```
dpkg -l | grep linux[ii  console-setup-linux                                  1.108ubuntu15.3                              all          Linux specific part of console-setupii  libselinux1:amd64                                    2.4-3build2                                  amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                                       1.10.0-1                                     amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                 1.10.0-1                                     amd64        Video4linux frame format conversion library
ii  linux-base                                           4.5ubuntu1~16.04.1                           all          Linux image base package
ii  linux-firmware                                       1.157.18                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.4.0.127.133                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-122                              4.4.0-122.146                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-122-generic                      4.4.0-122.146                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-124                              4.4.0-124.148                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-124-generic                      4.4.0-124.148                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-127                              4.4.0-127.153                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-127-generic                      4.4.0-127.153                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.4.0.127.133                                amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-101-generic                        4.4.0-101.124                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-103-generic                        4.4.0-103.126                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-104-generic                        4.4.0-104.127                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-108-generic                        4.4.0-108.131                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-109-generic                        4.4.0-109.132                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-112-generic                        4.4.0-112.135                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-116-generic                        4.4.0-116.140                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-119-generic                        4.4.0-119.143                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-121-generic                        4.4.0-121.145                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-122-generic                        4.4.0-122.146                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-124-generic                        4.4.0-124.148                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-127-generic                        4.4.0-127.153                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-96-generic                         4.4.0-96.119                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-97-generic                         4.4.0-97.120                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-98-generic                         4.4.0-98.121                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-101-generic                  4.4.0-101.124                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-103-generic                  4.4.0-103.126                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-104-generic                  4.4.0-104.127                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-108-generic                  4.4.0-108.131                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-109-generic                  4.4.0-109.132                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-112-generic                  4.4.0-112.135                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-116-generic                  4.4.0-116.140                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-119-generic                  4.4.0-119.143                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-121-generic                  4.4.0-121.145                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-122-generic                  4.4.0-122.146                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-124-generic                  4.4.0-124.148                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-127-generic                  4.4.0-127.153                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-96-generic                   4.4.0-96.119                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-97-generic                   4.4.0-97.120                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-98-generic                   4.4.0-98.121                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.4.0.127.133                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.4.0-127.153                                amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                 4.4.0.127.133                                amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-4.4.0-101-generic                 4.4.0-101.124                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-103-generic                 4.4.0-103.126                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-104-generic                 4.4.0-104.127                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-108-generic                 4.4.0-108.131                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-109-generic                 4.4.0-109.132                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-112-generic                 4.4.0-112.135                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-116-generic                 4.4.0-116.140                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-119-generic                 4.4.0-119.143                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-121-generic                 4.4.0-121.145                                amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-122-generic                 4.4.0-122.146                                amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-124-generic                 4.4.0-124.148                                amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-127-generic                 4.4.0-127.153                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-96-generic                  4.4.0-96.119                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-97-generic                  4.4.0-97.120                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-98-generic                  4.4.0-98.121                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic                           4.4.0.127.133                                amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  pptp-linux                                           1.8.0-1                                      amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                             3:6.03+dfsg-11ubuntu1                        amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                      3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                           2.27.1-6ubuntu3.4                            amd64        miscellaneous system utilities
```[/SIZE]

---

### Post by harfin on 2018-05-22
[SIZE=2]That was the output from:
 [COLOR=#000000][FONT=&amp]dpkg -l | grep linux[/FONT][/COLOR] 

Thanks for responding!
Does that hep?

Alan[/SIZE]

---

### Post by deadflowr on 2018-05-22
Interesting.
Is there anything related to the 4.4.0-81 kernel in the boot directory
```
ls /boot | grep 4.4.0-81
```
It might be that you have an orphan/rogue initrd.img file causing the updater to think the kernel is installed when in fact it is not.

---

### Post by harfin on 2018-05-22
[SIZE=2]In the synaptic package manager it states for that kernel:
[/SIZE][SIZE=2]This package provides the architecture dependant parts for kernel[/SIZE]
[SIZE=2]version locked tools for cloud tools for version 4.4.0-81 on[/SIZE]
[SIZE=2]64 bit x86.[/SIZE]
[SIZE=2]You probably want to install linux-cloud-tools-4.4.0-81-<flavour>

What would you do as regards the reinstallation / deletion?

Alan[/SIZE]

---

### Post by harfin on 2018-05-22
[SIZE=2]The output is:
initrd.img-4.4.0-81-generic

Alan[/SIZE]

---

### Post by harfin on 2018-05-22
[SIZE=2]&#8203;That output would suggest that you are right, wouldnt it?[/SIZE]

---

### Post by harfin on 2018-05-22
[SIZE=2]If so should I find that using the SPM and delete it?[/SIZE]

---

### Post by deadflowr on 2018-05-22
Try
```
sudo apt-get install --reinstall linux-image-4.4.0-81-generic
```
then double check the running kernel (which kernel is currently in use)
```
uname -r
```
if from some reason it shows the 4.4.0-81-generic kernel then I suggest reboot and choose another kernel at the boot menu.
(If the boot menu does not show you may need to press the shift or ESC key to invoke it.
You do this when the first machine BIOS screen goes blank, might require a few quick taps since sometimes a single tap can miss it)

Then if in another kernel 
```
sudo apt-get purge linux-image-4.4.0-81-generic
```
that should clear the issue.

Even though the kernel is not actually installed, the --reinstall flag should allow it to bypass the kinky issue that might happen because of the errant initrd.img file.

Post back if anything seems off.

---

### Post by harfin on 2018-05-22
[SIZE=2]I followed all the instructions, and after the purge step I did the uname -r and the result was the current kernel, 4.4.0-127-generic.

After all that, when I reboot without intervention of going through recovery mode, I end up with the system hanging again!

Alan[/SIZE]

---

### Post by harfin on 2018-05-23
[SIZE=2]Another day and same status as regards my system.

I boot up and all proceeds as normal until the home screen. The mouse pointer becomes a **X **and I am left with the few choices from the right mouse click menu. The only one that is of any material use is the item "Open Terminal", as that enables me to enter "shutdown" and thus turn off the laptop which enables me to close down properly.

So I then boot up and click "esc" to enter the Ubuntu advanced mode, and with that I can select to boot using one of the last three kernels in "recovery mode" (it matters not which kernel I choose as regards the outcome). Once the system has done it's thing I can then select "resume normal boot" and I am then returned to a standard logged in home screen which enables me to operate in a normal fashion. When I subsequently close down, I am initially returned to the pre-successful boot up black screen with white text which whizzes through a screen or two of text, before the laptop turns off.

I feel sure the issue that causes this problem is connected to the reports I had earlier regarding "Ubuntu has experienced an internal error" and which lists the fault details as 

[COLOR=#000000] /usr/lib/x86_64-gnu/unity/compiz-config-profile-setter. 

In a subsequent boot, the details for an "Ubuntu internal error" became just :-[/COLOR][/SIZE][COLOR=#000000]/usr/lib/x86_64-gnu/unity/compiz[/COLOR][SIZE=2][SIZE=2]
[/SIZE]
Is this something that I have to await an update from Ubuntu to correct this "internal error"?

Alan A Hart[/SIZE]

---

### Post by deadflowr on 2018-05-23
Okay, so basically let's first assume you've checked that updates are running as they should
```
sudo apt update
sudo apt full-upgrade
```
(I will assume that you've run these, or some form of updates either software updater or apt/apt-get.
But just in case... run the commands to double check. It's always best to have a fully-functional updater, then not to have a fully-funtional updater)

There have been some issues with compiz
[https://ubuntuforums.org/showthread.php?t=2387576]("https://ubuntuforums.org/showthread.php?t=2387576")
[https://ubuntuforums.org/showthread.php?t=2387028]("https://ubuntuforums.org/showthread.php?t=2387028")
[https://ubuntuforums.org/showthread.php?t=2386528]("https://ubuntuforums.org/showthread.php?t=2386528")

Does any of that give you insight as to the issue?

---

### Post by harfin on 2018-05-24
[SIZE=2]I use the auto updater just to **notify** me of all updates / upgrades and then use the commands [/SIZE]as is appropriate [SIZE=2]in the terminal e.g. [/SIZE] *[SIZE=2]sudo apt upgrade, sudo apt update, sudo apt autoremove[/SIZE]*[SIZE=2]. So far I have not used sudo apt full-upgrade; should I be using that?

[/SIZE]The reason that I do this is due to an issue a while back, where the boot area reserved for those who have encrypted hard drives runs out of space periodically, so I only have 2 or at most 3 earlier kernels in that space)
[SIZE=2]
The first thread you mentioned seems to mirror the issue I have, inability not to see my screen's toolbar (and it's icons). The other threads seem to be full of what I assume is very technical jargon which is are way outside of my level of competence.  The threads refer to "unity" and it's use, can you give me a wee bit more about that? How do I find out what I using ?

This morning it has taken ages to get back to any semblance of normality on the laptop. I finally went back to recovery mode using kernel 124 and thence to update grub bootloader and then resume before I got the desktop / toolbar / icons back.

I will try the steps in the first of the 3 threads you referred me to, when I have finished the tasks I need to do now. I will post back the result.

Alan
[/SIZE]

---

### Post by harfin on 2018-05-24
[SIZE=2]Well sad to say, when trying the steps in the 1st thread you gave me, the 1st change did not complete (*Code:    sudo rm -fr ~/.cache/compizconfig-1 *then [/SIZE]*[SIZE=2]sudo rm -fr ~/.compiz) [/SIZE]*[SIZE=2]it [/SIZE][SIZE=2]showed a fault saying "no such file or directory exists'.

The hint "*To cycle hit [FONT=Ubuntu Mono][FONT=&amp][SIZE=2][Super key]+[P key] [/SIZE][/FONT][/FONT]*[/SIZE]*[SIZE=2]a few times to sight the icons etc" [/SIZE]*[SIZE=2]just opened a wee box with letter p's in it. 

It seems that just one boot after the loss of screen icons etc all I may have needed to do was to press and hold down the Super Key to cycle to reveal them, as I tried out pressing and holding pressing the key before I shut down ( which I had booted using the recovery boot process) and the icons etc appeared.

So I then rebooted in my usual (pre-fault) manner[/SIZE] [SIZE=2]and after the boot process had run through it needed no intervention from me to display my normal desktop screen (with icons/ Dash) etc.

I will now repeat that to make sure it was not a one off fluke, and edit this post to confirm success.  

Delighted to be able to say, that the laptop's normal booting process is fixed!  Works (again) like a charm.

Deadflowr - you are very much alive!

Alan
[/SIZE]

---

### Post by harfin on 2018-07-28
[SIZE=3][B]Here we go again!

[/B]The merrygoround is twirling yet again.

Latest updates 3 days ago, which concluding with making changes to compiz and I am back where I was in May.

I have managed to link back to the forum, and seek help, although I am unable to get to toolbars, etc.

The so called 'super' key isn't super anymore.

I have rebooted heaps of times and still end up in limbo. Trying virtually all the so-called fixes to solve the problem. Success rate **nil.**

Can someone tell me please, what the heck is the problem with 16.04? Currently I am at a point now where I am sorely tempted to give try another operating set-up. 

The error report ("*Ubuntu has experienced an internal error . . ."* etc) went in, and in the meantime I am left "out on a limb". **Again.**

**&#8203;HELP!!**

[/SIZE]

---

### Post by harfin on 2018-07-28
[SIZE=3]Nobody able to make a suggestion?

I have ordered a DVD of 18.04 to update to the latest LT but I get that next week (2nd Aug). Hopefully that will not suffer the same hassles that 16.04 has !

[/SIZE][SIZE=3][/SIZE]

---

