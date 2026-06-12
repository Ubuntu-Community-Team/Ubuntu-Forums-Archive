---
title: "how to change file after install for first time with acpi=off command?"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by ihopvix on 2012-08-12
I just installed ubuntu for the first time on an unformated hard drive.  It wouldn't work just selecting 'start or install ubuntu' so I used the acpi=off command.  Now supposedly i need to change a file now.  Which file do I change and how?

---

### Post by drs305 on 2012-08-12
You might make sure your system, once installed, is going to work properly if you boot without that option. 

At the Grub menu (hold down the SHIFT key during boot if it doesn't appear), highlight the top entry and press 'e' to edit the entry. Cursor to the 'linux' line if "acpi=off" appears there and use the backspace key to remove it. Then CTRL-x or F10 to boot.

If it boots and runs properly, see if the command is set in the Grub 2 configuration file:
```

grep "acpi" /etc/default/grub
```

If you find the setting in the line containing "GRUB_CMDLINE_LINUX_DEFAULT=" you will need to edit the file as root:
```
gksu gedit /etc/default/grub
```
Remove "acpi=off", then save the file and run:
```
sudo update-grub
```

---

