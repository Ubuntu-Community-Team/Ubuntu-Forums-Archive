---
title: "How to logout/shutdown/etc"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tom56 on 2009-10-02
I just wanted to check something before I file a bug. I can't see any button to click to logout or shutdown (not on the panel, or in the system menu). Is this the same for everyone else?

I know that I can click my name, but only because I have used Ubuntu before. How is anyone else meant to guess that you click your name to shutdown. If there really is no icon, then I will file a bug.

Thanks
Tom

P.S. Searching for "logout" in help was of no assistance either.

---

### Post by scragar on 2009-10-02
I'm sure there's a logout option under system. Haven't used gnome in a long time though, could be wrong.

---

### Post by tom56 on 2009-10-02
No, there isn't.

---

### Post by cariboo on 2009-10-02
Shutdown/logout et al should be under fast user switch, normally in the top panel, in the top right corner. Make sure you have the applet installed, by right clicking the top panel and selecting add to panel.

---

### Post by ikt on 2009-10-02
> **tom56 said:**
> No, there isn't.

There was in alpha 2 !

---

### Post by rburkartjo on 2009-10-02
tom
 right click on our tool bar and then add to panel then indicator-applet-sessions should give you what you want

---

### Post by tom56 on 2009-10-02
I don't mean to be rude, but did you guys actually read my original post? I am aware of the fast user switch applet, but I am trying to test the beta with the view of, for example relatives I have installed Ubuntu for. Unless I tell them they would have no idea that you need to click your login name in order to shutdown. If there is no discoverable way to do this then I will file a bug.

Just to clarify, I have attached a screenshot of my top panel.

I would have expected a power symbol to the right of my name to indicate that I need to click there to shutdown.

I'm really worried I'm coming across as rude here. Thank you everyone for your suggestions, it's just I think we've gotten our wires crossed!

---

### Post by nhasian on 2009-10-02
i have to admit I was confused about it as well.  It makes sense to have the Shutdown/Suspend options under System.  when they were moved to the fast user switcher, i was opening up a terminal and typing ```
sudo shutdown -r now
```
until someone pointed out to me I had to click on my name in the top right corner.

---

### Post by 23meg on 2009-10-02
When you have the Indicator Applet Session added to your panel, the "Log Out...", "Lock Screen" and "Shut Down..." items will not be visible on the "System" menu. This is by design.

If you find the default setup unsuitable, you can remove the applet, and the items will be under the "System" menu.

---

### Post by tom56 on 2009-10-02
> **23meg said:**
> When you have the Indicator Applet Session added to your panel, the "Log Out...", "Lock Screen" and "Shut Down..." items will not be visible on the "System" menu. This is by design.

If you find the default setup unsuitable, you can remove the applet, and the items will be under the "System" menu.

I don't find the default setup unsuitable, in fact I really like it. However, how is one meant to discover it without any indication of the fact that that button logs you out? The only icon on the button is a speech bubble. I don't think anyone would ever make the connection between that and turning off a computer. It would be better if the layout of the button was:

[icon of speech bubble][name][icon of power on/off symbol]

---

### Post by 23meg on 2009-10-02
[QUOTE=tom56]However, how is one meant to discover it without any indication of the fact that that button logs you out? The only icon on the button is a speech bubble. I don't think anyone would ever make the connection between that and turning off a computer.[/QUOTE]

That's worth a bug report.

---

### Post by tom56 on 2009-10-02
> **23meg said:**
> That's worth a bug report.

I'm a little unsure what package to file against. The applet calls itself indicator-applet-session, but I could have sworn it's called fusa.

---

### Post by 23meg on 2009-10-02
> **tom56 said:**
> I'm a little unsure what package to file against. The applet calls itself indicator-applet-session, but I could have sworn it's called fusa.

Report it with ```
ubuntu-bug indicator-applet-session
```.

---

