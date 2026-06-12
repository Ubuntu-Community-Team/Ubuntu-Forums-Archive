---
title: "suspend works, resume on usb does not"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by ederopaa on 2012-04-29
I upgraded two almost identical systems:
ubuntu 11.10 -> ubuntu 12.04
mythbuntu 11.10 -> mythbuntu 12.04

On both I had suspend/wake on usb working in 11.10. The prior on wireless mouse/keyboard and the latter on a usb ir/mce remote.

Now after the upgrade wake on usb does not work. I have to wake things up with the power button. The light on my ir receiver does not flash either.

The original settings in the /etc/rc.local have not changed:



```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo sh -c "echo USB0 > /proc/acpi/wakeup"
sudo sh -c "echo USB1 > /proc/acpi/wakeup"
sudo sh -c "echo USB2 > /proc/acpi/wakeup"
sudo sh -c "echo USB3 > /proc/acpi/wakeup"
sudo sh -c "echo enabled > /sys/bus/usb/devices/3-1/power/wakeup"

exit 0

```

lsusb gives

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 003 Device 003: ID 195d:7777 Itron Technology iONE Scorpius wireless keyboard
```

cat /proc/acpi/wakeup gives:

```
Device	S-state	  Status   Sysfs node
P0P1	  S4	*disabled  pci:0000:00:1e.0
P0P4	  S4	*disabled  pci:0000:00:1c.0
P0P5	  S4	*disabled  pci:0000:00:1c.1
P0P6	  S4	*disabled  pci:0000:00:1c.2
P0P7	  S4	*disabled  
P0P8	  S4	*disabled  
P0P9	  S4	*disabled  
USB0	  S3	*enabled   pci:0000:00:1d.0
USB1	  S3	*enabled   pci:0000:00:1d.1
USB2	  S3	*enabled   pci:0000:00:1d.2
USB3	  S3	*enabled   pci:0000:00:1d.3
EUSB	  S3	*enabled   pci:0000:00:1d.7

```

Any ideas how to get things working?

---

### Post by pammo on 2012-04-29
You are not alone. 
I don't really understand the wakeup systems (12.04 or prior) but was using a similar script that checks the USB device for my keyboard and enables it if it was disabled. initially this script looked like it was failing to update /proc/acpi/wakeup but when I poked a little more I also noted that most of the devices in /proc/acpi/wakeup were now enabled by default instead of disabled. so I wonder if there is now setting(s) elsewhere that prevent wakeup from working.

I'll poke back here in the next couple days when I have more time to invest.

---

### Post by pammo on 2012-04-29
just glanced through your info again... I noted that you are updating a wakeup in path /sys/bus/usb/devices/*/power/wakeup
mine is "disabled" ATM  
I will play with that when I get a chance ... thanks

---

### Post by ederopaa on 2012-04-30
> **pammo said:**
> just glanced through your info again... I noted that you are updating a wakeup in path /sys/bus/usb/devices/*/power/wakeup
mine is "disabled" ATM  
I will play with that when I get a chance ... thanks

Hey pammo, I have understood that you are supposed to enable the wakeup...but who knows. Let's hope there is a easy and fast solution to this.

---

### Post by ederopaa on 2012-05-03
Got it to work by Googeling and error.

**On my Ubuntu and Wireless keyboard/mouse setup:**

Created a new rule:

```
$ sudo gedit /etc/udev/rules.d/90-keyboardwakeup.rules
```

Entered this in with the correct product and vendor id's (with the help of lsusb):

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52e" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"

```

After a reboot it worked.

**On my Mythbuntu and MCE remote setup:**

Created a new rule:

```
$ sudo gedit /etc/udev/rules.d/90-mcewakeup.rules
```

Entered this in with the correct product and vendor id's (with the help of lsusb):

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0815" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"

