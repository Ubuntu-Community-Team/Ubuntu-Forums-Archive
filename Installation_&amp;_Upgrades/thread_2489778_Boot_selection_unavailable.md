---
title: "Boot selection unavailable"
date: 2023-08-10
forum: Installation &amp; Upgrades
---

### Post by plrll on 2023-08-10
Hello everyone, I installed Xubuntu(most recent LTS) to dual boot with windows 10 and the installation was successful, however when I restart the system is booting directly to Xubuntu.
I read here that the system will show the boot menu to allow me to choose the OS I want to boot but that is not happening.
If I want to boot win10 I have to press F12 at boot.
I have tried the boot repair tool and I do not understand the Boot Info Summary so I have not done any repairs yet.
Here is the Boot Info Summary link: [https://paste.ubuntu.com/p/4pHHVmNnRp/](https://paste.ubuntu.com/p/4pHHVmNnRp/)
Can anyone help me understand this and is repairing recommended?

---

### Post by tea for one on 2023-08-10
Your grub file needs a little edit.
Boot into Xubuntu
Open a terminal and enter:-
```
sudo nano /etc/default/grub
```
Enter your password
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu [COLOR="#0000FF"]#originally hidden[/COLOR]
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
ctrl+o to save and ctrl+x to exit
```
sudo update-grub
```
Reboot
Any good?

---

### Post by plrll on 2023-08-10
Nope. After reboot it is still booting to Xubuntu without showing any menu.

---

### Post by tea for one on 2023-08-10
Whoops, I forgot OS_PROBER
Add this line to /etc/default/grub

GRUB_DISABLE_OS_PROBER=false

Then [COLOR="#0000FF"]sudo update-grub[/COLOR] and reboot
The terminal output from sudo update-grub should find Windows Boot Manager.

---

### Post by plrll on 2023-08-11
Update: Reparing with boot repair did not [COLOR=#111111][FONT=monospace]Unhide GRUB boot menu. I'll try contacting the devs.
[/FONT][/COLOR]If anyone would want to review the boot info file here are the links:
after [[COLOR=#000000]tea for one[/COLOR]]("https://ubuntuforums.org/member.php?u=585392")'s method:  [https://paste.ubuntu.com/p/cVXsPvSmk3/](https://paste.ubuntu.com/p/cVXsPvSmk3/)
after [[COLOR=#000000]ansarabbas8273[/COLOR]]("https://ubuntuforums.org/member.php?u=2181179")'s method and recommended repair with boot repair tool: [https://paste.ubuntu.com/p/Bj7B5vfDWR/](https://paste.ubuntu.com/p/Bj7B5vfDWR/)

Thanks everyone for sparing your time to help.
According to the device(thinkpad x1 carbon 3rd gen) manufacture, I'll have to keep using F12 at boot, that is until I don't need win10 anymore.
I will keep the thread open for sometime then mark it as solved.

---

### Post by tea for one on 2023-08-11
After you ran sudo update-grub, did you see terminal output to confirm that Windows Boot manager was found:-
 ```
edited@edited-xubuntu23-04:~$ sudo update-grub
[sudo] password for edited: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-24-generic
Found initrd image: /boot/initrd.img-6.2.0-24-generic
Found linux image: /boot/vmlinuz-6.2.0-20-generic
Found initrd image: /boot/initrd.img-6.2.0-20-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
[COLOR="#0000FF"]Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi[/COLOR]
Adding boot menu entry for UEFI Firmware Settings ...
done
edited@edited-xubuntu23-04:~$ 

```

---

### Post by plrll on 2023-08-11
Yes it was found but the boot device menu with with timeout is no show.

---

### Post by tea for one on 2023-08-11
> **plrll said:**
> Yes it was found but the boot device menu with with timeout is no show.
That's a little bit of progress.
Do you have Fast boot or similar in your UEFI settings?

---

### Post by MAFoElffen on 2023-08-12
Try this
```

sudo nano /etc/default/grub

```
Add this line to your /etc/default/grub file, right after the "GRUB_TIMEOUT=" line
```

GRUB_RECORDFAIL_TIMEOUT=10

```
Save and exit. The update grub to pick up the changes
```

sudo update-grub

```
Reboot and test...

---

