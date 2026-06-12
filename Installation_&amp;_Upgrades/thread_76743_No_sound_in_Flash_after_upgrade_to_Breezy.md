---
title: "No sound in Flash after upgrade to Breezy"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Jackster on 2005-10-15
Hi all, 
I can't get any sound in Flash in Firefox after the upgrade to Breezy!
I've tried everything in this thread: [http://ubuntuforums.org/showthread.php?t=75237](http://ubuntuforums.org/showthread.php?t=75237)

Any ideas?

Thanks,
Jack

(Breezy rawks!)

---

### Post by ?rious on 2005-10-17
I didn't upgrade, I got a brand new copy of Breezy on my fancy new laptop. I thought flash was just a problem with Breezy getting confused by the 2 sound cards on my desktop, byutmy laptop, blessed with one only, is also having trouble.

*EDIT* Ah ha! I've solved my laptop problem, I just had to install the nonfree plugin. For all those unfamiliar with repository navigation, go to a terminal and type:

sudo apt-get install flashplugin-nonfree

Solved my laptop problem, though my bicarded desktop still befuddles the otherwise mighty ubuntu. At least in flash. And I tried the solution previously published for hoary, with the sudo ln...so.1 thingy.

---

### Post by kwaanens on 2005-10-18
I have no sound in flash also. Sound works great otherwise. Using either flash-plugins does not help.

Help!

- Ketil

---

### Post by skylark on 2005-10-18
Same problem, except I just upgraded my 32 bit chroot install (I run amd64). The breezy upgrade broke sound in flash. Any ideas?

I just want to hear [http://www.badgerbadgerbadger.com/](http://www.badgerbadgerbadger.com/)

---

### Post by dexae on 2005-10-19
try this
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

---

### Post by wlx on 2005-10-19
[QUOTE=dexae]try this
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```[/QUOTE]
It is exist in my breezy, yet there is no sound in flash, even in Firefox or gflashplayer.

---

### Post by kwaanens on 2005-10-19
[QUOTE=dexae]try this
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```[/QUOTE]

/usr/lib$ ls -a libes*
libesd.so.0  libesd.so.0.2.36  libesd.so.1

Already tried this. It does nothing.

- Ketil

---

### Post by Jackster on 2005-10-19
it just occured to me i do actually have two sound cards in my PC, maybe thats it

*goes off to take out soundcard*

---

### Post by wlx on 2005-10-20
[QUOTE=Jackster]it just occured to me i do actually have two sound cards in my PC, maybe thats it

*goes off to take out soundcard*[/QUOTE]
I don't think it. I have only one soundcard.

---

### Post by kwaanens on 2005-10-22
[QUOTE=wlx]I don't think it. I have only one soundcard.[/QUOTE]

Me too.

- Ketil

---

### Post by kwaanens on 2005-10-23
Just installed Opera, and Flash sound works there, sort of. The sound is out of sync, but there *is* sound.
Opera uses Firefox' plugins, doesn't it? So why doesn't Firefox work?

- Ketil

---

### Post by kwaanens on 2005-10-26
Update to this problem. Getting weirder...

I used the info on [this page]("https://wiki.ubuntu.com/SoundProblemsHoary") (Yes, I know that is for Hoary) and [this page]("https://wiki.ubuntu.com/RestrictedFormats").

So now my esd.conf looks like this:
```
# https://wiki.ubuntu.com/SoundProblemsHoary
[esd]
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

# [esd]
# auto_spawn=1
# spawn_options=-terminate -nobeeps -as 2 -d duplex
# spawn_wait_ms=100
# # default options are used in spawned and non-spawned mode
# default_options=
```

I have an rc-file in my firefox-profile which states:
FIREFOX_DSP="none"

If I start Firefox from menu and open badgerbadgerbadger.com there's no sound. However if I:
```
$ firefox www.badgerbadgerbadger.com
```
there is sound! Good too. However, if I navigate to other pages there's no sound. Now, when I navigate back to badgerbadgerbadger.com I get no sound again?!? What's going on?

Tried replacing esound with polypaudio. I get sound in flash, but no system sounds, and Audacity does not get the usual problem, but instead launches a high pitched sound, not stopping until I reboot. Back with esound again now.

This *really* shouldn't be so hard!

Please help! (And badgerbadgerbadger.com is just a test site for me, there's a lot of other stuff I'd like to have flash sound for, I don't like the song that much...)

- Ketil

---

### Post by naaman on 2005-10-29
I have found a fix for my situation.  After upgrading from Hoary to Breezy, I too could not get sound to work for flash animations.  I investigated the libflashplayer.so file with the following:

```
ncampbell@naaman:~/.mozilla/plugins$ strings libflashplayer.so | grep esd
Desde
libesd.so
esd_open_sound
esd_get_server_info
esd_play_stream
esd_record_stream
esd_free_server_info
esd_get_latency
esd_close
libesd.so.1
/tmp/.esd/socket
esdescendercyrillic
```

This was how the "symlink hack" was discovered.  It turns out that Breezy (or maybe Gnome 2.12 more specifically), has changed the way it creates ESD sockets in the /tmp directory.  It creates a /tmp/.esd-1000 directory which differs to what the Flash Plugin is looking for.  Suggested fix:

```
ncampbell@naaman:~$ cd /tmp
ncampbell@naaman:/tmp$ mkdir /tmp/.esd
ncampbell@naaman:/tmp$ ln -s /tmp/.esd-1000/socket /tmp/.esd/socket
```

Now sound works in the same laggy way it did before.

A potential problem exists when this issue arises when a multiuser environment needs flash sound..

---

### Post by kwaanens on 2005-10-30
That actually works!
No lag here!

Thanks a million!

- Ketil

---

### Post by kwaanens on 2005-10-31
However: /tmp/.esd/ is removed when the machine is shut down and then restarted. Should I use a script to be run at boot?
What should it look like and where do I put it?

- Ketil

---

### Post by skylark on 2005-11-02
Update: I managed to get mine working. 

I'm running AMD64 and had previously updated only my 32-bit chroot to breezy. I recently updated my whole system to breezy then followed: [http://ubuntuforums.org/showthread.php?t=75237](http://ubuntuforums.org/showthread.php?t=75237) (specifically the alsa-oss section worked). Note I also installed alsa-oss on my amd64 (main) install (as well as in the chroot). This has fixed flash sound and also flash hanging firefox.

Update2:
Hmm... now I can't listen to flash and play music through rhythmbox at the same time like I used to undery Hoary. Any ideas how to fix this??

---

### Post by ago on 2005-11-02
[QUOTE=kwaanens]However: /tmp/.esd/ is removed when the machine is shut down and then restarted. Should I use a script to be run at boot?
What should it look like and where do I put it?

- Ketil[/QUOTE]

Same issue here. 

The guide [http://ubuntuforums.org/showthread.php?t=75237](http://ubuntuforums.org/showthread.php?t=75237) is useless without /tmp/.esd/socket and once this symlink is created (as well as the symlink /usr/lib/libesd.so.1 -> /usr/lib/libesd.so.0) I get flash sound without any need to mess with alsa. My questions are:

1) Why don't I have /tmp/.esd at boot? Why isn't esd "regenerating" the symlink? Why does my esd like so much /tmp/.esd-1000/socket instead? It is possible that I deleted (with sudo) the files of /tmp/. Might this be the reason of all this mess?

2) Shall I create a script to regenerate /tmp/.esd/socket at boot or is it a matter of setting the right onwership/permission so that the socket symlink does not get deleted? Or is it some esd/makedev setting?

3) Do other users have /tmp/.esd/scoket? What ownership/permissions for the folder?

