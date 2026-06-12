---
title: "Pitivi render is frustrating me"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by photographicd on 2010-04-05
This may not be the right place for this discussion but since the Pitivi editor seems to be premiering with lucid I thought I would mention it.  I was really excited when I heard that Ubuntu was featuring a good video editor with the next release.  I got the latest Beta (1) and started editing.  The interface was OK except lacking some features.. I realize these are features the developers would like to add.  But I got my video edited.

Then it came time to render the video.  I filmed my video with a 5D Mark 2 from Canon and was editing 1080p video.  I was expecting a good  1080p export.  What I got was a poor export with a gigantic black border around my actual video.  Since I noticed that ogg theora actually had a "black border" option for some reason.  (Who would want that! On by default!)  I tried switching to another h.263 format but that gave me the same gigantic black border around my video.

I'm posting this here on the Ubuntu boards because I really wish Ubuntu would mature into a usable product but it's really poor experiences like this why I can't invite people to use it.  Really frustrated and going back to Windows to edit my video..

---

### Post by Merk42 on 2010-04-05
Maybe this would be better suited in Art & Design or Multimedia?

Anyway, are you sure it wasn't a setting problem?

---

### Post by Keen101 on 2010-04-16
yeah, pitivi sucks. I was trying to fix a video with a syncing problem, and same deal when i went to render. The quality is nowhere near what was supposed to be exported, and this horrible black border was around my video as well.


I think im going to try kdenlive instead.

(and, yeah this thread is probably in the wrong place. I'm not using lucid at all.)

---

### Post by super breadfish on 2010-04-24
I started using Pitivi recently and had the same problem. I'm using Pitivi 0.13.4.

Try setting the rendering options in the Project Settings window (Project > Project Settings) and then render the project.

When I do this, the project renders properly, without a black border.

---

### Post by Rob2687 on 2010-04-24
It stopped rendering anything at all for me. When I choose the settings and click render the progress bar sits at 0% and the process uses no CPU at all.

---

### Post by philinux on 2010-04-24
Sounds like from the above a bug needs reporting if it hasn't already.

```
ubuntu-bug pitivi
```

---

