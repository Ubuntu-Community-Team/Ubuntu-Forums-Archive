---
title: "Can't boot windows 8 after install xubuntu 13.10 alongside windows"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by celso.gutierrez on 2013-12-08
Hi,
(sorry for my english, i'm latin)

I've installed xubuntu 13.10 alongside windows, and now i can't enter windows 8, i tried a lot of things included boot-repair and this is the last log [http://paste.ubuntu.com/6541783/](http://paste.ubuntu.com/6541783/), i think i messed up all :C. I can't reinstall windows because i've downloaded an iso and the key doesn't match with the bios one. I can't run the repairs in the windows install disc.

My machine its a lenovo g400s

Please help me :C

---

### Post by oldfred on 2013-12-08
It looks like you did the Ubuntu install to the entire hard drive. The only remaining part of Windows is the boot files in the efi partition, but you have no Windows c: drive or any other Winows NTFS partitions.

You may be able to contact Lenovo and see if they offer a image file for your computer at a nominal charge. Some vendors do, others do not. That would be a recovery image not a full Windows installer.

If you have a full copy of Windows, not an upgrade you should be able to install that. Do not know details, but Windows does not corectly see Linux partitions and your Ubuntu install may interfere with the new install. Also Windows may boot in both BIOS/CSM and UEFI modes from its install media. With gpt partitioning you need to boot in UEFI mode.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by celso.gutierrez on 2013-12-08
thanks for the answer!, in order to solve this problem faster, i did the following (not so closely related to ubuntu):
-Install win 8 from usb based on this guide [http://forum.notebookreview.com/asus/698920-installing-windows-8-pro-over-standard-oem-your-new-win8-certified-notebook.html](http://forum.notebookreview.com/asus/698920-installing-windows-8-pro-over-standard-oem-your-new-win8-certified-notebook.html) (the usb part its enough, dont need to burn a dvd)
-I had trouble selecting a drive to install , so i followed this guide: [http://forums.lenovo.com/t5/Windows-Base-de-conocimientos/No-se-puede-instalar-Windows-en-este-disco-el-disco-seleccionado/ta-p/1131345](http://forums.lenovo.com/t5/Windows-Base-de-conocimientos/No-se-puede-instalar-Windows-en-este-disco-el-disco-seleccionado/ta-p/1131345) to "reset" the hard drive
-Now i have my laptop working, but sadly without ubuntu, i hope to install it soon...
[U](note that i lost all my data)
[/U]
thanks again for the early reply!

---

