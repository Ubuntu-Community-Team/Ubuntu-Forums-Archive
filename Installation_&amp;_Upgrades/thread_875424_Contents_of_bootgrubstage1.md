---
title: "Contents of /boot/grub/stage1"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by clbaines on 2008-07-30
I need to know if this is a text file. I did an upgrade to 7.04 and 
it now is a binary or garbage. Anybody know.

 I would also like to get an unmodified copy of ubuntu 7.04 /boot/grub/menu.lst.

---

### Post by crwmike on 2008-07-30
stage1 is a binary file, it is what grub installs into the mbr

---

### Post by Herman on 2008-07-31
For an unmodified /boot/grub/menu.lst file, you can make a backup copy of your present /boot/grub/menu.lst file and call it /boot/grub/menu.lst.backup or something like that.
Then, delete your current /boot/grub/menu.lst and run update-grub.
Update-grub is a script which will automatically generate a new /boot/grub/menu.lst file for you if none exists, or update your /boot/grub/menu.lst if there is one already.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``````
sudo rm /boot/grub/menu.lst
``````
sudo update-grub
```Type 'y' when you are informed that update-grub 'Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N)'.

Now you will have a stock standard /boot/grub/menu.lst file. Do what you like with it.

If or when you want to restore your original /boot/grub/menu.lst file from your backup copy,
```
sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst
```Regards, Herman :)

---

