---
title: "Problem to reinstall Win XP"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by thecapricorn on 2011-04-17
Hi everyone,

I have erased my Windows partition to install Ubuntu on a partition taking all my hard drive. However, it does not recognise my fan so I would like to do a Dual Boot Windows/Ubuntu.

When I put my Windows XP Installer CD, the following message appear on a blue screen :
[INDENT]> a problem has been detected and windows shut down to prevent damages.
if it is the 1st time, restart. if it happens again :
check for viruses. remove any new hard drive or controllers. check the configuartion of your hard drive. 
run CHKDSK/F to check for hard drive corruption, and then restart.
technical info : 
***STOP : 0x000000&B (0xF78D2524, 0xC0000034,0x00000000, 0x00000000)

[/INDENT]

I have download GParted and formatted my hard drive from a live CD to only have one partition in NTFS, but the same problem appear. I have tried the CD of reparation Win XP, same blue screen with it.

Does anyone has an idea ?

---

### Post by Hedgehog1 on 2011-04-17
Making a new 'MBR' partition map on the hard drive ***should*** solve this. In Gparted do:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]


**Once you get Ubuntu installed again, please do this to resolve the fan issue:**

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by oldfred on 2011-04-17
A NTFS partition has to have the boot flag (active partition in windows) for windows to see it. It also has to be  a primary partition. sda1 thru sda4.

---

### Post by thecapricorn on 2011-04-17
Thanks for this quick answer !
I already have tried an unlocated partition, no more success. But I will give a second shot tomorrow.
I also had already found and tried the modification of grub solution, no success. My fan is still running very fast to automatically stop as soon as my labtop starts to heat.
I am afraid it is a little complicated...

oldfred -> i tried again gparted and i can choose ntfs, but have no more precision about the boot flag. how can i activate this ?

---

### Post by thecapricorn on 2011-04-19
So I kind of resolved my problem by switching from "RAID Auto/AHCI" to "RAID Auto/ATA" in the SATA operations.

However, I had loads of trouble during the installation of Windows : stop during the installation needing to restart the computer in the middle, now it is rather slow and does not have many functionality.

I still have re installed Ubuntu in Dual Boot but no change for my fan... Which work under WIndows. Was it stupid to think that a Dual Boot would change that ?

Thanks for your help :)

---

### Post by oldfred on 2011-04-19
Unless you are running RAID, you do not want RAID setttings in BIOS. Also that usually writes hidden meta data to a drive that interferes with an install.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Some comments by others on BIOS settings. 

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

You may need a parameter set while booting to resolve fan. Nomodeset is video, but other parameters may work for other issues.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by thecapricorn on 2011-04-30
i am focusing on this fan problem now.

nomodoset  did not do any change, i have read the second link but did not find anything that would allow to detect the fan.

i think ubuntu does not detect it as i tried to un fancontrol and the command 
[HTML]sudo pwmconfig[/HTML]
gave
[HTML]    /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed [/HTML]

i don't have more idea of how to detect it...

---

