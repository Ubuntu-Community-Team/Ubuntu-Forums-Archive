---
title: "Upgraded to Feisty - Gnome is b0rked"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by 8oluf7 on 2007-04-20
I upgraded to Feisty from an up-to-date Edgy installation using the 'click here' offered by Update Manager.

When I login the screen displays the default light brown with a white stripe at top and bottom. WAIT for 60 seconds. Icons appear on the white stripes. WAIT for 90 seconds. Desktop background from Edgy appears, with the icons I had on it before the upgrade. Right click on a folder icon and select 'Browser Folder'. WAIT for 60 seconds. File manager window opens.

Close file manager window - desktop icons have vanished.

Trying to get to the file system through 'Places' on the menu bar doesn't work any better. However, click on an application icon e.g.Thunderbird and everything works normally.
 
Breezy was OK; Edgy took longer to reveal the desktop - but this is ridiculous!

Any suggestions as to what is causing this and how I fix it would be much appreciated.

BTW the link to the 'shared folders' on my XP machine is totally broken.

---

### Post by Big_J on 2007-04-20
How old is your computer???

---

### Post by 8oluf7 on 2007-04-20
About two years old.

It has an Athlon64 3200 and 1GB RAM so it isn't a 'horsepower' thing.

---

### Post by Big_J on 2007-04-20
wow, and it takes you a few minutes to load. Something is very bad.
I have an old sempron that loads gnome and gets ready in less than 5 seconds.

---

### Post by 8oluf7 on 2007-04-21
Got it!

Did what I should have done in the first place - read the logs (System > Administration > System Logs).

Sure enough, there was an SMB lookup that was failing to find something - and retrying several times after an interval. Which all adds up to the sort of delays I was experiencing.

I uninstalled SAMBA and SMBFS completely (to remove the config. files) and restarted the machine. The Gnome desktop now arrives much more quickly. 

Now all I have to do is remember how I set up samba and smbfs to enable me to access the shared files on the Win XP machine on my network! Ho Hum

---

