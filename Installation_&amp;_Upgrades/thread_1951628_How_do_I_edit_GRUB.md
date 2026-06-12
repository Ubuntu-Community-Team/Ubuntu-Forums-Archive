---
title: "How do I edit GRUB"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by JXR on 2012-04-02
[COLOR=black][FONT=Verdana]I’ve succeeded in installing Ubuntu (dual boot) 10.04 but in the process the Dell Inspiron keyboard was disabled.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I read in another post **(How di I disable ACPI?)** that [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]1) [/FONT][/COLOR][COLOR=black][FONT=Verdana]GRUB line:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]linux /boot/vmlinuz-linuz-2.6.32-33-generic root=UUID=15b1e1d8-22e2-4a26-ab81-de70d6032835 ro quiet splash [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]needed to be appended with [/FONT][/COLOR][COLOR=red][FONT=Verdana]**noacpi **[/FONT][/COLOR][COLOR=black][FONT=Verdana](resulting in) [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]linux /boot/vmlinuz-linuz-2.6.32-33-generic root=UUID=15b1e1d8-22e2-4a26-ab81-de70d6032835 ro quiet splash [COLOR=red][FONT=Verdana]**noacpi **[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]in order to enable the keyboard and mouse pad.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I input “e” to edit the Grub file; edited the file (and then instructed it to boot) but that didn’t seem to work.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I then (restarted and) input “c” to go into command line mode, but when I input the line [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]linux /boot/vmlinuz-linuz-2.6.32-33-generic root=UUID=15b1e1d8-22e2-4a26-ab81-de70d6032835 ro quiet splash [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]the computer returned “error: file not found”[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]How do I edit Grub to include the command [/FONT][/COLOR]**[COLOR=red][FONT=Verdana]noacpi [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]or [/FONT][/COLOR]**[COLOR=red][FONT=Verdana]pci=noacpi ?[/FONT][/COLOR]**

---

### Post by lmarmisa on 2012-04-02
> **JXR said:**
> [COLOR=black][FONT=Verdana]I’ve succeeded in installing Ubuntu (dual boot) 10.04 but in the process the Dell Inspiron keyboard was disabled.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I read in another post **(How di I disable ACPI?)** that [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]1) [/FONT][/COLOR][COLOR=black][FONT=Verdana]GRUB line:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]linux /boot/vmlinuz-linuz-2.6.32-33-generic root=UUID=15b1e1d8-22e2-4a26-ab81-de70d6032835 ro quiet splash [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]needed to be appended with [/FONT][/COLOR][COLOR=red][FONT=Verdana]**noacpi **[/FONT][/COLOR][COLOR=black][FONT=Verdana](resulting in) [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]linux /boot/vmlinuz-linuz-2.6.32-33-generic root=UUID=15b1e1d8-22e2-4a26-ab81-de70d6032835 ro quiet splash [COLOR=red][FONT=Verdana]**noacpi **[/FONT][/COLOR][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]in order to enable the keyboard and mouse pad.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I input “e” to edit the Grub file; edited the file (and then instructed it to boot) but that didn’t seem to work.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I then (restarted and) input “c” to go into command line mode, but when I input the line [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]linux /boot/vmlinuz-linuz-2.6.32-33-generic root=UUID=15b1e1d8-22e2-4a26-ab81-de70d6032835 ro quiet splash [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]the computer returned “error: file not found”[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]How do I edit Grub to include the command [/FONT][/COLOR]**[COLOR=red][FONT=Verdana]noacpi [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]or [/FONT][/COLOR]**[COLOR=red][FONT=Verdana]pci=noacpi ?[/FONT][/COLOR]**

You have to edit the file /etc/default/grub and add your options to the key GRUB_CMDLINE_LINUX:

```

gksudo gedit /etc/default/grub

```

Save and exit.

Finally, type this command:

```

sudo update-grub

```

---

### Post by JXR on 2012-04-02
How do I get to a command line that starts with
gksudo >
 
grub> is the only command line I can get to from the initial ubuntu startup screen 
 
It does not recognize
 
