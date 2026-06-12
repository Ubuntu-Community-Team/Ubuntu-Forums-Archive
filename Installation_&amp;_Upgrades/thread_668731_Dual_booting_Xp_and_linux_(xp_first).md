---
title: "Dual booting Xp and linux (xp first)"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by pain1337 on 2008-01-15
i need help  i booted the cd and then the ubuntu stuff came on and i went tio the install thing and im stuck here what do i do please help

[http://i157.photobucket.com/albums/t79/phatfatd/Screenshot-Install.png](http://i157.photobucket.com/albums/t79/phatfatd/Screenshot-Install.png)

---

### Post by pain1337 on 2008-01-15
wow thanks for helping :(

---

### Post by &amp;wP*!) on 2008-01-15
I have edited my answer because I have not opened the picture you have shown.

If you choose "use entire disk" it means that Ubuntu installer will format the complete harddisk, which means to you that you will lose your Windows XP.
DON'T DO THAT! (unless you are an experienced user. You are not, otherwise you would not have opened this thread).

Choose manual and tell us the partition information.

You must empty some partition so that Linux can install itself! You can do it in Ubuntu installation but they said NTFS/FAT32 partitions corrupted which might result that you will lose Windows XP again.

You have 250 GB harddisk. Does it have 1 partition? If yes then resize it in Windows XP first. Don't install Ubuntu. Resize the partiton in such a way that it will create an unused partition area, like 20-40 GB. This is enough for you. Then install Ubuntu and choose "Manual" in the menu above.

---

### Post by RockHaxor on 2008-01-15
Personally I defrag Windows and then use Partition Magic to resize Windows XP ( this I believe is the safest way) and then create the 3 other partitions I will need (home, swap and /) in gparted.

Backing up your files is the best bet, I use an external hd to store my important data. I usually find myself reinstalling Windows every 6 months anyway (its like spring cleaning).

When you finally get to the screen you posted above use the manual entry and create your home swap and root directories. ( the home folder is useful to set up, its like a My Documents folder in XP and if you reinstall ubuntu at a later date you won't lose all your data stored there) A good rule of thumb: swap file twice your RAM, / (root) 10 GB, and the rest your home folder.

good luck!

---

