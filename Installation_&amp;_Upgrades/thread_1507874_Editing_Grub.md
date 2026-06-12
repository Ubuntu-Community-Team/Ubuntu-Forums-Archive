---
title: "Editing Grub"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by jarviser on 2010-06-12
In simple terms I need to stop the Grub in 10.4 from recognizing a Windows restore partition.

History:- My son's Lenovo Thinkpad R60 with XP was becoming a dog, so I restored XP to factory settings from the restore partition, shrank the fresh windows partition with GParted, installed 10.4 with Mac4Lin, Cairo-Dock etc. All successful and he LOVES it.

Now on Boot, Grub recognises both Linux Kernels etc, and the XP boot partition, but annoyingly also the XP restore partition. 

On at least one occasion I have paged down too far and started the XP restore (No damage done, just waited and exited when appropriate)

It would be nice to delete the entry from Grub, but I understand this new Grub2 probes all bootable partitions every time it updates??  Can I tell it to ignore the XP restore partition?

---

### Post by wilee-nilee on 2010-06-12
Here is a link for a grub2 tutorial.
[grub2](http://ubuntuforums.org/showthread.php?t=1195275)
Here is the grub2 wiki.
[grub2 wiki](https://help.ubuntu.com/community/Grub2#Hidden)

I have seen the commands to remove this recovery or any grub entry but I didn't save them.

---

### Post by jarviser on 2010-06-12
So I have to make 30_os-prober unexecutable?  Will that not remove XP entry as well?


[I]Extract...

Removing Entries from Grub 2
Entries should be removed by editing or removing files in the /etc/grub.d folder. The /boot/grub/grub.cfg file is read-only and should not normally require editing.

    ..... snip
          .......
          o To prevent one of the /etc/init.d files from running, remove the "executable" bit.
                + Example: If you don't want to see the "Memtest86+" entries, run this command:
                  Code:

                  sudo chmod -x /etc/grub.d/20_memtest86+

                + Run the update-grub command to allow the changes to be incorporated in grub.cfg[/I]

---

### Post by wilee-nilee on 2010-06-12
> **jarviser said:**
> So I have to make 30_os-prober unexecutable?  Will that not remove XP entry as well?


[I]Extract...

Removing Entries from Grub 2
Entries should be removed by editing or removing files in the /etc/grub.d folder. The /boot/grub/grub.cfg file is read-only and should not normally require editing.

    ..... snip
          .......
          o To prevent one of the /etc/init.d files from running, remove the "executable" bit.
                + Example: If you don't want to see the "Memtest86+" entries, run this command:
                  Code:

                  sudo chmod -x /etc/grub.d/20_memtest86+

                + Run the update-grub command to allow the changes to be incorporated in grub.cfg[/I]

The only thing I can suggest is make sure you understand what your doing, I have never been a file editing person by and large, especially grub. There are users that are very good at this and on the forum since it so big different times of the day. So since you have a working system that you have spent some time getting set up, just be careful to know whats up, and wait for some help if needed.

I believe there is a straight command to just hide that recovery so the right person has to notice the thread and give it to you, the command is executed then a update-grub is run.

---

### Post by jarviser on 2010-06-12
Ah, you noticed I don't know what I am doing then! I just about got to know Grub 1 when Grub 2 happened!  It was easy to just edit menu.lst  

All improvement is change but not all change is improvement.

---

### Post by oldfred on 2010-06-12
IF you turn off the executable bit or set disable to true as I do you have to copy your entries to 40_custom.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by confused57 on 2010-06-12
Another possibility would be to set up a "06_custom" entry:
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)

You should be able to just copy & paste your Window's entry from your /boot/grub/grub.cfg, then the Window's selection would appear first in your grub menu, if that's what you would want.

---

### Post by jarviser on 2010-06-12
I have enough to have a go now, Thanks.

---

### Post by wilee-nilee on 2010-06-12
> **jarviser said:**
> Ah, you noticed I don't know what I am doing then! I just about got to know Grub 1 when Grub 2 happened!  It was easy to just edit menu.lst  

**All improvement is change but not all change is improvement.** 

That's a good phrase, can I use that one.;)

---

