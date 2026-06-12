---
title: "Default folders in Hardy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Lord Landis on 2008-04-26
I'm sorry if this has already been asked, but I tried searching the forums and didn't find much...

How do I permanently remove the default folders that Hardy creates?  I'm talking about 'Documents', 'Music', 'Video', etc...  I do not want these folders created because I have my own organizational scheme and hate seeing un-necessary clutter in my /home.  Also, I don't want my applications thinking that they should default to a location I won't ever be using.  I know that I can re-configure the defaults, but I'd really rather just have them be gone.

I tried removing them and the user-config file that goes along with them, and they just came back on a reboot.  

Any help on permanently getting rid of these would be very greatly appreciated.

---

### Post by Lord Landis on 2008-04-26
Okay, so I think I figured this out (GiMF - [http://www.not404.com/node/16](http://www.not404.com/node/16)).  There should be a setting in user-dir.conf that can be set to 'false' to prevent them from being created.  I'll try it and let you know.

Which brings me to my next question...  Who thought this was a good idea?  I realize that newbies/converts from Windows might want to see 'familiar' folders from the get-go, but it's seriously annoying from a control-freak point-of-view.

---

### Post by Lord Landis on 2008-04-26
Also, I forgot to mention this.  More information on these accursed folders can be found here:
[http://www.freedesktop.org/wiki/Software/xdg-user-dirs](http://www.freedesktop.org/wiki/Software/xdg-user-dirs)

---

### Post by Lord Landis on 2008-04-26
Okay,

Setting the enable option in /etc/xdg/user-dirs.conf to 'false' did indeed eliminate these cursed things.

I hope this helps anyone else who doesn't want them around.

---

### Post by Ardrias on 2008-06-19
Nice. I'm not too fond of this behavior either.

---

