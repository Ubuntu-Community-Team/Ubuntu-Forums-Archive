---
title: "Compiz Issues"
date: 2008-07-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-01
Seems that Compiz doesnt play nice with other 3d processes. I was "testing" warzone 2100 (as any Ubunteroo does on an alpha!) and I found that the game flickered in and out on occasion amongst other unpleasantness. A major annoyance was having expo trigger from its defined screen hotspot.

Fix: turn off compiz

Real fix: Shouldnt fullscreen 3d apps kinda have their own "mode" where Compiz doesnt compete for the show?

I know that trying to get standards into Linux is "like hearding cats" but atleast the idea is there.

What else? Not sure if it should be bugged - maybe its more of a blueprint for the future?

---

### Post by psyke83 on 2008-07-01
> **Nullack said:**
> Seems that Compiz doesnt play nice with other 3d processes. I was "testing" warzone 2100 (as any Ubunteroo does on an alpha!) and I found that the game flickered in and out on occasion amongst other unpleasantness. A major annoyance was having expo trigger from its defined screen hotspot.

Fix: turn off compiz

Real fix: Shouldnt fullscreen 3d apps kinda have their own "mode" where Compiz doesnt compete for the show?

I know that trying to get standards into Linux is "like hearding cats" but atleast the idea is there.

What else? Not sure if it should be bugged - maybe its more of a blueprint for the future?

That problem has existed for a long time, and I believe it's a flaw in DRI. I think DRI2 (in whatever form it eventually takes) will fix this problem - unfortunately I doubt it will be ready for Intrepid. There's no need to file any blueprints etc, because this work is being done upstream (in Xorg/Mesa), not Ubuntu.

---

### Post by Nullack on 2008-07-02
Thanks. Theres another annoyance - I use compiz settings manager for custom compiz and having turned it off in appearances is there an easy way to re-enable it given that I dont want any of the default settings?

---

### Post by plun on 2008-07-02
Use fusion-icon

[http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)


If you have ccsm installed you also have a entry for that


3D apps such as gaming is a upstream challenge to solve.


For unknown reasons Ubuntu doesn't include fusion-icon as default,  unclear answer from Mr Vogt about this before Gutys release.

---

