---
title: "Can't boot into Windows 7 anymore"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by Abhishek_Kher on 2013-09-07
I just installed ubuntu 12.04 yesterday alongside Windows 7. I decided to go ahead and try to install 13.04 today and loaded it up on a bootable usb. I have a 500gb hdd + 25 gb ssd so the RAID data from the intel software was preventing the installer from recognizing the partitions. I tried to boot into windows to disable acceleration from intel smart response technology (this worked when I was installing 12.04) but there was no longer a Windows 7 boot option on the GRUB menu. I ran BootRepair but it did not help. The url it gave me was [paste.ubuntu.com/6076833]("http://paste.ubuntu.com/6076833/"). Thanks for the help everyone!

---

### Post by Coder88 on 2013-09-07
1. Where did you install Grub2, to your linux drive or to the Windows 7 drive?
2. Can you still boot into your linux system to edit Grub2 config files?
It used to drive me nuts not getting Grub to boot Windows, especially Windows 7, but now I have a pretty good handle on taming that beast, pretty easy now really. About ten minutes editing a file and running a couple of terminal commands and you will be good to go. I will check here tomorrow, bagging it for the evening here.

---

### Post by Abhishek_Kher on 2013-09-07
Yeah I actually figured I would just purge Grub and reinstall it onto each drive using Boot Repair, but that didn't help with my problem. So now it's installed on the drive I have ubuntu on and the drive with windows 7. Boot Repair gave me the url of [paste.ubuntu.com/6077202]("http://paste.ubuntu.com/6077202") after the reinstallation of grub2. I can boot into linux through grub and its working fine, I just can't boot into windows. Thanks again for the help

---

### Post by Coder88 on 2013-09-07
> **Abhishek_Kher said:**
> .... I can boot into linux through grub and its working fine, I just can't boot into windows. ...

Been there many times, no more! The key is editing 
/etc/grub.d/40_custom
and knowning what to put in the lines in that config (text) file. 

First do this of course (backup the file):
[FONT=courier new]$sudo cp /etc/grub.d/40_custom /etc/grub.d/40_custom.backup[/FONT]

So here is my 40_custom file that I also commented to show how to figure  out what to put in the file. You can edit your file with (use any text editor, i like gedit):
[FONT=courier new]$sudo gedit /etc/grub.d/40_custom[/FONT]
and all you need to do is copy what I have below then change what I have boldfaced (hda1, and the long hex code identifier).

As you will see in the comments of the 40_custom file, use
[FONT=courier new]$sudo blkid[/FONT]
to figure out the long hex code parameter to go with --set=root   The blkid command will show you the UUID (the long hex code) associated with your Windows 7 drive; you will see what I mean when you run that command. Look at my sample 40_custom file contents here below to see what I mean. Note that the hda1 and **BAFE4EDCFE4E9119** are for my Windows 7 not yours. The 'sudo blkid' command will get you that long hex code to replace mine for use in your 40_custom file. As for the hda1 that is also for my system, and you can pretty much figure it out by trial and error (or probably some other more rational way) when Grub boots by just using the down arrow to highlight the Grub2 option for Windows 7 and then tapping the 'e' key to edit that Grub2 boot entry at boot, and just try hda2 or hda3 or whatever depending on how your Windows 7 disk is viewed by Grub. on my system Windows 7 is on /dev/sda1 thus the hda1

Report back and let me know how it works. And remember, once you edit and save your /etc/grub.d/40_custom file be sure to 'sudo update-grub' before you reboot to hardware that file into the Grub menu.[INDENT=2][COLOR=#0000ff]
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#
# Remember to run 'sudo update-grub' after editing this file!
#
# This file exists in /etc/grub.d
#
# Use 'sudo blkid' to get '--set=root' code for Windows 7 disc partition
# and proper /dev/sdx device
#
# This info came from
# [http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition](http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition)

menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    insmod ntldr
    set root='(**hd1**,msdos1)'
    search --no-floppy --fs-uuid --set=root **BAFE4EDCFE4E9119**
    ntldr ($root)/bootmgr
}[/COLOR]
[/INDENT]



Then: 
[FONT=courier new]$sudo update-grub
$sudo shutdown -r now[/FONT]
You should see a listing in Grub when you restart so you can boot into Windows 7.

---

### Post by Coder88 on 2013-09-07
Once you get grub2 fixed so you can boot into Windows 7 or Ubuntu, you might want to install this grub2 configuration tool, really nice.
[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

---

### Post by oldfred on 2013-09-08
Just to add a bit to Coder88's instructions.

If you are using BIOS to boot from the drive shown as sda, the the drive in grub will be hd0. So use [COLOR=#ff0000](hd0,msdos2)[/COLOR]
Your Windows boot partition is sda2.

 Boot-Repair shows your correct UUID for sda2 on line 141. So use this UUID
/dev/sda2 [COLOR=#ff0000]       E83AEC693AEC35EA[/COLOR]                       ntfs       System Reserved

---

### Post by Abhishek_Kher on 2013-09-08
> **Coder88 said:**
> [INDENT=2][COLOR=#0000ff] 
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    insmod ntldr
    set root='(**hd1**,msdos1)'
    search --no-floppy --fs-uuid --set=root **BAFE4EDCFE4E9119**
    ntldr ($root)/bootmgr
}[/COLOR]
[/INDENT]



So my Windows 7 boot data is on /dev/sda2, so do I also need to change that in line 1 along with hd1 to hd0 and the UUID?[B]

EDIT[/B]: I decided to trust my intuition and ran your code with a few changes, along with the recommendations of oldfred. In case anyone with a similar problem sees this post, here is the code I used for my own configuration.

[COLOR=#0000ff]menuentry "Windows 7 (loader) (on **/dev/sda2**)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    insmod ntldr
    set root='(**hd0**,**msdos2**)'
    search --no-floppy --fs-uuid --set=root [/COLOR][COLOR=#0000ff]**E83AEC693AEC35EA**[/COLOR][COLOR=#0000ff]     
ntldr ($root)/bootmgr
}[/COLOR]

I found that my boot data was stored on sda2 through gparted. 

Thanks so much for your help coder88 and oldfred! You have helped me out a lot today

---

### Post by Coder88 on 2013-09-08
So were you able to boot into Windows 7?  I got to thinking, worried you overwrote your Windows 7 MBR (master boot record, equivalent of grub) on your windows disc; if necessary you could always attempt to boot to Windows and drop into Windows' rescue mode and restore the MBR. Grub kind of depends on their being an MBR on the Windows drive, but Windows always keeps a hidden backup copy of the MBR that you can restore if needed.

[COLOR=#0000ff]
[/COLOR]Looks like you found your long hex code to use via the blkid command. Just a matter then of being sure your Windows disc has an MBR, and figuring out that set root='(hdx,msdosy)' and figuring what the value of x and y are.

As for line one below, you can really make that anything you want (the stuff in quotes), for example you could have:

[COLOR=#0000ff]#menuentry "Windows 7 (loader) (on **/dev/sda2**)" --class windows --class os {
[COLOR=#0000ff]menuentry "My fantastic Windows 7 system" --class windows --class os {[/COLOR]
insmod part_msdos
    insmod ntfs
    insmod ntldr
    set root='(**hd0**,**msdos2**)'
    search --no-floppy --fs-uuid --set=root [/COLOR][COLOR=#0000ff]**E83AEC693AEC35EA**[/COLOR][COLOR=#0000ff]     
ntldr ($root)/bootmgr
}
[/COLOR]  

Study [http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition](http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition)

---