```

Edited one line in my grub (added "usbcore.autosuspend=-1 acpi_enforce_resources=lax"):

```
sudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1 acpi_enforce_resources=lax"
```

Then:

```
sudo update-grub
```

Then after a reboot tested it and it worked.

I don't know why the MCE needed the grub line?

---

### Post by jingo_man on 2012-05-04
Just upgraded from 11.10 to 12.04 in-line.

Contents of the /etc/rc.local are the same as before the upgrade:

```
echo US15 > /proc/acpi/wakeup
echo enabled > /sys/bus/usb/devices/4-3/power/wakeup
```

But unable to wake from USB.

Checking the 2 files I am editing, the /sys/usb/...../wakeup contents is "enabled".
The /proc/acpi/wakeup contents for US15 is "*disabled"

I can manually run the other to enable it, prefixing with a "sudo sh -c...." to the command.

I edited the contents to the following, but no further progress:

```
sudo sh -c "echo US15 > /proc/acpi/wakeup"
sudo sh -c 'echo "US15" > /proc/acpi/wakeup'
```

Can anyone suggest alterations that might be needed? Or how to trap further errors that are happening?

I thought that /etc/rc.local would be being executed as root on startup, so I should not need to elevate with the "sudo" call.

I know this file is being executed, as I commented out the 2nd line, and on reboot, the /sys/usb/..../wakeup file shows as "disabled"


Many thanks

---

### Post by ederopaa on 2012-05-04
jingo_man,

From your /etc/rc.local try to comment out the first line:

```
#echo US15 > /proc/acpi/wakeup
echo enabled > /sys/bus/usb/devices/4-3/power/wakeup

```

Then check you devices vendor and product id's with

```
$lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:09a5 Logitech, Inc. Quickcam 3000 For Business
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
``` 

and create a new rule with

```
$ sudo gedit /etc/udev/rules.d/90-keyboardwakeup.rules
```

to insert them in the file. In my case 046d and c52e:

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52e" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
```

reboot and try it.

---

### Post by jingo_man on 2012-05-05
@ederopaa

thanks, that worked like a charm, when i plugged in the values for my MCE receiver device.

have they deprecated the older method? why the change to this style?

---

### Post by SAM0 on 2012-05-06
cheers, great post.

---

### Post by fatski on 2012-05-14
CHeers for this solution man.

I wonder why they made it so much harder.

Be nice if this was configurable through power settings to be honest, it's got to be a good thing to have for a lot of people with HTPC's or wireless keyboards / mice.

---

### Post by Andrew James Collett on 2012-05-15
Agree with fatski. i had a long night trying to figure this out, and now its solved. thank you!!

---

### Post by sparhawkthesecond on 2012-05-15
Thank you! This worked great for me! If people are interested in troubleshooting a little more, I've put more details in [this post]("http://ubuntuforums.org/showthread.php?p=11940008#post11940008&postcount=5"), including manually toggling the enabled state without udev.

Your solution works great for my USB keyboard and mouse, but I'm still having trouble getting my laptop's internal keyboard or  trackpad to wake the computer. I'm not sure that it's considered a USB device, but I did some troubleshooting. Firstly, I tried ```
$ find /sys/devices/ -name wakeup
```Then (ignoring the "/sys/devices/platform/serial8250/tty/*" entries) I manually toggled all of the 18 disabled wakup files to enabled. None of them fixed the problem for me... Would anyone know if there's another wakeup file to find, or something else?

---

### Post by illumilore on 2012-05-20
I am confused. Why do the "#echo  USB2 >> /proc/acpi/wakeup" lines in rc.local not only no longer work, but if not commented out cause the /proc/acpi/wakeup devices to be disabled (assuming the 90.mcewakeuprules file is in place)?

---

### Post by sparhawkthesecond on 2012-06-15
Has anyone else found that a recent upgrade has broken this workaround? I presume it's the kernel upgrade to 3.2.0-25.

Since this upgrade, I cannot get my computer to suspend at all. I have a udev rule as described in this thread to allow my mouse to wake up the computer. If I attempt to suspend, the computer immediately wakes back up. I removed the udev rule (or rebooted the computer without the mouse plugged in) and I can suspend fine.

Oddly enough, if I manually alter the wakeup file instead (as per my post [here]("http://ubuntuforums.org/showthread.php?p=11940008#post11940008&postcount=5")), e.g. with```
$ sudo su
# echo enabled > /sys/bus/usb/devices/3-1.3/power/wakeup
```I can suspend fine, but the moues no longer wakes the computer up anyway.

---

### Post by ederopaa on 2012-06-20
> **sparhawkthesecond said:**
> can suspend fine, but the moues no longer wakes the computer up anyway.

What happens with wake up if you:

```
sudo update-grub
``` 

(and maybe a reboot)?

---

### Post by sparhawkthesecond on 2012-06-20
> **ederopaa said:**
> What happens with wake up if you:

```
sudo update-grub
```(and maybe a reboot)?

Fantastic! I did both steps, and that seems to have fixed it. Thank you for your help.

