---
title: "Acer Aspire E15, install failure"
date: 2014-11-16
forum: Installation &amp; Upgrades
---

### Post by dave156 on 2014-11-16
I have an Acer aspire E15 start which had Windows 8.1 initially installed. I attempted to install ubuntu 14.04 on it. After successfully booting using a USB drive, I attempted to install. After the request to restart, I got the message 'No bootable device found.' I attempted a re-install, that didn't change the story. However, once I got that, I can no longer boot from the USB at all, I get this bizarre error: 'Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Config.pm line 22'. I tried the boot-repair, which gave me a menu the very first time, and now doesn't work at all. I'm stuck. I can't even boot the damn thing anymore. Is there something I missed in the initial installation? Is there any any way to correct the mess?

---

### Post by nikwen on 2015-01-13
I know I am a bit late but I just had a similar problem myself, installing Ubuntu 14.10 on an Acer Aspire E15, when I stumbled across your post.
I felt like sharing the solution I found might help someone else who has the same issue in the future.

After finishing the installation, the first thing you should do is boot from the live disk again, open GParted from the dash and set the boot flag for the /dev/sda1 partition.
Next, boot into your BIOS by pressing F2 on the VAIO startup screen, go to the security tab and set a supervisor password. Remember this password, as you will need it whenever you want to open the BIOS in the future.
Then select the entry labelled "Select an UEFI file as trusted for execution" and press enter. On the following screens select "HDD0" (which is your internal hard drive), "<EFI>", "<ubuntu>", "shimx64.efi" and confirm it by entering a boot description (e.g. "shim").
Now reboot and your computer should start successfully. :)

When booting up Ubuntu 14.10, you will, however, probably notice that WIFI does not work. Run the following commands to fix this:

```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

NOTE: In order to be able to run this command, you will need to connect your laptop to the network using a LAN cable once. After the command has run, WIFI should be working properly.

Sources:
[http://ubuntuforums.org/showthread.php?t=1967515&p=11882998#post11882998](http://ubuntuforums.org/showthread.php?t=1967515&p=11882998#post11882998)
[http://youtu.be/iD3JtoSbfOo](http://youtu.be/iD3JtoSbfOo)

---

