---
title: "Mail applet in Notification Mockup?"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by syko21 on 2009-03-01
What mail applet is Mark Shuttleworth using in the demo video posted on his blog about the new notifications?
here's the link to his post [http://www.markshuttleworth.com/archives/253](http://www.markshuttleworth.com/archives/253)

---

### Post by hype on 2009-03-01
I think it's the new "Indicator Applet".
You can add it as a gnome-panel applet.

From what i understood, it's supposed to hold a kind of log of notifications you received lately.

From launchpad: 
"A small applet to display information from various applications consistently in the panel. Currently this includes support for messaging applications, but further enhancements are planned."

As of now, it supports pidgin and evolution.

---

### Post by olskar on 2009-03-01
Is it only me that thinks it would be nice if I didn't have to have evolution running to get the applet?

---

### Post by Jingo on 2009-03-01
> **olskar said:**
> Is it only me that thinks it would be nice if I didn't have to have evolution running to get the applet?

I feel the same.

I use gnubiff for my mailchecking! Does the trick!

Or you could try out specto. [http://specto.sourceforge.net/](http://specto.sourceforge.net/)

---

### Post by Sand &amp; Mercury on 2009-03-01
I thought it was made up, for that mockup...

---

### Post by syko21 on 2009-03-02
I'm using cgmail now, the evolution 2GB folder limit bug annoyed the hell out of me when i tried to sync the last time. I'll never touch it again.

---

### Post by macogw on 2009-03-03
The Indicator Applet is supposed to work with Pidgin as well.

---

### Post by zorkerz on 2009-04-11
So what email notification apps are integrated with the notification applet?

Ive been using checkgmail for a long time and like it a lot except that the icon can not disappear when there are no new emails. Ive never seen enough of a reason to use evolution the gmail web interface works just fine for me. 

So the ideal situation for me at the moment would be to have checkgmail just using the notification applet icon. I don't expect this to happen anytime soon. 

What might be a next best solution?

---

### Post by michaelzap on 2009-04-11
> **zorkerz said:**
> So what email notification apps are integrated with the notification applet?

Ive been using checkgmail for a long time and like it a lot except that the icon can not disappear when there are no new emails. Ive never seen enough of a reason to use evolution the gmail web interface works just fine for me. 

So the ideal situation for me at the moment would be to have checkgmail just using the notification applet icon. I don't expect this to happen anytime soon. 

What might be a next best solution?

I use mail-notification for a Google Apps account, and it works just fine in Jaunty (it uses the new notification pop-ups as long as you remove the buttons in gconf-editor, and the icon only appears when you have new email)

---

### Post by zorkerz on 2009-04-11
Hmm im having some trouble with mail-notification.

The first time I tried to start it I got this error.
> A fatal error has occurred in Mail Notification 
The default configuration has not been installed properly. Please check your Mail Notification installation.
Second time I tried to start it seemed to work fine. 

It does not appear to integrate with indicator-applet at all though. You mentioned changing some settings in gconf-editor. What ones specifically and what do they do?

I do like how the icon only appears when there is new mail but it does not compair to checkgmail in info it shows. I only have to go to gmail for about half of my emails now because of checkgmail.

---

### Post by michaelzap on 2009-04-11
> **zorkerz said:**
> It does not appear to integrate with indicator-applet at all though. You mentioned changing some settings in gconf-editor. What ones specifically and what do they do?

Go to apps -> mail-notification -> popups and just remove all the values in actions. The new notification pop-ups can't have any buttons in them yet. Yet.

---

### Post by zorkerz on 2009-04-11
Ah I see that makes sense. Im obviously having other problems with mail-notification though. Now when I try to open it I see the window briefly in the window list but it immediately closes. Ill try reinstalling it.

No help reinstalled and it still closes immediately.

run it from the terminal and it says
> ** Message: Mail Notification is already running

Ok well I can't seem to open the mail-notification popups tab. I ran gconf-editor and disabled buttons in the popups. I did not see one of the new notification bubbles but it could have happened while I was not looking. There is still a mail-notification icon though.

What Im really looking for is an app that will never show its own icon rather use the indicator applets icon. Pidgin now allows this so if my email notification application could to it would allow me to have one less icon cluttering up my panels. 

Thanks for the input.

---

