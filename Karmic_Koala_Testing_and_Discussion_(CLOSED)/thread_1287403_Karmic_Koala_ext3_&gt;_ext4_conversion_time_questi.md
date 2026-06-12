---
title: "Karmic Koala ext3 &gt; ext4 conversion time question."
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chris_andrew on 2009-10-10
Hi, all.

I've done a succesful upgrade to KK. I then followed the Ubuntu wiki guide to converting from ext3 to ext4. I have rebooted and my splashscreen (xfce mouse) just has a line across it and appears to be stuck.

I'm converting my / and /home, which totals about 90gb. I suspect the filecheck is still being done (2 hours), but can't hear whether any disk activity is happening because of my PC's fan.

Does anyone know whether this sounds like it is working as it should be?

Cheers,

Chris.

---

### Post by chris_andrew on 2009-10-10
A bit more information, can anyone help?

I did a successful update-manager -d upgrade, but when I did the ext3 > 4 conversion as per the Ubuntu wiki, my new boot is not happy.  Most times when I boot, I get the mouse splashscreen, then it seems to hang.  On one boot I got the log-on screen, but then I got lots of colours and it froze. I tried CTRL+ALT + Backspace, but nothing happened.  In Recovery mode I get this message: "cannot stat /tmp/.X11-unix (no such file or director), aborting".  Anyone got any ideas?  Failing this, I'll have to do a proper install.

Cheers,

Chris.

---

### Post by chris_andrew on 2009-10-10
Well things have gone from bad to worse.  I've tried everything I can think of to overcome my ext4 problem.  All my partitions are now gone, apart from /home which has ext4 and which I prefer not to delete (no, I didn't back-up).  

My question is, can I change my ext4 to something readable, or even something I can use to move my data somewhere else.

I have a spare HDD, so am more than happy to migrate the data if this helsp, I just don't want to lose it.

BTW, I used this guide to 'upgrade' from ext3 > 4:

[https://help.ubuntu.com/community/ConvertFilesystemToExt4](https://help.ubuntu.com/community/ConvertFilesystemToExt4)

Any help really appreciated.

Cheers,

Chris.

---

