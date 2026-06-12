---
title: "HH upgrade w/..."
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by shalemjale on 2008-07-05
I made the upgrade to Hardy Heron and it went well. The only problems I have noticed so far are :
1- I cannot change the number of desktops ( I am stuck w/ 2)
2- Apps on the desktop cannot be moved (resized...yes....moved...no)

Any help would be greatly appreciated!

---

### Post by LinuxRocks713 on 2008-07-05
Is your GNOME Configuration bad? Try this in the terminal:

cd $HOME
mv .gnome2 .gnome2backup
mv .gnome2_private .gnome2_privatebackup
mv .gvfs .gvfsbackup

Then logout and log back in. (or restart)

---

### Post by shalemjale on 2008-07-05
LR713, This is what I got back. Restarted and still acting the same. Keep in mind that I am relatively new to Linux.

desktop:~$ cd $HOME
desktop:~$ mv .gnome2 .gnome2backup
mv: cannot move `.gnome2' to `.gnome2backup/.gnome2': Directory not empty
desktop:~$ mv .gnome2_private .gnome2_privatebackup
desktop:~$ mv .gvfs .gvfsbackup
mv: cannot move `.gvfs' to `.gvfsbackup': Device or resource busy

---

### Post by LinuxRocks713 on 2008-07-05
> **shalemjale said:**
> 
mv: cannot move `.gvfs' to `.gvfsbackup': Device or resource busy

Restart in recovery mode, and try this:

cd $HOME
mv -r .gnome2 .gnome2backup
mv -r .gvfs .gvfsbackup

Then type:

sudo shutdown -r now

which restarts your system. 

Try logging in again and see what you get.

---

### Post by shalemjale on 2008-07-05
still nothing...it shows

"mv: invalid option -- r"

---

### Post by LinuxRocks713 on 2008-07-05
> **shalemjale said:**
> still nothing...it shows

"mv: invalid option -- r"

Well, if your system can't move it, then as a last resort you can delete the setting. Beware that your favourite GNOME Setting will be reset to factory defaults.

Boot to recovery mode:

```

cd /home/*username*
rm -r .gnome*
rm -r .gvfs
# restart and login
sudo shutdown now -r

```

Now, it should work!

---

