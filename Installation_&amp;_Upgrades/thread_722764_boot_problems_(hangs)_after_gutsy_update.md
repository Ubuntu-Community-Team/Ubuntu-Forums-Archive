---
title: "boot problems (hangs) after gutsy update"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by perler on 2008-03-12
after an upgrade from dapper to edgy to feisty  (where i had the "usplash problem") i now tried the upgrade to 7.10. gutsy

now booting into the kernel (with nosplash) hangs at random places, usually when checking scsi/usb/sata devices, the tape changer.

sometimes, i can get over this point with a ctrl-alt-del to get into single mode. from there i can start all services and use the server as i lilke, so basicaly everything seems to be fine on the hardware side.

i have the best chances to get to this point when the server was tuned off. noapic didn;t really help, the readout when the server hung was just different.

all previous versions booted just fine. 

for me, this looks like some race problem in udev or something along the line. the server is quite filled with hardware:

amd 64x2, asus 8n32 board, nvidia x300 graphics board
4gb ram
booting from 4 sata disks as raid5
2 ide hdd
adaptec 2940 scsi adapter
hp dds4 tape changer

is there a way to "safe boot" the server, with a lot of delays?

---

