---
title: "alert beeping does not shut off"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by libihero on 2009-10-14
maybe its cuz i'm a little of a n00b, but i can't get the alert beep to turn off (like when you backspace when there is nothing to backspace).  i went to the sound preferences and muted the alert volume, but it doesnt get rid of it.
is there anything else i need to do?

---

### Post by bschuteker on 2009-10-15
Same problem. Previous fixes do not work in Karmic.

Please help.

---

### Post by bschuteker on 2009-10-15
HA! found it. this should be under system---> Prefrences ---> Sound but it is not.

Open terminal
type alsamixer
when it opens tab over to system beep and type M
then escape and it will be gone.

YAY

---

### Post by billybob123 on 2009-10-15
A solution that worked for me is use gconf-editor and find

/desktop/gnome/peripherals/keyboard/bell_mode

Change it to 'off'.

---

### Post by bpickel on 2009-10-15
I think it has been fixed in the latest round of updates. I have been watching the issue.

I have all system sounds enabled and I no longer have the issue. 

[http://ubuntuforums.org/showthread.php?p=8109142#post8109142](http://ubuntuforums.org/showthread.php?p=8109142#post8109142)

Please let us know if this is the case for you as well.

---

### Post by skillllllz on 2009-10-16
I still have the issue. I wish I could just blacklist the pc-speaker but there seems to be no specific module for it anymore.

---

