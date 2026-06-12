---
title: "gdm/gconf errors after fresh install"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2010-11-11
I did a fresh install of Ubuntu 10.10 i386 on Asus EeePC S101 (1GB RAM, 32GB SSD).  On the first boot of the freshly installed system I get 2 error popups several seconds after the screen goes into black graphical mode:

popup 1:
```
Could not update ICEauthority file /var/lib/gdm/.ICEauthority
```After I close that popup, I immediately get another:

popup 2:
```
There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
```I've researched this through other posts, but they seem to be regarding a ".ICEauthority" file in the home directory.  In this case, it is in a system/gdm directory.  Further, it is missing.  The installation did not create such a file, nor was one created on first boot (at least before the popup error messages).

I have re-installed 3 times, all from scratch (always formatting all 4 partitions), and this happens every time.

On another machine I have running Ubuntu 9.10 amd64 I do see the file "/var/lib/gdm/.ICEauthority" does exist, and has about 18k bytes of content, consisting of a mix of binary and text, where the text parts looks like variations of file paths.

This is my 2nd attempt to post this, so I hope I didn't forget anything from the previous try (which failed because UF logged me back out and didn't save the buffer).

1.  Should this file exist after the install is done?  Or is it supposed to be created later?

2.  Can I fake this file by creating an empty one with touch, and using the same ownership and permissions as from the other system?

3.  How can I modify the installer ISO so that it will apply whatever corrections are needed?


Here are images of the popups taken by camera:

popup 1:
[IMG]http://phil.ipal.org/ufo/20101111/error-0001-could-not-update-iceauthority-file.jpg[/IMG]

popup 2:
[IMG]http://phil.ipal.org/ufo/20101111/error-0002-there-is-a-problem-with-the-configuration-server.jpg[/IMG]

I shrank these images to make them fit the page better.  Sorry for the Moiré pattern it created.

---

### Post by dino99 on 2010-11-11
same thread as yours:

[http://ubuntuforums.org/showthread.php?t=1081730](http://ubuntuforums.org/showthread.php?t=1081730)

---

### Post by Skaperen on 2010-11-11
> **dino99 said:**
> same thread as yours:

[http://ubuntuforums.org/showthread.php?t=1081730](http://ubuntuforums.org/showthread.php?t=1081730)

It RESEMBLES mine, but is NOT the same.  It may be the same bug in Gnome (if that's where there is a bug ... I don't know, yet).  But the circumstances are different.  In the referenced link, and in many others I saw when I researched this (note that my first post references this), they refer to the file in the user home directory, managed under the user permissions.

What caused these problems is the concern.  In the cases with the file in the home directory, something went wrong with handling the user, or user home directory.  In some I found, the cause was issues with user deletion and re-creation, and/or maybe involving restoring user files.

None of that applies in the case I encountered, because:

1.  It was not in any user home directory (and thus, could not be caused by anything done to the user or home directory).

2.  It was the result of a fresh install, and happened before any user ever logged in (and this, could not be caused by anything done to the user or home directory).

One "deficiency" (I don't call these bugs, but they may warrant improvements) in Gnome is by not telling more details about why it cannot update the file.  For example, does it expect the file to exist before hand?  If so, then we need to look back at the installer, or the package the initial file was to be in, or an initialization script that should have created it.  If the file wasn't expected to pre-exist, but would be created, then more detail about the failure to create it would help.  But from the messages, all that is known is that something didn't work as expected.

If there was a way to run the entire Ubuntu installation under strace, I might be able to figure it out.  I do figure out lots of bugs by seeing what programs TRY to do via syscalls viewed in strace.  For example, does it stat() the file first?  Does it open() with O_CREAT?

---

