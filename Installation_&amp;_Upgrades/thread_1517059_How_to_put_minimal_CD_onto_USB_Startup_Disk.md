---
title: "How to put minimal CD onto USB Startup Disk"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by entropy1 on 2010-06-24
I have downloaded the Ubuntu 10.04 "Lucid Lynx" Minimal CD.  I would like to use the Startup Disk Creator to put it on bootable USB.  However, when I run the Startup Disk Creator and click on "other" to select the downloaded .iso, my selection is ignored and does not show in the "Source disc" list of the dialog box.

Is there another way to create a startup USB from the minimal CD download?

---

### Post by kalistona on 2010-06-24
at least six different ways...
you are speaking about mini.iso.
it is done for usb and install remix.
maybe your usb creator is not for remix but for desktop version (see ubuntu.org : usb creator).
pendrivelinux is a site with 4 usb creator : unet bootin, universal creator,  usb live creator, ubuntu universal live creator,  etc...
do you want persistant ? 
casper rw is also on this site, but do not forget that not all iso accept persistance. 
they exist anothers and you can also mount yourself and create yourself your usb from ubuntu (terminal/console), i prefere use the soft !

---

### Post by mikewhatever on 2010-06-24
When the file browser opens, what's in the bottom right corner, 'CD images' or 'Disk images'. Try clicking there and changing the selection. That said, I am not quite sure the USB creator is suitable for writing the minimal iso.

---

### Post by oldfred on 2010-06-24
I like the method of just installing grub2 and loop mounting ISOs. I have 3 Uubntu's, one mini, system rescue, gparted, parted magic ISOs all installed on a 4GB with space for other data.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

---

### Post by shaftesburyiv on 2010-06-30
go to synaptic and download unetbootin ... it works 'perfectly', unlike the usb creator packaged with ubuntu.

---

### Post by C.S.Cameron on 2010-06-30
The method OldFred suggested works well with a lot of distros.
It has been automated, see:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

