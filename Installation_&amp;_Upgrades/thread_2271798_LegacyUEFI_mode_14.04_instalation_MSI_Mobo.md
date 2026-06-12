---
title: "Legacy/UEFI mode 14.04 instalation MSI Mobo"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by peter186 on 2015-04-01
Hi all!

I would like to ask for any advice.

I installed Ubuntu 14.04 on my new build (mobo msi gaming 5) but after instalation I am not able to acess BIOS. Also I am not able to move in GRUB menu with keyboard keys.

I am doing single boot Ubuntu, no dual boot option.

I have tried to correct GRUB with boot-repair but with any improvemet. Here is writeout of the boot-repair [http://paste.ubuntu.com/10719634/](http://paste.ubuntu.com/10719634/).
 
I have disabled all fast boot and any other related win (preinstaled 8.1 etc) booting options in BIOS. 
I am little confused with all this fuzz about UEFI instalation on my new mobo, I wanted to work with my computer, not to look for tons of threads on internet without any real solution (I am not really a IT guy, I am just using Ubuntu because of its scripting capability and FEM related possibilities, I am using Ubuntu since 2006).

I will apriciate any idea what to do with this UEFI realated boot issue.

!!!Thank you all for your time!!!

---

### Post by oldfred on 2015-04-01
You have installed in BIOS mode not UEFI mode, so all the issues on UEFI are moot.
But you have to set in UEFI to turn off secure boot as BIOS is not secure boot and have to either turn off UEFI boot and/or turn on CSM/BIOS boot for system to boot correctly.

       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

UEFI is a lot more complex than the old BIOS. And therefore has a lot more settings. Often you also have to turn on USB ports or some other setting that may not seem like it is related to USB ports to get USB devices to work like keyboard & mouse.
And you may have to turn off UEFI fast boot as then it boots so quickly that you do not have time to get into UEFI menu to make changes. Often a total cold boot will still let you get into UEFI, but my Asus-AR motherboard had a fast boot setting for cold boot also. Then if system issues you could end up with a brick. Most motherboard do have a final work around of jumpering pins on motherboard to totally reset system. 
With my new UEFI system I had many settings to change just to get it to work. 
But even with old system and only BIOS I did have a few settings like turning on USB keyboard & mouse that I had to change.

 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)


 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

---

### Post by peter186 on 2015-04-02
thanks for the answer...

how do I know in which mode do I have my system instaled? 

I have turned all fast boot and so boots off.

what is cold boot?

> **oldfred said:**
> You have installed in BIOS mode not UEFI mode, so all the issues on UEFI are moot.
But you have to set in UEFI to turn off secure boot as BIOS is not secure boot and have to either turn off UEFI boot and/or turn on CSM/BIOS boot for system to boot correctly.

       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

UEFI is a lot more complex than the old BIOS. And therefore has a lot more settings. Often you also have to turn on USB ports or some other setting that may not seem like it is related to USB ports to get USB devices to work like keyboard & mouse.
And you may have to turn off UEFI fast boot as then it boots so quickly that you do not have time to get into UEFI menu to make changes. Often a total cold boot will still let you get into UEFI, but my Asus-AR motherboard had a fast boot setting for cold boot also. Then if system issues you could end up with a brick. Most motherboard do have a final work around of jumpering pins on motherboard to totally reset system. 
With my new UEFI system I had many settings to change just to get it to work. 
But even with old system and only BIOS I did have a few settings like turning on USB keyboard & mouse that I had to change.

 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)


 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

---

### Post by oldfred on 2015-04-02
Cold boot is fully power down. If on a laptop remove battery also. And hold power switch to drain capacitors or any residual power. Or leave off for a period of time.
Warm boot is a total reboot but not shutdown, power remains to motherboard.

If you have an efi partition and gpt partitioning and boot from that then it is UEFI. And if you have a bios_grub partition then it is gpt partitioning but still a BIOS boot.
If you have MBR(msdos) partitioning then it has to be BIOS booting.

How you boot installer is how it installs. UEFI & BIOS are not really compatible and once you start in one mode to boot you cannot switch. Or if dual booting you can only use grub to boot systems installed in the same boot mode. But you can then dual boot from UEFI menu.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by peter186 on 2015-04-03
oldfred thank you for you advices

I have made efi partition with live usb, i have installed 14.04 and it is booting. i ahve to made nomodeset change not to have black screen after login to unity.

i am still not able to acess BIOS/UEFI (or whatever the name is) menu with "DEL" key as writen on the boot screen.

acess is partially important to me, couse i have K"grade" intel procesor with OC option.

thank you very much.

UPDATE: I am still not booting with efi. i am missing any sys/firmware/efi folder. sda1 which si an efi partition is missing /boot flag. 

UPDATE II: I have used repair Boot live CD and I am able to boot in EFI mode to Ubuntu. Still can't move in GRUB menu with keys, unable to press ENTER or to get into UEFI/BIOS menu.


> **oldfred said:**
> Cold boot is fully power down. If on a laptop remove battery also. And hold power switch to drain capacitors or any residual power. Or leave off for a period of time.
Warm boot is a total reboot but not shutdown, power remains to motherboard.

