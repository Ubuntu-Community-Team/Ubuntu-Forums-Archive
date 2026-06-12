---
title: "Ctrl-C not working in Jaunty"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Beau on 2009-03-14
Hi,

I'm running Jaunty (kubuntu) because the bluetooth stack in Intrepid didn't work with my BT-keyboard. 

Most things seem to run fine but ctrl-c doesn't kill an app in the terminal any more which is very annoying. Does anybody got the same problem or now how to reactivate it?

I got a few other problems like my hostname not getting set and the dhcp client not running but I'll search the forums first for those problem. 

Cheers,
Beau

---

### Post by kestrel1 on 2009-03-14
Jaunty is still in Alpha form, so there could be problems. You could also try logging a bug report if you feel this is a bug.

---

### Post by JochenJung on 2009-04-16
Got the same issue here in Ubuntu Jaunty Beta :-(

In the last releases Ctrl+C was used for copy when text was marked only.
Now it seems to be used for coping no matter a text is selected or not.

So I got no chance to cancel commands.

---

### Post by gali98 on 2009-04-16
Um.... It's working quite well for me.. 
Try this:
When you are in the terminal with out anything running, press ctrl + C.
It should start another line.
(i.e. maybe your keyboard is not working right?)
Kory

---

### Post by JochenJung on 2009-04-16
> **gali98 said:**
> When you are in the terminal with out anything running, press ctrl + C.
It should start another line.

No, it dosn't :-(

> **gali98 said:**
> (i.e. maybe your keyboard is not working right?)

Don't think so, for I can use Ctrl+C to copy text.
And just before the update, Ctrl+C was working for abort also.

---

### Post by gali98 on 2009-04-16
Are you on one of the ttys? (Like ctrl+alt+F?) or in the gnome-terminal?
The terminal may not be interpreting the keyboard right...
Have you updated today?
Kory

---

### Post by JochenJung on 2009-04-17
I'm in gnomes terminal. The one at Applications - Accessories - Terminal
Ctrl+Alt+F1, F2, ...  only gives me blank screens (but I think thats another issue), so I cannot test this.
I updated two days ago.

Is there a config file, where such keyboard shortcuts are handled? In the menu there is an option called keyboard shortcuts, but none of them seams to be the appropriate for me.

---

### Post by JochenJung on 2009-04-17
I just found a solution.
I gnome terminal there is edit - keyboard shortcuts.
If I assign annother Key combo for coping there (i.e. Ctrl+F) Ctrl+C words again for abort.

Though I liked the old behavior, where Ctrl+C was for copy, when text was selected and for abort, if none was selected.

---

### Post by gali98 on 2009-04-17
The default in gnome-terminal for copy was never Ctrl+C.
It is Ctrl+Shift+C....
Kory

---

