---
title: "after ubuntu 10.04 install bottom gnome panel (task-bar) does not work"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by zappal on 2010-04-30
Hi ya'll,

This is strange a fresh install of 10.04 Lynx when i first logged in everything was cool, then i right clicked on the 4 desktop switching boxes on the bottom right corner; then the bar blipped off.

Now after i re-login the bar is at the bottom but does nothing. When i open windows or anything they are not showing up, the only way I can navigate through my windows if Alt+Tab

Any idea how I can get it back to default?

---

### Post by zappal on 2010-04-30
I figured i should add info about this.
When i right clicked the desktop switcher boxes and selected edit
then it crashed
then i got two pop up messages asking if i want to restore them
I'm wishing I clicked yes.
This is the only thing stopping me from enjoying my new Lynx experience this evening.

---

### Post by zappal on 2010-04-30
Notice how I have 3 apps running, but none appear in the bottom taskbar panel
I was using ALT+Tab to cycle thru
[IMG]http://bayimg.com/image/bambkaace.jpg[/IMG]
[IMG]http://bayimg.com/BAmbkAACE[/IMG]

---

### Post by akand074 on 2010-04-30
Why not delete it (right click and delete panel)? Then go to the top panel, right click and choose "new panel" now you have a brand new panel. Also the window list could have been deleted. Write click and choose "add to panel" and choose "Window List" from the list on either panel and it will show up. Weird issue, never had it. Good luck!

---

### Post by zappal on 2010-04-30
Hymm, thanks, I kinda got it. But it not exactly the way it originally was
I remember seeing some commands that will reset gnome panels to default but I can't seem to find them now.
It was around 2 or 3 commands followed by a kill command
[IMG]http://bayimg.com/image/camblaace.jpg[/IMG]

---

### Post by akand074 on 2010-04-30
Well you can drag and move those to wherever you want. I completely change my panels as soon as I install Ubuntu to how I prefer them. I don't know how to reset them off hand but yeah if you remember what it looked like just drag the desktop switcher to the right hand and the window list to the left hand side (might have to right click on the item and uncheck "Lock" to let it move. But Yeah If I were you I'd customize it to however works best for you.

---

### Post by zappal on 2010-04-30
I searched and found an old post about this
it was kinda a crude way. I think it for an old gnome
the 1st command generated errors, but now everything is back to normal after i relogin

gnome-session remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

Thanks for your input akand. ill get around to customization later. I still would like to see the clean commands with the final kill command. If i find it I'll edit this post.

---

### Post by martintremblay on 2010-05-11
Try this - Its a script bithacker wrote that resets all panels/bars back to default.
 - It was easy and worked perfect for me!

[http://bithacker.posterous.com/restore-the-default-gnome-panels-in-ubuntu-10](http://bithacker.posterous.com/restore-the-default-gnome-panels-in-ubuntu-10)

---

### Post by Zunair on 2010-06-29
thanks for the info brother helped me

---

### Post by cash1981 on 2010-06-29
Thanks. This helped me too.

---

