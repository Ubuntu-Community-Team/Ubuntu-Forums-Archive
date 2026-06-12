---
title: "Error during installation..."
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by SirShiv on 2008-10-08
Hey all,

Just built a new comp (this is my first build) and was going to install Ubuntu on it. I made a Ubuntu DVD burning at the slowest speed possible as recommended. I started the process and entered all the info as asked then I got to the installation process. Only a few seconds in I got the following error message:

"The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda)failed."

I need to know what this means?/what is wrong?/what did i do wrong?

My comp specs are:
Mobo- ASUS M3N-HD/HDMI
RAM- 2gb Corsair Dominator Twin2X4096-8500C5DF
GFX- EVGA GeForce 8800 GT
HDD- 1TB Segate Barracuda
CPU- AMD Phenom quad core

---

### Post by Partyboi2 on 2008-10-08
It means that the installer was unable to create the ext3 filesystem on your hard drive. Try making the partitions with gparted (System>Admin>Partition Editor) before running the installer.

---

### Post by Pumalite on 2008-10-08
Or use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by SirShiv on 2008-10-08
Am I able to or is there a way to do that with no OS on the comp? (I apologize, I'm a noob to both building and Ubuntu)

---

### Post by Partyboi2 on 2008-10-08
Use the ubuntu live cd >gparted (System>Admin>Partition Editor) or as mentioned by Pumalite use the gparted live cd. It does not matter that there is no os installed as both of these methods do not require a os installed.

---

### Post by SirShiv on 2008-10-08
Gparted is not finding my drive....I read that it sometimes is slow if your bios say there is a floppy when there is none...which may be my case...however, would that cause it to not read my drive at all?  Or do I need to set my HDD as my primary boot source instead of my optical drive in my bios? ....or am i just lost? (dont answer that last question, i think i know already :P )

---

### Post by Partyboi2 on 2008-10-09
Is you bios seeing your hard drive?

---

### Post by SirShiv on 2008-10-09
yes, and when I go to install Ubuntu it sees my hard drive and allows me to select it using the Guided-use entire disk option (it says SCSI1 (0,0,0)(sda)- 1.0 TB ATA ST31000340AS under the guided option). When I select that and hit next it goes on to start installation, but then I get the message in my original post. Just can't seem to get it to read my drive when partitioning.

---

### Post by Partyboi2 on 2008-10-09
Try giving [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/4") ago.

---

### Post by SirShiv on 2008-10-09
bleh, i feel like an idiot...but where would i be looking for that text?....

---

### Post by Partyboi2 on 2008-10-09
I would say, boot to the ubuntu live cd desktop then press Alt+F2 and type in the box
```
gksudo gedit /lib/partman/commit.d/30parted
```
then add to the bottom of the file ```
update-dev
```
so it would look like this:
> #!/bin/sh
 . /lib/partman/definitions.sh
 disable_swap
for dev in $DEVICES/*; do
    [ -d "$dev" ] || continue
    cd $dev
    open_dialog COMMIT
    close_dialog
    update-dev
done
 Then save and try installing ubuntu.

---

### Post by SirShiv on 2008-10-09
Well I did that and tried to save it and got "There is not enough disk space to save the file. Please free some disk space and try again." For some reason my bios sees my HDD but the OS does not.I read somewhere that someone suggested plugging the HDD in SATA 5 or SATA 6.....dunno how that will help me, but I'll give it a try in the mean time. I have no idea why the OS can't see the drive.

---

### Post by SirShiv on 2008-10-09
Rebooted and tried again and it let me save it....but it didn't change anything on the installation, still doing the same thing.

---

### Post by Tunguska on 2008-10-13
I'm having the same problem. Were you able to solve it? If so, how? Thanks in advance.

---

