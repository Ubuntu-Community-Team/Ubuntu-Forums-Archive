---
title: "&quot;Open With&quot; selections duplicated in 9.10 install"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2009-11-20
Had NO problems doing the update from 9.04 to 9.10 (took 6 hrs. to get the files with cable connection, but that's a Comcast problem!) --  However, now I find that when I right-click on a video file and select the "Open with" box, I get the following for all the video formats that I have on my system (all have "Other" following the listings as well):

_.flv_
Movie Player
Avidemux (GTK+)
Avidemux (GTK+)
Movie Player
VLC Movie Player
VLC Movie Player

_.wmv_
Movie Player
MPlayer Movie Player
MPlayer Movie Player
VLC Movie Player
Movie Player
VLC Movie Player

_.mpg_
Movie Player
MPlayer Movie Player
MPlayer Movie Player
Avidemux (GTK+)
VLC Movie Player
Avidemux (GTK+)
Movie Player
VLC Movie Player
xine

_.mp4_
Movie Player
VLC Movie Player
Movie Player
VLC Movie Player

_.avi_
Movie Player
Movie Player
MPlayer Movie Player
MPlayer Movie Player
VLC Movie Player
VLC Movie Player
Avidemux (GTK+)
Avidemux (GTK+)
xine

My default is Movie Player, and that opens just fine, etc. etc.

BUT, why do I have doubled listings, in a seemingly random order, and how do I get rid of that?  :confused: 

Thanks in advance!!  dk

---

### Post by ajgreeny on 2009-11-20
Right click on a file and choose Properties, go to Open With tab and highlight one of the two versions of the various players and Remove it with the remove button.

Odd why there should be two, no doubt something to do with the update as opposed to a clean install, but this way should get rid of one of the duplicates showing.

---

### Post by dkolars on 2009-11-20
Thanks...

I neglected to mention that I'm viewing the file listing with Gnome-Commander...  
so...
I click on "Properties", and the File Properties window opens with 3 tabs:  Properties, Permissions, & Metadata.

On the Properties page, there is a "Change" button to click on after the "Opens with: Movie Player" listing.  But, clicking it opens nothing.  Clicking the "Help" button on the bottom does nothing...

Suddenly realizing that my problem might be caused by Gnome-Commander (I've been using a 2-pane file viewer since Norton Commander came out!), I found the Ubuntu File viewer and was able to delete duplicate listings...  

They still show up in Gn-Commander, however, so that is probably where the problem is...  thanks again...

---

