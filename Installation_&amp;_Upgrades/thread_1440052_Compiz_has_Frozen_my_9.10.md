---
title: "Compiz has Frozen my 9.10"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Ichido on 2010-03-27
I installed (Synaptic) Compiz and tried a few 3-D desktop teaks and it froze everything.
Now my system boots to desktop and then everything Freezes.
NO touch-pad, mouse or keyboard function.
Tried to boot an earlier version in the GRUB, still nothing.
Tried a Install of 9.10 in the same /sda3 as the frozen one and still no change.
Cannot start a terminal.
Cannot start, remove or change anything.
I'm using my Backup 9.04 on my /sda1 to get here.
Is there a way to get into the Frozen O.S. and remove Compiz?
Any help would be greatly appreciated.

---

### Post by srix on 2010-03-27
If you're able to boot the system from /sda1, you could mount the 9.10 partition, remove the compiz configuration files and restart. That should get you to the default compiz configuration (which I assume was working before you tried the 3D tweaks).

Once you're into /sda1, create a temporary directory somewhere (e.g. /tmp/910).
$ sudo mount /dev/sda3 /tmp/910
$ cd /tmp/910/<your home folder>/.gconf/apps
$ rm -r compiz
$ cd
$ sudo umount /tmp/910

Reboot into 9.10. Hopefully that should restore the default compiz settings.

---

### Post by Ichido on 2010-03-27
> **srix said:**
> If you're able to boot the system from /sda1, you could mount the 9.10 partition, remove the compiz configuration files and restart. That should get you to the default compiz configuration (which I assume was working before you tried the 3D tweaks).

Once you're into /sda1, create a temporary directory somewhere (e.g. /tmp/910).
$ sudo mount /dev/sda3 /tmp/910
$ cd /tmp/910/<your home folder>/.gconf/apps
$ rm -r compiz
$ cd
$ sudo umount /tmp/910

Reboot into 9.10. Hopefully that should restore the default compiz settings.

Every terminal command above produces "command not found".

---

### Post by srix on 2010-03-27
That's strange! Are you able to run any other command at all in the terminal? ls, for instance?
(Also, I hope you didn't include the "$ " in the commands you typed? You only need to type the stuff after the "$ " on each of the lines).

---

### Post by Ichido on 2010-03-28
> **srix said:**
> That's strange! Are you able to run any other command at all in the terminal? ls, for instance?
(Also, I hope you didn't include the "$ " in the commands you typed? You only need to type the stuff after the "$ " on each of the lines).


"cd /tmp/910/<your home folder>/.gconf/apps"

How/Why do I "move/copy" my /'home' folder into /tmp/910/ ??

Also: "sudo mount /dev/sda3 /tmp/910" causes Terminal to "spin it's wheels"?

---

### Post by srix on 2010-03-29
> **Ichido said:**
> "cd /tmp/910/<your home folder>/.gconf/apps"

How/Why do I "move/copy" my /'home' folder into /tmp/910/ ??

Also: "sudo mount /dev/sda3 /tmp/910" causes Terminal to "spin it's wheels"?

That's a "change directory" command - to change your current working directory to your home folder on the bad installation, which is temporarily mounted under "/tmp/910".

Once you boot into the good 9.04 installation, could you run the "mount" command in a terminal and post the output here? Also the output of the "sudo fdisk -l" command.

---

### Post by Ichido on 2010-03-29
"sudo mount /dev/sda3 /tmp/910" = "command not found"

"sudo fdisk -l" =

"Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00060f2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6997    56203371   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda3            6998       13995    56211435   83  Linux
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order"


Thanks for your help so far.

---

### Post by srix on 2010-03-31
I can't imagine why the mount command should fail.

Another alternative is to boot into the 9.10 (sda3) system in single user mode. To do that, while in the grub menu, select the 9.10 boot image and type 'e' to edit the boot command. It should show you the entire command used for booting (something like "kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=6f2f6599-29c9-44d1-9a8c-b504f1b57ba0 ro quiet splash"). Move using the arrow keys to the end of this line and add the word "single" (without quotes), and press enter to boot. 
This should get you into a shell prompt, from where you can cd into your home directory and remove the ".gconf/apps/compiz" directory as mentioned in the earlier posts.

---

