---
title: "&quot;Files&quot; freezes for ~30 seconds when deleting video files"
date: 2015-01-17
forum: Installation &amp; Upgrades
---

### Post by rolf4 on 2015-01-17
I'm running Ubuntu 14.10, but I originally installed 14.04.  When I was using 14.04, I had no trouble deleting files.  Ever since I upgraded (several weeks ago) from 14.04 to 14.10, I find that the "Files" application freezes for about 30 seconds most of the time when I delete a video file.  (I've tried .mkv, .avi, mp4).  I would say that 90% of the time, the Files program freezes up; after a few seconds it fades to grey, and then after about 30 seconds, it returns to life.  Only the "Files" application is frozen during this time.  I can switch tasks and run other things without any trouble.

I have tried deleting these types of files from the command-line without any delay.  And I've tried it with the trash empty, and with the trash full of lots of files.  That didn't seem to make any difference.

Is anyone else experiencing this in 14.10?  Is this some artefact of the upgrade?  How can I avoid this delay?

---

### Post by ajgreeny on 2015-01-17
Sending to trash or totally deleting these files and how big are they?

I assume sending to trash in view of your comment about full or empty trash, but what happens if you hit delete holding shift to totally delete those files?

---

### Post by rolf4 on 2015-01-17
I did some experimenting and found some interesting results.

First, I will answer your question.  I does not matter if I hold shift.  Permanently deleting the file or just sending it to the trash causes the same 30 second delay.  In fact, when I hit shift+delete, it takes 30 seconds just to show the prompt asking me if really want to permanently delete the file.

Now, I noticed something else.  This only happens if I recently played the file with VLC.  My normal usage pattern is to watch a video with VLC, when the video finishes I close VLC and immediately try to delete the file.  Under those circumstances, Files locks up for 30 seconds.

If I wait about 30 seconds after closing VLC, then I can delete the files without any delay.  It's as if VLC is somehow holding a lock on those files that is preventing Files from deleting them.  I checked, and the VLC process disappears from "ps" output immediately after I close the GUI [it doesn't hang around for 30 seconds or anything like that].

---

### Post by ajgreeny on 2015-01-18
Very strange!

I have no answers to that, I'm afraid.

---

