---
title: "Messed with GRUB"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by alescribano on 2014-09-30
Hi there,

I have a Dual-Boot installation (Win7+Ubuntu 14.04). I would like my PC to automatically start Win7 unless I press something (like Shift or ESC), giving me the opportunity to choose other OSs... I've been playing with the GRUB parameters, and installed GRUB-Customizer as well, with no success at all. Finally, I've  been googling around and in most cases the experts say it is not possible... Is that true? Isn't ther any workaround to achieve what I need? I think it is very simple, besides that, GRUB uses to be a very well featured booter, so I can not believe it, but...

Thanks in advance.

---

### Post by Vladlenin5000 on 2014-09-30
Hi, welcome.

[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

---

### Post by alescribano on 2014-09-30
Thanks a lot for your reply. However, this other thread explains how to set Windows as the default boot OS. This is can be done just modifying the GRUB_DEFAULT entry. But, if you want to HIDE the GRUB Menu as well, you have to deactivate the OS_PROBER (GRUB Customizer shows a message which says that, if you don't, the HIDE option will not work). If you deactivate the OS_PROBER ("Search for other OSs" option actually), it will not find Windows, and then your DEFAULT selection doesn't work, and the DEFAULT becomes Ubuntu...

In short, the behaviour I'm looking for is:
1) No GRUB Menu should be shown as default (HIDDEN), unless a Key is pressed within a specific TIME-OUT
2) If nothing is pressed within the TIME-OUT, then automaticaly boot on Win
3) If a key is pressed within the TIME-OUT, and only in that case, then show the menu, allowing the user to choose any present OS to boot on.

Best Regards!

---

### Post by oldfred on 2014-09-30
You can also set show menu to 1 sec. Some that set it to 0 sec then never get back to grub menu.

Grub Customizer has added its own scripts into the script folder so I do not know how that may change script order.

       Configuring the Boot Menu in Ubuntu - Boot Order in grub
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)
/etc/default/grub


 or a new file that will be first in the menu
sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom

      
 find your windows entry - full boot stanza in this and copy into 06_custom
gedit /boot/grub/grub.cfg

    gksudo gedit /etc/grub.d/06_custom 

After any grub change:

 sudo update-grub

To clear grub customizer you may have to totally purge grub and reinstall. And you may have to make sure none of the customizer scripts are still in /etc/grub.d

 sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by alescribano on 2014-09-30
Thanks! It seems interesting. I will give it a try and will come back to tell the results!!!

PD: The first option is the one I already have at the moment ;)

---

### Post by Dennis N on 2014-09-30
> **alescribano said:**
> 
In short, the behaviour I'm looking for is:
1) No GRUB Menu should be shown as default (HIDDEN), unless a Key is pressed within a specific TIME-OUT
2) If nothing is pressed within the TIME-OUT, then automaticaly boot on Win
3) If a key is pressed within the TIME-OUT, and only in that case, then show the menu, allowing the user to choose any present OS to boot on.

Best Regards!

I have a setup that works this way. The relevant part of /etc/default/grub:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

This has a 5 sec (visible) countdown - press ESC key within that 5 seconds, the menu appears; press nothing and the default OS boots (no grub menu seen). OS_PROBER has to be disabled. If OS_PROBER detects another OS, and GRUB_TIMEOUT=0, it inserts a stanza into grub.cfg setting the timeout back to 10. So, I use a custom menu to multi-boot.

---

### Post by alescribano on 2014-10-01
Thank you both. I couldn't try your suggestions last night, but I will tonight for sure.

Hi, Dennis. I see your GRUB_DEFAULT is set to "0". In my case, "0" means Ubuntu in my boot sequence. So, if nothing is pressed, Ubuntu will start automatically, right? What I'm looking for is automaticaly booting Window$ 7 when nothing is pressed. I'm not sure but I think that, if you disable OS_PROBER, you will not be able to boot Window$ 7. If you enable OS_PROBER, you will not be able to HIDE de Menu... I think that's the issue. Did you get to set Windows as your "0" entry on your boot sequence while disabling OS_PROBER?

Thank you again!

---

### Post by Dennis N on 2014-10-01
> **alescribano said:**
> Thank you both. I couldn't try your suggestions last night, but I will tonight for sure.

Hi, Dennis. I see your GRUB_DEFAULT is set to "0". In my case, "0" means Ubuntu in my boot sequence. So, if nothing is pressed, Ubuntu will start automatically, right? What I'm looking for is automaticaly booting Window$ 7 when nothing is pressed. I'm not sure but I think that, if you disable OS_PROBER, you will not be able to boot Window$ 7. If you enable OS_PROBER, you will not be able to HIDE de Menu... I think that's the issue. Did you get to set Windows as your "0" entry on your boot sequence while disabling OS_PROBER?

Thank you again!
GRUB_DEFAULT=0 means the first (top) entry in the grub menu will start automatically.

To have another menu entry boot by default, change the number to 1 for automatic second entry, 2 for third entry, etc.

What I did:

With two or more OS on the disk, you update-grub with OS prober active to create a complete updated grub.cfg. Then you use the menu entries from grub.cfg for each OS to make a custom menu entry for each (see guide linked below). Run update-grub, and check that the custom entries work. Then, disable the OS_PROBER, update grub again, and you have a new grub.cfg with only the custom entries and the current OS. This will now work ok with GRUB_TIMEOUT=0 since OS_PROBER didn't run. But Windows (and any other OS you might have) is now a custom menu entry (looks the same as the normal one, as it's just a copy) and can be loaded.

You can make the custom menu entries following this guide. You need to study this before proceeding. 

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Might look complicated, but it is just copying menu entries from grub.cfg and pasting them into the template 40_custom, saving it to /etc/grub.d with a better name, and then running update-grub to insert them into grub.cfg (which generates the grub menu). 

You could save 40_custom as 06_custom-entries which will put them at the top of the grub menu. Don't turn off OS_PROBER until you have tested the custom entries. Once you are are sure they all work, turn off OS_PROBER and update-grub one more time.

You can break the custom entries into _separate_ files if you want. That is actually what I do. My /etc/grub.d:

```
dmn@Erica:/etc/grub.d$ ls -l
total 84
-rwxr-xr-x 1 root root  9424 Apr 11 03:48 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 08:58 05_debian_theme
[COLOR="#FF0000"]-rwxr-xr-x 1 root root   909 Jul  6 13:42 07_Xubuntu-1404
-rwxr-xr-x 1 root root   852 Apr 27 13:06 08_Ubuntu-1204
[/COLOR]-rwxr-xr-x 1 root root 11608 Apr 11 03:48 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 03:48 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11 03:48 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 03:48 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 03:48 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 03:48 41_custom
-rw-r--r-- 1 root root   483 Apr 11 03:48 README

```
 
Files beginning 07 and 08 are the custom entries - each file made by pasting just one menu entry from grub.cfg to a copy of 40_custom, then saved with their present names. They need to be set as executable. (You can also disable OS_PROBER here by making its file not executable).

---

