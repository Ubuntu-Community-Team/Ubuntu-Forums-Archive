---
title: "Hardy Fresh Install Trouble"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by victor9098 on 2008-04-26
Hi all,

I have been trying to do a clean install of Hardy but keep getting the same problem. I have download direct from Ubuntu and the torrent. Have checked md5sum and tested the cd before trying to install. Everything comes up with no errors. But when I hit install Ubuntu or even try to use the Live CD the "loading linux kernal" come up, goes to 100% then I get the following on the next screen:

[   46.035183] ACPI:EC:acpi-ec-wait timeout, status=0, expect_event=1
[   46.03520] ACPI:EC:read timeout, command=128

I have tried several times and keep getting the same error. I am currently trying to upgrade (have a slow connection so I downloaded the full versions at work!).

Any advice??

---

### Post by Pumalite on 2008-04-26
Try the Alternate CD. You might have a bad burn. Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 43x or less on CD-R, check CD integrity before install. Clean the lens in your burner. If after all this you continue having problems, we'll try some boot parameters.

---

### Post by victor9098 on 2008-04-26
The CD's were good, I followed the guides and did all the checks. I installed Fiesty & Gutsy the same way and never saw that screen.

At home will take me about 10-12 hours to download the Alternate CD, while there is 7 hours left to my Upgrade.

Will post an update after the upgrade

Thank you!

---

### Post by victor9098 on 2008-04-26
Update!

Good news is that I managed to get the Hardy Upgrade downloaded. Everything went to plan then I restarted...

Bad news is that computer would not restart. Instead I got the following error:

[   20.5595141] ACPI:EC:acpi-ec-wait timeout, status=0, expect_event=1
[   20.55956] ACPI:EC:read timeout, command=128

So I turned off laptop. Unplugged everything (ext hd, usb modem) then tried again, the following error appeared:

[   16.021266] ACPI:EC:acpi-ec-wait timeout, status=0, expect_event=1
[   16.021313] ACPI:EC:read timeout, command=128

So I turned off again. Inserted my Gutsy CD and reinstalled. Have just finished getting up the updates and put in my 'Home' backup and now I am getting an error at log in that the user does not have permission to save to the .dmrc file???????

Now I am starting to pull my hair out. Both Fiesty and Gutsy went flawlessly and I have followed the EXACT same procedure and carried out all the checks as the guides say.

Any thoughts or advice would be very welcome!

---

### Post by victor9098 on 2008-04-26
Reported as a bug!

[https://bugs.launchpad.net/ubuntu/+bug/222864](https://bugs.launchpad.net/ubuntu/+bug/222864)

---

### Post by alek01 on 2008-04-26
Hi,
I've been running the last 3 Ubuntu versions without PB. I did the UPGRADE, which took all night eventhough I have fiber optic and now when I try to boot Ubuntu I get the same message that you do:
[ 20.5595141] ACPI:EC:acpi-ec-wait timeout, status=0, expect_event=1
[ 20.55956] ACPI:EC:read timeout, command=128
Except I get different numbers.
I cannot access the PC at all now. Did you get an answer from the bug report?
Thank you,
Alek

---

### Post by mathenge on 2008-04-26
Try booting the live-cd with ACPI off.

At the boot prompt, press ESC and type:

       acpi=off

Or

       noapic

See how far you get.

---

### Post by victor9098 on 2008-04-26
It is 4.30am (at my location) so giving up to sleep now!

I have just got a response from launchpad suggesting to turn off the ACPI and follow the following:

[https://help.ubuntu.com/community/BootOptions#head-fd6993472b20e64d715ae8f44a496dc2cf9f7cbd](https://help.ubuntu.com/community/BootOptions#head-fd6993472b20e64d715ae8f44a496dc2cf9f7cbd)

Will get back to this later!

Thanks again for the help

---

### Post by alek01 on 2008-04-27
Using the GRUB I have successfully booted on "Safe mode"( I'm using it for this post). But I cannot access my NTFS partition, my Bluetooth mouse does connect and Windows networking (Samba) is not working. Plus everything is very slow.
The system doesn't work when I try to boot in "normal" mode.

---

### Post by Pumalite on 2008-04-27
Check concordance between 'blkid' 'menu.lst' and 'fstab' when it comes to UUID's

---

### Post by alek01 on 2008-04-28
Thank you for the link
I have set PCI=ACPI and I can now access the NTFS partition. There must be an error in my Samba cnfiguration because the Network Grou appear OK with the name of the computers on the network but when I clik on them it says "connection failed". I have solved the bluetooth mouse issue with "sudo hidd --connect IP address"
But I still need to boot in "Recovery mode", otherwise I get the "ACPI:EC:acpi-ec-wait timeout, status=0, expect_event=1 etc..." message.
But, at least I can use my machine.

Thanks again,

Alek

---

### Post by victor9098 on 2008-05-03
Found the time to do another fresh install.

After getting to the boot screen I followed the instructions (hit F6, added acpi=off, then enter). Hardy booted to Live CD. Installed with the guide. Partitioning I choose manual, Hardy had already detected my root, home, swap partitions...installed.

Writing this from Hardy Heron now...except none of my sound is working, I have this constant 'echo' effect coming from my speakers! Looks like a few more tweaks are needed to fix this release. Hopefully that is the last of my problems to solve though.

---

