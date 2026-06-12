---
title: "New sound applet now working"
date: 2009-01-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-06
I cant get the Volume Control to open.  I click the applet and get the new slider bar with the "Volume Control..." button and if I click nothing.  Right click on it and choose "Open Volume Control" and nothing happens as well.

---

### Post by LordVeovis on 2009-01-06
Checked for more updates manually and that fixed it.

---

### Post by Slug71 on 2009-01-14
> **LordVeovis said:**
> I cant get the Volume Control to open.  I click the applet and get the new slider bar with the "Volume Control..." button and if I click nothing.  Right click on it and choose "Open Volume Control" and nothing happens as well.

I now have this issue.

---

### Post by LordVeovis on 2009-01-15
This seems to come and go for me as well.  It seems that after a restart it will fix it most times.  But it is likely to come back again.  Any ideas to figure out why?

---

### Post by DougieFresh4U on 2009-01-15
I am still having the 'lock up' issue if I click volume control open. When menu drops down the whole desktop locks up and I have to do a 'hard shutdown'. I think it may be related to my 'Intel' graphics issue. I can put 'cursor' over applet and use the scroll wheel to turn volume up or down, but as soon as I click, 'freeze'.

---

### Post by Yellow Pasque on 2009-01-15
Does the GNOME "Volume control.." button work for anyone that doesn't have PulseAudio installed? Anyone using OSS4?

The problem is that a user can no longer access Sound/Gstreamer/Event Sound Preferences through the System->Preferences sound menu.

I can right-click on the volume control icon and select preferences. This allows me to select the device controlled by the volume control app (but doesn't give access to any other sound settings).
Another partial workaround is to launch "gstreamer-properties" from the terminal. This gives a dialog similar to the first tab on the old GNOME Sound Prefs.

I still have not found a workaround to access Event sound preferences.

EDIT: Link to GNOME's bug report about the volume control not starting: [http://bugzilla.gnome.org/show_bug.cgi?id=566835](http://bugzilla.gnome.org/show_bug.cgi?id=566835)

---

