---
title: "Indicator Applet position problems?"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-04-04
Hello,
Recently I've noticed that I can't move the Indicator Applet where I want it to be (which is next to the notification applet) instead I can only drag it so far, leaving a gap between the two. I have all my applets unlocked to see if I could fiddle with it a bit more but no, it won't let me. What is it with my life?

Here is a screenshot:
[img]http://localhostr.com/files/6589e6/Screenshot.png[/img]

Is anyone else having these types of problems?

Lee

---

### Post by rburkartjo on 2009-04-04
lee i have the same problem

---

### Post by chrisccoulson on 2009-04-04
It's likely that there is some other applet in the way that isn't showing anything on the panel. Please run "gconftool-2 -R /apps/panel" and attach the output as a text file.

---

### Post by Polygon on 2009-04-04
no, it does that on a fresh install. I get the same thing, except the indicator applet annoyed me because it doesn't seem to do anything so i just removed it.

---

### Post by chrisccoulson on 2009-04-04
I can't recreate it. Fresh install or not, if you don't post more information (such as the panel config I suggested), then it's difficult for anyone to help.

---

### Post by go7Ul1ai on 2009-04-04
I would have got the information out to you earlier but I have higher priorities right now, if you are a bit more patient with people then you may also get better responses.

Anyway, the information you requested is attached as "panelinfo.txt".

Lee

---

### Post by Polygon on 2009-04-04
reproduced it, but my screenshots got lost becuase of an other jaunty bug which locks up my computer and causes data loss.

ill try to get it next time

---

### Post by go7Ul1ai on 2009-04-05
Every time I start up my computer, the Indicator Applet moves further and further away and I can't move it any closer to where it was before, this is a really strange bug. I think it's similar to the bug I've noticed with Banshee (that's been happening for months) where the columns move further apart every time I open it.

---

### Post by Polygon on 2009-04-05
its really hard to move if you have no programs that use indicators. to move it more easily, start up pidgin, then the thin line becomes an icon and then you can right click > move it back

but yeah , it seems after every reboot it moves farther away.

---

### Post by phenest on 2009-04-05
Or perhaps it's not a gap between it and the next applet, but rather it is the size (width) of the applet that is growing. To a developer, they are different, but to you still a bug.

---

### Post by Polygon on 2009-04-05
no, because when you first start up your computer, and have no apps with indidcators, the applet is just a thin vertical line. 

You cannot MOVE this applet unless you manage to right click the thin little line....so if the applet itself was expanding, then you should be able to right click it easier. 

Also, when the applet actually does something (like you start an app with an indicator), you can move it back to where it is supposed to go, so therefore the applet is moving, not expanding

and has anyone reported a bug on this yet?

---

### Post by chrisccoulson on 2009-04-05
> **lee.jarratt said:**
> I would have got the information out to you earlier but I have higher priorities right now, if you are a bit more patient with people then you may also get better responses.

Anyway, the information you requested is attached as "panelinfo.txt".

Lee

The data is not complete, so is not much use.

---

### Post by go7Ul1ai on 2009-04-05
> **chrisccoulson said:**
> The data is not complete, so is not much use.

Well I can't get the terminal to display all of it for some reason, I scroll all the way up and select it all then I copy it and paste it into a text file, It won't let me display any more :S

---

### Post by Polygon on 2009-04-05
the command chriscoulson provided you should of have been this

gconftool-2 -R /apps/panel > panelinfo.txt

then there will be a panelinfo.txt with the complete output in your home folder (or wherever directory your terminal is currently in)

---

### Post by go7Ul1ai on 2009-04-06
> **Polygon said:**
> the command chriscoulson provided you should of have been this

gconftool-2 -R /apps/panel > panelinfo.txt

then there will be a panelinfo.txt with the complete output in your home folder (or wherever directory your terminal is currently in)

Thanks man :)

---

### Post by chrisccoulson on 2009-04-06
> **lee.jarratt said:**
> Thanks man :)

In between the indicator applet that isn't locked and the notification area, you have a further 6 locked indicator applets on the panel (which is why you see the behaviour you describe).

The best thing to do is to just nuke your existing panel config and start again:

```
gconftool-2 --recursive-unset /apps/panel
```

This will restore the panel to the original configuration

---

### Post by go7Ul1ai on 2009-04-06
Thanks man, that solved it.. but it's still a bug though because other people are having this problem? I mean I don't remember adding the applet 6 times?

Lee

---

### Post by Polygon on 2009-04-06
> **chrisccoulson said:**
> In between the indicator applet that isn't locked and the notification area, you have a further 6 locked indicator applets on the panel (which is why you see the behaviour you describe).

The best thing to do is to just nuke your existing panel config and start again:

```
gconftool-2 --recursive-unset /apps/panel
```

This will restore the panel to the original configuration

i can guarantee you that i have not added any more instances of indicator-applet since i installed jaunty, so there IS a bug where indicator-applet is cloning itself or something.

---

