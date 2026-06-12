---
title: "System program problem detected when installing ubuntu 24.04 LTS"
date: 2024-08-05
forum: Installation &amp; Upgrades
---

### Post by digitalknight on 2024-08-05
Never came across this issue in the past. Seems to get most of the way thru the install before that error pops up. I read other have had this issue also and had to use a legacy install file?

---

### Post by euol on 2024-08-06
Check if the Ubuntu ISO file you downloaded is not corrupted. You can verify the checksum (MD5/SHA256) of the ISO file against the official values provided on the Ubuntu download page.

Otherwise it would be useful to have more information from logs which can be found in /var/log

---

### Post by digitalknight on 2024-08-07
Thank you for the reply. The checksum does match:[COLOR=#FFFFFF]fa[/COLOR]81fae9cc21e2b1e3a9a4526c7dad3131b668e346c580702235ad4d02645d9455 Not sure how to post or attach log files here?[COLOR=#FFFFFF]e9  adf af a[/COLOR]

---

### Post by currentshaft on 2024-08-07
.

---

### Post by tea for one on 2024-08-07
> **digitalknight said:**
> Never came across this issue in the past. Seems to get most of the way thru the install before that error pops up. I read other have had this issue also and had to use a legacy install file?
Which utility did you use to prepare the USB?

I use one or other of the following and rarely is there any difficulty:-
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
Startup Disk Creator (included in Ubuntu iso)

---

### Post by digitalknight on 2024-08-07
> **tea for one said:**
> Which utility did you use to prepare the USB?

I use one or other of the following and rarely is there any difficulty:-
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
Startup Disk Creator (included in Ubuntu iso)

balenaEtcher

---

### Post by digitalknight on 2024-08-07
Main error I am seeing on the log is: Unexpected error while running command. Command: unshare --fork --pid mount-proc=/target/proc chroot /target grub-install dev/sda Exit code: 1

Also I see: grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..

Then a:  Stderr: ""

last line is "curtin command install"

---

### Post by tea for one on 2024-08-07
> **digitalknight said:**
> Main error I am seeing on the log is: Unexpected error while running command. Command: unshare --fork --pid mount-proc=/target/proc chroot /target grub-install dev/sda Exit code: 1
Also I see: grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..
Then a:  Stderr: ""
last line is "curtin command install"
A BIOS Boot partition is required when you install in old-fashioned Legacy mode.
Your target PC, is it not UEFI compatible?

---

### Post by digitalknight on 2024-08-08
Yes it is. Lenovo T520

Let me mess around a bit in the BIOS and see if I can get it to install.

---

### Post by digitalknight on 2024-08-08
Good to go! I loaded in the default BIOS setting and then checked everything. I noticed that UEFI/Legacy was set to both, I then checked the order and it was set to Legacy first so I set that to UEFI first and restarted and everything installed correctly this time around. :popcorn:

Thanks for everyone's help here.

---