I do find it odd that this was necessary though. Do you always manually update grub after a kernel update?

Cheers.

---

### Post by ederopaa on 2012-06-21
> **sparhawkthesecond said:**
>  Do you always manually update grub after a kernel update?


No, not really. But lately I've had to do this (and fool around with the other stuff in this thread) in order to get suspend/resume to work. Maybe its a bug or maybe it is a feature? ;) So far this has been a question of trial and error for me. I thought of writing up some experiences because I know I'm not alone...I'm just a regular MythTV user.

---

### Post by sparhawkthesecond on 2012-06-21
Ah okay. Thanks for sharing your advice. Something to keep in mind I guess.

Cheers.

---

### Post by derekr05 on 2012-07-18
You are god



:guitar:

> **ederopaa said:**
> jingo_man,

From your /etc/rc.local try to comment out the first line:

```
#echo US15 > /proc/acpi/wakeup
echo enabled > /sys/bus/usb/devices/4-3/power/wakeup

```

Then check you devices vendor and product id's with

```
$lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:09a5 Logitech, Inc. Quickcam 3000 For Business
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
``` 

and create a new rule with

```
$ sudo gedit /etc/udev/rules.d/90-keyboardwakeup.rules
```

to insert them in the file. In my case 046d and c52e:

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52e" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
```

reboot and try it.

---

### Post by bilboubu on 2012-07-24
Thanks!!

---

### Post by uomiarz on 2012-08-14
THX !
Adding new rule worked great.
Always something new with Ubuntu :)

Remote reciver
```
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
```

and a rule
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0471", ATTRS{idProduct}=="0815" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
```

---

### Post by jonnybignote on 2012-11-07
Hey - is any of this approach good for 12.04 machine that freezes on either suspend or resume?  It ofter manages it one, but from then on it will crash.

I'm assuming my issue is more along the lines of unloading kernel modules that are conflicting, but in any case, its driving me nuts to have to leave on my eexpensive noisy combined fe/be to reecord scheduled items.  Was working fine in 10.04 and 11.04...about 3 days on it so far..sigh

---

### Post by KingOfTheNothing on 2013-06-03
Hi all!

I am using 13.04 but this method does not work for me.

Here are my details.


johan@johan-asus:~$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
P0P1      S4    *disabled
PEG0      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
XHC1      S3    *enabled   pci:0000:00:14.0
EHC1      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *disabled
USB2      S3    *disabled
USB3      S3    *disabled
USB4      S3    *disabled
EHC2      S3    *enabled   pci:0000:00:1a.0
USB5      S3    *disabled
USB6      S3    *disabled
USB7      S3    *disabled
HDEF      S4    *disabled  pci:0000:00:1b.0
RP05      S4    *disabled
RP06      S4    *disabled
RP07      S4    *disabled
RP08      S4    *disabled
WLAN      S3    *disabled  pci:0000:02:00.0
RP03      S4    *disabled
XHCI      S3    *disabled
RP04      S4    *disabled  pci:0000:00:1c.3
GLAN      S4    *enabled   pci:0000:03:00.2
XHC      S4    *disabled
SLPB      S4    *disabled


johan@johan-asus:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
johan@johan-asus:~$ 


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo "enabled" > /sys/bus/usb/devices/usb/4-3/power/wakeup
exit 0

