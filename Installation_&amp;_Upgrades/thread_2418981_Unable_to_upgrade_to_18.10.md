---
title: "Unable to upgrade to 18.10"
date: 2019-05-14
forum: Installation &amp; Upgrades
---

### Post by Edward_Diener on 2019-05-14
I can not upgrade from 18.04 to 18.10 on my computer. No matter what I try, when I reboot into 1810 I eventually see the boot screen message:

"fsckd-cancel-msg: Press Ctrl-C to cancel all filesystem checks"

and nothing further occurs.

Does anybody know how I can determine what is causing my problem ? I have checked my partitions with fsck and everything is fine.

---

### Post by TheFu on 2019-05-15
For any lurkers ... 

fsck happens to all file systems after a specific number of reboots. It is automatic. You can alter how often it happens for ext4/3 file systems using tune2fs. Probably best not to alter it on a normal desktop.
If you can, **boot from alternate boot media** (like the _Try Ubuntu_ install disk), then run fsck on each partition. If there are errors, copy/paste those back here using Adv Reply (#) - that code tags.  If you didn't boot from alternate media, then you haven't run fsck on every partition. If you aren't positive how to accomplish it, run **lsblk** and copy/paste it here, using code tags so the indentation is correct.

Upgrades between releases isn't something to do on a whim. The system needs to be fully up-to-date before starting.  That would be **sudo apt update && sudo apt dist-upgrade** working without any errors. Errors tend to explode during release migrations. I've never seen a problem system get better by forcing a new release. Reboot if anything gets installed, then make a full know-you-can-restore backup. Not optional.

We are all different, but I would stay on 18.04 which is an LTS release with 5 yrs of patches and wait for a few months after the next LTS is released in 20.04. If you move passed 18.04, then you are signing up to install a new OS every 6 months until 20.04 is released.

Support for 18.10 ends shortly, about 6 weeks. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)   Non-LTS releases have 6-9 months of support.

---

### Post by rsteinmetz70112 on 2019-05-16
Just to agree I would not upgrade to 18.10 without some compelling reason. I'd wait for 20.04 at least.
I wouldn't even attempt an upgrade unless everything was working as expected. 
I don't understand what you mean by "when I reboot into 18.10" 
If you're running 18.04 how are you booting into 18.10? Are you attempting a release upgrade? If so how are your doing that?

---

### Post by Edward_Diener on 2019-05-21
> **TheFu said:**
> For any lurkers ... 

fsck happens to all file systems after a specific number of reboots. It is automatic. You can alter how often it happens for ext4/3 file systems using tune2fs. Probably best not to alter it on a normal desktop.
If you can, **boot from alternate boot media** (like the _Try Ubuntu_ install disk), then run fsck on each partition. If there are errors, copy/paste those back here using Adv Reply (#) - that code tags.  If you didn't boot from alternate media, then you haven't run fsck on every partition. If you aren't positive how to accomplish it, run **lsblk** and copy/paste it here, using code tags so the indentation is correct.

Upgrades between releases isn't something to do on a whim. The system needs to be fully up-to-date before starting.  That would be **sudo apt update && sudo apt dist-upgrade** working without any errors. Errors tend to explode during release migrations. I've never seen a problem system get better by forcing a new release. Reboot if anything gets installed, then make a full know-you-can-restore backup. Not optional.

We are all different, but I would stay on 18.04 which is an LTS release with 5 yrs of patches and wait for a few months after the next LTS is released in 20.04. If you move passed 18.04, then you are signing up to install a new OS every 6 months until 20.04 is released.

Support for 18.10 ends shortly, about 6 weeks. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)   Non-LTS releases have 6-9 months of support.

I did boot from alternative media, the Ubuntu 18.04 installation disk. I did run fsck on each Ubuntu partition. There were no errors or problems of any kind.

I am trying to upgrade from 18.04 to 19.04 but can not do this through the Ubuntu GUI environment. Instead, in the GUI environment, I have to go to 18.10 first and then from 18.10 to 19.04. Therefore my only reason for going from 18.04 to 18.10 is so I can go to 19.04.

---

