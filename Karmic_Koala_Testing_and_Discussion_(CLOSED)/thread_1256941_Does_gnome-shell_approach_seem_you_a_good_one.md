---
title: "Does gnome-shell approach seem you a good one?"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Joe_Bishop on 2009-09-03
I just wondering how they managed to arrive to such an idea. This approach seems to me inconvenient at all - too many clicks even for basic operations. In addition, I hate massive redrawing for simple operations like opening point from Places, it's hard to eye.
It's technical implementation isn't good too:
1) Windows redrawing, is the pain in the X architecture. Now with mutter it's much slower than with metacity/compiz/etc.
2) Moving windows: window lags behind mouse pointer when moving.
3) General slowness. They say javascript is fast enough, my user expirience tells it isn't. For example, opening application menu takes ages. They use mozilla's tracemonkey javascript engine, which isn't optimized for x86_64 proccessors.

---

### Post by gnomeuser on 2009-09-03
I have objections to the general approach. 

1) Workspaces are a solution looking for a problem
2) A further move away from task oriented towards application oriented problem solving.

1 is a problem because the data simply doesn't support that workspaces is the solution because the problem is ill defined. Supposedly we are aiming to handle the clutter of having multiple open windows and not lose track of information, for which it is assumed that workspaces is the only suitable solution and that it doesn't have downside. E.g. the new Windows 7 taskbar is a solution for the same problem space without using workspaces.

2 is a problem because it assumes the user would rather use applications than have a streamlined approach to task resolution. Neither solution can fully accomplice it's goal for all tasks, take the web browser e.g. it's currently an application but it's a window to a number of applications and tasks such as email so it clashes with a task oriented approach. It fits poorly into a task oriented approach this doesn't however mean the task oriented approach isn't good. More research should probably be done before declaring application centric workflows the one true solution.

Additionally I have problems with the choice of Javascript, it's an entirely new language for the platform, it relies on introspection which is also a new component of our platform. It's slow, it's insecure by design and worst of all while there is a standard everyone seems to ignore it with their own extensions. This is the cause of the gnome-shell now being tied to the mozilla javascript engine instead of allowing distributions to pick their own, e.g. some cases might benefit from using V8 or the WebKit engine (whose name I sadly forgot).

The final problem I have with the gnome-shell is the means by which it is included into the GNOME desktop. Every other component goes through extensive reviews and debates in the community, problems can be highlighted. This is the reason why WebKit e.g. has been disallowed as a dependency since the accessibility people have continued to voice concerns and unwillingness to accept temporary regressions (despite extensive progress in the area). Gnome-shell however has never been debated for inclusion on the mailing list, it sails right in along with it's list of dependencies basically defining a whole new GNOME out of the minds of a few developers who seeming are "above the law", debated chiefly at a conference where only a very minor subset of the community was able to attend.

I really don't like any part of the gnome-shell, it's bad on technical, design, performance and community grounds.

---

### Post by simius on 2009-09-03
> **Joe_Bishop said:**
> It's technical implementation isn't good too:
1) Windows redrawing, is the pain in the X architecture. Now with mutter it's much slower than with metacity/compiz/etc.
2) Moving windows: window lags behind mouse pointer when moving.
3) General slowness. They say javascript is fast enough, my user expirience tells it isn't. For example, opening application menu takes ages. They use mozilla's tracemonkey javascript engine, which isn't optimized for x86_64 proccessors.
I think there are some changes planned to make window redrawing faster. There shouldn't be any reasons for it to be slower than using Compiz. Many operations can be optimized, and some problems are specific to graphics card drivers that will soon be improved. (Intel has had large improvements over the last year, and the open source drivers for nVidia and Ati seem to be improving.)

As far as I know, JavaScript is not a bottleneck here. The slowness of the Activities overview for example is partly due to slow (re)loading of icons, which is implemented in C code.

> **gnomeuser said:**
> 1) Workspaces are a solution looking for a problem
Re-posting my [comment]("http://ubuntuforums.org/showpost.php?p=7881477&postcount=349") from the main GNOME Shell thread:

The new shell is probably even less focused on using multiple workspaces than GNOME 2. The feature is more or less hidden, initially only displaying a (+) button in a corner of the screen, while GNOME 2 creates two or four workspaces by default and shows a confusing switcher in the panel. The shell and its Activities overview really shine when you use only one workspace.

I think workspaces are mainly added for edge cases and for not decreasing functionality for users who actually work more efficiently with them.

> **gnomeuser said:**
> 2) A further move away from task oriented towards application oriented problem solving.

[...]

2 is a problem because it assumes the user would rather use applications than have a streamlined approach to task resolution. Neither solution can fully accomplice it's goal for all tasks, take the web browser e.g. it's currently an application but it's a window to a number of applications and tasks such as email so it clashes with a task oriented approach. It fits poorly into a task oriented approach this doesn't however mean the task oriented approach isn't good. More research should probably be done before declaring application centric workflows the one true solution.
A lot of research has been done in this area. It seems the designers have studied a lot of relevant articles and books, as listed in [Design References]("http://live.gnome.org/GnomeShell/Design/References").

GNOME Shell is in good company with the choice for ‘app-centric’: Windows 7 and the Mac OS X Dock seem to have similar behavior. (Read [Pay no attention to the processes and X Windows behind the curtain]("http://cgwalters.livejournal.com/25818.html") for a detailed description of how the new app launching works.)

It also presents a very clear and well-known model to the user: when you want to do something, use an app. I think a good task-oriented solution would provide a very different model (probably like [Mozilla Ubiquity]("http://ubiquity.mozilla.com/")’s), and require a lot of redesigning and rewriting in the whole GNOME platform. Without having proof that it actually works better.

---

### Post by Merk42 on 2009-09-03
Shouldn't this be merged with the existing GNOME Shell thread?

---

