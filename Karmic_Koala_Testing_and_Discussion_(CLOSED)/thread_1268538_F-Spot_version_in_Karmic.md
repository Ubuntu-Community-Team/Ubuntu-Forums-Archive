---
title: "F-Spot version in Karmic?"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MadsRH on 2009-09-17
Hi
Can anyone tell me which version of F-Spot is in Karmic?

I know that we're past feature freeze and so this question might be kind of obsolete, but is there any chance of getting the newly released F-Spot 0.6.1.2 in Karmic?

It fixes db upgrade for the people who went in holidays in the far future. Now F-Spot can update a db with photos taken (or reported to be) after 2038. It also fixes a crash while running on gtk+ 2.14.

The LiveWebGallery extension is now merged into the main tree, and installable, from the Manage Extension dialog, on any F-spot > 0.6. The extension crashing on gtk+2.14 is part of the past too.

More info here: [http://blog.reblochon.org/2009/09/news-from-f-spotters.html](http://blog.reblochon.org/2009/09/news-from-f-spotters.html)

---

### Post by 23meg on 2009-09-17
> **MadsRH]Can anyone tell me which version of F-Spot is in Karmic?[/QUOTE]

[packages.ubuntu.com]("http://packages.ubuntu.com") always can  said:**
> I know that we're past feature freeze and so this question might be kind of obsolete, but is there any chance of getting the newly released F-Spot 0.6.1.2 in Karmic?


[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess) has information regarding this.

---

### Post by gnomeuser on 2009-09-17
I suspect we will need to request a freeze exception for f-spot.

Latest one to hit the buildsystem is 6.1
[https://lists.ubuntu.com/archives/karmic-changes/2009-September/007873.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/007873.html)

---

### Post by MadsRH on 2009-09-17
If someone has time to do the upload, I'm sure nobody can argue against a bug fix update. The only issue I see is that because a new feature is introduced the documentation and translation teams might need to be notified. And of course the size of the package might have increased.

So, from looking at the [FreezeExceptionProcess wiki]("https://wiki.ubuntu.com/FreezeExceptionProcess"), it looks like I should file a bug? :confused:
My first thought was to post a message on the ubuntu-desktop mailinglist, cuz maybe the update is already planed.

---

