---
title: "Flickering system tray in Natty"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by tarahmarie on 2011-05-03
I've looked for this issue, but don't see it.

I just did a fresh install of Natty. My systray is flickering, the information widget moves around unless I hover over the systray, My icons aren't showing up.

Anyone know?

---

### Post by frankvdh on 2011-05-03
Not sure if it's the same issue as yours, but I've had big problems with the display in 11.04.

People who don't want the whole gory history can skip to the last paragraph...

I online upgraded to 11.4 from 10.10, and things became painful!

There was a tremendous amount of flickering of the screen when starting  apps, like the system was frantically refreshing both the app that should  be visible, and then visibly redrawing all the windows that should be  invisible behind it, and then redrawing the app that should be in the  foreground. This also applies to opening menus.

It also appeared to me that there was some confusion in Linux over which  Workspace background was currently being displayed the physical screen...

Switching from one workspace to another, it appeared that the screen  continued to display Workspace 1's screen (including the background,  windows, icons, menu bar, and the Workspace-selector icon on it, etc).  At this stage, clicking on a visible 'icon' had weird effects, because  the action of the corresponding point on the invisible Workspace is  performed. Moving the mouse over icons on the invisible Workspace  refreshed icons from the invisible Workspace onto the screen. Moving  icons or other objects (once they're visible) on the screen refreshed  the background from the invisible Workspace 2 onto the screen.

 Once an app is running fullscreen, and the whole system knows its there,  things seem to stabilise and there's no more flickering.

 My screensaver also seemed to be involved in  this... once it was activated, it was hard to get the screen redrawn  properly.

Starting a 'Previous Linux Version' from grub still ran 11.04, with the same outcome. [IMG]http://static.linuxquestions.org/questions/images/smilies/frown.gif[/IMG]

I then downloaded the natty-dvd-i386.iso and did a clean install of 11.04 from the DVD, and still had the same issue [IMG]http://static.linuxquestions.org/questions/images/smilies/frown.gif[/IMG]

After lots of experimentation, I found that...

[SIZE=4]_**Long story short...**_[/SIZE]
...choosing the "Ubuntu  Classic (_**No Effects**_)" option on the login screen fixes most of the problems. There are still a couple of artefacts on the panel, but at least  the system is now usable. [IMG]http://static.linuxquestions.org/questions/images/smilies/smile.gif[/IMG]

Hope this helps someone.

---

### Post by tarahmarie on 2011-05-05
No, it's not the same issue, unfortunately.

Is there any reason why this keeps happening? Or why my KeepassX and VLC icons appear overlaid in a small box at the top left hand corner of my desktop instead of in my System Tray? Or why my Dropbox icon lives in a small window now instead of my System Tray?

WTF?

---

### Post by tarahmarie on 2011-05-09
bump

---

### Post by Visual Echo on 2011-05-09
I'm also seeing this in Kubuntu (changed over from regular Ubuntu).  Other windows become useless as applications (pidgin, fusion-icon) which try to put an icon in the system tray steal focus constantly, flickering and trying really really hard to put the icon in there.  I've solved it temporarily by removing the systray from the panel.  I had hoped it was just normal problems as a result of upgrading from 10.10 to 11.04, but a fresh install does the same thing.  Very disappointed, doesn't anybody run compiz desktop cube?

---

### Post by tarahmarie on 2011-05-09
> **Visual Echo said:**
> I'm also seeing this in Kubuntu (changed over from regular Ubuntu).  Other windows become useless as applications (pidgin, fusion-icon) which try to put an icon in the system tray steal focus constantly, flickering and trying really really hard to put the icon in there.  I've solved it temporarily by removing the systray from the panel.  I had hoped it was just normal problems as a result of upgrading from 10.10 to 11.04, but a fresh install does the same thing.  Very disappointed, doesn't anybody run compiz desktop cube?

Yes, this is the exact same problem I'm experiencing, and I did the same (remove systray), but it's very annoying, as I have set up a great deal of my workflow in the system tray (dropbox, vuze, vlc, amarok, etc), and not having those icons there is quite annoying. Is this a bug or simply a setting you and I haven't configured yet?

Notably, compiz-fusion isn't working for me right now.

---

