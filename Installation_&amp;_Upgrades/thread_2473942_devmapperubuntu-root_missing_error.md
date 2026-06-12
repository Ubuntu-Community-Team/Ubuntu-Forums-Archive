---
title: "/dev/mapper/ubuntu-root missing error"
date: 2022-04-19
forum: Installation &amp; Upgrades
---

### Post by w-kym-wittal on 2022-04-19
Using Ubuntu 18.04.6 LTS server version.  Not sure how I managed to do this (was adding packages prior to reboot, although that all seemed normal), when I reboot, I end up with the following:

ALERT! /dev/mapper/ubuntu-root does not exist.  Dropping down to shell.

I then have the initramfs shell to use.  I have been looking around but, so far no success.

Can someone point me in the right direction to begin to address this error?

Thanks, Kym.

---

### Post by CharlesA on 2022-04-19
Hi,

You should boot off a livecd and run this tool and post a link to the results:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by w-kym-wittal on 2022-04-19
> **CharlesA said:**
> Hi,

You should boot off a livecd and run this tool and post a link to the results:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


As requested, the Boot-Repair information is at link:
[http://paste.ubuntu.com/p/c8DNfxxQjK/]("https://paste.ubuntu.com/p/c8DNfxxQjK/")

Thanks, Kym.

---

### Post by CharlesA on 2022-04-20
The partitions look good and boot repair suggests trying t reinstall grub. Let it do that and see if the root file system is detected.

---

### Post by w-kym-wittal on 2022-04-20
> **CharlesA said:**
> The partitions look good and boot repair suggests trying t reinstall grub. Let it do that and see if the root file system is detected.

Significant success.  The Boot-Repair upload file after the repair is at [http://paste.ubuntu.com/p/vXmQFQsRxQ/](http://paste.ubuntu.com/p/vXmQFQsRxQ/)

The machine boots, goes past Ubuntu splash screen, seems to load everything, but will not display login graphics on the local terminal.  The first reboot after the Boot-Repair, the screen flashed on and off, last entry showing "Started User Mgr for UID 116".  The second reboot shows a blank screen only.  The good news is I can CTRL-ALT-F2 to get to a local terminal screen and I can access remotely. Everything seems to be there and I can access the drives, etc.

I am going to attempt to view log files to see what might have gone wrong with the display issue.  Are you aware of what I should be looking for or any advice as to where to look?

Thanks again for the assistance thus far.  Kym.

UPDATE:  The last line of the boot.log file is "Started GNOME Display Manager".  When I check the status of the GDM, it is running, but has child process errors. I am thinking it might make sense to purge "ubuntu-gnome-desktop" (is gdm3 the same??) and re-install it.  Any thoughts?

2nd UPDATE: Unfortunately I will be away for 4 weeks now, so unable to try things.  I will monitor this thread and re-start when I get back.  Thanks, Kym.

---

### Post by w-kym-wittal on 2022-05-26
To update and close this off:

1.  Updated system via terminal, rebooted and the graphical interface appeared again (not sure what caused this to occur??)
2.  All looks in place, everything seems to be working.


Since this appears to be back to 'normal', thank you for your assistance, Kym.

---

