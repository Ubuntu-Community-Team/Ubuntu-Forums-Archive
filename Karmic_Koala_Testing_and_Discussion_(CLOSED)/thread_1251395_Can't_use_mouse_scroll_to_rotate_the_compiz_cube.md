---
title: "Can't use mouse scroll to rotate the compiz cube"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by medeshago on 2009-08-27
It was working fine until I upgraded to Karmic. Now I can't scroll to move the cube and if I try to put the default buttons in ccsm it goes back to "Disabled" as the video shows:
[http://www.youtube.com/watch?v=82jNdFrOfIE]("http://www.youtube.com/watch?v=82jNdFrOfIE")

---

### Post by overdrank on 2009-08-27
Moved to Karmic Koala Testing and Discussion

---

### Post by habtool on 2009-08-27
refer to:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/414170](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/414170)

Use gconf editor to modify (dont use ccsm for now)

/apps/compiz/plugins/vpswitch/allscreens/options/next_button Button5

/apps/compiz/plugins/vpswitch/allscreens/options/prev_button Button4

Hope this helps

---

### Post by eluminx on 2009-09-22
@habtool that didn't work is there any other options to try?  Thanks for the help.

---

### Post by Longinus00 on 2009-09-22
Install the compiz config settings manager and then set the keybindings via the "rotate cube" plugin.

---

### Post by habtool on 2009-09-22
> **eluminx said:**
> @habtool that didn't work is there any other options to try?  Thanks for the help.

Sorry eluminx, thats how I got it to work for my setup.
Not sure what else you can do if the above did not work.

---

### Post by eluminx on 2009-09-22
> **Longinus00 said:**
> Install the compiz config settings manager and then set the keybindings via the "rotate cube" plugin.

Well apparently using the viewport switcher ui worked instead of doing it through the gconf-editor.  Thanks for Longinuss and habtool.

---

### Post by michaelPendleton on 2009-09-22
I know this is in the wrong place. I am new so I don't even know how to post. I just happened on this reply option. I just installed Ubuntu and need help installing a canon pixma ip1800. I am used to W*****s so all this is very new to me

---

### Post by Longinus00 on 2009-09-22
> **michaelPendleton said:**
> I know this is in the wrong place. I am new so I don't even know how to post. I just happened on this reply option. I just installed Ubuntu and need help installing a canon pixma ip1800. I am used to W*****s so all this is very new to me

Try posting in here.
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by dn* on 2009-10-17
Worked for me, thanks!

---

### Post by tnolen on 2009-10-23
> **habtool said:**
> refer to:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/414170](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/414170)

Use gconf editor to modify (dont use ccsm for now)

/apps/compiz/plugins/vpswitch/allscreens/options/next_button Button5

/apps/compiz/plugins/vpswitch/allscreens/options/prev_button Button4

Hope this helps



This worked for me. I believe this is a regression, but I'm not sure it is the same bug as they are talking about in 414170.  This is still happening as of RC.

---

