---
title: "Updating friendly recovery"
date: 2021-02-18
forum: Installation &amp; Upgrades
---

### Post by tmichaelmcn on 2021-02-18
While updating Ubuntu 20.04 this morning, the update seems to have stopped while "updating friendly-recovery."  There has been no progress for at least an hour.  The last seven lines of the update show:

Setting up friendly-recovery (0.2.4lubuntu0.20.04.1)
Sourcing file `/etc/default/grub
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image:  /boot/vmlinuz-5.4.0-65-generic
Found initrd image:  /boot/initrd.img-5.4.0-65
Found memtest86+ image:  /boot/memtest86+.elf
Found memtest86+ image:  /boot/memtest86+.bin

The cancel button is greyed out.  How can I get out of this?

---

### Post by schragge on 2021-02-18
[postinst script]("https://wiki.debian.org/MaintainerScripts") for **friendly-recovery** first runs [update-grub]("https://manpages.debian.org/unstable/grub-legacy/update-grub.8.en.html") to..., well, to update GRUB, and then [systemctl]("https://manpages.debian.org/unstable/systemctl/systemctl.1.en.html") and [deb-systemd-invoke]("https://manpages.debian.org/unstable/init-system-helpers/deb-systemd-invoke.1p.en.html") to  reload the service. Check what command it got stuck at:
```
ps -ef|egrep '[u]pdate-grub|[s]ystemctl|[d]eb-systemd-invoke'
```

---

### Post by tmichaelmcn on 2021-02-18
Here's the output:  

```
tmichael    7449    7434  0 10:47 pts/3    00:00:00 grep -E --color=auto update-
grub|systemctl|deb-systemd-invoke
```

---

### Post by deadflowr on 2021-02-18
The point it has stopped at is grub's os-prober.
This is where grub probes for any other Operating Systems on the machine.
Which begs the question do you or have you had any other operating system on the machine?

---

### Post by ActionParsnip on 2021-02-18
If you use the terminal, is it OK. Rules out the GUI having a bad time

---

### Post by tmichaelmcn on 2021-02-18
Windows 7 is installed on the same hard drive as the boot sector.  Ubuntu runs on a second hard drive.

---

### Post by tmichaelmcn on 2021-02-18
I just re-started, and the computer will no longer boot to Windows.  And whenever I try to run software updater it indicates that it is still trying to update friendly-recovery.  How can I get it to exit this process?  As things stand, I can no longer update the software on my Ubuntu 20.04 system.

---

### Post by grahammechanical on 2021-02-18
Try

```
sudo update-grub
```

And see if that get you loading Windows. To update through the terminal

```
sudo apt update
sudo apt upgrade
```

See if that bypasses Software Updater.

Regards

---

### Post by tmichaelmcn on 2021-02-18
Thanks for your suggestions.  Unfortunately, sudo-update grub gets the same response as in my original post.  sudo apt update just gets me a list:  [FONT=monospace][COLOR=#000000]"3 packages can be upgraded. Run 'apt list --upgradable' to see them."  sudo apt upgrade shows the error message [/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]"Could not get lock /var/lib/dpkg/lock-frontend."[/COLOR]
[/FONT][/COLOR][/FONT]

---

### Post by deadflowr on 2021-02-18
/var/lib/dpkg/lock-frontend means you have a running apt somewhere, it usually means a gui like the software updater or synaptic.
You can clear it by usually running
```
sudo rm /var/lib/dpkg/lock*
sudo dpkg --configure -a
```

But I feel you might need to run some checks first.
Otherwise you risk running into the same issue over and over again.

If you have the Ubuntu installer you can us it to run boot repair:
see [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
You can try running the boot summary from the live session and post the paste link it provides.
It might reveal information about what's going on with the Windows side of things.

---

### Post by tmichaelmcn on 2021-02-19
Thanks so much for your suggestions.  I'll have some time tomorrow to check them out.

---

### Post by tmichaelmcn on 2021-02-20
I'm not sure what did it, but the problem is resolved.  Boot Repair got hung up on "Scanning systems (BIOS sessions)."  I shut it down after a half hour.  I then ran 
sudo fuser -cuk /var/lib/dpkg/lock
sudo rm -f /var/lib/dpkg/lock
as recommended on [https://omgfoss.com/fix-broken-packages-ubuntu-20-04-lts/](https://omgfoss.com/fix-broken-packages-ubuntu-20-04-lts/)
The former logged me out of my session.  I logged back in and ran the latter.  I then launched Software Updater, and it completed the install that had stalled and finished normally.  Thanks to all for the suggestions.

---

### Post by deadflowr on 2021-02-20
Can you boot into Windows?
Just to make sure all is copacetic.

---

### Post by tmichaelmcn on 2021-02-20
Actually, I can't (I didn't discover that until after I closed the thread).  No login screen for grub appears.  It just loads Ubuntu.  But it is Windows 7, and I will never use it again, so that's no really an issue for me.

---

### Post by deadflowr on 2021-02-20
If you don't use or need windows 7 then you should either remove it from the disk it's on, 
or you can disable the os-probing in grub  so that it never tries to even look for it.

To disable os-prober:
```
sudo chmod -x /etc/grub.d/30_os-prober
```
the chmod sets file permissions and the -x means to remove executable function, which will render the os-probing off.
This should prevent it from ever hanging on that part again.

---

### Post by tmichaelmcn on 2021-02-20
Thanks, I'll do that.

---

