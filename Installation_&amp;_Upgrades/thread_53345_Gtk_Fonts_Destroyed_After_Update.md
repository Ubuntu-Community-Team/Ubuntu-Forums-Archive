---
title: "Gtk Fonts Destroyed After Update"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by DimitrisChr on 2005-07-31
Well i updated to the latest versions of packages in the apt-get source list and i installed some extra apps like amule, some games (tuxkart, supertux), and i found that something happened that changed the fonts used by gtk1 applications such as xmms. As you can see from the picture the fonts now look huge and terrible.
I am not sure but i think it has something to do with libwxgtk since it was one of the last packages installed before i noticed the problem. I am not sure if it has anything to do with that but i have 2 versions of the above package installed at the same time 
libwxgtk2.4 and libwxgtk2.5.3.
Any ideas how i can change the fonts to look the way they did when i first installed Ubuntu. For gtk1 applications only. Gtk2 looks great!
Thanks in advance!

[IMG]http://i16.photobucket.com/albums/b39/LinuxRulez/9b29724f.png[/IMG]

---

### Post by DimitrisChr on 2005-07-31
Ok i think i found whats wrong. Somehow the file /etc/gtk/gtkrc.utf-8 got edited and uses some fonts that are just plain horrible!!!

When i edit the file i see changes in the fonts used by gtk1 applications.

Can someone plz post his gtkrc.utf-8 file so that i can put back the original font settings used by ubuntu.

Thanks!!!

---

