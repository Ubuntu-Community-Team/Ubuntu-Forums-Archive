---
title: "How to install Ubuntu in a &quot;secret&quot; partition and only access it using the POST menu?"
date: 2020-02-24
forum: Installation &amp; Upgrades
---

### Post by moraisu on 2020-02-24
I am going to just say what I mean by that in the following manner.

- I boot up my laptop and it just boots into Windows 10.
- I boot up my laptop, press enter right when it boots (it's a Lenovo Thinkpad) I pick select boot partition and I can pick Ubuntu or Windows 10

I was able, I don't have no idea how, to do that very same thing in a Lenovo Thinkpad X250, I was having issues with Ubuntu installer picking my Windows 10 installation, it eventually detected a Windows Manager, and then it just went on a boot loop, I tried fixing the boot-file, used Ubuntu boot fixer, nothing seemed to work, changed some settings on the laptop BIOS and Lo and Behold! it booted into Windows 10, even faster than before... I went "I do wonder...." pressed F12 to pick the loading media and There it was, the option Windows Manager and Ubuntu alongside USB, HDD, LAN, etc...

Has anyone got an idea how to do that on purpose?

I know it's way too much work for just that, but the idea of that fast boot into Windows 10 and only using Ubuntu when I want it (and "turning off GRUB" because he is no longer needed) is something that I wondered if could be done for a long time, it seems to be related with UEFI and how it's capable of picking up the OS that belongs to a partition a treat is as it's own media.

Thanks for any help of the matter.

---

### Post by oldfred on 2020-02-24
If you have Windows fast start up / hibernation on, grub will not boot Windows nor will the Linux NTFS driver load hibernated NTFS partitions. Also if UEFI Secure Boot is on grub will not boot Windows. Something about chain of secure boot is lost.
And both Windows & Ubuntu need to be in UEFI boot mode.

But you can still dual boot from UEFI boot menu, your f12.

When you install or update Windows it normally will make itself first in boot order.
When you install or update Ubuntu grub will make itself first in boot order.

You should be able to change boot order in UEFI, f2 with many systems and UEFI boot tab. 

In Ubuntu you can change boot order with efibootmgr.

To change order it is the -o option in efibootmgr.
Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

You also can turn off os-prober, so it does not find & add Windows to grub menu. If grub menu only has one entry, it should auto boot without showing grub menu. Then to get menu if issues, you have to use escape key right after UEFI screen but before grub runs.

In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub

or turn off executable bit, so not run when grub updates.
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by dragonfly41 on 2020-02-24
There is a method [documented here]("https://forums.linuxmint.com/viewtopic.php?t=287353") to toggle (flag/unflag) boot flags. It is equivalent to disconnecting the Windows drive so that only Ubuntu is seen in a Windows/Ubuntu setup.
But rarely used. If misused it could result in a non bootable system (always have a LiveUSB on standby to restore boot flags).

---

