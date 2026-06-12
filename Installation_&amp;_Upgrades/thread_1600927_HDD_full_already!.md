---
title: "HDD full already!"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by rick astley on 2010-10-19
I partitioned my primary HDD using Windows 7. I gave it 20GB and called the partition Linux, for easy reference. So I used the WUBI installer yesterday and everything installed fine. I rebooted and have been using Ubuntu 10.10 very happily for the past day. Then while in Ubuntu I get an error message saying "Only 136MB left on Disk."

Wondering how in the world 20GB could be full already after only installing a few programs, I booted back into Windows. I navigated to the folder which contains the Ubuntu files. This is what I saw:

[IMG]http://i.imgur.com/9zO8Y.jpg[/IMG]

This is a little strange! Three files of the exact same size. I am losing space triple-fold. Please advise!

Apprehensive,
Rick

---

### Post by SgtPepperKSU on 2010-10-19
Since you used WUBI instead of a normal installation, Ubuntu was not installed directly onto the partition you created.  Instead, files were created that act as mini pseudo-partitions.  The Ubuntu files are then created within those "partitions".  They're all the same (large) size because that is the size of the "partition".

If you want to see which "partition" is full, you'll need to do it from within Ubuntu.  Open a terminal and run the *df* command.  This should give you usage information for every mount (/ corresponds to root.disk, /home corresponds to home.disk and /usr corresponds to usr.disk).

Since you've already created a partition for Ubuntu, you may consider a real installation instead of using WUBI.  Note, though, that that would replace the Windows bootloader with GRUB (though, GRUB is perfectly capable of booting both Windows and Linux).

---

### Post by rick astley on 2010-10-20
Thank you for clarifying that! I ran the df command and here's what ubuntu had to say:

[IMG]http://i.imgur.com/4ZYcH.png[/IMG]

Can this remedy my original query?

I wouldn't mind doing a proper install of ubuntu on that partition but I would like to copy over all my settings. 
How can I achieve this? Thank you.

Rick.

---

### Post by P4man on 2010-10-20
Do a real install, and never ever do a wubi again. Ever. :)

To copy over your settings, there is no perfect  way (one more reason not to use wubi), but backup up your /home folder to a spare drive or USB stick and saving a list of all installed packages gets you close enough to a full migration:

```
sudo dpkg --get-selections > my-packages
```

Save that file somewhere. If you finished your new install, copy that file to your homefolder and run

```
sudo dpkg --set-selections <my-packages
sudo apt-get -u dselect-upgrade
```

That will install all apps and packages you had on the  wubi install (provided its in the repo's)

---

### Post by rick astley on 2010-10-20
Thank you for that P4man. I'll steer clear of WUBI in future!

rick.

---