---

### Post by kwaanens on 2005-11-02
[QUOTE=ago]It is possible that I deleted (with sudo) the files of /tmp/. Might this be the reason of all this mess?[/QUOTE]

I doubt it. I have the same issue, and I have never messed with /tmp in any way. Isn't it just that it is a temporary folder which gets emptied when you shut down, and then some scripts put stuff in it when you boot up again?

- Ketil

---

### Post by skylark on 2005-11-02
[QUOTE=kwaanens]However: /tmp/.esd/ is removed when the machine is shut down and then restarted. Should I use a script to be run at boot?
What should it look like and where do I put it?[/QUOTE]
I've reverted to this method since it lets me listen to flash and music from other programs simultaneously. Here is how I setup my startup scripts to create /tmp/.esd automatically on restart:

1. Goto where startup scripts are kept:
cd /etc/init.d
2. Create a "flash-sound" script...
sudo vim flash-sound (replace vim with your choice of text editor)

3. make flash-sound contents look like:
```
#!/bin/sh
#Create symlink under /tmp for esd to get flash player working

mkdir /tmp/.esd
ln -s /tmp/.esd-1000/socket /tmp/.esd/socket
```

4. make sure your new script has the correct permissions:
sudo chmod 755 flash-sound

5. finally let the system know to execute it at startup:
sudo update-rc.d flash-sound start 51 S .
(don't miss the dot "." at the end of the line above)

---

### Post by kwaanens on 2005-11-02
Thanks! Problem solved!

-K

---

### Post by Donza on 2005-11-10
Thanks skylark! Problem finally solwed! This guide should be in How-to section. \\:D/ badger badger badger...

---

### Post by jrib on 2005-12-11
Wow, good job in figuring out the problem.  After reading it through, I thought I might be able to just "fix" libflashplayer.so.  So I opened it up in ghex2 and played around a bit.  Here's what I did:

1.  installed ghex2
2.  made a backup of /usr/lib/mozilla/plugins/libflashplayer.so and then edited it with ghex2
3.  edit -> goto byte -> "0x1D5C4C" -> OK
5.  (made sure I was NOT in insert mode) typed:  ```
30 00 2F 74 6D 70 2F 2E 65 73 64 2D 31 30 30 30 2F 73 6F 63 6B 65 74 00
```
which corresponds to changing: 1./tmp/.esd/socket.Macro to 0./tmp/.esd-1000/socket.
6. saved

No more need for symbolic links and I have sound in my flash playing alongside BMP :)

