---
title: "Anyone else notice the new mail notifications?"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DarkReaper79 on 2009-04-01
I did a update today, and while looking through my menus, I noticed a new item. Mail Notifications. I open it up and it allow me to have Evolution closed, but still get a pop up when new mail arrives. So far it works good. You can specify you email addy and password. Nice touch!:p

---

### Post by mc4100 on 2009-04-01
Hm. Is it:
System -> Preferences -> Mail Notification ?

That will allow you to check your mail without a client, but it is, as far as I know, provided by the "mail-notification" package -- which isn't installed by default. Or has this been added to the default install?

---

### Post by DarkReaper79 on 2009-04-01
> **mc4100 said:**
> Hm. Is it:
System -> Preferences -> Mail Notification ?

That will allow you to check your mail without a client, but it is, as far as I know, provided by the "mail-notification" package -- which isn't installed by default. Or has this been added to the default install?

Yes, that is how i got to it. All I did was do an update (wish the notifications for that worked :( Then I noticed it there, maybe they added it as a default, like you said:confused:
 One of the options is for evoliution, but you will need to have it running. I use gmail so I just selected it, so i dont need to have evo running.

---

### Post by PRGUY85 on 2009-04-01
Does it support the new notification system?

---

### Post by DarkReaper79 on 2009-04-01
> **PRGUY85 said:**
> Does it support the new notification system?
Yes it does, you have the option to have a popup window too. IM really liking it so far, hope its not a April fools joke on us

---

### Post by mc4100 on 2009-04-01
> **DarkReaper79 said:**
> ... it does, you have the option to have a popup window too.
To elaborate, it seems it will show in the new notification way if:
[list][*]Enable Message Popups box is checked
[*]Expiration is set to anything but "Never"
[/list]
Otherwise, you'll get the fallback pop-up box.

Edit: Further to the above, while the "test messages" will show fine in the new way, when tested with 'real' messages there can be nothing but the fallback box regardless of settings, i.e., it needs to be patched. Damn.

---

### Post by FuturePilot on 2009-04-01
I don't have this. But it sounds nice. Where can I get it?

---

### Post by fooman on 2009-04-01
> **FuturePilot said:**
> I don't have this. But it sounds nice. Where can I get it?

the usual suspects....add/remove, synaptic,  or:

```
sudo apt-get install mail-notification
```

then look in system > preferences > mail notification

---

### Post by DarkReaper79 on 2009-04-01
The new updates I installed today must of added it on it own. I didnt install anything today (thats a first) 

I just noticed that I get a popup window when new mail comes. I can live with it till patched.

---

### Post by FuturePilot on 2009-04-01
> **fooman said:**
> the usual suspects....add/remove, synaptic,  or:

```
sudo apt-get install mail-notification
```

then look in system > preferences > mail notification

But the OP mentioned they didn't install anything. This is odd :?

I was thinking it was something new.

---

### Post by DarkReaper79 on 2009-04-01
Ok now im loosing my mind on this. I looked at my synaptic history, mail notifications were installed on 3/29. But the menu option was never there till today, after the update. No menus were edited.... Im hoping it was the updated or this means Im loosing whats left of my mind...

---

### Post by phaed on 2009-04-01
That's a handy little app.  It lets you set up mail notifications for Evolution, IMAP, POP3, Gmail, Yahoo! Mail and Windows Live/Hotmail.  I use Gmail and I wasn't expecting it to handle that, but it does.

---

### Post by mike919 on 2009-04-02
Does anyone else have a problem with the notifications for this?  The test messages appear correctly in the new notification system but when I get an actual email through my Gmail account it creates a new window with full 'Open', 'Ok' buttons.

Otherwise, I agree this is extremely useful.

Mike

---

### Post by smbm on 2009-04-02
You can use cgmail, the version in my PPA has been patched for the new notifications.

It also supports pop3 and imap (although I haven't tested those)

[https://launchpad.net/~t.vetterlein/+archive/ppa](https://launchpad.net/~t.vetterlein/+archive/ppa)

If you do install it let me know how you get on.

---

### Post by mike919 on 2009-04-02
Thanks for the tip smbm.  However, I get no notifications from cgmail at all, error or otherwise.  There might be some problem with the notifications on my end.  Anyway, I can live with just the mail icon in the corner for now.  I might try it again after the full 9.04 release.

Thanks again.

---

### Post by smbm on 2009-04-02
> **mike919 said:**
> Thanks for the tip smbm.  However, I get no notifications from cgmail at all, error or otherwise.  There might be some problem with the notifications on my end.  Anyway, I can live with just the mail icon in the corner for now.  I might try it again after the full 9.04 release.

Thanks again.

Bizarre. Does the icon change in the systray or does the whole thing just do nothing?

---

### Post by mike919 on 2009-04-02
I got no signs of life at all from cgmail.  I had the option for error notifications turned on and did some things to try to generate an error, like putting in a wrong password or waiting for a timeout, but nothing.  The icon in the corner never changed either.

---

### Post by smbm on 2009-04-02
> **mike919 said:**
> I got no signs of life at all from cgmail.  I had the option for error notifications turned on and did some things to try to generate an error, like putting in a wrong password or waiting for a timeout, but nothing.  The icon in the corner never changed either.

Hmm, interesting. Do you have emails in your inbox for it to report on?

---

### Post by mike919 on 2009-04-02
Yeah, I sent myself a few emails while I was testing cgmail out.  I also removed mail-notifications just in case there was any conflict.

On a positive note, mail-notification is doing a good job keeping up with this exchange. ;)

---

### Post by smbm on 2009-04-02
> **mike919 said:**
> Yeah, I sent myself a few emails while I was testing cgmail out.  I also removed mail-notifications just in case there was any conflict.

On a positive note, mail-notification is doing a good job keeping up with this exchange. ;)

Very strange. Seems to be running fine here.

If you feel like it can you run it from a terminal and post any errors?

Glad that you've found some kind of mail notification that works. I tried mail-notification once and it kept crashing on me, that's irony at work I guess.

---

### Post by olskar on 2009-04-02
> **mc4100 said:**
> To elaborate, it seems it will show in the new notification way if:
[list][*]Enable Message Popups box is checked
[*]Expiration is set to anything but "Never"
[/list]
Otherwise, you'll get the fallback pop-up box.

Edit: Further to the above, while the "test messages" will show fine in the new way, when tested with 'real' messages there can be nothing but the fallback box regardless of settings, i.e., it needs to be patched. Damn.

Noticed that too, but since it seems to be installed by default (?) now, it should propably get patched :) I think it is very nice!

---

### Post by Mr. Picklesworth on 2009-04-02
There actually is a patch out there. Not sure if it works, but it's there ;)
[https://bugs.launchpad.net/bugs/332767](https://bugs.launchpad.net/bugs/332767)

---

### Post by michaelzap on 2009-04-02
RE: mail-notification - You can remove the buttons from the pop-ups using gconf-editor and that makes the notifications show up the new way.

RE: The other notification icon in the system tray - I have an indicator-applet in my system tray since I installed Jaunty beta (last night). I don't use Evolution, so it isn't showing me any new mail notifications (I'm using mail-notification for that). If there's a way that I can check my Google Apps account for new mail using that applet, I haven't figured it out yet.

The indicator-applet is confusing because it's an envelope by default (just like mail-notification, except that it's always that way whereas mail-notification only shows that when you have new mail). Plus it shows Pidgin when I click on it, which is odd. Maybe I need to enable new mail notifications in Pidgin for this applet to work for email?

I think I'll probably end up removing indicator-applet from my panel unless I can figure out how to make it useful to me, but for now I'm taking a wait-and-see attitude since I don't want to break notifications in general (the new ones are purty).

---

### Post by dirtylobster on 2009-04-02
> **michaelzap said:**
> RE: mail-notification - You can remove the buttons from the pop-ups using gconf-editor and that makes the notifications show up the new way.

This worked, thanks. I now have the new notifications. However the app doesn't start when I restart the computer. Is this default behaviour?

---

### Post by michaelzap on 2009-04-02
> **dirtylobster said:**
> This worked, thanks. I now have the new notifications. However the app doesn't start when I restart the computer. Is this default behaviour?

I just create a new Startup Application (Preferences -> Startup Applications in Jaunty; they were called Sessions before that) with the following command:

mail-notification --sm-disable

---

### Post by waffen on 2009-04-06
> **dirtylobster said:**
> This worked, thanks. I now have the new notifications. However the app doesn't start when I restart the computer. Is this default behaviour?

How you make this? I dont found the way...](*,)

---

### Post by waffen on 2009-04-06
> **waffen said:**
> How you make this? I dont found the way...](*,)

