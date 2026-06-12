---
title: "Brightness and Volume function(fn) keys not working"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by scibot on 2012-12-22
Hi guys,
Long story short, my brightness and volume function keys don't work (you might already know this).
I've had this problem for quite some time now, with intermittent bursts of trying to fix it, but bearing no results. I'm pretty much a beginner at using ubuntu so I guess there are a lot of basics I don't know. Additionally I'm not a native English speaker, so please be considerate.

I've seen some threads with similar problems, where a third party driver fixed the problem or changing a line in the grub file. This didn't work for me, but I might also have been doing it wrong, I really don't know what I'm doing.

I have an acer aspire one za3, about three or four years old. I'm using ubuntu, but with the lubuntu desktop since the unity environment(I think) was running extremely slow. The volume fn-keys are the up and down arrow keys and the brightness the left and right ones.

If you have an idea for a fix or maybe just a useful link, please don't hesitate to respond.
Thanks.

---

### Post by Toz on 2012-12-23
Hello and welcome to the forums.

Can you give these kernel parameters a try? **acpi_backlight=vendor acpi_osi=Linux**:
[LIST=1]
[*]Open the grub config file for editing
```
gksu gedit /etc/default/grub
```
[*]Add the parameters
Change the line:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor acpi_osi=Linux"
```
[*]Save the file
[*]Update grub
```
sudo update-grub
```
[*]Reboot
[/LIST]
Once rebooted, test the function keys and post back the results of:
```
cat /proc/cmdline
```

If that doesn't work, can you also try **acpi_backlight=vendor acpi_osi=Linux acer_wmi.blacklist=yes** using the same procedure as above.

---