### Post by Mr. Picklesworth on 2009-10-02
I foresaw this problem and filed the bug report with Jaunty. Feel free to subscribe yourself :)

[https://bugs.launchpad.net/bugs/343219](https://bugs.launchpad.net/bugs/343219)

(Alas, the people doing these shiny new panel applets really don't do enough to follow the HIG).

---

### Post by tom56 on 2009-10-02
> **Mr. Picklesworth said:**
> I foresaw this problem and filed the bug report with Jaunty. Feel free to subscribe yourself :)

[https://bugs.launchpad.net/bugs/343219](https://bugs.launchpad.net/bugs/343219)

(Alas, the people doing these shiny new panel applets really don't do enough to follow the HIG).

Slightly different issue. In Jaunty there was a power icon next to the name so it was clear you could click there to log out. I have no problem with this being the only way to logout, it just needs to be clearer that this is the button to click.

---

### Post by tom56 on 2009-10-05
Bug reported here: [https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/443029](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/443029)

---

### Post by phrizek on 2009-10-14
Am I missing something here, or does karmic feature a huge usability regression when it comes to doing one of the most basic operations on a computer: shutting it down/resetting etc. In previous versions, the shutdown option was removed from the system menu. This was okay because it was replaced with a huge red power icon on the top right of your screen next to your name which allowed you to select what you wanted to do when you clicked it. In karmic, this icon seems to be gone, without anything else in its place to indicate to beginners how to shut down/restart/hibernate their systems. I could see this as a very frustrating thing for newbies, since it is not completely obvious that you must click on your username in the corner to perform these basic functions.

Has anyone else noticed this? Is this going to be fixed by the final release? I'm running the beta fresh off the disc and I don't know if any changes have been made since then, so it would be nice to know if anything has been done to fix this.

---

### Post by 23meg on 2009-10-14
Merged with the existing thread on the same subject. Note the bug report.

---

### Post by andrewabc on 2009-10-14
I asked in another thread but no response that I remember.

How do I get rid of 60 second shutdown timer? If I click on shutdown, I want it to shutdown now. Or at least let me change the timer amount.

This same problem was apparent in Jaunty development and got fixed later on (after beta I think).

In Jaunty problem solved with right click on top right corner (username/icon)->preferences:
Uncheck "show confirm dialogues for logout, restart and shutdown"

Please do the same with Karmic.

---

### Post by tom56 on 2009-10-14
This has been fixed in a recent update

---

### Post by Merk42 on 2009-10-14
> **tom56 said:**
> This has been fixed in a recent update

By 'this' you mean the whole original bug of how it's not discoverable since the Chat Bubble has since been replaced with a Power Symbol, correct?

---

### Post by louieb on 2009-10-15
> **andrewabc said:**
> ... How do I get rid of 60 second shutdown timer? If I click on shutdown, I want it to shutdown now. Or at least let me change the timer amount.
... In Jaunty problem solved with right click on top right corner ... Please do the same with Karmic.

+1 I want the ability to turn off the Shutdown timer too.

---

### Post by novafluxx on 2009-10-15
I noticed this too, but with Empathy open the symbol changes back to the chat bubble. Most people I know dont close every program they have open before shutting the system off (if they every shut it off!), so this still may be confusing to new users who are making the plunge for the first time, whether by purchasing a system pre-installed with Ubuntu or by a friend/relative installing it for them.

I removed that applet, as I never used it for anything but turning off/logging out.

On a side note: I just now am exploring all the neat applets available for me to play with wooo hoo!!

---

### Post by mdurham on 2009-10-16
> **louieb said:**
> +1 I want the ability to turn off the Shutdown timer too.

Restart/Shutdown 60 sec wait dialogue disable key
is in gconf-editor, under apps, indicator-session

---

### Post by louieb on 2009-10-17
> **mdurham said:**
> Restart/Shutdown ... gconf-editor, under apps, indicator-session

Thanks, that did it. I was looking in all the wrong places.

---