[edit] and for the record I tested with badger badger badger too!
*don't simply mimic these instructions blindly since it will depend on what your libflashplayer.so looks like*

---

### Post by jrib on 2005-12-11
sound is still incredibly lagged though... any ideas?

---

### Post by rwabel on 2005-12-17
work fine for me. the only difference for me is that the plugin is here: ~/.mozilla/plugins/libflashplayer.so

---

### Post by qwertz on 2006-01-16
[QUOTE=_jason]
1.  installed ghex2
2.  made a backup of /usr/lib/mozilla/plugins/libflashplayer.so and then edited it with ghex2
3.  edit -> goto byte -> "0x1D5C4C" -> OK
5.  (made sure I was NOT in insert mode) typed:  ```
30 00 2F 74 6D 70 2F 2E 65 73 64 2D 31 30 30 30 2F 73 6F 63 6B 65 74 00
```
which corresponds to changing: 1./tmp/.esd/socket.Macro to 0./tmp/.esd-1000/socket.
[/QUOTE]

I guess this only works if the user with uid 1000 is the only user on the system. A cleaner workaround would be to
[LIST=1]
[*]only modify "1" (0x31) to "0" (0x30) at 0x1D5C4C in /usr/lib/mozilla/plugins/libflashplayer.so (using ghex2)
[*]write a wrapper script for esd which symlinks /tmp/.esd-<uid>/socket to /tmp/.esd/socket
[/LIST]

---

### Post by MadL on 2006-02-10
Thanks, skylark! Ran into this problem when the solutions in the Ubuntu wiki didn't work for Firefox 1.5, and came across your post. I agree that this would be a good addition for the howto. :)

---

### Post by jrib on 2006-02-24
[QUOTE=qwertz]I guess this only works if the user with uid 1000 is the only user on the system. A cleaner workaround would be to
[LIST=1]
[*]only modify "1" (0x31) to "0" (0x30) at 0x1D5C4C in /usr/lib/mozilla/plugins/libflashplayer.so (using ghex2)
[*]write a wrapper script for esd which symlinks /tmp/.esd-<uid>/socket to /tmp/.esd/socket
[/LIST][/QUOTE]

good point, didn't realize that's how it works but it makes sense

---

### Post by s|k on 2006-03-06
[QUOTE=naaman]I have found a fix for my situation.  After upgrading from Hoary to Breezy, I too could not get sound to work for flash animations.  I investigated the libflashplayer.so file with the following:

```
ncampbell@naaman:~/.mozilla/plugins$ strings libflashplayer.so | grep esd
Desde
libesd.so
esd_open_sound
esd_get_server_info
esd_play_stream
esd_record_stream
esd_free_server_info
esd_get_latency
esd_close
libesd.so.1
/tmp/.esd/socket
esdescendercyrillic
```

This was how the "symlink hack" was discovered.  It turns out that Breezy (or maybe Gnome 2.12 more specifically), has changed the way it creates ESD sockets in the /tmp directory.  It creates a /tmp/.esd-1000 directory which differs to what the Flash Plugin is looking for.  Suggested fix:

```
ncampbell@naaman:~$ cd /tmp
ncampbell@naaman:/tmp$ mkdir /tmp/.esd
ncampbell@naaman:/tmp$ ln -s /tmp/.esd-1000/socket /tmp/.esd/socket
```

Now sound works in the same laggy way it did before.

A potential problem exists when this issue arises when a multiuser environment needs flash sound..[/QUOTE]
This worked for me! Thanks. :)

---

### Post by chokuchou on 2006-09-04
This is a perfect solution!

*But* when I run Rhythmbox, it stops working. There is no flash sound. Even after I shutdown Rhythmbox and restart esd. It only works when I haven't run Rhythmbox yet on my laptop after a fresh boot...

Strange, eh?

---

### Post by hanulbada on 2006-09-15
Haha, sorry if I'm a little noobish at these things but, what is sudo?

---

### Post by surfjdh on 2007-11-09
solved for me 2, had flash 9, and firefox/opera, upgraded to 7.10 and sound in flash broke, but its ok now

---