### Post by Edward_Diener on 2019-05-21
> **rsteinmetz70112 said:**
> Just to agree I would not upgrade to 18.10 without some compelling reason. I'd wait for 20.04 at least.
I wouldn't even attempt an upgrade unless everything was working as expected. 
I don't understand what you mean by "when I reboot into 18.10" 
If you're running 18.04 how are you booting into 18.10? Are you attempting a release upgrade? If so how are your doing that?

I am trying to go from 18.04 to 19.04 using the GUI environment. In this environment I must do 18.04 -> 18.10 -> 19.04.

After running the upgrade from 18.04 to 18.10 in the GUI environment the instructions tell me to reboot my machine to complete the upgrade. When I reboot my machine the grub2 menu choice eventually gives me a boot screen with boot messages. The last message I see is the 'fsckd... etc." and the bootup freezes at that point and no further messages occur.

---

### Post by rsteinmetz70112 on 2019-05-21
Are you saying that grub does not give you a choice to boot into 18.10 or other options? Or does it offer that choice then drop you into a shell of some sort?
 
I have found doing release upgraded from the command line is less of a problem, at least for me.

---

### Post by TheFu on 2019-05-21
Did you run **sudo apt update && sudo apt dist-upgrade** without any errors being reported before starting?  You'll need to do the same with 18.10 before trying to move to 19.04 as well.

I must say, I've never used the GUI tools for OS migrations. If that is your need, someone else will need to help.
I always use **sudo do-release-upgrade** from a prompt.

---

### Post by rsteinmetz70112 on 2019-05-21
> **TheFu said:**
> 
I always use **sudo do-release-upgrade** from a prompt.

I discovered recently that do-release-upgrade does not require a sudo. It will download the upgrade software then prompt for authorization. I'm not sure whether it's always been that way.

---

### Post by rsteinmetz70112 on 2019-05-21
> **TheFu said:**
> 
I always use **sudo do-release-upgrade** from a prompt.

I discovered recently that **do-release-upgrade** does not require a **sudo** . It will download the upgrade software then prompt for authorization. I'm not sure whether it's always been that way.

---

### Post by Edward_Diener on 2019-05-23
> **rsteinmetz70112 said:**
> Are you saying that grub does not give you a choice to boot into 18.10 or other options? Or does it offer that choice then drop you into a shell of some sort?
 
I have found doing release upgraded from the command line is less of a problem, at least for me.

I am saying that once the GUI upgrade is complete and I am told to reboot, the grub2 screen shows the boot to the kernel for 18.10 as the default, and after I choose the default the bootup sequence hangs after showing the "fsckd..." messages as the last messages I see.

---

### Post by Edward_Diener on 2019-05-23
> **TheFu said:**
> Did you run **sudo apt update && sudo apt dist-upgrade** without any errors being reported before starting?  You'll need to do the same with 18.10 before trying to move to 19.04 as well.

I must say, I've never used the GUI tools for OS migrations. If that is your need, someone else will need to help.
I always use **sudo do-release-upgrade** from a prompt.

I ran the latest GUI upgrade using Synaptic before starting the GUI upgrade process.

---

### Post by Edward_Diener on 2019-05-23
> **TheFu said:**
> Did you run **sudo apt update && sudo apt dist-upgrade** without any errors being reported before starting?  You'll need to do the same with 18.10 before trying to move to 19.04 as well.

I must say, I've never used the GUI tools for OS migrations. If that is your need, someone else will need to help.
I always use **sudo do-release-upgrade** from a prompt.

I guess I should try the command line upgrade the next time to see if that is more successful.

---

### Post by rsteinmetz70112 on 2019-05-23
> **Edward_Diener said:**
> I am saying that once the GUI upgrade is complete and I am told to reboot, the grub2 screen shows the boot to the kernel for 18.10 as the default, and after I choose the default the bootup sequence hangs after showing the "fsckd..." messages as the last messages I see.

If grub shows alternate kernels try them and see if they boot, then run fsck from there.

---

### Post by Edward_Diener on 2019-05-29
> **rsteinmetz70112 said:**
> If grub shows alternate kernels try them and see if they boot, then run fsck from there.

