---
title: "Awesome Sauce!"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Insane_Homer on 2010-04-24
WOW! another fantastic job Ubuntu Team.

Performed an upgrade on 9.10 to 10.04 RC this morning. All went very smoothly. No problems to report as yet.

1st impressions are great so far. very slick and fast (has it ever been any other way).

Best noticeable improvement so far, Bootchart reports boot time has gone from ~1min 22sec in 9.10 to ~45 seconds in 10.04.

=D>

---

### Post by andrewabc on 2010-04-24
> **Insane_Homer said:**
> Best noticeable improvement so far, Bootchart reports boot time has gone from ~1min 22sec in 9.10 to ~45 seconds in 10.04.

=D>

That is because in 9.10 bootchart added an extra 45 seconds by default (you could usually see firefox/apps open in bootchart).
So it looks like boottime improved a little bit for you.

If you have both 9.10 and 10.04 bootcharts available you could put them on imageshack and put in the bootchart thread in this forum (check back a page or two and thread should be there). Then we can compare them. :)

---

### Post by Vishal Agarwal on 2010-04-24
What is Bootchart ? where I can found it ?

---

### Post by andrewabc on 2010-04-24
> **Vishal Agarwal said:**
> What is Bootchart ? where I can found it ?

[http://ubuntuforums.org/showthread.php?t=1343305](http://ubuntuforums.org/showthread.php?t=1343305)
Has some info.

---

### Post by lavinog on 2010-04-24
> **andrewabc said:**
> That is because in 9.10 bootchart added an extra 45 seconds by default (you could usually see firefox/apps open in bootchart).

I thought it was the other way around.  Bootchart ends when the desktop is displayed in 10.04, and ends when gdm is loaded with 9.10

---

### Post by andrewabc on 2010-04-24
> **lavinog said:**
> I thought it was the other way around.  Bootchart ends when the desktop is displayed in 10.04, and ends when gdm is loaded with 9.10

Maybe they did fix it (doesn't look like it for 9.10 changelog for bootchart).

I definitely remember in 9.10 that there was a 45 second delay. I remember looking at my bootchart and since I have an SSD it was timed at 50 seconds even though I had firefox running at 10 second mark. (removed the delay and bootchart was 10 seconds).

There was a big discussion about it, and they've basically changed how bootchart times between 9.04/9.10/10.04. Each version had different stop time. I'm pretty sure in 9.10 (maybe they fixed it after 9.10 release), it had 45 second delay.

[url=http://ubuntuforums.org/showthread.php?t=531453&page=63]Attach your boot-chart!
[/url]
Check out my post with my two bootcharts. You can't make them out because of newer forum restrictions, but looking at them you can tell 9.10 was adding 45 seconds to bootchart.

[Surprise of today's upgrade](http://ubuntuforums.org/showthread.php?t=1304952&page=5)
Another thread where 45 second delay in 9.10 was documented by me.

[Post your Karmic bootcharts or boot times!](http://ubuntuforums.org/showthread.php?t=1229111&page=11)
Where it was originally documented that bootchart was adding 45 second delay and how to get rid of it.

45 second delay is not happening in 10.04, but from what I remember reading it is using another stop point different from 9.04/9.10, so comparing bootcharts between different ubuntu versions has become kinda pointless.

According to [changelog](http://changelogs.ubuntu.com/changelogs/pool/main/b/bootchart/bootchart_0.90.2-7/changelog) for 10.04
> Crop the chart down to the first idle period after gnome-panel has started.  LP: #438015.

---