If you have an efi partition and gpt partitioning and boot from that then it is UEFI. And if you have a bios_grub partition then it is gpt partitioning but still a BIOS boot.
If you have MBR(msdos) partitioning then it has to be BIOS booting.

How you boot installer is how it installs. UEFI & BIOS are not really compatible and once you start in one mode to boot you cannot switch. Or if dual booting you can only use grub to boot systems installed in the same boot mode. But you can then dual boot from UEFI menu.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2015-04-03
Many systems require you to turn on USB ports in UEFI/BIOS. Or enable USB keyboard and mouse.
Grub does not have the same drivers as Windows or Ubuntu and relies on UEFI for what it can do.

Did you try cold boot?

I direct boot ISO, so do not see grub menu on UEFI boot. Do you have this entry?
```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
```


And can you use keyboard when  booting live installer?

---

### Post by peter186 on 2015-04-04
My USB ports are set to on in UEFI/BIOS, I don't see any option to enable keyboard/mouse.

I am able to acess UEFI/BIOS ONLY AFTER cold boot (reseting BIOS/UEFI). After that my UEFI/BIOS goes to default settings - LEGACY/UEFI - 1 order boot is LEGACY HDD. 

After setting UEFI boot, logging in Ubuntu, restarting I am NO MORE able to acess UEFI/BIOS and keyboard is not responding to any key pushing.

My /etc/grub.d/30_uefi-firmware

is here

```

#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2012  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="/usr"
datarootdir="/usr/share"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"

. "${datarootdir}/grub/grub-mkconfig_lib"

efi_vars_dir=/sys/firmware/efi/vars
EFI_GLOBAL_VARIABLE=8be4df61-93ca-11d2-aa0d-00e098032b8c
OsIndications="$efi_vars_dir/OsIndicationsSupported-$EFI_GLOBAL_VARIABLE/data"

if [ -e "$OsIndications" ] && \
   [ "$(( $(printf %x \'"$(cat $OsIndications | cut -b1)") & 1 ))" = 1 ]; then
  LABEL="System setup"

  gettext_printf "Adding boot menu entry for EFI firmware configuration\n" >&2

  onstr="$(gettext_printf "(on %s)" "${DEVICE}")"

  cat << EOF
menuentry '$LABEL' \$menuentry_id_option 'uefi-firmware' {
    fwsetup
}
EOF
fi

```

> **oldfred said:**
> Many systems require you to turn on USB ports in UEFI/BIOS. Or enable USB keyboard and mouse.
Grub does not have the same drivers as Windows or Ubuntu and relies on UEFI for what it can do.

Did you try cold boot?

I direct boot ISO, so do not see grub menu on UEFI boot. Do you have this entry?
```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###
```


And can you use keyboard when  booting live installer?

---

### Post by oldfred on 2015-04-04
You posted the script that creates the UEFI boot entry in the grub menu.

What brand/model system is this.
Gigabyte motherboards have an IOMMU setting that must be changed for USB3 ports to work.

Have you tested all ports for keyboard/mouse?
Do you have the old ps/2 ports? On my old system I switched to them until I figured out that I had to turn on  BIOS setting.

---

### Post by peter186 on 2015-04-04
motherboard is msi gaming 5, pc is my own build

i have tested all usb ports, i dont have any old ps2 port keyboard or mouse.


> **oldfred said:**
> You posted the script that creates the UEFI boot entry in the grub menu.

What brand/model system is this.
Gigabyte motherboards have an IOMMU setting that must be changed for USB3 ports to work.

Have you tested all ports for keyboard/mouse?
Do you have the old ps/2 ports? On my old system I switched to them until I figured out that I had to turn on  BIOS setting.

---

### Post by oldfred on 2015-04-04
Not sure what to suggest. Almost always something in UEFI menu.
Have you updated to the newest UEFI from MSI?

If gaming is the only type of model, then the user in the link in post #2 seemed to be able to install and have it dual boot as it is exactly the same model. But he may have been booting from UEFI menu not grub menu?

---

### Post by peter186 on 2015-04-04
oldfred thank you for all your advices!!!

i went to a friend of mine and borrowed an ps2 keyboard.... the keyboard is working!!! usb peripherals are not working!!!

the only thing to solve is missing screen resolutions after UEFI bootup :) I gues i will be able to find answer somewhere around here.. 

thank you once again for your help!!!

> **peter186 said:**
> motherboard is msi gaming 5, pc is my own build

i have tested all usb ports, i dont have any old ps2 port keyboard or mouse.

---

### Post by oldfred on 2015-04-04
Some of the old keyboard I have came with USB to ps/2 adapters, which I kept even though those old keyboards are long gone.

Post a new thread on video issues with that in title if you cannot find a solution. Post what card/chip you are using in that thread. Starting point here as this is what I would post in your new thread first.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by peter186 on 2015-04-05
if anybody came to end of this thread and want to know how to deal with missing display resolution - with intel HD 4600 graphics or any intel onboard graphics

i installed kernel 3.19 which is implemented with all needed intel graphic stuff... no need to install newest graphic drivers from intel pages

---

