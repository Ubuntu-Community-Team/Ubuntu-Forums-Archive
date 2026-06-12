---
title: "WinXP has vanished from GRUB!"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Dark_Jester on 2008-05-16
I am still a beginner and don't know how to fix this one. Probably simple. 

I started Ubuntu on my dual booting laptop, and noticing that there were package updates available, got them. This required a reboot, so I let it - only to find that Windows XP had vanished from my GRUB menu and now I can't reach it! 

Any help would be greatly appreciated, as I desperately need to do some work in Windows before Tuesday.

---

### Post by dppowell on 2008-05-16
Just a quick reply to tell you that you'll be fine and not to panic.  I think this just entails an edit to your grub.list (?) file.  I haven't dual-booted in ages, so I don't remember the exact name/location of the grub config file...someone will have a proper answer for you soon (if they haven't already by the time I finish typing this)!

---

### Post by rlcomstock3 on 2008-05-16
You need to check to see if the partition has been delete, chances are it is still there, and all you need to do is to setup the grub menu again.  

Here are the steps you can take to figure it out...  Boot ubuntu then look for the mounted partitions, is your winxp there?  If so then just look at the grub config file...  (I use vim)  /boot/grub/menu.1st

After your Ubuntu (at the bottom of the file) you should see the windows part... mine is as follows...

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title    Microsoft Windows XP Professional
root     (hd0,3)
savedefault
makeactive
chainloader +1

If you don't have that then add it, you will need to change which partition it is, that is the root (hd0,3) part to match your partition for your local system.  

I hope that helps.

---

### Post by Dark_Jester on 2008-05-16
I can't see my WinXP partition in the list of places in the file browser, but I found it in the list of partitions for the drive in device manager. I have no idea how to get it back to GRUB.

---

### Post by Dark_Jester on 2008-05-16
How can I see a list of the partitions on the drive including their HD(0,1,2) codes so I know which one to put in my GRUB menu.lst?

---

### Post by rlcomstock3 on 2008-05-16
What is the output of

$ ls /dev | grep sd

Then I need the output of 

$ df -h

We might be able to figure it out from there.

---

### Post by zvacet on 2008-05-16
```
sudo fdisk -l
```

For example: if you after runing above command see your win partition on hda3 you will do this 

```
gksudo gedit /boot/grub/menu.lst
```

and you will add below this line 

# This entry automatically added by the Debian installer for a non-linux OS

title              Windows
roootnoverify      (hd0,2)
chainloader +1

save file and close.After reboot you will see win on grub.

---

