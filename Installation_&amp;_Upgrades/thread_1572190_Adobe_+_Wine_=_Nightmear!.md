---
title: "Adobe + Wine = Nightmear!"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by darkenvy6 on 2010-09-10
Now I have adobe photoshop CS2, adobe suite CS4 and adobe suite CS5. I am having the most difficult time getting anything to run under wine. I actually don't want anything but CS5 installed. I see guides online, I have followed them with no success. One guide told me to install on Windows then copy to my wine folder. No sucess, different error. But when I try to install from wine I get an error while installing. Please help, I need to use this computer for my graphic design work but refuse to use windows ;)

Thanks
~Darkenvy

---

### Post by QIII on 2010-09-10
CS5 is given a "garbage" rating on [www.winehq.com](www.winehq.com).

You may need to be pragmatic about Windows if that is what you need.

Might you consider running windows in a virtual environment?

---

### Post by dirghrabadia on 2010-09-10
Well, currently CS2 isn't fully functional on Wine ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631))
So you might want to consider using other options i.e under Windows if you must use Adobe products or you might want to try GIMP, which is fairly comparable to Photoshop  :)

---

### Post by darkenvy6 on 2010-09-10
yea, the thing is that my compatibility is to run side-by-side with all the macs on campus with CS5 so no GIMP for me. So a virtual Machine is all I have as an option huh? Well Virtualbox doesn't support drag and drop (which is an issue to me) and it would be cool if I could get a CS5 file on Ubuntu to open CS5 up in Windows. That way I can leave windows virtual-box running but execute the file from Ubuntu. Is that possible?

What about this wine-tricks?

---

### Post by QIII on 2010-09-11
Drag and drop can be done, sort of.

You can set up a shared folder (pointed at a directory on your host) in your Vbox vm and use the normal Windows functionality to move files to and from it while working in the Windows guest.

---

