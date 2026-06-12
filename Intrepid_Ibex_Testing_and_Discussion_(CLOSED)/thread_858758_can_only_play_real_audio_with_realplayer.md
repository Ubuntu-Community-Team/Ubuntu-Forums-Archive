---
title: "can only play real audio with realplayer"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-07-13
I cannot play realaudio streams except with realplayer . I usualy use the "radio" screenlet (which uses mplayer) to play the bbc world service , since the upgrade to the .26 kernel only realplayer will play the streams . I can see the stream comming down in the netmon screenlet but no mater if I use the radio screenlet or enter the url directly into mplayer ( or any other media player that does streams)  I get no output . it is not the audio problem because I can play mp3s's etc no problem , I upgraded from hardy when the repos opened and this was working to start with but went away about the time of the upgrade to 2.6.26 . is anyone else experiencing this or have I missed something ?

---

### Post by psyke83 on 2008-07-13
> **ronacc said:**
> I cannot play realaudio streams except with realplayer . I usualy use the "radio" screenlet (which uses mplayer) to play the bbc world service , since the upgrade to the .26 kernel only realplayer will play the streams . I can see the stream comming down in the netmon screenlet but no mater if I use the radio screenlet or enter the url directly into mplayer ( or any other media player that does streams)  I get no output . it is not the audio problem because I can play mp3s's etc no problem , I upgraded from hardy when the repos opened and this was working to start with but went away about the time of the upgrade to 2.6.26 . is anyone else experiencing this or have I missed something ?

Wouldn't mplayer (as well as Totem/gstreamer0.10-pitfdll) need the w32codecs package from Medibuntu to play RealAudio content?

---

### Post by ronacc on 2008-07-13
I don't remember installing them in hardy but perhaps yo are right , I don't see an intrepid repo in medibuntu yet so I'll grab the codecs from mplayer.hu .

edit the question may be moot I think I just nuked my intrepid install .

---

### Post by psyke83 on 2008-07-13
> **ronacc said:**
> I don't remember installing them in hardy but perhaps yo are right , I don't see an intrepid repo in medibuntu yet so I'll grab the codecs from mplayer.hu .

Medibuntu's Hardy repository should work OK (no guarantees, though).

---

### Post by ronacc on 2008-07-14
I'll try medibuntus hardy repo after I install the latest daily live , a copy operation ( I think) went badly wrong and now I can't even log into a terminal , a forced fsck didn't help .

---

### Post by Nullack on 2008-07-14
.....must resist a post about how mplayer is the only real multimedia solution for linux....must resist :)

---

### Post by plun on 2008-07-14
ronacc

Please take a look at this thread..

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


It gives a user a working PC for the commercial world.

(maybe also Mplayers own media pack is needed, going to check)

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Binary Codec Packages

---

### Post by ronacc on 2008-07-14
actualy I was in the process of installing the codecs from mplayerhq.hu when things went south on me .  I don't think it had anything to do with the codecs or mplayer . I'll try again this evening after I reinstall intrepid .

---

### Post by plun on 2008-07-14
> **ronacc said:**
> actualy I was in the process of installing the codecs from mplayerhq.hu when things went south on me .  I don't think it had anything to do with the codecs or mplayer . I'll try again this evening after I reinstall intrepid .

OK

The only issue I got is that I must change channel then it plays. (and a pango warning)

> plun@dunder:~$ screenlets-manager
True
/usr/lib/python2.5/site-packages/screenlets/utils.py:205: PangoWarning: Error loading GPOS table 0x157f
  img = gtk.gdk.pixbuf_new_from_file_at_size(img_path,width,height)
Starter already exists.
DAEMON FOUND!
True
**Launch Radio**
Launching Screenlet from: /home/plun/.screenlets/Radio/RadioScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/RadioScreenlet.log
REGISTER screenlet: RadioScreenlet
True
/home/plun/.screenlets/Radio/RadioScreenlet.py:225: PangoWarning: Error loading GPOS table 0x157f
  ctx.show_layout(self.p_layout)





PulseAudio settings   ?   Do you have Pulseaudios GUIs installed ?


EDIT

With BBC which uses ram files I got errors

> /home/plun/.screenlets/Radio/RadioScreenlet.py:225: PangoWarning: Error loading GPOS table 0x157f
  ctx.show_layout(self.p_layout)
