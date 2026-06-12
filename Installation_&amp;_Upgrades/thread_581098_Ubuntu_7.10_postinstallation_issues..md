---
title: "Ubuntu 7.10 postinstallation issues."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by MoxPooshi on 2007-10-19
Hi, All!
I'm new to Linux and would very much appreciate any help in the following issues:

After completing the fresh install of Gutsy on IBM R40 laptop on the following reboot there's no logo on the screen (after the Grub menu) . The screen goes black, I see a little activity on HDD led, it stays like that for awhile . After 2 mins the LAN adapter gets alive and after 2 more minutes I finally get the login screen, There's also no Logo on shutdown/restart, only a black screen.
I reinstalled the system 3 times already.It's the only OS on my HDD.The same effect with/out enabled wireless/infrared built-in adapters.


Thanks in advance
Best Regards
Dima

---

### Post by Sef on 2007-10-19
It sounds like a problem with your video card.  Could you post what kind you have and your system specs too.  Thank you.

---

### Post by argosreality on 2007-10-19
Sounds like a device or driver is hanging. Check your messages file for any errors or timeouts

---

### Post by MoxPooshi on 2007-10-19
I have an ATI Mobility Radeon 7500(32MB) and in Hardware Information it says that the driver installed currently is Radeon Mobility M7 LW [Radeon Mobility 7500]. It's the same driver that was installed in 7.04 and it worked quite well with no issues.
Other sysinfo:
CPU 1.5Ghz Centrino
512MB RAM



How can I check the messages file /error logs ?

---

### Post by exile on 2007-10-19
You can start by typing the following in the command prompt (Applications -> Accessories -> Terminal)

```
cat /var/log/message | less 
```

For what it's worth I am having exactly the same problem. Haven't found the cause yet though.

A good idea suggested to me was to try bootchart [http://www.bootchart.org/]("http://www.bootchart.org/")

Good luck.

---

### Post by MoxPooshi on 2007-10-19
Well, it's becoming even more interesting. Just after enabling compiz effects (animations and cube) and restarting a laptop got the following message:


<<There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.>>

And after that the default human theme changed dramatically (colors,icons )


Right now I'm comparing 2 message files, but what should I look for? 

Wow, what a day !

---

### Post by dcroxton on 2007-10-19
I had the same problems with the gnome-settings-daemon.  It turned out that it was because my network connection was down.  (Yes, I know that makes no sense, but it seems to be true.)  Once I did

sudo ifdown eth1
sudo ifup eth1

(probably substitute eth0 for your network card), I could then run

gnome-settings-daemon &

(do not run as root) and it worked fine.

Sincerely,
Derek

---

### Post by MoxPooshi on 2007-10-19
Thanks Derek,
The error message is gone, Gnome-settings-daemon is ok.
 But the most annoying part still persists. It takes >4mins to boot to login screen, and there's no Ubuntu Logo on bootup/shutdown.
I've checked the message file for errors. Part of the output is here (the suspicious part IMHO):

Oct 19 16:41:31 Mox exiting on signal 15
((((((((((((((  7 minutes gap ??? )))))))))))
Oct 19 16:48:40 Mox syslogd 1.4.1#21ubuntu3: restart.
Oct 19 16:48:41 Mox kernel: Inspecting /boot/System.map-2.6.22-14-generic
Oct 19 16:48:41 Mox kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Oct 19 16:48:41 Mox kernel: Symbols match kernel version 2.6.22.
Oct 19 16:48:41 Mox kernel: No module symbols loaded - kernel modules not enabled. 
Oct 19 16:48:41 Mox kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Oct 19 16:48:41 Mox kernel: No module symbols loaded - kernel modules not enabled.
Oct 19 16:48:42 Mox kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
Oct 19 16:48:42 Mox kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Oct 19 16:48:42 Mox kernel: [    4.803832] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 19 16:48:42 Mox kernel: [    5.077707] Local APIC not detected. Using dummy APIC emulation.
Oct 19 16:48:42 Mox kernel: [    5.105228] ACPI: ACPI bus type pnp unregistered
Oct 19 16:48:42 Mox kernel: [    5.105233] PnPBIOS: Disabled by ACPI PNP
Oct 19 16:48:42 Mox kernel: [    5.105292] PCI: Using ACPI for IRQ routing
Oct 19 16:48:42 Mox kernel: [    5.105296] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 19 16:48:42 Mox kernel: [    5.111987] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
Oct 19 16:48:42 Mox kernel: [    5.111991] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
Oct 19 16:48:42 Mox kernel: [    5.111994] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
Oct 19 16:48:42 Mox kernel: [    5.111998] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved


It's really annoying :(

---

### Post by MoxPooshi on 2007-10-19
Well, it's solved!
For those who still searches for an answer -

The solution provided by FCUMOK

<<<To fix the no boot splash I did the following:

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

>>>

It did the trick!

Hamsters and Rangers everywhere !!
Rejoice!
Thank to all! The best support ever!
Ubuntu FOREVER!

---

### Post by xylon89del on 2008-03-02
forgive my ignorance in IT

Can someone teach me how can i perform the following steps

1)Change the resolution in /etc/usplash.conf to 1024x768
2)Add vga=791 to the kernel line in /etc/bootmenu.1st
3)sudo update-iniframfs-u-k 'uname-r

---

