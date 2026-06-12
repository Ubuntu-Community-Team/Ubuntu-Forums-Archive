---
title: "Volume Applet?"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by labaom on 2010-03-12
Hello,

Ever since upgrading to 10.04, my volume applet is missing. I already tried removing and reinstalling the notifications area. Only for my battery and wifi to show. I can still control volume with my keyboard but I would like to be able to have a visual on top. On a side note, my battery keeps disappearing one in awhile even though I put it to always display icon.

Thanks

---

### Post by castrojo on 2010-03-12
Do you have indicator-sound installed?

---

### Post by labaom on 2010-03-12
> **whiprush said:**
> Do you have indicator-sound installed?

I don't see an option for that in add to panel?

---

### Post by svaens on 2010-03-12
I also have this problem. 
Volume applet was there before, .... certainly with the live CD, but on install and update ... it is gone! 

I do have sound though...

EDIT!
AHHHHHhhhggrrr.. . I worked it out. 
I did have it of course, until I did the update of the packages.... at which time my system broke (see my other thread: [http://ubuntuforums.org/showthread.php?t=1428371](http://ubuntuforums.org/showthread.php?t=1428371)) which broke several things to do with the ubuntu theme.. 
as my adium-theme-ubuntu won't install. I guess if i change themes it will fix the volume applet problem? I'll try it.

---

### Post by castrojo on 2010-03-12
It won't be seperate, it would show up in "indicator applet", which is in the add to panel menu.

---

### Post by labaom on 2010-03-12
> **whiprush said:**
> It won't be seperate, it would show up in "indicator applet", which is in the add to panel menu.

Well I got it to work now. But it just seems extremely weird having wifi separate from the rest. Anyway to get rid of the microblogging mail part of the applet removed?

---

### Post by knarf on 2010-03-12
If you - like me - are not to keen on the indicator applet with its useless but space-consuming blogging nonsense you can add the original gnome-volume-control-applet to the panel by adding it to your session.


[LIST]
[*]Start gnome-session-properties
[*]click '_A_dd'
[*]enter a _N_ame and Comm_e_nt which have some meaning for you
[*]enter 'gnome-volume-control-applet' in the 'Co_m_mand' field
[*]click _S_ave
[/LIST]
Done. The volume control applet will start automatically the next time you start your session (by logging in).

---

### Post by castrojo on 2010-03-12
> **labaom said:**
> Well I got it to work now. But it just seems extremely weird having wifi separate from the rest. Anyway to get rid of the microblogging mail part of the applet removed?

The text field won't show up unless you set up a microblogging account but I don't think that fix has landed yet.

The network applet (like Tomboy) will not be ported due to all the fancy UI bits it's currently using.

---

### Post by mdurham on 2010-03-12
> **knarf said:**
> If you - like me - are not to keen on the indicator applet with its useless but space-consuming blogging nonsense you can add the original gnome-volume-control-applet to the panel by adding it to your session.


[LIST]
[*]Start gnome-session-properties
[*]click '_A_dd'
[*]enter a _N_ame and Comm_e_nt which have some meaning for you
[*]enter 'gnome-volume-control-applet' in the 'Co_m_mand' field
[*]click _S_ave
[/LIST]
Done. The volume control applet will start automatically the next time you start your session (by logging in).
Thanks knarf, that's a great tip, it's how it should be.

---

### Post by tekstr1der on 2010-03-12
> **labaom said:**
> Anyway to get rid of the microblogging mail part of the applet removed?

Yes. Just remove indicator-messages package.

```

sudo aptitude remove indicator-messages
```

---

### Post by seeker5528 on 2010-03-12
Looks like no indicator applet for me.

A: I am not willing to install a bunch of pulse audio stuff just to get this appindicator volume thingy to work. On it's own not a big deal for me personally, but that leads to.....

B: If I have the indicator applet loaded in the panel and I have gone to 'preferences --> startup applications' and added kmix with the command '/usr/bin/kmix --keepvisibility', the indicator application seems to kill all the useful functionality of kmix. If I remove the indicator applet, log out, log in, then kmix works, assuming the notification applet is running in the panel. If I left click the volume icon I get the full mixer window and if I right click then choose 'show mixer window' I get the volume slider, but that's another story and I can live with that. 

While I am completely comfortable using kmix in Gnome, it probably won't be acceptable to some who are anal about not running any KDE/QT stuff in their Gnome environment.

Later, Seeker

---

### Post by labaom on 2010-03-12
> **tekstr1der said:**
> Yes. Just remove indicator-messages package.

```

sudo aptitude remove indicator-messages
```

I tried that. Instead it ruined my indicator session applet as it would not respond. I removed it and tried putting it back on the taskbar but its not listed anymore. Can you please help me get it back?

---

### Post by castrojo on 2010-03-12
> **seeker5528 said:**
> While I am completely comfortable using kmix in Gnome, it probably won't be acceptable to some who are anal about not running any KDE/QT stuff in their Gnome environment.

Can you please post screenshots of your problem? I am having a hard time understanding what the problem is. At the core level App indicators are just KDE's KStatusNotifierIcon ported to GNOME so a KDE app should be "Just working" in that environment.

---

### Post by seeker5528 on 2010-03-13
> **whiprush said:**
> At the core level App indicators are just KDE's KStatusNotifierIcon ported to GNOME so a KDE app should be "Just working" in that environment.

With the indicator applet a left click on the volume icon gives me this:

[img]http://home.comcast.net/~seeker5528/Screenshot-kmix-indicator.png[/img]

I can select the master channel and I am assuming that mute works, but no slider and the option to run kmix is greyed out.

If I right click it shows me stuff related to the indicator applet instead of stuff related to kmix.

For comparison, without the indicator applet, left clicking the volume icon in the notification area gives me the mixer and a right click gives me this:

[img]http://home.comcast.net/~seeker5528/Screenshot-kmix-notification.png[/img]

I have not logged into a KDE session for a while, so I don't know how this stuff is working there, but I can see some potential that maybe this is related somehow to the behavior in the notification case that a left click brings up the full mixer and right clicking then choosing to show the mixer brings up a single slider for the master volume, the older I get the more I swear I must be dyslexic but any way you look at it this seems backwards to me. 

EDIT:

OK, I logged into a KDE session and if I left click the volume icon I get a single slider for the master volume and if I right click then choose to open the mixer I also get the single slider for the master volume, so for some reason kmix is behaving differently in Gnome than in KDE when you left click.

Later, Seeker

---

### Post by ffi on 2010-04-06
> **knarf said:**
> If you - like me - are not to keen on the indicator applet with its useless but space-consuming blogging nonsense you can add the original gnome-volume-control-applet to the panel by adding it to your session.


[LIST]
[*]Start gnome-session-properties
[*]click '_A_dd'
[*]enter a _N_ame and Comm_e_nt which have some meaning for you
[*]enter 'gnome-volume-control-applet' in the 'Co_m_mand' field
[*]click _S_ave
[/LIST]
Done. The volume control applet will start automatically the next time you start your session (by logging in).

thanks

---

