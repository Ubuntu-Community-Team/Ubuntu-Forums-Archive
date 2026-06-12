---
title: "HP Mini, not booting properly"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by Checkeroogle on 2012-11-29
Hey, I don't post often, but I'm having this problem with an HP Mini 311. I've installed Ubuntu 10.04, and it runs like an absolute dream from the Live USB. 

However, when I boot from the Hard Drive, all I get is the flashing cursor, no ISOLINUX, grub, or anything of that sort. I can post boot information upon request. It would be great if anyone would give me a solution, I already tried reinstalling.

---

### Post by oldfred on 2012-11-30
Are you dual booting or do you get grub menu, then cusor?

Or if you hold shift key from BIOS until menu appears do you get a menu or the flashing cursor.

If you do not get grub menu, run Boot-Repair on post link for Bootinfo report. If you can get grub menu it probably is a video issue.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
What video chip? and can you add nomodeset at grub menu as explained here:
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Checkeroogle on 2012-11-30
> **oldfred said:**
> Are you dual booting or do you get grub menu, then cusor?

Or if you hold shift key from BIOS until menu appears do you get a menu or the flashing cursor.

If you do not get grub menu, run Boot-Repair on post link for Bootinfo report. If you can get grub menu it probably is a video issue.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
What video chip? and can you add nomodeset at grub menu as explained here:
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Not dual booting. No grub menu, nothing. As soon as it goes to boot from hard drive, cursor.

---

### Post by oldfred on 2012-12-01
Then post link to BootInfo report.

---

