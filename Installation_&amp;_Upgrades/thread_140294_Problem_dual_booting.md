---
title: "Problem dual booting"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by cx323 on 2006-03-05
I recently got a new hard drive and i installed server 2003 on the main sata hard drive.  I then partitioned the other pata hard drive as storage and raw.  I went throught the kubuntu installation and partitioned the raw space as ext3 and a swap file.  Then i get to the installation of grub and it says is windows 2000/xp installed and i said yes and grub installed.  Then i rebooted and server 2003 loaded and grub never did.  What did i do wrong?

Thanks for any help

---

### Post by ffadmraven on 2006-03-05
Did you save GRUB to the MBR or somewhere else?

---

### Post by cx323 on 2006-03-05
yea, i saved it on the mbr

---

### Post by ffadmraven on 2006-03-05
Then it should have booted Grub.  I would retry the install, and verify that it is setting up GRUB correctly.  It might have accidently set it up to boot only the Windows partition instead of either or.

---

### Post by cx323 on 2006-03-05
sorry for the noob question, but how do i verify that?

---

### Post by ffadmraven on 2006-03-05
When it gets to the point of setting up GRUB, it should say something along the lines of :

The Following Operating Systems were found:
Windows 2000/XP

Would you like grub to add this to your start up choices? y or n

I would say Y, and then make sure you choose MBR for place to install, and that it was successful installing it.  the other option, is you can create a boot disk with GRUB installed on it, and that would bypass your harddrive altogether.

---

### Post by cx323 on 2006-03-05
i tried installing again and said yes and installed to the mbr.  it didn't give me any errors, but when i rebooted windows started.  could you give me a link or explain how to make a bootdisk with grub on it.  thanks

---

### Post by ffadmraven on 2006-03-05
I'm currently at work, but if you give me about an hour, I can get you that link.
Edit:

Ok, here is what I found off of gnu grub's faq.  I'm still looking for a way to do it from the ubuntu installer.

     4. How to create a GRUB boot floppy with the menu interface?
        Create a filesystem in your floppy disk (e.g. mke2fs /dev/fd0).
        Mount the floppy on somewhere, say, /mnt.
        Copy the GRUB images to the directory /mnt/boot/grub. Only stage1, stage2 and menu.lst are necessary. You may not copy *stage1_5.
        Unmount the floppy.
        Run the following commands (note that the executable grub may reside in a different directory in your system, for example, /usr/sbin): 

             /sbin/grub --batch --device-map=/dev/null <<EOF
             device (fd0) /dev/fd0
             root (fd0)
             setup (fd0)
             quit
             EOF

I'll post anything else I might find, as soon as I find it.

---

### Post by ffadmraven on 2006-03-06
Also, you might want to try ubuntu first, and then server 2003, and see if that works, and verify your jumper settings, your computer might be booting the server 2003 hardrive, and GRUB is on the other hard drive.  This would also cause it to not boot GRUB like it should.  Just a suggestion.

---

### Post by cx323 on 2006-03-06
thanks for all your help.  you were right that grub was on the wrong drive

---