grub> gksudo gedit /etc/default/grub (error: unknown command 'gskudo')
 
or
 
grub> gedit /etc/default/grub (error: unknown command 'gedit')

---

### Post by lmarmisa on 2012-04-02
> **JXR said:**
> How do I get to a command line that starts with
gksudo >
 
grub> is the only command line I can get to from the initial ubuntu startup screen 
 
It does not recognize
 
grub> gksudo gedit /etc/default/grub (error: unknown command 'gskudo')
 
or
 
grub> gedit /etc/default/grub (error: unknown command 'gedit')

Hi JXR,

my procedure is oriented to add persistent additional options to GRUB. But it requires that the system is able to boot and this is not your case.

You should add the appropriated option (noacpi) manually using the 'e' command of GRUB for the first boot of your system. Then, when the system starts, you could follow my procedure for fixing the boot problem permanently.

---

### Post by JXR on 2012-04-02
> **lmarmisa said:**
> Hi JXR,
  
You should add the appropriated option (noacpi) manually using the 'e' command of GRUB for the first boot of your system. Then, when the system starts, you could follow my procedure for fixing the boot problem permanently.
 
 
That was what I tried first. 
 
But it never took the command.
  
I advanced the cursor 
  inserted noacpi 
  the only option was Cntl-X (to boot) which never enabled the keyboard 
 
Am I using the GRUB 'e' option wrong? (I never saw any way to execute a Save.)

---

### Post by oldfred on 2012-04-02
Check BIOS and enable USB keyboard & mouse.

Sometimes the USB keyboard do not work in grub because they are not enabled in BIOS. Both Windows and Ubuntu seem to use their own drivers so BIOS setting does not matter, but with grub it does.

edit, you may be able to do this also, change sda5 to partition where your install is.

#Normally we do not directly edit grub.cfg. Edit from liveCD.
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

gksudo is just a link in Ubuntu to gksu

---

### Post by JXR on 2012-04-03
BIOS (F2 during startup brings up BIOS) has no setting enabling USB Keyboard and Mouse.
 
The Dell Inspiron does have a pci port and USB ports. The USB mouse is the only way I can navigate after boot. However a keyboard plugged into the PCI port doesn't activate. I don't have another USB Keyboard so for the time being that is unavailable.
 
I thought that GRUB and Ubuntu were the same. Obviously the keyboard works when I enable the "e"dit option (the one you suggested -- also the "c"ommand line option) but once Unbutu is launched the keyboard doesn't work.
 
I don't know what you mean by "edit...change sda5 to partition where your install is" or how to implement this. (Also I don't know where Unbutu does its install. All that was taken care of by Unbutu when I chose to have it execute the dual boot option.)
 
One thing I can do. I can initialize the machine from CD (the way Unbutu's CD was the first device to mount) AND while booting Unbutu from the CD (not using the hard disk install) I can (F6) instruct Unbutu to noacpi. When the Unbutu CD-based desktop comes up the keyboard and touch pad are available. But I don't know whether I can access and edit disk-based files while in this linux system. Is there some sort of Command Prompt window I can bring up within which I can execute
 
sudo chmod 777 /mnt/boot/grub/grub.cfg
 
sudo chmod +w /mnt/boot/grub/grub.cfg
 
or
 
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
 
In other words, is having the Unbutu install disk mount its CD-based desktop, a way I can access and change the disk files required to fix the ptoblem?

---

### Post by oldfred on 2012-04-03
Ubuntu will be in a Linux partition. This will show all your partitions and if you only have one ext3 or ext4 partition that will be where Ubuntu is installed.
```

sudo fdisk -lu
```

Often Windows in NTFS uses sda1 & sda2. A vendor recovery may be sda1 or sda4. Since Linux works from logical partitions and the first logical partition is sda5, it often is in sda5 but not always.

---

### Post by JXR on 2012-04-03
The problem was finally solved by using a USB keyboard. I presume that once in Unbutu that I would be able to permanently activate the laptop keyboard by finding out how to implement a command window that allowed me to input sudo commands but it seems I won't find out because now the screen is almost totally black. (see post "Black Screen Problem???")

---

