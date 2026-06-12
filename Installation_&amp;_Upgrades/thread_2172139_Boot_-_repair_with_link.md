---
title: "Boot - repair with link"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by EkDEAzf on 2013-09-03
Hello all,

I installed Ubuntu 12.04.3 amd64 onto my Toshiba Satellire A305-S6839 labtop. 

After installing and restarting I get the following message: Kernel panic - not syncing: No init found. Try passing init= option to kernel. See Linux Documentation/init.txt for guidance. 

I looked at the document and checked my architecture to see if is supported. I appears from my end that it is. 

After googling I ran across boot-repair and followed the instructions and performed the Recommend Repair.   

So continuing to follow directions I'm here now asking for your help. =)

The following is a link to the boot info:
[http://paste.ubuntu.com/6059163/](http://paste.ubuntu.com/6059163/)

Cheers,
Chuck Rock

---

### Post by oldfred on 2013-09-03
Welcome to the forums.

If you hold shift down from BIOS, do you get grub menu. And can you try recovery mode, second menu entry. Or just hit down arrow once right after BIOS.

What video card/chip do you have?

---

### Post by EkDEAzf on 2013-09-04
Howdy OldFred thanks for welcoming me to the forum!


If you hold shift down from BIOS, do you get grub menu. -- In BIOS (that cool grey and blue screen) the header reads "InsydeH20 Setop utility rev. 3.0".

When I press shift, nothing happens.
 
And can you try recovery mode, second menu entry. Or just hit down arrow once right after BIOS. -- Recovery gives me the same 
error as pressing enter as the main Kernel panic - not syncing: No init found. Try passing init= option to kernel. See Linux 
Documentation/init.txt for guidance. 


I can press 'e' to edit the commands before booting which is: 
setparams 'Ubuntu, with Linux 3.80-29-generic'


recordfail
gfxmode $linux_gfx_mode
insmod gzoi
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root c9fd8eb4-8a09-42ee-8ca5-9319aa382f36
linux /boot/vmlinux-2.80-29-generic root=UUID=c9fd8eb4-8a09-42ee-8ca5-9319aa382f36 ro   quit splash $vt_handoff
initrd /boot/initrd/img-3.8.0-29-generic




I can also press 'c' for a command line which bring me to the GNU BRUB version 1.99-21ubuntu3.10




What video card/chip do you have? Specs Link: [http://www.cnet.com/laptops/toshiba-satellite-a305-s6839/4507-3121_7-32906241.html](http://www.cnet.com/laptops/toshiba-satellite-a305-s6839/4507-3121_7-32906241.html)


Video Card: ATI Mobility Radeon HD 3470 - 256.0 MB 
 


I can use the live USB and run Root-repair, but after several trys noting chanings. 


I hope the information I provided helps, and if any more inforamtion is needed i'll be sure to get it. 


Also, I have been trying diffrent approaches to fix by following some 


Also, I ran boot-repair again: [http://paste.ubuntu.com/6061577/](http://paste.ubuntu.com/6061577/)


After running the boot-repair I recieved the following errors in the terminal:
(glade2script:5974): Gtk-WARNING **: Attempting to store changes inot '/root/.locla/share/recently-used/xbel'. but failed: failed to create file
'/root/.local/share/recently-used.xbel.Q11X2W': no such file or directory 


(glade2script:5974): Gtk-WARNING **: Attempting to store changes inot '/root/.locla/share/recently-used/xbel'. but failed: 
no such file or directory 




Cheers,
Chuck Rock

---

### Post by oldfred on 2013-09-04
Are you getting grub menu by default. Normally with just one system, menu is not shown. But it will usually show menu after a boot failure or crash.

Use e on grub menu and change quiet splash to nomodeset. 
linux /boot/vmlinux-2.80-29-generic root=UUID=c9fd8eb4-8a09-42ee-8ca5-9319aa382f36 ro [COLOR=#ff0000]quiet splash[/COLOR] $vt_handoff

It looks like you hand copied your boot stanza. A lot of work :) , but if you look at BootInfo report you will see the boot stanza as it outputs the entire grub.cfg file.

Boot-Repair backups and stores temporary things. It looks like some error on trying to write some of that data as a temporarily folder does not exist. Do not think that is really an issue.

Nomodeset set works for many video issues. But I do not know AMD. Also some issues like you seem to be having may also need nomodeset and other boot parameters, but try just nomodeset first.

some more info, I think yours is now a legacy version, so you do not want to install the current AMD drivers as they do not support your version. Current driver is 5000 series or newer.

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)

---

### Post by EkDEAzf on 2013-09-07
Appologizes for the late reply...

So I change quiet splash with nomodeset and press F10, but when I go back to edit command its changed back to quite splash... no idea how to save these changes. 

The funny thing is that on live USB it boots up fine.

Also, 
Grub> boot
error: no loaded kernel

Cheers,
Chuck Rock

---

### Post by oldfred on 2013-09-08
It is a one time boot change and you have to boot immediately after the edit with control x or whatever. Normally you do not want nomodeset as a permanent parameter. You install the proprietary drivers that match your system. With your old AMD, the current AMD may not apply. Not sure if then you install a legacy AMD or configure the open source driver so it works. I have nVidia so I do not know details of AMD issues.

If you now are getting grub> then you need to run Boot-Repair or reinstall grub to MBR as something is out of sync. Often grub inconsistency or menu or other boot files now missing.

---

### Post by VMC on 2013-09-08
That must be an old Radeon graphics chip, as this [2009 topic]("http://ubuntuforums.org/showthread.php?t=1067164&p=7040562#post7040562") shows. It lead me to this [AMD/ATI support page]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide"). I have a really old laptop, with a Radeon, that I have to use "radeon.modeset=0" permanently on grub.

Make sure you read this section on that AMD/ATI page: "Installing Proprietary Drivers a.k.a. Catalyst/fglrx**"**

---

