---
title: "sopcast player not opening any channel"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by shuster on 2013-03-17
I have the sopcast player not opening any channel anymore since upgrading to 12.04 LTS.
This ist the output from terminal when launching sopcast player:

```
(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.

(sopcast-player.py:5986): libglade-WARNING **: unknown attribute `swapped' for <signal>.
```

Nothing more!
I checked my libstdc++. I have 5 and 6 installed.
VLC and TV-maxe working correctly.
Some idea??
thanks.ciao.Rob.

---

### Post by amanitu on 2013-08-17
I get it as "(sopcast-player.py:6028): libglade-WARNING **: unknown attribute `swapped' for <signal>." with end:

> Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 712, in on_exit
    self.config_manager.player_width(self.window.get_allocation()[2])
  File "/usr/share/sopcast-player/lib/pySopCastConfigurationManager.py", line 84, in player_width
    return self.__getter_setter("getint", "player", "width", value)
  File "/usr/share/sopcast-player/lib/pySopCastConfigurationManager.py", line 139, in __getter_setter
    self.write()
  File "/usr/share/sopcast-player/lib/ConfigurationManager.py", line 46, in write
    configfile = open(self.__file_name, 'wb')
IOError: [Errno 13] Permission denied: '/home/amanitu/.pySopCast/pySopCast.cfg'
^CTraceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 785, in <module>
    pySop.main()
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 185, in main
    gtk.main()


Trying to open any link from the browser, my sopcast (0.8.5) would simply not work with VLC (2.0.8) as an external player. I tried to type 'vlc' under Preferences->Player->Use external player, but to no avail - nothing changes, and after closing and reopening Sopcast, the old native player is still in place. 

Any ideas? I'm still not used to Ubuntu, and all those codes do not say much to me.

PS: I have a 32-bit Ubuntu 12.04.

---

### Post by ethanay on 2014-06-16
I installed sopcast from a ppa (there are a couple of them, google them to find them or one is avialable from the sopcast main project download page, linked to a google code site, which links to the ppa :), and it was not loading any channels.

First, I had to refresh the channel list, which helped.  Second, I needed to follow the advice of this site:
[https://code.google.com/p/sopcast-player/issues/detail?id=100#makechanges](https://code.google.com/p/sopcast-player/issues/detail?id=100#makechanges)

By doing this:
```
sudo ln -s /usr/lib/i386-linux-gnu/libstdc++.so.* /usr/lib/
```

---

