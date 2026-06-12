---
title: "Elisa is now Moovida"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by plun on 2009-08-17
Wow...this is just great....:)

> Moovida offers you more.
By bringing together all your movies, TV shows, tunes and photos in one simple innovative interface.
More than that, Moovida brings you the best of internet video, music and images to play on your HDTV, laptop or PC. 

Info:
[http://www.moovida.com/](http://www.moovida.com/)


Uploaded yesterday evening to Karmic

> moovida (1.0.6-0ubuntu1) karmic; urgency=low

  * New upstream release. (LP: #414267)
  * debian/control: Add dummy package to allow dist-upgrade
    upgrade from Elisa.

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006397.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006397.html)



Note:
**The F-key** is very useful for switching full screen to windowed mode !


[[img]http://ubuntu-pics.de/thumb/22152/snapshot13_OeQx0S.png[/img]](http://ubuntu-pics.de/bild/22152/snapshot13_OeQx0S.png)   [[img]http://ubuntu-pics.de/thumb/22153/snapshot14_7XFFFT.png[/img]](http://ubuntu-pics.de/bild/22153/snapshot14_7XFFFT.png)


:popcorn::guitar:

---

### Post by Scotty Bones on 2009-08-17
Just installed it earlier today. looks pretty sweet so far, it's really shaped up quite a bit since I last checked it out.

Now if I can just figure out how to get my music and videos in it.

---

### Post by Darkshade on 2009-08-17
> **Scotty Bones said:**
> Just installed it earlier today. looks pretty sweet so far, it's really shaped up quite a bit since I last checked it out.

Now if I can just figure out how to get my music and videos in it.

By default it scans the folders Music, Pictures and Videos in your /home directory. You can change them by editing the file /home/username/.moovida/moovida.conf

---

### Post by meborc on 2009-08-17
the change was a while ago now [http://ubuntuforums.org/showthread.php?t=1176411](http://ubuntuforums.org/showthread.php?t=1176411)

great to see it land in karmic... have not really needed a media center on my test karmic box, but why not :) let the testing begin

---

### Post by Nburnes on 2009-08-17
Looks really good.

---

### Post by ELD on 2009-08-17
I've honestly never seen the need for a media centre type program, i keep videos in a video folder, pictures in a picture folder, i don't want an extra program to view through them when i can just go to the folders?

---

### Post by | MM | on 2009-08-17
Out of curiosity what is the ideal input device for this app (besides a mouse)?  Some kind of wii remote type device?

---

### Post by Scotty Bones on 2009-08-17
> **Darkshade said:**
> By default it scans the folders Music, Pictures and Videos in your /home directory. You can change them by editing the file /home/username/.moovida/moovida.conf

It picked up the pictures on my notebook just fine. All my media is on my server though.

This is what I had tried.

#music = [u'/home/scotty/Music']
music = [u'smb://atlantis/music/']

but no dice.

---

### Post by plun on 2009-08-17
One Finding:

**The F-key** is very useful for switching full screen to windowed mode !

---

### Post by ronacc on 2009-08-17
the interface is wierd , will take some getting used to . The shoutcast plugin only shows some genres can that be changed ?

---

### Post by inportb on 2009-08-17
> **ELD said:**
> I've honestly never seen the need for a media centre type program, i keep videos in a video folder, pictures in a picture folder, i don't want an extra program to view through them when i can just go to the folders?

I agree.

---

### Post by meborc on 2009-08-17
well... you are not forced to use it

it is for those people missing the windows media center, i guess ;)

---

### Post by scaine on 2009-08-17
Moovida (well, Elisa v2 really) is cool, but the interface needs some work.  Functionally, it's better than Elisa, but a long way from XBMC.  The media player I've been impressed the most by recently is Boxee, but I've just discovered that it won't run on Karmic due to dependency issues (it relies on a library which would break xulrunner).

Another weird thing - there's no way to exit Moovida without the mouse!  Apparently, you just press "esc", but that just switches between full screen mode (the same as the 'F') in Karmic.

Disappointing, but easily fixed.

One more thing to note, Boxee, based on XBMC, has built-in support for VDPau hardware acceleration.  But I just use it because it's got an incredible IPlayer module.

---

### Post by Schendje on 2009-08-17
I've been using it for a little while now, I think it's absolutely fantastic.

A great-looking 10-foot interface, web plugins, automatic album/poster art fetching.

I've put it on a nice big screen and will hide the keyboard and mouse when they're not needed. I'll control it with a Bluetooth script from my Sony Ericsson phone.

Looking forward to future updates for Moovida.:guitar:

---

### Post by andrewsomething on 2009-08-17
> **Darkshade said:**
> By default it scans the folders Music, Pictures and Videos in your /home directory. You can change them by editing the file /home/username/.moovida/moovida.conf

No need to edit the conf file by hand, though I will agree that this isn't all that intuitive. Take a look at the following screen shoots.

To add a folder, first navigate left to "Devices & Share."

Next, select the source that the folder you'd like to add is in (i.e. "On This Computer" for something in your Home folder or "Attached Devices" for something on an external drive).

The next screen allows you to dig down into the different folders. When a folder is highlighted, a plus sign is show next to it. To add that folder as a source, select the plus sign. Moovida will determine the contents of the folder and display them in the correct menus.

---

### Post by vishalrao on 2009-08-17
> **Scotty Bones said:**
> It picked up the pictures on my notebook just fine. All my media is on my server though.

This is what I had tried.

#music = [u'/home/scotty/Music']
music = [u'smb:/**/**/atlantis/music/']

but no dice.

try adding a third slash after the smb: part?

---

### Post by Scotty Bones on 2009-08-17
> **vishalrao said:**
> try adding a third slash after the smb: part?

nope, that didn't do it either.

---

### Post by Scotty Bones on 2009-08-17
> **andrewsomething said:**
> No need to edit the conf file by hand, though I will agree that this isn't all that intuitive. Take a look at the following screen shoots.

To add a folder, first navigate left to "Devices & Share."

Next, select the source that the folder you'd like to add is in (i.e. "On This Computer" for something in your Home folder or "Attached Devices" for something on an external drive).

The next screen allows you to dig down into the different folders. When a folder is highlighted, a plus sign is show next to it. To add that folder as a source, select the plus sign. Moovida will determine the contents of the folder and display them in the correct menus.

None of my network share show up there. My ipod will though.

---

### Post by bear24rw on 2009-08-17
moovida restarts my computer!! After its been scanning my music/movies directory for a while my computer will reboot lol I havent checked any logs or anything because i dont plan on using moovida but does this happen to anyone else?

---

### Post by oldgit on 2009-08-17
#music = [u'/home/scotty/Music']
music = [u'smb://atlantis/music/']

Try [u'~/.gvfs']

to pick up mounted samba shares

---

### Post by MaX on 2009-08-17
I'm missing Picasa support last.fm support and that it takes forever to load all the covers... And there is no quit button

---

### Post by ronacc on 2009-08-17
> **MaX said:**
> I'm missing Picasa support last.fm support and that it takes forever to load all the covers... And there is no quit button

hit the letter f (lowercase) to toggle fullscreen mode then you can exit . 
this thing shows promise but needs work .

---

