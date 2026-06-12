---
title: "Moving /home after upgrade"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by koolcracker on 2008-05-08
I tried to follow a guide on the internet, but it wouldn't work out for me, so I was wondering if someone here could please help me. I just upgraded to ubuntu 8.04 and when I did, it moved my old home folder to a drive located at media/hda3. How can I change that so that it will be the new home folder again and restore all of my files and path directories? I'm sure its a simple process, but I am having real trouble. Thanks in advance for the help.

---

### Post by Rallg on 2008-05-08
If you have only one /home folder (wherever it is), try this:

sudo gedit /etc/fstab

that opens your mount point list. Save a copy in case you make an error. Now, look at the list of mount points. I cannot advise you as to exactly what to do, since I do not know your entire system. But it may be obvious what you need to edit. As long as you do not attempt to mount different things to the same place, you won't make things worse than before if you miss-guess.

If your edit is so bad that it makes Ubuntu unbootable, then use the live CD to restore your backup copy of /etc/fstab. (You may need sudo or change to root, to do that).

---

