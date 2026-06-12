---
title: "Get the following error message when trying to install on /dev/sdc"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by travis28 on 2015-02-14
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Calibri]“The attempt to mount a file system with type swap in SCSI5(0,0,0), partition #2 (sdc) at none failed.[/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT="Calibri"][COLOR=#000000]You may resume partitioning from thepartitioning menus”[/COLOR][/FONT]

---

### Post by steeldriver on 2015-02-14
Hello and welcome to the forums

A bit more context for your question would be nice - what install method? where exactly are you in the process? did you choose the "something else" partitioning option? - however what it looks like is that you are trying to create swap space on a **disk** (/dev/sdc) instead of on a **partition** (which would be something like /dev/sdc1, /dev/sdc2 etc.)

---