I tried the process again of upgrading using the GUI and the same problem occurred when I booted into 18.10 with the latest default kernel. I then tried booting into 18.10 with the previous kernel and the same problem occurred. Finally I tried booting into 18.10 with the default kernel in recovery mode, and first chose 'fsck' from the recovery mode menu. The result was:

/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcS: No such file or directory
fsck from util-linux 2.32
/dev/sdb6 is mounted.
e2fsck: Cannot continue, aborting.

---

### Post by rsteinmetz70112 on 2019-05-29
> **Edward_Diener said:**
> I tried the process again of upgrading using the GUI and the same problem occurred when I booted into 18.10 with the latest default kernel. I then tried booting into 18.10 with the previous kernel and the same problem occurred. Finally I tried booting into 18.10 with the default kernel in recovery mode, and first chose 'fsck' from the recovery mode menu. The result was:

/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcS: No such file or directory
fsck from util-linux 2.32
/dev/sdb6 is mounted.
e2fsck: Cannot continue, aborting.
Have you tried do-release-upgrade in a terminal window?
I'm not running 18.10, my latest machines are 18.04 LTS
The message suggests that there should be a file or directory named /etc/default/rc5. 
Perhaps someone can confirm if /etc/default/rcs is a valid file on 18.10
There is an /etc/default/rcS on my machines. 
The file is a script and on my machines everything seems to be commented out.

I'd try adding one manually and see if that makes a difference. 
I'd try also running fsck manually on all partitions in recovery mode and see if that helps.
I'd try booting a live session and running fsck on every partition to see if that helps

---

### Post by Edward_Diener on 2019-06-13
> **rsteinmetz70112 said:**
> Have you tried do-release-upgrade in a terminal window?
I'm not running 18.10, my latest machines are 18.04 LTS
The message suggests that there should be a file or directory named /etc/default/rc5. 
Perhaps someone can confirm if /etc/default/rcs is a valid file on 18.10
There is an /etc/default/rcS on my machines. 
The file is a script and on my machines everything seems to be commented out.

I'd try adding one manually and see if that makes a difference. 
I'd try also running fsck manually on all partitions in recovery mode and see if that helps.
I'd try booting a live session and running fsck on every partition to see if that helps

I am now getting the same result whether I upgrade using the GUI or do-release-upgrade in a terminal window. The actual upgrade occurs with no problems, but when I reboot into 18.10 the boot window messages now ends with:

```
[ OK ] Started Permit User Sessions.
Starting Hold until boot process finishes up...
Starting GNOME Display Manager...
[ OK ] Started OpenVPN service.
[ OK ] Started Hostname Service.
[ OK ] Started GNOME Display Manager.
```

No further boot messages occur and the boot process stops and does not show my login screen.

Rebooting into recovery mode I am able to look at the boot log to see what is happening. What I am seeing is

1)

```
org.gnome.Screensaver[2554]: Unable to init Server: Could not connect: Connection refused
gnome-screensav[2587]: Cannot open display:

```

and a little later:

2)

```
systemd[1]: Started NVIDIA Persistence Daemon.
gnome-session-binary[2572]: Unrecoverable failure in required component org.gnome.Shell.desktop
```

with CRITICAL FAILURE messaging in both situations.

In Ubuntu 18.04 I do have this additional driver information:

```
NVIDIA Corporation: GM206 [GeForce GTX 960]

Using NVIDIA driver metapackage from nvidia-driver-390(proprietary,tested)
Using X.Org X server -- Nouveau display driver from xserver-xorg-video-nouveau (open source)

```

Where the first choice of the two above, the NVIDIA driver metapackage, is being used. If I switch to the second choice, the X.Org X server -- Nouveau display driver, I end up with a 640 x 400 screen which makes it impossible to get anything done in 18.04.

My gut feeling is that the NVIDIA support for my graphics card, GeForce GTX 960, is broken in Ubuntu 18.10 and that this is causing the bootup screen for 18.10 to not be able to display my login screen, and therefore just freeze up. The GeForce GTX 960 is a fairly modern graphics card so I do not know why Ubuntu 18.10 does not appear to support it properly. Windows10, and various other Linux distros, which I can multi-boot along with Ubuntu, give me no problem with my graphics card.

