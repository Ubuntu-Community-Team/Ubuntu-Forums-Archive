---
title: "Updating a kernel never completes and blocks dpkg"
date: 2020-02-27
forum: Installation &amp; Upgrades
---

### Post by fred66 on 2020-02-27
I am running Ubuntu 18.04 (I am very busy these days, so I thought I'd stick with LTS and not be distracted by frequent upgrades), waiting for 20.04. I chose the Mate desktop, since I just don't like Gnome, and KDE Plasma, while great in many ways, was slowing my aged computer too much. Anyway, everything was going well, until I set up an update (via sudo apt upgrade) and the update got stuck when trying to install a new kernel. Now, every time I try to get updates, either via apt or via Synaptic, I am blocked by the incomplete installation. Specifically, this is what I get when I try sudo apt upgrade:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
fede@milton:~$ sudo dpkg --configure -a
Setting up linux-image-5.3.0-7629-generic (5.3.0-7629.31~1581628854~18.04~2db8a7a~dev) ...
Processing triggers for linux-image-5.3.0-7629-generic (5.3.0-7629.31~1581628854~18.04~2db8a7a~dev) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-7629-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-7629-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-7629-generic
Found initrd image: /boot/initrd.img-5.3.0-7629-generic
Found linux image: /boot/vmlinuz-5.3.0-7625-generic
Found initrd image: /boot/initrd.img-5.3.0-7625-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin

after which, the process just stalls. I see a request to reboot the computer, but after I do that, we are back to square one. I guess I should reinstall Ubuntu from scratch, but I got work to do, and it's not like I am otherwise crippled by this issue. so I might just wait for 20.04 and install that from scratch (a bummer: I got a lot of software installed, and it would have been nice to keep it... oh, well). However, if someone can point me to a way to clean up whatever this mess is already now, I would be extremely grateful. Thank you!

---

### Post by TheFu on 2020-02-27
Usually, when a kernel update fails, it is from an out of storage condition.  There would usually be an error about that.
Run these to see how storage it going:
```
df -hT
df -i
```

To cleanup extra packages, these are normal methods:
```
sudo apt autoremove
sudo apt autoclean
```

And just to be 100%, you are running:
```
sudo apt update
sudo apt upgrade
```
yes?  RHEL, CentOS to the update part automatically. Ubuntu does not.

It would really help if all commands and output were wrapped in _code tags_ when posting here. That makes the columns line up and helps greatly with readability.  Easier to read means more people are likely to read and help. We are used to seeing terminal output with monospaced fonts.

Is there anything in the log files on the system?

---

### Post by fred66 on 2020-02-28
Thank you for your suggestions (and my apologies for my previous careless posting without ```
 tags)

I tried a number of things following your suggestions, and nothing seemed to work at first (still the same stall when creating the GRUB configuration), but in the end it looks like something actually did, since sudo upgrade finally did download updates. It also, on its own, removed a Linux kernel, even though I didn't do an autoremove (when I earlier tried it refused, with the usual message that dpkg had been interrupted):

[CODE]The following packages will be REMOVED:
  linux-image-5.3.0-22-generic
The following packages have been kept back:
  fwupdate fwupdate-signed
...

```

This never happened before, but I suppose it happened because of the messed up situation that apt/dpkg was mopping up.

Than you for your help!!
I am not sure what was the thing that fixed the issue, but I am happy it was fixed (fingers crossed)

---

### Post by fred66 on 2020-02-28
OOps! Spoke too early. After starting the upgrade I went on to other things, and when I ogt back to the temrinal I found this (again, stuck when generating the GRUB configuration):

```

(Reading database ... 734135 files and directories currently installed.)
Removing linux-image-5.3.0-22-generic (5.3.0-22.24+system76~1573660262~18.04~d11b582~dev) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.3.0-22-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-7629-generic
Found initrd image: /boot/initrd.img-5.3.0-7629-generic
Found linux image: /boot/vmlinuz-5.3.0-7625-generic
Found initrd image: /boot/initrd.img-5.3.0-7625-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
---
Progress: [  3%] [####.......

```
It's always the same spot where this stalls. It went farther than before (it downloaded the package updates), but it still won't work to the end... :(

---

### Post by webaake on 2020-02-29
Did you try to run update-grub by itself? Might give some more information.

> sudo update-grub

---

### Post by TheFu on 2020-02-29
Dude, if you don't tell us EXACTLY what you've tried and actually show what we ask, nobody can help.  Also, SHOW ALL COMMANDS. Don't make the people trying to help guess what was typed.

Please.

We can't read your mind.

---

### Post by mörgæs on 2020-02-29
> **fred66 said:**
> ...so I might just wait for 20.04 and install that from scratch

There is only minor difference between 19.10 and 20.04. If you consider a clean install of 20.04 you could just as well do the same for 19.10.

---

### Post by fred66 on 2020-02-29
I am sorry I was not clear enough. I tried to run apt upgrade and get as response

```
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

Running the command results in the output that I posted, stalling at the end on the GRUB configure sequence.

---

### Post by fred66 on 2020-02-29
Thanks. I tried, and i get the same result: update-grub stalls at the same spot as after dpkg --configure -a:
```

Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-7629-generic
Found initrd image: /boot/initrd.img-5.3.0-7629-generic
Found linux image: /boot/vmlinuz-5.3.0-7625-generic
Found initrd image: /boot/initrd.img-5.3.0-7625-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin


```

---

### Post by webaake on 2020-03-01
A quick googling on this suggests that you may have av corrupt install of Grub, or some disk mounting problems. Yes, Grub can get confused by even a SDC card mounted somewhere on your system. So there you have two avenues of research. Sorry I can't help you more...

---

### Post by fred66 on 2020-03-04
Thank you. I never did anything to a second HD with a never activated Windows 7  installation, and, following your comment, I tried to access it (I was able to, long time ago, just accessing the directory), but I was greeted with an error message. I'll try to reformat the disk and see if that helps. At least I should end up with extra storage...

---

