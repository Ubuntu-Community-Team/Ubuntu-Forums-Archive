---
title: "Access encrypted /home from Rescue Shell"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by faulty_tower on 2010-05-01
Hello forums!

I have installed Kubuntu 10.04 x64 from scratch using the alternate installation CD and unfortunately I'm experiencing some serious troubles. Everything worked fine, installed packages, moved my backed-up data to my encrypted /home partition - until I rebooted. Usually I reboot the system right after the installation process to see if the boot process shows any errors, but what can I say, seems like I forgot to do it this time :-|.

The problem is that the boot process just "hangs" right before the login window should disappear. By "hang" I mean dead: no switching to virtual terminals, no CTRL-ALT-DEL - the system just freezes.
I'm quite familiar with doing things shell-wise, so I started the "Rescue Mode" from the alternate CD and was able to mount my root partition. 

Problem #1:

No faulty log entries whatsoever: dmesg, boot.log, messages etc. all looking fine - except Xorg.0.log. I suspect the proprietary Nvidia drivers to be the culprit here, because what I'm getting is:

"Caught signal 11 (Segmentation Fault). Server aborting"

Running "startx" as root from the rescue shell gives the same results: complete system freeze. "Looks like a reinstallation candidate, let's just backup my data" I thought, which brings us to

Problem #2:

I can't mount my encrypted /home from the rescue shell. The exact steps involved are:


[LIST=1]
[*]Mount my root partition and chroot to it.
[*]Issuing "ecryptfs-mount-private" gives the following error message: "ERROR: Encrypted private directory is not setup properly"
[*]Becoming my user "su - faulty" and trying step 2 again yields the same results.
[/LIST]
I feel like I'm almost there: I'm executing commands in my root environment, just can't seem to access my data which I'd like to backup before doing a clean reinstall. Any thoughts?

Regards, faulty

---

### Post by faulty_tower on 2010-05-02
*bump*

---

### Post by faulty_tower on 2010-05-03
*bump*

Is there any way I can do a "mount -t ecryptfs ...." that gives me a password prompt? I think my main problem here is that I don't get any password prompt, just the error message posted above.

---

### Post by faulty_tower on 2010-05-04
Even my last hope failed:

```

#md1 is my home partition

cryptsetup luksOpen /dev/md1 crypt1
mount /dev/mapper/crypt1 /home

```

No error message shown on line 1, but on line 2 it says "dev/mapper/crypt1" is not a device - and guess what, it does not exist in /dev/mapper. I think the problem is that line 1 does not even ask for my d*** password...

Giving up now

---

