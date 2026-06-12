---
title: "[SOLVED] weird totem/youtube no redraw of gui bug"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 0xdeadc0de on 2008-10-22
it works fine underneath, but on my first try I searched for aerosmith.. it popped up a lot of videos. So I added some to my playlist, and started scrolling down adding more videos as I scrolled. 

Then at one point it appeared the gui locked up, the videos were still playing however. I killed totem and restarted it, did another youtube search for something else, and nothing popped up in the sidebar - BUT, when I double click on the blank area where the video results should be it played the video I searched for. So it's all working in the background but won't redraw any of the gui (movie/edit/view/etc/playlist dropdown menu in sidebar, nothing of the gui redraws)

Also happens every time with second search. On first search it works fine, second search it "locks up"

It "freezes" at "fetching search results" after the orange bar moves from left to right once...(hope that makes sense)

solved by doing rm /tmp/totem*

restarting totem doesn't fix it, only removing the tmp file does.

am I alone with this little bug?

---

### Post by 0xdeadc0de on 2008-10-22
*Removed post, was useless

---

### Post by 0xdeadc0de on 2008-10-22
Okay, please ignore the above post, that fixed nothing. But, I spent a couple hours hacking away at module, and found a couple startling mistakes... I'll be submitting the patch to the totem project, it's attached here as well. I submit it to the Ubuntu community first because, well, I love Ubuntu just that much.

For me this patch appears to get rid of ALL flakiness of the youtube module - so far. More testing needed of course, but I think it's done.

to apply:

gunzip youtubefixup.patch.gz
sudo patch -p1 < youtubefixup.patch

It should patch /usr/lib/totem/plugins/youtube/youtube.py

:guitar::popcorn:

Filed bugreport with gnome bugzilla:
[http://bugzilla.gnome.org/show_bug.cgi?id=557470](http://bugzilla.gnome.org/show_bug.cgi?id=557470)


*** Please use the latest patch on the bug report at [http://bugzilla.gnome.org/show_bug.cgi?id=557470](http://bugzilla.gnome.org/show_bug.cgi?id=557470)

---

