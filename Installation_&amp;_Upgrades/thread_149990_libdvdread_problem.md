---
title: "libdvdread problem"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by parsival on 2006-03-25
Hi Forum,
       I am having a problem playing DVDs.
I can play audio CDs and browse data CDs and DVDs.

Using mplayer, vlc or totem-xine I get an error message related to libdvdread. The error message is
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).

The output for totem is below. I can give you the output for
mplayer and vlc if you think they might be revealing.

Here are the relevant library versions. 

libdvdcss2               1.2.5-1  
libdvdnav4               0.1.9-3
libdvdread3              0.9.4-5

I have searched on the error message. While it appears in a number of postings (not on this forum) I dont really understand the advice being offered.

Bye
Parsival


(totem:8827): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:8827): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
libdvdnav: Using dvdnav version 1.0.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: RHIENGOLD
libdvdnav: DVD Serial Number: 3B4AB345___MVB__
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/robd/.dvdnav/RHIENGOLD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000018a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000002df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00002523
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002571
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
libdvdnav: *** pgci_ut handle is NULL ***

---

### Post by parsival on 2006-03-26
Hi Forum,

I read a suggestion that a way forward would be to copy 
video_ts from the dvd and try to play them directly with mplayer.

I tried to copy video_ts and and got lots of errors. 
After a bit of lucking around I uncommented

/dev/hda {
       dma = on
       interrupt_unmask = on
       io32_support = 0
}

in /etc/hdparm

(I already had dma on).I dont know what these parameters are doing but I seem to get less errors when copying
from the dvd (I still get some). More interestingly I now have mplayer playing a dvd!!

Bye 
Rob

---

