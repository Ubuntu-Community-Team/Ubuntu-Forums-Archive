---
title: "output a list of user-installed packages to text file?"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by kyfho23 on 2007-09-09
'lo, all...
none of the "similar threads" had quite what i was looking for...somewhere in the forums, there was a post with either a script or a command that would output all the user installed programs added since the last install, and output them to a text file. Can anyone point me to it?

i searched. i really did:confused: 

chris


SOLVED: the script is here: [http://ubuntuforums.org/showthread.php?t=393615](http://ubuntuforums.org/showthread.php?t=393615)

---

### Post by earobinson on 2007-09-09
this information is stored in /var/log/dpkg.log but the system zips the info into .gz files, you could unzip them all to read it

or view the info in synaptics history function file -> history

hope this helps

---

### Post by kyfho23 on 2007-09-09
i should have mentioned i'm using kubuntu.  :oops::oops::oops:[http://ubuntuforums.org/images/smilies/icon_redface.gif](http://ubuntuforums.org/images/smilies/icon_redface.gif)

thank you, tho!

---

