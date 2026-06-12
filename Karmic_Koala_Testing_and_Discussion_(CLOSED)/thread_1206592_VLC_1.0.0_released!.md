---
title: "VLC 1.0.0 released!"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CoreyB. on 2009-07-07
[http://forum.videolan.org/]("http://forum.videolan.org/")

---

### Post by ELD on 2009-07-07
Awesome news updating my windows install right now, will update when i boot into linux next :)

---

### Post by tjeremiah on 2009-07-07
I searched and only see the rc2 version.
EDIT : Its showing up now.

---

### Post by tjeremiah on 2009-07-07
it does not want to install in karmic.

---

### Post by budluva04 on 2009-07-07
where are you guys installing this from? it hasn't hit repos yet?

why are you using a development os, and not helping test it? wait until it hits repos in a few days and then help out

you all know you can't file bugs against a package you haven't installed from ppa/repos right? you'll have to file directly to vlc if you run into any problems...

---

### Post by Reiger on 2009-07-07
VLC provides its own *deb files which in turn find their way to Debian Sid which is currently the source of (most) Koala packages... ? Am I missing something here?

And as you can see:
```
sudo apt-cache policy vlc
vlc:
  Installed: 1.0.0~rc2-1ubuntu1
  Candidate: 1.0.0~rc2-1ubuntu1
  Version table:
 *** 1.0.0~rc2-1ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/universe Packages
        100 /var/lib/dpkg/status

```

We're not that far behind. ;)

---

### Post by vishalrao on 2009-07-07
i thought that since debian import freeze has passed, you need to file a bug/request for an exception to merge into the karmic packages repos?

---

### Post by budluva04 on 2009-07-08
no its coming within the next few days down the pipes

---

### Post by Teamgeist on 2009-07-08
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

---

### Post by vaibhav on 2009-07-08
> **Teamgeist said:**
> [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)
Hardy package is still 0.9.9a :(

---

### Post by jpeddicord on 2009-07-08
> **vishalrao said:**
> i thought that since debian import freeze has passed, you need to file a bug/request for an exception to merge into the karmic packages repos?

That just means that imports are no longer automatic. It is still very easy to request a sync from Debian up until feature freeze.

---

### Post by nazia on 2009-07-08
W00t VLC.
I am waiting for it to arrive on synaptic package manager...

cheers
Nazia Assad

---

### Post by ronacc on 2009-07-08
built vlc from source on karmic amd64 , make threw alot of warnings but completed and the install went ok , but it wont start . from term it gives .
```
vlc: error while loading shared libraries: libvlc.so.2: cannot open shared object file: No such file or directory
```
the lib is there in /usr/local/lib , actualy a symlink to libvlc.so.2.2.0 
which is there also .

---

### Post by jpeddicord on 2009-07-08
Run `sudo ldconfig` to update your library cache, then try again.

---

### Post by ronacc on 2009-07-08
> **jacobmp92 said:**
> Run `sudo ldconfig` to update your library cache, then try again.

that got it . Thanks .

---

### Post by plun on 2009-07-12
Available for Karmic....;)

> **vlc (1.0.0-1ubuntu1) karmic**; urgency=low

  * Remaining changes to debian:
    - build against libxul-dev instead of iceape-dev
    - build against libass-dev and libx264-dev
    - build against and install libx264 plugin
    - add Xb-Npp header to vlc package

**vlc (1.0.0-1) **unstable; urgency=low

  * New Upstream Release
    + Closes: #536081, LP: #396548
    + Refresh patches
  * no longer closes when pausing from the notification area, LP: #371515
  * fix encoding bug when opening subtitles with non-latin characters,
    LP: #394449
  * Don't install the alsa and OSS access module on kfreeBSD (Closes:
    #535101) - thanks to Javier Mendez Gomez
  * Force at least libvlc 1.0.0 becasue of tha soname change of
    libvlccore
  * Delete a symbols who was present by mistake.
  * No need for dh_desktop. It's a no-op
  * New standard version. No change needed
  * Fix make distclean. New patch taken from upstream
  * Upstream make distcheck has been fixed. No need to save Changelog

[https://lists.ubuntu.com/archives/karmic-changes/2009-July/003943.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/003943.html)



---

### Post by yelo3 on 2009-07-12
My audio is really choppy with the alsa plugin (I can hear only some glitches), and also with the pulse plugin (the audio works less for 1 second, then there is a glitch, than it works again for 1 second, and so on)
do you know a fix?

---

### Post by tjeremiah on 2009-07-12
> **plun said:**
> Available for Karmic....;)

*jumps for joy*

---

### Post by tjeremiah on 2009-07-12
> **yelo3 said:**
> My audio is really choppy with the alsa plugin (I can hear only some glitches), and also with the pulse plugin (the audio works less for 1 second, then there is a glitch, than it works again for 1 second, and so on)
do you know a fix?

sometimes it works, sometimes it doesnt in Karmic and I notice the problem continues with this new release. Anyway, the way I try to fix it is :

Tools > Preferences > at the bottom left click 'all' > click the audio tab > Output Modules > select alsa > set a device for it

If that doesnt work, play around with the other modules until it works.

---

### Post by psyke83 on 2009-07-12
> **yelo3 said:**
> My audio is really choppy with the alsa plugin (I can hear only some glitches), and also with the pulse plugin (the audio works less for 1 second, then there is a glitch, than it works again for 1 second, and so on)
do you know a fix?

You need to enable glitch-free playback in PulseAudio. I think that the next pulseaudio update will do this, but in the meantime, see [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/132") comment to manually enable glitch-free.

After making this change, keep using the Pulse plugin in VLC, as the ALSA plugin still causes slight problems. Other applications should be more stable with ALSA output (e.g. WINE), but only if your hardware works with glitch-free.

---

### Post by yelo3 on 2009-07-13
totem works correctly, so I'm wondering why vlc needs this hack

---

### Post by psyke83 on 2009-07-13
> **yelo3 said:**
> totem works correctly, so I'm wondering why vlc needs this hack

It's not a hack. Totem may work correctly without glitch-free, but many other applications do not - Skype and WINE are the biggest examples.

See: [https://fedoraproject.org/wiki/Features/GlitchFreeAudio](https://fedoraproject.org/wiki/Features/GlitchFreeAudio)
The bug report that I mentioned also goes into some details if you're patient enough to read the comments.

---

