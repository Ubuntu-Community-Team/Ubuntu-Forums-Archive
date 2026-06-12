---
title: "Can't boot Ubuntu. Getting busybox. :("
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Jbknight3 on 2009-11-20
I'm Super new to Ubuntu, so please bare with me here. Also i know there are alot of posts about this, but none of them helped me specificly. So here is what's happening.
 
First off. The Wubi installer is not functioning like it should be. I double-clicked the installer and it gives my like 20-30 errors messages saying something about putting in a disk... After all of the messages, it finally started Wubi installer and I successfully installed Ubuntu to my External Hard Drive, seeing as how my primary drive is only 30GB with only 12GB free. (also my external is NTFS format and I cant change it unless I burn a crap-load of backup disk for all the files.)
 
Secondly, when I reboot the computer (with Start > Restart, not forcing it to shutdown), and select to load Ubuntu, it says 2 lines of stuff then the screen goes black. I then hit the enter key so I would have more then just a black screen, and it gave me some "Busybox" and "Initramfs" stuff which i have no idea what it's talking about. Anyways, Ill have an attachement with the screen shot of it. 
 
Tell me what you need to know and Ill do my best to give you the information.
 
So any help on getting it to run would be appreciated. Thanks In Advance!
 
_____________________
 
Jon

---

### Post by neoscreenager on 2009-11-20
press "esc" at boot after selecting "Ubuntu", choose "Verbose Mode" . That will provide more information.Also post the information here. You can also check window side installation logs in your temp folder (%temp%).

Since you are using an external disk, problem might be in identifying the disk. Have you put your wubi installer in that external disk and then have it run from there? If not, try to uninstall wubi and then attach your external disk,paste installer in it, fire it from there. Make sure that the "installation drive" selected is your external drive. Then click on install and see what happens.

---

### Post by neoscreenager on 2009-11-20
also let us know that your external disk is usb or not.. your bios might not support booting from usb devices.

---

### Post by Jbknight3 on 2009-11-21
Yes, my external hard drive is USB. And I did do "Verbose mode" after pressing "escape" and like 50 lines of text showed up. So now I need to know what lines of text would be helpful to figure this problem out. Thanks in advance.
 
__________
 
Jon

---

### Post by Jbknight3 on 2009-11-21
Bump. Still need help. Anyone?

---

### Post by neoscreenager on 2009-11-27
does your system supports boot from usb hard disk.. because if it dosen't then you would not be able to boot from the external drive.
If bios support booting from usb device, then simply put copy wubi installer on ur usb disk and install ubuntu there, then select boot from usb option in bios and boot from there.
Or you can simply install ubuntu through wubi on your windows(ur fixed disk) and then move wubi ubuntu install to ur external USB drive. You can find how to do this here:::
[http://www.pendrivelinux.com/move-wubi-ubuntu-install-to-an-external-usb-drive/#more-507](http://www.pendrivelinux.com/move-wubi-ubuntu-install-to-an-external-usb-drive/#more-507)

---

