---
title: "Dual booat - can't find Windows 7"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Ironwil on 2011-02-12
I have two physical hard drives. One was to be used for OS installation, the other for storage. I partitioned the first hard drive into two large partitions, over 200GB each. I installed Windows 7 on the first partition and then installed Ubuntu 10.10 on the second one. I thought that Grub would find my different operating systems, but this didn't happen. I'm no longer able to boot into Windows. 

I recall from awhile ago when I used to do a lot of work in Linux (over 7 years ago) that I needed to do some manual editing of Grub to get all the OS's to work together. I had a machine booting 4 OS's at one time. However, that was a long time ago and I don't recall how to do it, or if it's still necessary. Now that I have both installed I'd rather not have to start over if it's not necessary. Can anyone advise me as to how to get the Windows OS to show up in Grub now?

---

### Post by wilee-nilee on 2011-02-12
Your referring to manual grub-legacy menu.list, you have grub2 though. The two are different grub2 should be picking up windows 7 automatically.

Have you in the ubuntu terminal run 
sudo update-grub.
If this doesn't fix it follow the next paragraph.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Quackers on 2011-02-12
Welcome to UF.
In Ubuntu, open up a terminal and run
```
sudo update-grub
```
then watch as grub.cfg is run to confirm that the Windows Loader is picked up. If it is, reboot and try to boot Windows from the new grub menu.
If the Windows Loader is not picked up please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Ironwil on 2011-02-12
Thanks for both of your replies. There were both right. I was running updates and left to run some errands. I came back, rebooted to complete the updates and Grub found my Windows 7 installation without issue.

---

### Post by Quackers on 2011-02-12
Glad to hear that -  enjoy  :-)

---

### Post by theozzlives on 2011-02-12
Please mark this Thread as solved.

---

