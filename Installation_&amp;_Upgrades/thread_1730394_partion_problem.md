---
title: "partion problem"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by george.shoni on 2011-04-16
[COLOR=#000000][FONT=MS Shell Dlg 2][FONT=Calibri]I installed ubuntu10.4 .when I tried to make new partion .there is an error[/FONT][/FONT][/COLOR]
[FONT=MS Shell Dlg 2][COLOR=#000000][FONT=Calibri]mkfs.ext3: Device size reported to be zero. Invalid partition specified, or[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]partition table wasn't reread after running fdisk, due to[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]a modified partition being busy and in use. You may need to reboot[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]to re-read your partition table[/FONT] [/COLOR]
[COLOR=#000000]any one give replay..[/COLOR]
[/FONT]

---

### Post by falko on 2011-04-16
What exactly did you do (what commands?) when you created the partition?

---

### Post by Rubi1200 on 2011-04-16
If you are on a LiveCD/USB, please post the output of this command:

```
sudo fdisk -l
```
(lowercase L not 1)

---

### Post by george.shoni on 2011-04-18
> **falko said:**
> What exactly did you do (what commands?) when you created the partition?
 
I did this camaands
#fdisk /dev/sda
 :n
create partion size 
:w
#mkfs.ext3 /dev/sda4(new created partion no.)
then I got this error

---

