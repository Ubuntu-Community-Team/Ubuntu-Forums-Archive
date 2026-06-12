---
title: "Upgrading to Skype 2.2 broke video and causes Gtk_WARNING"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by tomtom12 on 2011-04-07
I just upgraded to Skype 2.2 on Ubuntu 10.10 64bit and got:

[I]tom@tom-Q330:~$ skype

(<unknown>:6501): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6501): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6501): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6501): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6501): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64[/I]
[I]
(<unknown>:6501): Gtk-WARNING **: Loading IM context type 'ibus' failed

[/I]Reinstalling ia32-libs did not help.  Problems in skype are now: bad or no video :sad:  I thought this issue was solved..

Last time we started skype with 'skype-wrapper'  but that does not work anymore :(

See also [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/754162](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/754162)

---

### Post by MrEgg on 2011-04-07
Try :
```
env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```
and see how this goes. This is how I get my webcam supported.

---

### Post by tomtom12 on 2011-04-07
Thank you. I tried it and got same result.

[I]    tom@tom-Q330:~$ env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
    (<unknown>:6795): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64
[/I]
[ and so on ...]

---

### Post by GsL9vBab on 2011-04-07
Hi.  Just confirmed that the workaround works.

---

### Post by llenchikk on 2011-04-07
If put this command in menu shortcut skype logo became empty.
There is skype logo icon?
Workaround working for me too. Thank you!

P.S. I found it! /usr/share/icons/skype.png

---

### Post by tomtom12 on 2011-04-07
Still does not work for me:(  How can it that it works for others? Might I have the wrong lib?

---

### Post by jawilljr on 2011-04-07
Doing the below does not work for me either:

```
env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```The only thing that worked was to downgrade to the earlier version.

Jerry

---

### Post by tomtom12 on 2011-04-07
@jerry: how did you downgrade ?

---

### Post by jawilljr on 2011-04-07
I read [This post](http://forum.skype.com/index.php?showtopic=809765&view=findpost&p=3366039) on the Skype forum. I downloaded it and found out it was for Intrepid. So I searched for another one and couldnt find one and since it was the same Skype version for Maverick I decided to install it... it works fine.

[Here is the direct link](http://uploading.com/files/a6b9144a/skype-ubuntu-intrepid_2.1.0.81-1_amd64.deb/)

BTW I uninstalled the new first.

Jerry

---

### Post by tomtom12 on 2011-04-08
@jerry: thanks will give it a try later if no one can help to solve this mystery... 

Why does Skype 2.2 work for some people and not for others? I just did regular upgrade via Ubuntu Software Centre... that should not break things, should it? .... :(

---

### Post by plucky on 2011-04-08
Please subscribe to [Bug Report](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/754162) might get it fixed faster.

Good Luck

---

### Post by ottosykora on 2011-04-08
I had this 2.1 from the skype site, then it went updated by the ubuntu repos. Now I have 2.2, but it works strange. I can use it, but lot of strange terminal windows pop up for short time, with lot of errors in it. Somehow unusual all that. i think I will try to remove this one and replace it with the 2.1 from skype site again.

---

### Post by tomtom12 on 2011-04-08
After downgrade I got same problem now :(  Seems something else caused the trouble recently ?

---

### Post by ItalOz on 2011-04-10
I have troubles with new version of skype in the computer of my parents, their video disappeared after upgrading and now I am in a lot of problems because I am trying to fix it from my house in a remote assistance and we live in different continents,

I think it has been a very bad move from skype to post an upgrade that is causing so many problems, skype should be out of the repositories like it wsas once so there is no risk of automatic upgrade with software that does not work.

Now I am downloading a few versions here and there and I'll try to see which one works in my parents' computer.

Very disappointing

---

### Post by tomtom12 on 2011-04-11
Ok, seeing a lot of issues around Skype 2.2.  Was a mistake to make it as standard Update in Ubuntu.... I rely heavily on Skype... and now see myself using a Windows laptop just for Skype. And that while I did not touch a Windows PC in 4 years !

---

### Post by tomtom12 on 2011-04-11
Ok tip:  Download older version of Skype like 3.0 and install in VirtualBox on Windows XP... that works. Not elegant.. still hate Windows after all these years... but at least there they have some decent video-library strategy...

---

### Post by ItalOz on 2011-04-12
following the instructions given in this [link]("http://forum.skype.com/index.php?showtopic=810077") from the skype forums I have been able to fix my parent's skype webcam using remote assistance.

Thanks to LINUX...

Ah... and I have locked the version of skype!

---

### Post by AKADAP on 2011-04-17
> **ItalOz said:**
> following the instructions given in this [link]("http://forum.skype.com/index.php?showtopic=810077") from the skype forums I have been able to fix my parent's skype webcam using remote assistance.

Thanks to LINUX...

Ah... and I have locked the version of skype!

None of those solutions work for me.
```
$ skype

(<unknown>:4635): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4635): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:4635): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4635): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:4635): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4635): Gtk-WARNING **: Loading IM context type 'ibus' failed
^C
$ env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

(<unknown>:4700): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4700): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:4700): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4700): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:4700): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4700): Gtk-WARNING **: Loading IM context type 'ibus' failed
^C
$ env LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

(<unknown>:5791): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:5791): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:5791): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:5791): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:5791): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:5791): Gtk-WARNING **: Loading IM context type 'ibus' failed
^C

```

Skype runs, test call works, test video works, but it won't let me share my video when I'm in an actual call. I can see & hear the other party, and they can hear me, but clicking on the share my video button gets ignored.

---

### Post by psuresh0207 on 2011-12-24
I also had the same problem with skype 2.2 in lucid 11.04, but downgraded to 2.1.0.81-1 and droidcam works fine :). Thanks guys.

---

