---
title: "Problem dual booting ubuntu and windows 8.1"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by Jose_L on 2015-01-15
Hello all,

I installed ubuntu on my PC the other day as a dual boot alongside windows 8.1. Ubuntu installed fine but now I cannot get Windows 8.1 to show up in GRUB when I bootup the computer. The only OS that shows up is Ubuntu. I used bootrepair and I think this is where the problem began as I am failry sure I messed up something when I was partitioning the drive. Here is the the record of the boot repair:

[http://paste.ubuntu.com/9740429](http://paste.ubuntu.com/9740429)

Any help is greatly appreciated! Thanks!

---

### Post by grahammechanical on 2015-01-15
> [COLOR=#BB4444]1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.[/COLOR]

In the Boot Repair report I see Linux partitions but not a Windows partition listed as having Windows in. Another point to consider; Windows 8 is usually installed in EFI mode and that means we must install Ubuntu in EFI mode. Otherwise, the Ubuntu bootloader will not be able to load Windows 8.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by Jose_L on 2015-01-17
Thanks for your reply graham.

After further tinkering, I think I have made things worse. 

I downloaded and tried to booth windows 8.1 to do a fresh install and that didn't work. I got the file from [here]("http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media").

When I boot from the USB where that file is located I get this error screen:


[ATTACH=CONFIG]259318[/ATTACH]


If I press F8 I get the following:

[ATTACH=CONFIG]259319[/ATTACH]

And if I select any of the options I get the same error screen (the one from the first picture).

Now, if I boot from the ubuntu usb I get this screen:

[ATTACH=CONFIG]259320[/ATTACH]

For some reason the system isn't picking up that I had already installed ubuntu. It's like it isn't finding ubuntu or windows 8.1 installed.

And finally if I start up the computer with no usb sticks attached I get this:

[ATTACH=CONFIG]259321[/ATTACH]



So that's where I'm at right now! At this point, I just want to get windows 8.1 working again (my original OS) since school starts in 3 days and a working computer would be nice. Any help would be appreciated!

---

### Post by oldfred on 2015-01-18
Think the only way will be start over. And officially your Product key is only valid for the OEM version that came from the vendor. You should contact your hardware vendor to see if you can get a recovery set of DVDs. Some only charge a nominal shipping fee.
A full new install of Windows will require you to pay for a new license within 30 days.

Windows requires either a blank drive or partitions that it expects. And how you boot install media is how it installs. So if you boot in UEFI mode then it installs in UEFI mode with gpt partitioning, If in BIOS mode it installs in BIOS mode with MBR(msdos) partitioning.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

