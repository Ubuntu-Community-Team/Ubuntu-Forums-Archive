---
title: "Windows question (installing from linux)"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by kennny2004 on 2005-08-19
i need to install windows and linux on 2 difirent drives the problem is that i can not boot into my windows setup so i tryed useing wine to install windows tahts freezes or i do not have enough patients then i tryed burning cd not luck with new windows burner does't work ( i got post on other thread). i was thinking of getting bootdisk for windows xp but i got no floppy kkkkkk anyone got any other idea lol.
thanks \\:D/

---

### Post by joaoeb on 2005-08-19
If you can boot to Ubuntu, you can use grub to boot windows

Open a terminal, and do:

```
cd /boot/grub
sudo cp menu.lst menu.lst.backup
```
This will make a backup of the original menu.lst. This  file  controls the grub bootloader. Don't close the terminal yet.
Now you must know where the drive with windows is connected, if is in the primary IDE or secundary IDE and the position in the cable. 
```

IDE0       IDE1
|             |
|             |
hd1        hd3
|             |
|             |
hd0        hd2

```
the "|" represents the cable

Knowing this do in the open terminal:
```
sudo gedit menu.lst
```
This will open the file in a editor.
go to the end of file and search for this:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
If yours don't have this section add it to your file.
Now can you see this line:
```
root       (hd0,0)
```
This means: "Windows is instaled in the first HD in the first IDE(hd0) and in the first partition in that HD (,0)"
Now change this to reflect your case, for example, if yours is the first drive in the second IDE it will be (hd3,0) (remenber my crude drawing).
Ok, save the file reboot and test it.
If it doesn't work come back here :)

---

### Post by kennny2004 on 2005-08-19
i don't have windows anywhere on the system only ubuntu on one hard drive and thats everything i need to get windows installation to open on boot somehow
thanks

---

### Post by Oxygene on 2005-08-19
[QUOTE=kennny2004]i don't have windows anywhere on the system only ubuntu on one hard drive and thats everything i need to get windows installation to open on boot somehow
thanks[/QUOTE]
 So you want to install Windows, but you have no Windows installation media? That won't work.
You either need a drive image of a complete windows installation (what you apparantly do not have) or a Windows CD to boot from (what you do not have either as it seems).

Try to get a Windows installation CD, boot it, install windows (taking care not to delete your Linux installation) and after this, boot from a ubuntu-CD to restore your bootloader, since windows will most certainly install it's own boot manager that doesn't care to give you the option to boot ubuntu.

---

### Post by kennny2004 on 2005-08-20
i got windows but it does not boot and it works and i can't open with wine it freezes

---

### Post by mcmuffy on 2005-08-20
If you are wanting to run Windows from within Linux you will need a virtual machine program such as VMware which sets up a pretend machine for windows or many other OS's to run on.

---

### Post by kennny2004 on 2005-08-20
Thanks i am dling it right now i might post if i get problems with installing thanks (hmm the only option i did not try was that but i could not find a decent program for it

---

### Post by Velox Letum on 2005-08-20
Just a word of warning, VMware Workstation is not free.

---

### Post by kennny2004 on 2005-08-20
i know i know someone who uses it and i got the serial from him so it all kool he probably is going to give me the whole cd anyways  :smile:  :smile:  but heh so i got it installed now how i go upon installing my unbootable windows disk lol i am confused i created the right virtual machine but when i turn it on it ask me for bootable windows cd :( am i doing something wrornng or is ther other way

---

### Post by mcmuffy on 2005-08-20
I'm not sure if VMware takes anything from bios but if it does make sure that cd is set as your 1st boot device. Other than that I can only suggest getting a 'microsoft approved' copy of windows or a better warez source  :razz:

---

### Post by kennny2004 on 2005-08-20
well thanks anyways for  the replys at least i learned few things lol yah i am not filling like spending 300 bucks on xp i guess i will stick to linux then lol

---

### Post by mcmuffy on 2005-08-20
Don't forget at least the same again if you wanted office and again if you wanted a development system.  :roll:

---

### Post by Oxygene on 2005-08-20
[QUOTE=kennny2004]well thanks anyways for  the replys at least i learned few things lol yah i am not filling like spending 300 bucks on xp i guess i will stick to linux then lol[/QUOTE]
 If spending money on software is not your thing, linux and free software in general is something for you indeed.

---

### Post by kennny2004 on 2005-08-20
nah i don't mind spending cash on software i got a lot of games i just don't like going overboard! :???:

---