As far as your comments, /etc/default/rcS does not exist on Ubuntu 18.04 and should not be there according to my searching on the Internet. Also fsck in all situations which I have tried, whether in recovery mode or live boot disc, gives no errors of any kind for my partitions. Furthermore as I say just above the I am no longer freezing up with a fsckd... message, but with the sequence I give.

---

### Post by rbmorse on 2019-06-13
Your GeForce 960GTX should work fine with Nvidia 390 and Ubuntu 18.10, but you can't have both the Nvidia Proprietary driver and the Nouveau driver loaded at the same time. They are not compatible. 

Try blacklisting the Nouveau driver:

```

$ sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"


Confirm the content of the new modprobe config file:


$ cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf
blacklist nouveau
options nouveau modeset=0


Enter the following linux command to regenerate initramfs:
$ sudo update-initramfs -u


Reboot your system:
$ sudo reboot

```

---

### Post by Edward_Diener on 2019-06-13
> **rbmorse said:**
> Your GeForce 960GTX should work fine with Nvidia 390 and Ubuntu 18.10, but you can't have both the Nvidia Proprietary driver and the Nouveau driver loaded at the same time. They are not compatible. 

Try blacklisting the Nouveau driver:

```

$ sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"


Confirm the content of the new modprobe config file:


$ cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf
blacklist nouveau
options nouveau modeset=0


Enter the following linux command to regenerate initramfs:
$ sudo update-initramfs -u


Reboot your system:
$ sudo reboot

```

I doubt they are both loaded at the same time. They just appear as choices for the GeForce 960GTX in the Additional Drivers tab of the sofware sources, and I have the radio check box for the first of the two, the NVidia proprietary driver. It is not reasonable to believe that just because they are offered as the two choices for the GeForce 960GTX they are both being loaded at the same time by Ubuntu 18.04. If that were so it would be a serious bug in Ubuntu which would affect plenty of people, since you would be saying that Additional Drivers choices for any hardware, simply by being listed, means all choices are being loaded at the same time.

---

### Post by TheFu on 2019-06-13
Have you tried using a different tty - not the GUI (c-a-F7), but one of the text logins, like ctl-alt-F1?
Not worth fighting to solve a GPU driver issue for an intermediate update, IMHO.

---

### Post by rbmorse on 2019-06-13
> **Edward_Diener said:**
> I doubt they are both loaded at the same time. They just appear as choices for the GeForce 960GTX in the Additional Drivers tab of the sofware sources, and I have the radio check box for the first of the two, the NVidia proprietary driver. It is not reasonable to believe that just because they are offered as the two choices for the GeForce 960GTX they are both being loaded at the same time by Ubuntu 18.04. If that were so it would be a serious bug in Ubuntu which would affect plenty of people, since you would be saying that Additional Drivers choices for any hardware, simply by being listed, means all choices are being loaded at the same time.

All right, but you still have to make sure the nouveau driver is blacklisted.

---

### Post by Edward_Diener on 2019-06-13
> **TheFu said:**
> Have you tried using a different tty - not the GUI (c-a-F7), but one of the text logins, like ctl-alt-F1?
Not worth fighting to solve a GPU driver issue for an intermediate update, IMHO.

I am actually trying to go from 18.04 to 19.04, but as I understand it I must first go from 18.04 to 18.10 before I go from 18.10 to 19.04. Otherwise I would not be bothering to go from 18.04 to 18.10 but would choose to go directly from 18.04 to 19.04.

---

### Post by Edward_Diener on 2019-06-13
> **rbmorse said:**
> All right, but you still have to make sure the nouveau driver is blacklisted.

I do not understand why, if it is not being chosen. Are you saying that the noveau driver is being chosen by default for 18.10 even though I have the proprietary driver chosen for 18.04, and this is causing my problem trying to boot into 18.10 ? The boot messages suggest that the NVIDIA driver is being used during the boot sequence.

---