*** glibc detected *** mplayer: corrupted double-linked list: 0x09543628 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6a14ebf]
/lib/tls/i686/cmov/libc.so.6[0xb6a16017]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb6a163f6]
/usr/lib/libpulse.so.0(pa_xfree+0x21)[0xb7ad85e1]
/usr/lib/libpulse.so.0[0xb7af5a35]
/usr/lib/libpulse.so.0[0xb7ae5e6e]
/usr/lib/libpulse.so.0[0xb7abbc88]


But it plays....  seems to be a pulse issue.

---

### Post by ronacc on 2008-07-14
I didn't try launching it from terminal but its log shows no errors , I don't think its a pulse problem in my case since other formats play fine in mplayer but .ram won,t even if I enter the url directly in mplayer.

---

### Post by mc4man on 2008-07-14
I'm finding that the debian testing libs and codecs (w32codecs, ect.)are matching up good with 8.10 vs. hardy Medibuntu which is down anyway
[http://debian-multimedia.org/pool/main/](http://debian-multimedia.org/pool/main/)

---

### Post by Nullack on 2008-07-14
Ive bugged it, but the repo mplayer is ancient

Really, mplayer should be compiled from svn, along with libdvdread svn, libdvdnav svn, lidvdcss2 and x264.

---

### Post by ronacc on 2008-07-14
just an update to let you know I haven't dropped off the face of the earth. waited until I had time to try to resuce my install before reinstalling , no luck , something wrond with gdm it seems but I can't find any indication what , it just fails to start, also can't log into a term as user that fails at cd'ing to /home/ron , can login as root but gdm wont start from there either but I can get to an x session without gdm so it isn't x thats fubar . d/l'd the daily live  that runs but stalls at the partitioner ( thats mentioned in another thread also) d/l'ing the alternate now .

---

### Post by BwackNinja on 2008-07-15
I had the same problem (not quite fixed though). I was able to log in after chmod -R 765'ing my whole filesystem, chmod -R 700'ing my home folder, and chmod 644'ing my ~/.dmrc. Unfortunately sudo won't work for me now (probably from messing around so much) and I can't find anyone who has gotten out of this non-working sudo situation, only people who've given up and just reinstalled.

---

### Post by ronacc on 2008-07-15
I considered changing permissions like you did but that basicly would have rendered the system unsuitable for testing which is the whole point of running an alpha . I wiped and reinstalled and found a couple of bugs in the process .

---

### Post by cpcnw on 2008-07-17
I was hoping to get 'embedded' real streams from bbc.coc.uk played within Firefox windows. I have installed mplayer, vlc and now realplayer which does work in its own Window but not embedded.

There are some suggestions that the mplayer plugin works and it is listed in about:plugins under realplayer 9 as well as a host of other formats so at least FF is picking mplayer plugins up.

Perhaps I have gone a bit over board on players which leads me to another question ...

Say I install VLC, it needs alot of other files. A complete uninstall only removes VLC - how do I revert back i.e. remove everything my last action did?

Do you think I should remove VLC and Realplayer and try and get the mplayer plugin working?

---

### Post by cpcnw on 2008-07-17
[http://ubuntuforums.org/showthread.php?t=540412&highlight=realplayer+bbc](http://ubuntuforums.org/showthread.php?t=540412&highlight=realplayer+bbc)

Duh, just found this and it actually worked first time !!!

Having said that though alot of the new news items are in a different video format which plays fine too. Also, iPlayer worked before doing the above ... theres a (the only?) tech program called 'Click' the quality on the real stream is terrible but pretty good on iPlayer!

Now... how to completely remove vlc / realplayer .....

---

### Post by ronacc on 2008-07-17
why remove them ? are you short of space ? I keep a bunch of different media players around .

---

### Post by cpcnw on 2008-07-17
Some threads have suggested that the plugins from multiple players cause problems. I generally prefer to have one app for each task, as long as it does the job!

Have looked at autoremove and gtkorphan however I was wondering whether a .deb has a 'package list' or a 'dependency list' that way, anything sucked into an install could be removed later?

---

### Post by psyke83 on 2008-07-17
> **cpcnw said:**
> Some threads have suggested that the plugins from multiple players cause problems. I generally prefer to have one app for each task, as long as it does the job!

Have looked at autoremove and gtkorphan however I was wondering whether a .deb has a 'package list' or a 'dependency list' that way, anything sucked into an install could be removed later?

Yes, browser plugins can cause conflicts or crashes, but you don't need to uninstall an entire application (after all, it's nice to have a choice of media players for a variety of reasons). In Firefox, go to Tools/Add-ons/Plugins and disable whatever plugins you don't want to use.

---

