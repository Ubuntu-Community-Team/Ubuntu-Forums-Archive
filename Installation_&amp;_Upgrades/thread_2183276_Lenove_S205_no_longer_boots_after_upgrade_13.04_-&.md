---
title: "Lenove S205 no longer boots after upgrade 13.04 -&gt; 13.10"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Holger_Durer on 2013-10-24
Today the upgrade suggestion popped up and I let my ubuntu 13.04 upgrade.  Everything worked without problem it seemed but after the final stage (reboot), the computer no longer comes up.

I used to have an entry "ubuntu" in the "BIOS"'s config section on boot order.  (I say "BIOS" because the Lenovo S205 is of course some early UEFI shitware which always only barely worked with Ubuntu and I don't know the correct name for what the BIOS is now called in this brave new world).

Now the only entries are USB HDD, ATA HDD0, USB FDD USB CD, PCI LAN 

If I boot normally (i.e. without pressing F2 to get into the "BIOS") I only see two options:
[FONT=courier new]1. ADA HDD0: TOSHIBA MK3265GSX
2. PCI LAN: Realtek PXE B02 D00[/FONT]

Selecting 1. just seems to do a normal reboot going back to that selection screen after maybe 2-3 seconds.

So, I guess something in the upgrade (installing the latest kernel?) blew that UEFI boot entry...

Any idea how to get that back?  Do I need to do a new install from USB?

---

### Post by oldfred on 2013-10-25
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Holger_Durer on 2013-10-25
Thanks, oldfred.

The report is at [http://paste.ubuntu.com/6302924/](http://paste.ubuntu.com/6302924/)

---

### Post by Holger_Durer on 2013-10-25
And the link after trying the default repair is [http://paste.ubuntu.com/6302945/](http://paste.ubuntu.com/6302945/)

I will try to reboot now... wish me luck... :-)

---

### Post by Holger_Durer on 2013-10-25
It worked!  After the repair I get a grub menu (I never did before) and it boots.
Thanks so much!

Of course wifi doesn't work any more - it used to do that and I'd have to move the ubuntu entry into second position in the bios boot order section (I know it sounds unbelievable, but it worked reliably).
Now there is no ubuntu entry so nothing to move...
Oh well...

---

### Post by oldfred on 2013-10-25
It looks like a standard UEFI boot with efi partition and Ubuntu root & swap only.

But your UEFI menu is not showing an ubuntu entry which it should. Maybe you have to boot from it once to get it into the menu as saved. See lines 1138 & 1166, which should be what you see in your UEFI menu. Current default is USB - 0004 entry.

You also have multiple kernels and may want to house clean some of those. I have always preferred synaptic, but they do not install that anymore by default

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels 
dpkg --list | grep linux-image

sudo apt-get install synaptic

 In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic
#current install:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)f

---

### Post by Holger_Durer on 2013-10-26
Thanks for all those pointers.

The ubuntu entry so far hasn't come back and my attempts to re-add it have failed.

I cleaned up the kernels and re-ran the boot-repair for good measure ([http://paste.ubuntu.com/6307292/](http://paste.ubuntu.com/6307292/))

Finding [http://askubuntu.com/questions/348269/after-update-ubuntu-12-04-does-no-longer-boot-on-a-uefi-machine](http://askubuntu.com/questions/348269/after-update-ubuntu-12-04-does-no-longer-boot-on-a-uefi-machine) I tried:
[FONT=courier new]$ efibootmgr -c -d /dev/sda -p 1 -l \\EFI\\ubuntu\\grubx64.efi -L ubuntu -v && echo ok || echo fail: $?[/FONT]
[FONT=courier new]fail: 1
[FONT=arial]
But that doesn't do anything (also note the exit failure code).
[/FONT][/FONT][FONT=courier new][FONT=arial]
[/FONT][/FONT][FONT=courier new]$ efibootmgr [/FONT]
[FONT=courier new]BootCurrent: 0003[/FONT]
[FONT=courier new]Timeout: 0 seconds[/FONT]
[FONT=courier new]BootOrder: 0004,0003,0002,0005,0006[/FONT]
[FONT=courier new]Boot0000  Setup[/FONT]
[FONT=courier new]Boot0001  Boot Menu[/FONT]
[FONT=courier new]Boot0002* USB FDD:[/FONT]
[FONT=courier new]Boot0003* ATA HDD0: TOSHIBA MK3265GSX                       [/FONT]
[FONT=courier new]Boot0004* USB HDD:[/FONT]
[FONT=courier new]Boot0005* USB CD:[/FONT]
[FONT=courier new]Boot0006* PCI LAN: Realtek PXE B02 D00[/FONT]

[FONT=courier new][FONT=arial]Any other ideas? Much appreciated.[/FONT]
[/FONT]

---

### Post by oldfred on 2013-10-26
Did you by any chance turn secure boot on? It will only show secure boot systems in boot menu when secure boot is on.

---

### Post by Holger_Durer on 2013-10-31
OK, I marked this thread as solved as my main issue was resolved.

For the record in case other people happen on to this thread:  I did not see anything about secure boot in the bios but just for testing did a boot repair with secure boot set to true.  That made everything break again.

At that point I thought I should try a fresh install as I had always wanted to try the encrypted home dir feature.
But I can report that a regular Ubuntu 13.10 install on a Lenovo S205 fails to bring up a bootable system.  I currently have a very ugly door stop.

---

