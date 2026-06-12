---
title: "The Horror"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by koulanji on 2007-04-21
So I decided to upgrade from 6.10 to 7.0.4 by using the normal upgrade methods stated in the instructions. However, once doing so, I return to find that my xserver has crashed. The nvidia-glx of course could not be loaded due to kernel conflict. I decided to purge the old version of envy and grab envy 0.9.2, which is supported by feisty fawn. I tried cleaning any nvidia driver that I had installed on it and reinstalling the drivers itself. After I reinstalled the drivers, I got the following errors:

So after installing the drivers, I get a message stating that errors were encountered while processing nvidia-glx

rm: cannot remove /usr/share/envy/*.deb No such file or directory

rm: cannot remove /usr/share/envy/*.asc No such file or directory

rm: cannot remove /usr/share/envy/*.changes No such file or directory

Then it tries to start the x-server and i get sudo: /etc/init.d/kdm: command not found

The last one is very interesting since I am not using kdm at all. I emailed the guy in charge of the script and he told me that these errors were completely normal and he told me to try this:

[Type:

sudo /etc/init.d/gdm stop (if you use GDM)
OR
sudo /etc/init.d/kdm stop (if you use KDM)

Then:
startx -- -verbose 5 -logverbose 5

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C
(select NO if it asks you if you want to see the output of the error or
something like that)

Then type this in order to copy the output of the error to your home folder:
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
sudo nano /etc/X11/xorg.conf
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
sudo /etc/init.d/gdm restart (if you use GDM)
OR
sudo /etc/init.d/kdm restart (if you use KDM)]

I followed those instructions and everything went smoothly until I tried restarting the gdm, which would not start at all, because according to ubuntu there is still a problem with the xserver.

I then emailed the guy in charge of the script and i was told to this:

[ls /etc/X11/

and find the backup of your xorg.conf

then type:
sudo cp /etc/X11/name_of_the_backup_file /etc/X11/
] However, when I typed the second command, I was told that the backup file had the same name and it would not copy. Does anyone have an alternate fix to this, because I would really like to regain my gui. I should mention that I am using an NVIDIA 7600GT 256MB

---

### Post by raja on 2007-04-21
> **koulanji said:**
> 
then type:
sudo cp /etc/X11/name_of_the_backup_file /etc/X11/
] However, when I typed the second command, I was told that the backup file had the same name and it would not copy. 

Did he want you to restore the backup as the actual conf file? In that case, the command should be ```
sudo cp /etc/X11/backup_file /etc/X11/xorg.conf
``` The command in its present form would generate an error since you are copying into the same folder without giving a new name.

---

### Post by koulanji on 2007-04-21
[
Did he want you to restore the backup as the actual conf file? In that case, the command should be
Code:

sudo cp /etc/X11/backup_file /etc/X11/xorg.conf

The command in its present form would generate an error since you are copying into the same folder without giving a new name.]

Sorry man, I tried that and I still have no GUI whatsoever. I've pretty much run out of options. Does anyone have any suggestions besides a fresh install?

---

### Post by Levenly on 2007-04-22
I'm having the same problem too.  I saw that there were errors when upgrading the feisty, and the update manager kept saying "aborting upgrade" so I figured I had nothing to worry about.  I saw this error about 4 times though so I'm sure I might have more problems...

---

