---
title: "Repairing/restoring GRUB"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by alanh on 2006-06-27
I'm new to Ubuntu and recently installed 6.06 on a PC, with XP, from the Live CD.   Everything was working fine with the dual boot but, unfortunately, I couldn't just leave well alone :(  and decided to try another boot manager - Paragon Boot Manager.  When I rebooted the PC the boot manager did not recognise the linux installation.  I returned to the Paragon boot manager set-up and found an option to reuse the previous MBR (which was apparently backed-up).  I selected this and the boot manager now gives me an option to boot with the "GRUB MBR sector", as well as the floppy and XP.  Unfortunately, when I select that option I get a screen full of the word "GRUB" which is constantly updated.  Any ideas on what I've done and on how to fix this?

Thanks

---

### Post by zxee on 2006-06-28
From the live cd you should be able to re-install grub. Say your ubuntu install is on /dev/hda2 *
code: sudo mount /dev/hda2  *
code: chroot /dev/hda2 *
code: grub
At this point you should be in grub which looks like this: grub>
type: find boot/grub/stage1
the above command should give you a response in grub notation e.g. (hd0,1)
*If your install is not on hda2 then you of course need to use the correct partition.
Remember grub starts counting from 0 so the example above is as grub would see hda2=(hd0,1) 
To get grub configured after the find command (above) outputs the ubuntu partition just type:
setup (hd0,1) *again use the correct drive/partiton #'s the entries here are just an example.
Then hopefully you can reboot and boot into ubuntu.

---

### Post by alanh on 2006-07-01
Many thanks for this, I'm back up and running.  In case it's of any help to others, here's my experience.

It took me a little while, as I didn't realise that I had to define a mount point in step 1 (I'm a real newbie to Linux and haven't used UNIX for about 15 years).  I created a temp folder and mounted to that.  The second hurdle was a typo in the "find" command in grub>, there was slash missing at the beginning of the command.  After that everything went fine.  I also found the following thread useful:  [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=HOWTO%3A+restore+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=HOWTO%3A+restore+grub)

Thanks again.

---