I response to me:

[http://ubuntuforums.org/showpost.php?p=6962165&postcount=11]("http://ubuntuforums.org/showpost.php?p=6962165&postcount=11")

---

### Post by macogw on 2009-04-07
> **michaelzap said:**
> RE: mail-notification - You can remove the buttons from the pop-ups using gconf-editor and that makes the notifications show up the new way.

RE: The other notification icon in the system tray - I have an indicator-applet in my system tray since I installed Jaunty beta (last night). I don't use Evolution, so it isn't showing me any new mail notifications (I'm using mail-notification for that). If there's a way that I can check my Google Apps account for new mail using that applet, I haven't figured it out yet.

The indicator-applet is confusing because it's an envelope by default (just like mail-notification, except that it's always that way whereas mail-notification only shows that when you have new mail). Plus it shows Pidgin when I click on it, which is odd. Maybe I need to enable new mail notifications in Pidgin for this applet to work for email?

I think I'll probably end up removing indicator-applet from my panel unless I can figure out how to make it useful to me, but for now I'm taking a wait-and-see attitude since I don't want to break notifications in general (the new ones are purty).
It's an envelope because envelopes are regarded to mean messages in general, not just emails (ex: text message).  The goal is that all the messaging (email, IM, IRC, microblogging, etc) apps have one place to show all those messages.  So far, Pidgin, Evolution, and Gwibber (not the version in repos) support it.  Someone's working on Empathy.

---

### Post by biji on 2009-04-07
can i have mail notification for thunder bird (but not using built in thunderbird notify)

---

### Post by macogw on 2009-04-07
> **biji said:**
> can i have mail notification for thunder bird (but not using built in thunderbird notify)

If you write a Thunderbird plugin that uses the Indicator Applet, sure.

---

### Post by michaelzap on 2009-04-07
> **macogw said:**
> It's an envelope because envelopes are regarded to mean messages in general, not just emails (ex: text message).

Not really. Envelope icons have always been used to imply email afaik. And given that indicator-applet can't currently check my email whereas mail-notification can and does and their icons are almost identical and in the same location, I'd say this is a usability issue.

---

### Post by zorkerz on 2009-04-13
So am I correct that unless we use evolution there is no way to use the indicator-applet to get email notifications?

I really like the potential of the indicator-applet to congregate the messages from various apps but so far its just doing my pidgin messages and in a way that I have to click an extra time to see them.

---

### Post by biji on 2009-04-13
yup.. extra click.. maybe indicator applet should cycle to existing events when single clicked

---

### Post by zorkerz on 2009-04-13
What if a single left click automatically went to the most recent notification? Or used some other desirable formula to pick which notification to go to say always go to a pidgin notification over an email one. Then you could right click to select youself which one to go to. There are some downsides to this but it would save a mouse click for the majority of interactions I think.

---