(not sure if usb/4-3 is correct how can I verfy this?


I have created this rule

johan@johan-asus:~$ sudo gedit /etc/udev/rules.d/90-keyboardwakeup.rules
[sudo] password for johan: 


SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52b" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"




GRUB
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1 acpi_enforce_resources=lax"








Many thanks in advance anyone who solves this I can pay 50 $ on paypal! Thanks!

---

### Post by clueo8 on 2013-07-11
You have double entries of GRUB_CMDLINE_LINUX_DEFAULT in your grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and at the bottom

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1 acpi_enforce_resources=lax"

You should just update the top one to have usbcore.autosuspend=-1 acpi_enforce_resources=lax and remove the bottom one and then run sudo update-grub after.  Then reboot.

---

### Post by matt06 on 2013-07-11
Thanks to ederopaa.  I upgraded one of my frontends (Revo) to 12.04 and tried everything under the sun to get resume to work.  I didn't have to modify grub, just added the new rule for my mceusb reciever device ids.

Edit:  Interestingly, lsusb shows my device at bus 004-device 002, but I had to use 4-1 in my rc.local.

lsusb:
> Bus 004 Device 002: ID 1784:0001 TopSeed Technology Corp. eHome Infrared Transceiver

rc.local:
> echo enabled > /sys/bus/usb/devices/4-1/power/wakeup

---

### Post by gnomicon on 2013-10-11
Damn it was working before ubuntu 12.04 LTS and i had to use wake on lan from my phone until bored today (LTS = Long Term S... ?) 

This in rc.local is fine for me:
```
for f in /sys/bus/usb/devices/usb*/power/wakeup ; do echo enabled > $f ; done
```

Thanks to [http://askubuntu.com/questions/129148/resume-from-suspend-with-mce-remote-doesnt-work-after-mythbuntu-upgrade](http://askubuntu.com/questions/129148/resume-from-suspend-with-mce-remote-doesnt-work-after-mythbuntu-upgrade)

---

### Post by humpty88 on 2013-11-17
Just some observations.
Apparently the /proc/acpi/wakeup method doesn't work anymore. Mine doesn't even accept any USBs, just UHC1s, ECHs EXPs and AZAL.

The new (more succesful) methods seem to be toggling all the wakeup files that can be found in the device trees that are either vendor / usb related.
This is easier than hunting down the wakeup files yourself.
e.g
/sys/bus/usb/devices/usb2/power/wakeup	   (bus?)
/sys/bus/usb/devices/usb2/2-1/power/wakeup	   (port?)
/sys/bus/usb/devices/usb2/2-1/2-1.1/power/wakeup   (keyboard - the only value that sticks after reboot)
/sys/bus/usb/devices/usb2/2-1/2-1.2/power/wakeup   (mouse click) 

..are all wakeup files.
Somehow, some of them keep resetting back to 'disabled' after reboot. Which is why the need for rc.local or the vendor-rule method.

I'm not sure what the connection with grub is (don't use grub myself). I managed to get a solution with just rc.local with just the four paths.

---

### Post by test0r284 on 2013-11-23
> **ederopaa said:**
> jingo_man,

From your /etc/rc.local try to comment out the first line:

```
#echo US15 > /proc/acpi/wakeup
echo enabled > /sys/bus/usb/devices/4-3/power/wakeup

```

Then check you devices vendor and product id's with

```
$lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046d:09a5 Logitech, Inc. Quickcam 3000 For Business
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
``` 

and create a new rule with

```
$ sudo gedit /etc/udev/rules.d/90-keyboardwakeup.rules
```

to insert them in the file. In my case 046d and c52e:

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c52e" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup'"
```

reboot and try it.

Hi all,

this works great for my k400 and ubuntu 13.10 but now i get another issue.
if i use the method above i can wake up the pc with my keyboard but after the boot is done (and also several minutes after) my k400 wont work.
if i dont use the method above i cant ofcourse wake up my pc with usb but if i wake it up with the power button then my k400 works fine.

sometimes i have to reinsert the dongle, sometimes i have to reinsert it to a different usb port (front to back).

[FONT=arial]another forum suggested to insert 
```

sleep 2
modprobe -r hid_logitech_dj
sleep 2
modprobe hid_logitech_dj
```[/FONT][COLOR=#8B8B8B][FONT=Monaco]
[/FONT][/COLOR]
[http://www.raspberrypi.org/phpBB3/viewtopic.php?f=46&t=18139](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=46&t=18139)

this did not help anything at all. i also inserted a sleep 20 ... did not work.

does anyone else has this issue or solved this? have i done anything wrong? i also inserted the grub cmd lines but that didnt do the trick either.
hope you can help me.

---

### Post by ederopaa on 2014-02-16
I had to return to this subject once again, since my resume stopped working. Still running a Mythbuntu 12.04 on my frontend with Mythtv 0.27.

The good news is I found a really good solution to my problems. Thanks to Nicolas Bernaerts!

[http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid](http://bernaerts.dyndns.org/linux/74-ubuntu/220-ubuntu-resume-usb-hid)

Before following the instructions I removed my /etc/udev/rules.d/90-mcewakeup.rules -file

```
sudo rm /etc/udev/rules.d/90-mcewakeup.rules
```

and disabled the following wakeup line from /etc/rc.local:

```
#sudo sh -c "echo enabled > /sys/bus/usb/devices/3-1/power/wakeup"
```

and the did a 

```
sudo update-grub
```

and a reboot.

Then I followed the instructions by Nicolas Bernaerts.

---

