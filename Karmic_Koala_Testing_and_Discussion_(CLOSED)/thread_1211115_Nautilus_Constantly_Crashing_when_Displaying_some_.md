---
title: "Nautilus Constantly Crashing when Displaying some video files"
date: 2009-07-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by martinpm24 on 2009-07-12
Nautilus window freeze when Displaying some video files, not all the files, some. Generally freeze after 30-60sec. The thumbnails is OK. The video are .mkv and .avi,

---

### Post by morryis on 2009-07-12
I experience the same, nautilus becomes non-responsive after a few seconds when displaying folders with video files. My bug report: [#397192]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/397192").

Please confirm it and try to add a backtrace of the crash as requested by Sebastien

---

### Post by martinpm24 on 2009-07-12
yes, the same.

---

### Post by MacUntu on 2009-07-12
Can anyone provide a file that's causing the freeze?

---

### Post by martinpm24 on 2009-07-12
In my case, the size of the file and h264 encoded appear to be the problem. With avidemux, make a cut of the file (sample), to upload it, but i realize that nothing happend with the sample i made... So i increase the size of (the sample), more, more, when i reach more than 1 giga in the size (of the sample), the sample start to freeze nautilus.

---

### Post by morryis on 2009-07-12
For everyone who wants to test, the 1080p MPEG-4/AVC version of ["Sita Sings the Blues"]("http://www.archive.org/download/Sita_Sings_the_Blues/Sita_Sings_the_Blues_1080p.mp4") is one file that is causing nautilus freezes on my system. Just download this file and put it in a folder, open this folder with nautilus and wait for 20-30 seconds.

---

### Post by ronacc on 2009-07-12
could you maybe supply a file that won't take 7hrs to d/l ?

---

### Post by psyke83 on 2009-07-12
> **ronacc said:**
> could you maybe supply a file that won't take 7hrs to d/l ?

That's the point; only large files trigger the problem. Do you not have a large movie available to test this issue? It may be more economical to self-rip a DVD to an .avi format, than to download something.

I don't have a link to any content, but I can tell you that a 700mb xvid file will also trigger this issue, so there's no need to download a 4gb file.

---

### Post by ronacc on 2009-07-12
ok I tried a an avi file (1.4 gb ) and yes it crashed nautilus  also mplayer threw an error , when I restarted nautilus and tried the same file using "open with" from nautilus to play the file with VLC it played fine but still crashed nautilus , the crash of nautilus did not interfere with vlc playing the file .

---

### Post by MacUntu on 2009-07-13
I'll later try to get a backtrace if I can (and nobody could provide one in the meantime).

The only thing I've observed so far is a slowdown because nautilus generates the preview pic for the movie (by scanning through the whole clip?).

---

### Post by MacUntu on 2009-07-13
Just finished downloading this "Sita Sings the Blues" (ya, rly! :D). Nautilus starts taking a lot of RAM (~1GB) and uses a lot of CPU (system monitor shows 100% but it's more like 50% of my dual core setup).

Should it actually crash nautilus? The window is unresponsive but no crash.

---

### Post by martinpm24 on 2009-07-13
> **MacUntu said:**
> Just finished downloading this "Sita Sings the Blues" (ya, rly! :D). Nautilus starts taking a lot of RAM (~1GB) and uses a lot of CPU (system monitor shows 100% but it's more like 50% of my dual core setup).

Should it actually crash nautilus? The window is unresponsive but no crash.

Yes you are right, unresponsive window, no crash.

---

### Post by ronacc on 2009-07-13
yes I think "crash" is a bad description , on my sys like yours nautilus becomes unresponsive but can be closed with the close button , which brings up a dialog box saying " filename.xxx is not responding , force quit" .

---

### Post by martinpm24 on 2009-07-13
ok i edit the first post :grin:

---

### Post by MacUntu on 2009-07-13
Added a backtrace (which doesn't look useful to me but that doesn't mean anything :D).

---

### Post by morryis on 2009-07-13
No freezes when you disable preview i.e. thumbnail generation in nautilus.

---

