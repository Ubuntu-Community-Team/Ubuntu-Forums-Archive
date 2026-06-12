---
title: "Upgrading Mandriva to Ubuntu"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by fmpuk on 2005-08-11
I recently gave Kubuntu a go but I had loads of problems with it, things wouldn't display right, continual errors etc. What I was wondering was what is the best way to update Mandriva to Ubuntu? &#921; plan to use my existing home partition with the Ubuntu install and I feel this may have been the problem with Kubuntu - do I need to change any files/settings etc in my home directory - basically stuff that may have been Mandriva specific? I haven't got Gnome installed on Mandriva le 2005 so would that mean I shouldn't have a problem with installing the OS? Thanks a lot, any tips on achieving a clean install along with all my files would be greatly appreciated.
Thanks a lot

---

### Post by Hairy_Palms on 2005-08-11
if you use your current home folder then the only problems will be all the program settings in hidden folders, if u purge them all your documents should be useable fine

---

### Post by tread on 2005-08-11
Yep, the settings don't work .. I've tried. There isn't any reason why they shouldn't (at least, not evident to me) but the documents should carry over fine.

---

### Post by Hairy_Palms on 2005-08-11
i can only assume the differences are the places mandrake installs things with rpm.
id assume this wouldnt affect ubuntu as much as kubuntu because the kde settings are the ones most likely to cause problems and ubuntu doesnt use kde.

---

### Post by tread on 2005-08-11
Well, where it installs stuff shouldn't really be an issue, right? After all, we are (at least I am) talking about gnome settings .. which are in .gnome etc. in my home directory. And gnome is gnome, I don't think distros modify the desktop environment itself. :???:

---

### Post by fmpuk on 2005-08-11
Thanks for the replies :) 
So from what I can gather my best bet would be too delete everything out of my home directory apart from my documents? I mean, for a completely clean install that sounds like my best bet. Would I be able to delete everything from my home partition while i am running Mandriva with KDE or will I need to do it using a different method? Maybe run IceWM or do it from failsafe?
Thanks a lot so far :)

---

### Post by tread on 2005-08-11
Doing it under icewm would be a good option, better yet, just boot into command line and delete everything but your documents. (of course, as usual, don't delete, move it into a separate folder in case you need to refer to it later)

---

