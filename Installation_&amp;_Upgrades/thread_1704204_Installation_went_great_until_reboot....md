---
title: "Installation went great until reboot..."
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by tbhesswebber on 2011-03-10
When I rebooted the computer after installation, it took me to XP, which I had told the computer to overwrite.  How do I get it to automatically take me to Ubuntu?  I assume in BIOS, but I don't know where Ubuntu was installed to.  Is there a way to check?

I don't know if it makes a difference, but I installed it from a flashdrive.

Thanks in advance for any help.

---

### Post by An Sanct on 2011-03-10
Welcome to the forums!

Well, it depends on *how* you installed, if you selected to use the whole disk, as the single OS, then it should have used the space XP used before.

If you are on a live USB, can you tell us what results you get, running this command in terminal (Applications>Accessories>Terminal)
```
sudo fdisk -l
```
This will list all the partitions on your disks

---

### Post by tbhesswebber on 2011-03-10
Are you saying to do this from XP?  I'm not seeing anything called terminal except hyper terminal.  Unless you meant to use the command prompt...

---

### Post by An Sanct on 2011-03-10
No, from XP, Right click on "My Computer" select "manage" and in the treeview on the right select "Disk management"

This will show graphically how your disk is partitioned.

If you could provide a screenshot of just that window, we can assume what happened.

PS. Ctrl + [Print Screen] will take a snapshot of the whole desktop, you can then crop it in paintbrush.

---

### Post by tbhesswebber on 2011-03-10
Heres the screen shot

---

### Post by An Sanct on 2011-03-10
On disk 2, there is a "healthy, unknown partition" is it possible, that Ubuntu is there?

If you restart the computer, do you see something like this?
[IMG]http://www.davestechsupport.com/blog/images/grub.png[/IMG]

---

### Post by tbhesswebber on 2011-03-10
No, when i restart, it just takes me through the standard XP loading screens.

---

### Post by tbhesswebber on 2011-03-10
And disk 2 is my external harddrive, which I just replugged in not long ago, but after giving up on Ubuntu

---

### Post by An Sanct on 2011-03-10
Hm ... if you realy wish to go to Ubuntu, try a reinstall.

---

### Post by tbhesswebber on 2011-03-10
I would love to go to Ubuntu.  I am attaching a picture of the same screen as before, but without my normal external and with the external that I used as the installer for Ubuntu.  The management screen recognizes that its there, but it does not give me the option of opening it in my computer. Any ideas?

---

