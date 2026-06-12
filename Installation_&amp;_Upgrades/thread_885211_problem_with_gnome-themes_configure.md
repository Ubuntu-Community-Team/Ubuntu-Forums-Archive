---
title: "problem with gnome-themes configure"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by boblq on 2008-08-09
My attempt to upgrade to 8.04 bombed out with an error message about the configuration of gnome-themes. I try

$> sudo dpkg--configure gnome-themes 

and get 

gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_once_init_enter_impl. 

In an earlier forum post I find:
[http://ubuntuforums.org/showthread.php?t=576431](http://ubuntuforums.org/showthread.php?t=576431)

<quote>
/usr/lib/libgdk_pixbuf-2.0.so.0 points to the file /usr/lib/libgdk_pixbuf-2.0.so.0.1200

I read on a forum that one other person had a problem like this with version 1200 of the pixbuf and he was able to get around it by changing the pointer to an earlier version (libgdk_pixbuf-2.0.so.0.1000). So, I did that and was able to apt-get install gnome-themes gnome-accessibility-themes ubuntu-desktop. The apt-get dist-upgrade to finish the upgrade.
</quote>

I am pointing at libgdk_pixbuf-2.0.so.0.1200.  Where can I get libgdk_pixbuf-2.0.so.0.1000? 

This seems to precede the problem posted earlier with the X server not starting. This appears to be a fairly common problem that recurs from time to time. It would be nice to have a fix. 

TIA,

BobLQ

---

### Post by boblq on 2008-08-10
bump.

He's back. I am going to keep bugging you folks. I have been bragging to all of my friends about how "Ubuntu just works." Now I have to eat my words. This upgrade has cost me at least two days work. 

I am hunting libgdk_pixbuf-2.0.so.0.1000 and seem to be closing in on it by compiling gtk+  Just figuring out which version of gtl+ contains libgdk_pixbuf-2.0.so.0.1000 is something I only know haw to do by compiling gtk+. There must be abetter way. If I find a solution I will post it. 

Help though would be appreciated.

BobLQ

Success is the ability to go from one failure to another with no loss of enthusiasm.
   
    Sir Winston Churchill





> **boblq said:**
> My attempt to upgrade to 8.04 bombed out with an error message about the configuration of gnome-themes. I try

$> sudo dpkg--configure gnome-themes 

and get 

gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_once_init_enter_impl. 

In an earlier forum post I find:
[http://ubuntuforums.org/showthread.php?t=576431](http://ubuntuforums.org/showthread.php?t=576431)

<quote>
/usr/lib/libgdk_pixbuf-2.0.so.0 points to the file /usr/lib/libgdk_pixbuf-2.0.so.0.1200

I read on a forum that one other person had a problem like this with version 1200 of the pixbuf and he was able to get around it by changing the pointer to an earlier version (libgdk_pixbuf-2.0.so.0.1000). So, I did that and was able to apt-get install gnome-themes gnome-accessibility-themes ubuntu-desktop. The apt-get dist-upgrade to finish the upgrade.
</quote>

I am pointing at libgdk_pixbuf-2.0.so.0.1200.  Where can I get libgdk_pixbuf-2.0.so.0.1000? 

This seems to precede the problem posted earlier with the X server not starting. This appears to be a fairly common problem that recurs from time to time. It would be nice to have a fix. 

TIA,

BobLQ

---

### Post by boblq on 2008-08-10
The fix referred to above works. My question,

"Where can I get libgdk_pixbuf-2.0.so.0.1000?" has the following answer. This library is part of gtk (Gimp Tool Kit). I downloaded the source for gtk+-2.9.4 from ftp.gimp.org. Then I compiled it. Actually I tried several versions before finding libgdk_pixbuf-2.0.so.0.1000. 

HTH someone else. 

It was a PITA though. Something better handled by the distro than me. 

Does anyone know where to get libgdk_pixbuf-2.0.so.0.1000 without compiling it. Or some apt-get magic? I may well have done this the hard way. 

I still have a major problem with X not starting. See
[http://ubuntuforums.org/showthread.php?t=884780&highlight=boblq](http://ubuntuforums.org/showthread.php?t=884780&highlight=boblq)

I am learning more about Gimp, GTK, Pango, Cairo, etc and now X than I really want to know.

So it goes,

BobLQ

---

