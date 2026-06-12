---
title: "XFS: Which UTF8 mount option in fstab?"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by schitthoch2 on 2010-05-09
Hello

I have since quite a long time the problem that files using special characters in their filenames are not displayed in various applications. In console or Thunar i have a special "white questionmark in a rhombus" sign for every special character.

It is an XFS partition. I have read a few times that this can be solved by using the iocharset=utf8 option in /etc/fstab, but this option is not recognized and the mount inhibited.

I used other options: utf8 as well as nls=utf8, but that was not recognized neither.

What option do i need to specify to enable utf8 for XFS ?

BTW: Samba works. That means i can play an MP3 file in Windows exported from the XFS disk using Samba, although the special character is then shown as "_" in Windows.

---

### Post by schitthoch2 on 2010-05-13
bump

the "questionmark in a rhombus" mentioned above looks like this: &#65533;

---

### Post by dino99 on 2010-05-13
not an easy problem:
first into synaptic, check that the "language(s)" packages are well installed
then check system-prefs-keyboard settings: search into synaptic, some apps have special language file (i10n), and search "utf8" to add some extra packages if needed.

with the apps where you have issues, set your prefs again

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by schitthoch2 on 2010-05-28
Hi dino99

Well I do understand what you are suggesting, but i doubt, that neither Thunar, nor the Terminal do support utf8 by default.

I could not find any language / utf packages related to them ...

---

### Post by schitthoch2 on 2010-05-30
Diagnosing any further:

I mooved the files to newly created ext4 partition. And they still have that sign. Files and folders having a &#65533; in the name are not even shown i.e. in Thunar.

I think they could have went corrupt when i copied them using rsync at the time.

So now my question is different and i have [opened another thread]("http://ubuntuforums.org/showthread.php?t=1497234") how to actually rename the affected files/folders.

---

