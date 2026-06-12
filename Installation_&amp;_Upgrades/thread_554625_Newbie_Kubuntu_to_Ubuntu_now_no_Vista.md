---
title: "Newbie Kubuntu to Ubuntu now no Vista"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by bodone on 2007-09-19
Hello All,

tried searching for similar issues, but not sure if they completely describe my issue.

Have Vista installed on it's own drive, then installed kubuntu to it's own partition on a separate HD. All worked fine including the Grub menu until i started playing with ATI drivers. I have an ATI 1950 with a 20" apple cinema display, couldn't get things working so decided to install Ubuntu over Kubuntu using the live CD. Used the same partitions, formatted them and install went fine.

Problem is after install reboot i get to the Grub menu and when i select ubuntu it says mount not found, aha i thought, i'm in a rush so i'll boot vista and read my mails before i head to the office. No luck, i get the message about NTLDR not being found.

The physical disks seem to be fine as i can see them in the bios boot/post screens, i'm not at home at the moment, but any pointers would be good.

cheers.

---

### Post by bodone on 2007-09-19
if it helps, i get error message 17 in grub. I can boot the ubuntu install CD and i can see all the disks and files in the file/disk browser?

cheers

---

### Post by Pumalite on 2007-09-19
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by bodone on 2007-09-20
Thanks for the guide, i've managed to sort my problem out but i think more through luck than design.

My underlying issue was that i have vista installed to a sata HD connected to the motherboard sata controller, Ubuntu was installed on an ide disk that is connected (with another ide disk) to a pcie ide controller card. This caused the mount point to switch between boots and hence grub get confused. I've now switched over to the vista boot loader which boots vista fine and which also points to Neogrub which points to the correct ide disk with ubuntu installed.

Like i say more through chance through design, but i kept reading and once i knew my important data was backed up ok and all i would lose would be time, it gave me the confidence to bash those shell commands in.

cheers all.

---

