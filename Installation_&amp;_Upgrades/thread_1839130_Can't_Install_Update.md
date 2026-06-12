---
title: "Can't Install Update"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by KutWrite on 2011-09-05
The Update Manager recommended some new security updates for Firefox and Gnome, plus a bunch of other stuff I don't understand. I tried several times to do the update, but it comes back:

- - - - -

(European "no entry" symbol)

Package operation failed

The installation or removal of a software package failed.

installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:
 field name `/usr/share/gnome/help-langpack/gnome-power-manager/de/gnome-power-manager.xml' must be followed by colon

- - - - -

I have 11.04 Natty (Ubuntu studio version)  (the Forum CP won't let me update this, or anything else)

It also won't install any new software, giving me the same message.

Each time I re-try, it says the pkg is already downloaded, then starts to make mods, then re-displays the above error msg.

I can't see how to re-download the pkg or otherwise diddle with it to make it work.

20 min. later.  I figured out there's a file called "Available" that needs a colon.  I found the file and found the line that's wrong, however, I don't have permission to do anything to it: edit, rename, or delete.  All the other lines in that file show up as #### in Libreoffice.  Gedit refuses to open the file.  

I also found a file "Available-old".  It has similar info in it but no 5,000 ### marks.

Another 20 min. later:  I used sudo libreoffice to start libreoffice as root. I edited the "available" file by putting in the colon. I felt very smart 'til I saved that and tried the update Manager again.  It still refused to perform the update saying:
 
"installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/available' near line 7: 
 missing package name"

Can you help?

Dan    :confused:

---

### Post by KutWrite on 2011-09-05
OK... I found the answer elsewhere.

In case someone else has this problem, this guy's solution works:

[http://www.bitsbythepound.com/fix-dpkg-available-file-in-ubuntu-364.html](http://www.bitsbythepound.com/fix-dpkg-available-file-in-ubuntu-364.html)

BUT!  Note he mistyped "sudo dpgk"  it should be "sudo dpkg"

Also, you might not have "aptitude" installed. I didn't and couldn't while this problem existed.  I found that as soon as I executed the "clear" command, I could get new programs.  Then, I could download Aptitude and use it to rebuild the "available" file.

Whew!

---

### Post by Sef on 2011-09-05
Thank you for posting the solution and pointing out the error.

---

