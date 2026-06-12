---
title: "Upgrade edgy to feisty borked! python issues"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by Skeorx13 on 2007-08-02
My roommate was upgrading from edgy to feisty and for some reason everytime it tried to install python 2.5 it threw up an error: "subprocess post-installation script returned error exit status 1" apt-get update works fine. apt-get upgrade throws an error as well. apt-get -f install also throws an error. I tried moving the pycentral out of the usr/bin directory and tried to upgrade again. It updated a few files but errored on the python stuff again. Tried changing the specific lines of pycentral from true to false. That allowed me to update a few more files, but still got same errors for python. Update manager does not load. Gedit does not load anymore. The menu bars are frozen. Nautilis only works when I insert a usb drive. I can't figure out what the hell the problem is. I'm afraid to try to restart the system. cat etc/issue shows feisty as installed though. Please someone help!

---

### Post by Skeorx13 on 2007-08-02
the system got restarted by my roommate and now it won't load anything. It does an automatic fsck and aborts and says to do a manual fsck. I do that and it gets an error and asks to ignore. I ignore it and then it asks to re-write. I don't know if that would wipe anything important so I said no. It said that something was the wrong size and asked to fix it. I said no and the system locked up on me. can anyone please tell me what the heck is going on??

---

### Post by Skeorx13 on 2007-08-02
I ran fsck again and corrected the errors in the blocks but now the GUI won't fully load. I can log in and I can do ctrl+alt+del to get the system monitor but there is no background (just orange) and no menu bars or desktop.

---

