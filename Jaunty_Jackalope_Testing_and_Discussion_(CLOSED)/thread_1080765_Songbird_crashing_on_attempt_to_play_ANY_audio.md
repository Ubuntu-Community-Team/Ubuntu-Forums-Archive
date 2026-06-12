---
title: "Songbird crashing on attempt to play ANY audio"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShakataGaNai on 2009-02-25
I'm running Jaunty Netbook Remix Alpha i386 (up to date as of today 2009-02-25) on an Eee PC 1000.  Sound (input and output) and video work just fine on the system through other apps (like VLC).  I know it's not exactly "supported" but I was hoping someone had seen an error similar and could direct me in the right direction.  

I installed Songbird 1.0 from Unter-Hund.com per [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird) .  When I run it, I get the following output:
```
$ songbird 

(songbird-bin:6113): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsttheora.so': /usr/lib/gstreamer-0.10/libgsttheora.so: undefined symbol: gst_util_seqnum_next

(songbird-bin:6113): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_plugin_add_dependency_simple

(songbird-bin:6113): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstgnomevfs.so': /usr/lib/gstreamer-0.10/libgstgnomevfs.so: undefined symbol: gst_query_set_uri

(songbird-bin:6113): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstgio.so': /usr/lib/gstreamer-0.10/libgstgio.so: undefined symbol: gst_query_set_uri
*** Search: Starting search engine enumeration...

*** Search: search engine enumeration done...

```
I'm not sure if that is a big deal.  But I suspect it might be.  When I go to try and play any audio (mp3 or SHOUTcast), I dumps the following and crashes:
```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
(messages repeat dozens of times)

E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
E: shm.c: mmap() failed: Cannot allocate memory
(message repeats over 10,000 times)

E: client-conf-x11.c: XOpenDisplay() failed
E: shm.c: shm_open() failed: Too many open files
E: shm.c: mmap() failed: Cannot allocate memory
E: mainloop.c: ERROR: cannot create wakeup pipe

** ERROR **: file pulsesink.c: line 207 (gst_pulsesink_init): assertion failed: (pulsesink->mainloop)
aborting...
Trace/breakpoint trap (core dumped)

```

I'm at a loss as to what to do.  Any input would be appreciated.

---

### Post by Yellow Pasque on 2009-02-25
I've seen Songbird becoming increasingly popular, so I'm going to have a go at playing with various .debs and building from source on my test Intrepid install in the next few days.

I just wanted to subscribe to this thread so that if I figure anything out, I can pass it along.

---

### Post by ShakataGaNai on 2009-02-25
I just wanted to add that all 4 lib files do exist.  I also tried installing gstreamer0.10-plugins-ugly-multiverse and gstreamer0.10-plugins-bad-multiverse without an effect on the outcome.  To be honest, I don't know the differences between good/bad/ugly and in verse/multiverse.  Shot in the dark.

---

### Post by ShakataGaNai on 2009-02-26
2 other updates that might help.  #1 - While checking on an unrelated issue I noticed that pulseaudio was throwing errors into the syslog about not having permissions for my Equalizer tinkering.  I have since disabled the .asoundrc file and this error is now gone.  There is no entries into syslog with the exception of this on boot: "warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)"

#2 - Songbird works perfectly if I launch it as root.

So many problems solved by being root.... but it's not exactly a graceful fix.  Thoughts?

---

### Post by Yellow Pasque on 2009-02-26
> disabled the .asoundrc file
I'm sorry, but I don't understand what that means. Can you explain?

Can you post the output of:
```
groups
```

---

### Post by ShakataGaNai on 2009-02-26
> **Temüjin said:**
> I'm sorry, but I don't understand what that means. Can you explain?



I followed the following guide (See Apendix D): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) . I've now disabled it, so it's no longer an issue.

`groups` output:
```
(MyUsername) adm dialout cdrom plugdev lpadmin pulse-rt admin fuse sambashare
```

---

