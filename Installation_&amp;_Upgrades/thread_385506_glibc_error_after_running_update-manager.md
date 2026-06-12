---
title: "glibc error after running update-manager"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by jvector on 2007-03-15
Hi,
just got back from a week's holiday and my Feisty update-manager icon
told me that there were 226 updates waiting; I went ahead and
installed them, and my gnome-panel disappeared! Restarted X, 
still no panel. It "flickers" into and out of existence about 8 or 9 times
then stays absent. The rest of the desktop works "ok".

Running gnome-panel from a terminal showed a big crash trace, starting with
victor@ss07:~$ gnome-panel
*** glibc detected *** gnome-panel: munmap_chunk(): invalid pointer:
0x00007fff918946a0 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2af91d4d03a6]
/usr/lib/gnome-panel/libclock-applet.so[0x2af926453ae5]

followed by lots of traceback and a memory map dump. [1]

Googling for "glibc detected" "invalid pointer" gnome-panel led
eventually to a recommendation to use

export MALLOC_CHECK_=1 # Report error and continue

before running the crashing program. Sure enough if I do that then the
panel runs, reporting this in the terminal:
victor@ss07:~$ gnome-panel
malloc: using debugging hooks
malloc: using debugging hooks
*** glibc detected *** gnome-panel: free(): invalid pointer:
0x00007fff0de6b3f0 ***
*** glibc detected *** gnome-panel: free(): invalid pointer:
0x00007fff0de690b0 ***
*** glibc detected *** gnome-panel: free(): invalid pointer:
0x00007fff0de697d0 ***
*** glibc detected *** gnome-panel: free(): invalid pointer:
0x00007fff0de68a10 ***

(gnome-panel:16737): Gtk-WARNING **: gtk_widget_size_allocate():
attempt to allocate widget with width -12 and height 24
*** glibc detected *** gnome-panel: free(): invalid pointer:
0x00007fff0de6d0d0 ***

that last line continues appearing and eventually other apps like gnome-terminal fail to start, reporting "too many open files". If at that time I do lsof there are indeed hundreds of files open on gnome-panel; I can then kill gnome-panel and then restart it.

This is my box:
victor@ss07:~$ uname -a
malloc: using debugging hooks
Linux ss07 2.6.20-9-generic #2 SMP Sun Feb 25 22:59:06 UTC 2007 x86_64 GNU/Linux

(The reason I am on feisty is because 6.10 did not have the sky2 module required by my ethernet card)

The ref I found suggested putting that export MALLOC_CHECK_=1 into
/etc/profile, but this seems like a bit of a fudge. That invalid
pointer message has popped up another 9 times while I've been writing
this message.

Is this a problem I should be reporting? And is there a way to find a
better solution?

[1] [http://hantslug.pastebin.com/897754](http://hantslug.pastebin.com/897754)

---

