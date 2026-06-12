---
title: "Shutdown Question"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vgrisham on 2008-10-03
Hi,

I've just upgraded and so far, I love Intrepid! I used the alternate cd to upgrade. I fully expected to have to do a clean install, but it worked great. It's nice to not to have to spend days on end reinstalling applications. 

The question that I have relates to the shutdown button on the system menu. What is the actual command that this button invokes? I use Avant Window Navigator and the shutdown applet issues the command "gnome-session-save --kill" which only allows one to signout or switch users. The AWN quit applet allows one to edit the quit command however, so if I can figure out with Itrepid's shutdown / restart command is, I can correct it in the AWN shutdown applet. 

Thanks in advance. 

Vaughn

---

### Post by vgrisham on 2008-10-17
I hate to do this, but you've left me no choice.

Bump.

The newly separated Shut Down and Log Out routines are putting a couple of cramps in my style.

First, the shutdown button on my keyboard now pulls up the log out / switch user dialogue. The same is true with Avant Window Navigator's quit button. 

However, it will be easy to customize these two buttons actions if I simply could find out what the command would be from the terminal to execute the shut down / restart procedure. 

Any takers?

---

### Post by mc4100 on 2008-10-17
What about, for shutting down:
```
/sbin/shutdown -h now
```
And for rebooting:
```
/sbin/shutdown -r now
```
Does this work?

Edit: Also, if you want the **shutdown menu** to appear, use this:
```
gnome-session-save --shutdown-dialog
```

---

### Post by Foaming Draught on 2008-10-18
I was as perplexed as you, vgrisham, when shutdown disappeared from the main menu and buttons.  I assumed that it was a bug which would be fixed many months ago, but it seems to be a feature which we're stuck with.

All is not lost, at least if you've still got a Gnome panel.  "Add to panel" right click includes a Shutdown button.  I've added it back to the right of my clock at the top right of my panel.

---

### Post by mariner09 on 2008-10-18
That's interesting..

I have the shutdown button on my std main menu, however, I do like to use gnome-main-menu and shutdown has disappeared from there.  I tried to modify the systems.xbel file to invoke the gnome-session-save --shutdown-dialog, but it's not working.

Any ideas there?

---

### Post by vgrisham on 2008-10-18
> **mc4100 said:**
> 

Edit: Also, if you want the **shutdown menu** to appear, use this:
```
gnome-session-save --shutdown-dialog
```

That last one does it! Thanks. For those of you using Avant Window Navigator, right click the quit button. Choose preferences and replace the word kill with the words shutdown-dialog (leave the two leading dashes alone).

Thanks mc4100!

---

### Post by kaibob on 2008-10-29
> **mc4100 said:**
> ...Edit: Also, if you want the **shutdown menu** to appear, use this:
```
gnome-session-save --shutdown-dialog
```

Thanks! The separate dialogs in Intrepid has been a problem for me and this command gets me where I want to be.

---

