---
title: "Kernel 5.4.0-24 breaks networking in Focal beta 20.04"
date: 2020-04-17
forum: Installation &amp; Upgrades
---

### Post by rtimai on 2020-04-17
I wish to report here that the current Linux kernel linux-image-5.4.0-24-generic breaks networking in the current beta release of Ubuntu 20.04:

**BACKGROUND**
I followed instructions for forcing a distribution upgrade from 19.10 to 20.04 beta. I did this because I read that upgrading early allowed you to naturally transition to the final release without going through the dist-upgrade process that checks for and removes incompatible software and settings. The extended COVID19 stay-home policy wasn't announced yet, and I was trying to avoid bad timing.

**THE DIST-UPGRADE PROCESS ACTUALLY PROCEEDED WITH NO MAJOR PROBLEMS.** I have been running the beta since Apr 1 without problems. The problem occurred when Software Updater installed the newest linux kernel (e.g., newest available through Canonical.) 

**Kernel 5.4.0-24-generic breaks networking.**
After the last update which included a kernel update, Networking disappeared from the status menu in the GNOME3 topbar (I use a Wired connection because it's faster than my wi-fi connection, which also was not found -- but that's another issue.) Networking also disappeared from the System Settings tool.

I checked and determined that networking was managed by NetworkManager, not the networkd daemon. But all attempts to restart networking (nmcli) failed.

**WORKAROUND**
I found that restarting with the previous kernel restored normal networking operation. So, this is my current workaround until I can test the next kernel released to Focal. I hope this helps somebody else.

**Current system information:**
~$  dpkg -l | grep linux-image | awk '{print$2}' # LIST ALL INSTALLED KERNELS
linux-image-5.3.0-18-generic
linux-image-5.3.0-24-generic
linux-image-5.3.0-40-generic
linux-image-5.3.0-42-generic
linux-image-5.3.0-45-generic
linux-image-5.4.0-21-generic
linux-image-5.4.0-24-generic <== BREAKS NETWORKING IN FOCAL
linux-image-generic

~$  lsb_release -drs ; uname -rp ; gnome-shell --version ; echo $XDG_SESSION_TYPE
Ubuntu 20.04 LTS
20.04
5.4.0-21-generic x86_64
GNOME Shell 3.36.1
wayland

---

### Post by slickymaster on 2020-04-17
This forum is populated by volunteer end-users just like you. Even the Staff are volunteers. None of us work for Canonical, nor are we Ubuntu developers. Ubuntu, developed by Canonical, is only one of hundreds of Linux distributions.

You should be reporting that at [https://bugs.launchpad.net/~ubuntu-kernel-team](https://bugs.launchpad.net/~ubuntu-kernel-team)

---

### Post by rtimai on 2020-04-17
I wanted to make this information available to anyone else running Focal beta, not so much to report a bug.

But, thank you for the suggestion. I could find no bug report facility on Launchpad, but sent a message to the ubuntu-kernel-networking team. And I marked this thread Solved.

---

### Post by 0n0w1c on 2020-04-17
I am using 20.04 with the current kernel.
5.4.0-24-generic #28-Ubuntu SMP Thu Apr 9 22:16:42 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

I detect no issues with the networking currently on my qemu guest, possibly it could be specific to your network device?
Do you see your network card with lscpi?

If you do see your network card, possibly then a gnome3/networking issue.
I don't use the gnome3 desktop, I run on the Lubuntu Desktop and my network gui config tool (nm-connection-editor) works fine.

---

### Post by rtimai on 2020-04-17
@0n0w1c: Thanks for your interest. The output I get from 'lspci' is identical (17 lines) on either kernel 5.4.0-21 and -24, and does 'see' the network controllers: 
 
 07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 07)
 0d:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)

Here is some interesting file listings. Notice that only the files in /etc/network/ are dated Apr 16, the time of the suspected update, and the four 'wpasupplicant' softlinks in the subdirectories below were probably created Apr 15. The rest of the config files are from the 19.10 installation. Could be, the problem is somewhere in there.
 
```
~$  ls -l /etc/netplan/
total 4
-rw-r--r-- 1 root root 104 Oct 17  2019 01-network-manager-all.yaml

~$  cat /etc/netplan/01-network-manager-all.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

~$  ls -l /etc/network/
total 16
drwxr-xr-x 2 root root 4096 Apr 16 22:10 if-down.d
drwxr-xr-x 2 root root 4096 Apr 16 22:10 if-post-down.d
drwxr-xr-x 2 root root 4096 Apr 16 22:10 if-pre-up.d
drwxr-xr-x 2 root root 4096 Apr 16 22:10 if-up.d

~$  ls -l  /etc/network/if-pre-up.d/
total 8
-rwxr-xr-x 1 root root 4191 Sep 15  2018 wireless-tools
lrwxrwxrwx 1 root root   32 Apr 15 03:08 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh

~$  ls -l /etc/network/if-up.d/
total 16
-rwxr-xr-x 1 root root  923 Aug 21  2018 avahi-autoipd
-rwxr-xr-x 1 root root  484 Aug 21  2018 avahi-daemon
-rwxr-xr-x 1 root root 1677 Aug 25  2019 clamav-freshclam-ifupdown
-rwxr-xr-x 1 root root  385 Sep  5  2019 openvpn
lrwxrwxrwx 1 root root   32 Apr 15 03:08 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh

~$  ls -l /etc/network/if-down.d/
total 12
-rwxr-xr-x 1 root root 1015 Aug 21  2018 avahi-autoipd
-rwxr-xr-x 1 root root 1677 Aug 25  2019 clamav-freshclam-ifupdown
-rwxr-xr-x 1 root root  372 Sep  5  2019 openvpn
lrwxrwxrwx 1 root root   32 Apr 15 03:08 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh

~$  ls -l /etc/network/if-post-down.d/
total 4
lrwxrwxrwx 1 root root   23 Apr  8 06:43 avahi-daemon -> ../if-up.d/avahi-daemon
-rwxr-xr-x 1 root root 1409 Sep 15  2018 wireless-tools
lrwxrwxrwx 1 root root   32 Apr 15 03:08 wpasupplicant -> ../../wpa_supplicant/ifupdown.sh

~$
```
(I left in the 'total' lines because I didn't know what they meant.)

FORUM ADMIN: Ah sorry, I guess the intrigue got the best of me. Please feel free to delete this message if you feel it's inappropriate.

---

