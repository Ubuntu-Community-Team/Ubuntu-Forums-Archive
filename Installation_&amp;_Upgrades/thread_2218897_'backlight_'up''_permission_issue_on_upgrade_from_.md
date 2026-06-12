---
title: "'backlight 'up'' permission issue on upgrade from Precise to Trusty"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by david-c on 2014-04-22
The backlight 'up' and 'down' function keys on my Toshiba Satellite now require an admin password everytime I use them. For some reason (which I can't remember) in the distant past, I set it up to use the ctrl-F6 and ctrl-F7 key combinations rather than Fn-F6 and Fn-F7 for their control. Any ideas?

---

### Post by matt_symes on 2014-04-22
Hi

> **david-c said:**
> The backlight 'up' and 'down' function keys on my Toshiba Satellite now require an admin password everytime I use them. For some reason (which I can't remember) in the distant past, I set it up to use the ctrl-F6 and ctrl-F7 key combinations rather than Fn-F6 and Fn-F7 for their control. Any ideas?

Policy kit ?

What is the output of this command from the terminal ?

```
cat /usr/share/polkit-1/actions/org.gnome.settings-daemon.plugins.power.policy
```

Kind regards

---

### Post by david-c on 2014-04-22
```
cat /usr/share/polkit-1/actions/org.gnome.settings-daemon.plugins.power.policy
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>

  

  <vendor>GNOME Settings Daemon</vendor>
  <vendor_url>http://git.gnome.org/browse/gnome-settings-daemon</vendor_url>
  <icon_name>battery</icon_name>

  <action id="org.gnome.settings-daemon.plugins.power.backlight-helper">
    
    <description gettext-domain="gnome-settings-daemon">Modify the laptop brightness</description>
    <message gettext-domain="gnome-settings-daemon">Authentication is required to modify the laptop brightness</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/lib/gnome-settings-daemon/gsd-backlight-helper</annotate>
  </action>
```

---

### Post by matt_symes on 2014-04-22
Hi

That file looks fine to me.

What about the output of this command ?

```
pkaction | grep backlight
```

Kind regards

---

### Post by david-c on 2014-04-22
```
pkaction | grep backlight
com.ubuntu.unity-settings-daemon.plugins.power.backlight-helper
org.gnome.settings-daemon.plugins.power.backlight-helper
```

---

### Post by matt_symes on 2014-04-22
Hi

I see you're using Unity. I'm using Xubuntu so there may be some difference.

We need to look at 

```
com.ubuntu.unity-settings-daemon.plugins.power.backlight-helper
```

Can you post the output of these two commands please.

```
pkaction --action-id com.ubuntu.unity-settings-daemon.plugins.power.backlight-helper --verbose
pkaction --action-id org.gnome.settings-daemon.plugins.power.backlight-helper --verbose
```

Kind regards

---

### Post by david-c on 2014-04-22
```
david@david-laptop:~$ pkaction --action-id com.ubuntu.unity-settings-daemon.plugins.power.backlight-helper --verbose
com.ubuntu.unity-settings-daemon.plugins.power.backlight-helper:
  description:       Modify the laptop brightness
  message:           Authentication is required to modify the laptop brightness
  vendor:            Unity Settings Daemon
  vendor_url:        http://git.gnome.org/browse/gnome-settings-daemon
  icon:              battery
  implicit any:      no
  implicit inactive: no
  implicit active:   yes
  annotation:        org.freedesktop.policykit.exec.path -> /usr/lib/unity-settings-daemon/usd-backlight-helper
```

and

```
david@david-laptop:~$ pkaction --action-id org.gnome.settings-daemon.plugins.power.backlight-helper --verbose
org.gnome.settings-daemon.plugins.power.backlight-helper:
  description:       Modify the laptop brightness
  message:           Authentication is required to modify the laptop brightness
  vendor:            GNOME Settings Daemon
  vendor_url:        http://git.gnome.org/browse/gnome-settings-daemon
  icon:              battery
  implicit any:      no
  implicit inactive: no
  implicit active:   yes
  annotation:        org.freedesktop.policykit.exec.path -> /usr/lib/gnome-settings-daemon/gsd-backlight-helper
```

---

### Post by matt_symes on 2014-04-22
Hi

I can't see much wrong there either.  I am assuming the keys also use {gnome,unity} daemon though. 

Does it require a password if you use the GUI and not the keys ? (I assume you can change th brightness using the GUI. It's been a while since i used Unity).

How did you remap the brightness keys in the first place ?

Out of interest, does this command require the admin password ?

```
pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper  --set-brightness $(( $(pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --get-brightness) / 2))
```

It should cut the screen brightness by half.

Kind regards

---

### Post by david-c on 2014-04-22
Thanks for being patient with me. Now I'm struggling! My knowledge of Ubuntu/Linux is extremely limited and very out of date. I have ADHD which results in my working memory being similar to a goldfish, lol!

>  I am assuming the keys also use {gnome,unity} daemon
Sorry, I have no idea...
> Does it require a password if you use the GUI and not the keys ?
Is there a GUI? Where might I find it?
> How did you remap the brightness keys in the first place ?
I can't remember, but I would have done a lot of Googling and following instructions blindly (I know, its a dangerous method).
> ...does this command require the admin password ?
```
david@david-laptop:~$ pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper  --set-brightness $(( $(pkexec /usr/lib/gnome-settings-daemon/gsd-backlight-helper --get-brightness) / 2))
david@david-laptop:~$
```
It ran silently, with no output whatever.

---

### Post by matt_symes on 2014-04-22
Hi

> It ran silently, with no output whatever.

But did it reduced the screen brightness ?

Kind regards

---

### Post by david-c on 2014-04-22
Sorry,
No brightness change.

---

### Post by matt_symes on 2014-04-22
Hi

> **david-c said:**
> Sorry,
No brightness change.

Hmm. That's a surprise. 

I don't have Unity installed on this laptop and It's been a while since i used it so i'm not sure what changes have happened to it.

I'll have a think tonight and post back tomorrow.

Someone else may also be able to step up and help.

Kind regards

---

### Post by david-c on 2014-04-22
Another observation which may help is that previous to upgrading from 12.04 to 14.04, removing the power cable used to cause the screen to dim. This no longer happens.

Tried this suggestion; [Toshiba Satellite P755-S5269 keyboard backlight doesn't work]("http://askubuntu.com/questions/426163/toshiba-satellite-p755-s5269-keyboard-backlight-doesnt-work"), including running update-grub as root, but this edit made no difference on rebooting the system.

---

### Post by david-c on 2014-04-22
Tried using 'System Settings': 'Brightness & Lock'.
Brightness slider and 'Dim screen to save power' appear to have no affect whatsoever.

Fn-F6 (which is supposed to dim the screen) and Fn-F7 (supposed to brighten screen) both bring up a nice graphic, but fail to change the actual screen brightness.

Searching the Ubuntu Wiki revealed: [DisplayBrightness]("https://wiki.ubuntu.com/Kernel/Debugging/Symptom/DisplayBrightness?highlight=%28brightness%29")
This indicated two possible types of issue. I have initially chosen to explore the second of these, [Kernel/Debugging/Backlight]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight").
Debugging information to provide in my bug report:

Executed at a terminal each of the following in order, with default Ubuntu kernel parameters:

[LIST]
[*]ls /sys/class/backlight
[*]grep -r . /proc/acpi
[*]sudo acpidump -o acpidump.txt
[LIST]
[*]Generated acpidump.txt required by following commands and included as a compressed attachment
[/LIST]
[*]acpixtract acpidump.txt
[LIST]
[*]Generated DSDT.dat, SSDT1.dat, SSDT2.dat, and SSDT3.dat which I bundled together as attachment called acpixtract
[/LIST]
[*]iasl -d dsdt.dat
[LIST]
[*]Generated dsdt.dsl which was huge so compressed and included as an atachment
[/LIST]
[*]sudo fwts > fwts
[LIST]
[*]Generated a large file called 'results.log' which has been compressed and attached - the lcd brightness test successfully dimmed the screen, so a glimmer of hope!
[/LIST]
[*]sudo fwts method > fwts_method
[LIST]
[*]Results appended to 'results.log'
[/LIST]
[*]dmesg | grep 'ACPI: Video' > video
[*]sudo dmidecode > dmidecode.log
[*]cat /proc/version > version
[/LIST]

```
david@david-laptop:~$ ls /sys/class/backlight
intel_backlight  toshiba
```

```
david@david-laptop:~$ grep -r . /proc/acpi
/proc/acpi/toshiba/version:driver:                  0.19
/proc/acpi/toshiba/version:proc_interface:          1
/proc/acpi/toshiba/keys:hotkey_ready:            0
/proc/acpi/toshiba/keys:hotkey:                  0x0000
/proc/acpi/toshiba/lcd:brightness:              7
/proc/acpi/toshiba/lcd:brightness_levels:       8
/proc/acpi/button/lid/LID/state:state:      open
/proc/acpi/wakeup:Device	S-state	  Status   Sysfs node
/proc/acpi/wakeup:USB0	  S3	*enabled   pci:0000:00:1d.0
/proc/acpi/wakeup:USB1	  S3	*enabled   pci:0000:00:1d.1
/proc/acpi/wakeup:USB2	  S3	*enabled   pci:0000:00:1d.2
/proc/acpi/wakeup:EHC1	  S3	*enabled   pci:0000:00:1d.7
/proc/acpi/wakeup:USB3	  S3	*enabled   pci:0000:00:1a.0
/proc/acpi/wakeup:USB4	  S3	*enabled   pci:0000:00:1a.1
/proc/acpi/wakeup:USB5	  S3	*enabled   pci:0000:00:1a.2
/proc/acpi/wakeup:EHC2	  S3	*enabled   pci:0000:00:1a.7
/proc/acpi/wakeup:HDEF	  S3	*disabled  pci:0000:00:1b.0
/proc/acpi/wakeup:PXS2	  S4	*disabled
/proc/acpi/wakeup:RP05	  S4	*disabled  pci:0000:00:1c.4
/proc/acpi/wakeup:PXS5	  S5	*enabled   pci:0000:07:00.0
/proc/acpi/wakeup:LID	  S4	*enabled
```

```
david@david-laptop:~$ dmesg | grep 'ACPI: Video'
[    2.805104] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
```

```
david@david-laptop:~$ cat /proc/version
Linux version 3.13.0-24-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014
```

Lots of information, but not sure what to do with it all as yet. Hope it may be of use.

---

### Post by david-c on 2014-04-23
Continuing to work through the Ubuntu Wiki [Backlight]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight") page.
With the kernel parameter acpi_backlight=vendor :
```
david@david-laptop:~$ ls /sys/class/backlight
intel_backlight  toshiba
```
```
david@david-laptop:~$ ls -la /sys/class/backlight/intel_backlight/
total 0
drwxr-xr-x 3 root root    0 Apr 23 11:52 .
drwxr-xr-x 4 root root    0 Apr 23 11:52 ..
-r--r--r-- 1 root root 4096 Apr 23 12:34 actual_brightness
-rw-r--r-- 1 root root 4096 Apr 23 12:34 bl_power
-rw-r--r-- 1 root root 4096 Apr 23 12:34 brightness
lrwxrwxrwx 1 root root    0 Apr 23 12:34 device -> ../../card0-LVDS-1
-r--r--r-- 1 root root 4096 Apr 23 12:34 max_brightness
drwxr-xr-x 2 root root    0 Apr 23 12:34 power
lrwxrwxrwx 1 root root    0 Apr 23 12:34 subsystem -> ../../../../../../../class/backlight
-r--r--r-- 1 root root 4096 Apr 23 11:52 type
-rw-r--r-- 1 root root 4096 Apr 23 11:52 uevent
```
However,
```
echo 8 > /sys/class/backlight/intel_backlight/brightness
```
caused my laptop to crash. I tested 'echo 8' with a different (random) command (# echo 8 > /proc/sys/kernel/printk) and it did not crash.

---

### Post by david-c on 2014-04-23
Continuing from before, I have now temporarily removed the kernel parameter 'acpi_backlight=vendor' and replaced it with 'video.use_bios_initial_backlight=0':

The result was that the brightness graphic is now fully controlled by the respective function keys, whereas previously the graphic only managed a sinlge unit of brightness reduction. *But*, the actual screen brightness remained the same. The 'Brightness & Lock' gui had no affect on brightness whist adjusting the brightness slider, and/or swapping from mains to battery power.

---

### Post by matt_symes on 2014-04-23
Hi

I see your still trying to fix the issue. 

This looks like more than just an admin/sudo issue implied by the password required for the brightness keys.

For a start, you have 2 modules loaded for the backlight by the looks of it.

Try these two commands.

```
echo 5 | sudo tee /sys/class/backlight/toshiba/brightness
```

```
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Do either of then work and, more importantly, do any of them reduce the back light brightness ?

Try them both with and without the ```
acpi_backlight=vendor
``` kernel command line.

Kind regards

---

### Post by david-c on 2014-04-23
Welcome back matt_symes,

With 'acpi_backlight=vendor'
```
david@david-laptop:~$ echo 5 | sudo tee /sys/class/backlight/toshiba/brightness
5
```

However,
```
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
killed the laptop, or at least the screen.

Without  'acpi_backlight=vendor' I am fully able to control the brightness graphics with the function key, but with no actual change in screen brightness.
```
david@david-laptop:~$ echo 5 | sudo tee /sys/class/backlight/toshiba/brightness
5
```

```
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` killed the session.

I have now permanatly removed the 2 acpi kernel parameters from grub which I had inserted in the hopes of a fix.
I think I am making progress...

---

### Post by david-c on 2014-04-23
The two kernel parameters I have just removed from Grub were 'acpi_osi=linux' and 'acpi_backlight=vendor'. They were inserted based on the recommendation I refered to in #13 of this thread.

---

