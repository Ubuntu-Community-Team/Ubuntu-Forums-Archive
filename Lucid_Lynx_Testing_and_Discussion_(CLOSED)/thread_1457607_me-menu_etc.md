---
title: "me-menu etc"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-04-18
Although this is all pretty much academic, since I suspect it's too late to make changes now but I would like to share my thoughts on the subject.
I'm not a heavy user of things such as facebook, twitter, IM etc but I do actually like all this me-menu business.

However, there are things I think need changing.

Main thing is the email bit.  I hate Evolution and for many reasons I will never use it as default and I know many people feel the same way and the section in the menu should really be set to use your default mail app really (whatever is set in "Preferred Applications").  The chat section should maybe do the same though I'm not sure how a default IM would be defined.

I also think the email bit of the menu is very pointless since you have to have Evolution running to make use of it.

There is an app I have used in the past called "Mail-notification".
This is an app that sits in your tray and you configure your email accounts through that and it checks for messages for you.  Once these are notified you can THEN click the icon to open up your default email client so there is no need for it to be running all the time.
(I may be wrong but I think you can also compose messages from it as well).

I think it would make a lot more sense if the indicator/me menu thing worked like that, rather than being tied to a particular app, it would be tied to the email account(s).

Maybe even better is if "About Me" could be used to enter email and instant messenger accounts and any app would automatically use those accounts without you having to configure them?

Just some ideas anyway. I will wait to see what happens by release but with gwibber being a bit flaky (and not giving notifications) I'm not sure this whole social networking thing is going to work and the me-menu and indicator applet may end up being pretty pointless and one of those thing people automatically disable after install.

---

### Post by donato roque on 2010-04-18
+1 this all makes sense to me.

---

### Post by cariboo on 2010-04-19
You can go to /usr/share/indicators/messages/applications and remove evolution from the menu and add you favorite email client for example:

```
/usr/share/applications/thunderbird.desktop
```

---

### Post by x-shaney-x on 2010-04-19
> **cariboo907 said:**
> You can go to /usr/share/indicators/messages/applications and remove evolution from the menu and add you favorite email client for example:

```
/usr/share/applications/thunderbird.desktop
```

Does removing the Evolution actually take away the Mail, Compose New Message and Contacts entires from the menu?

I know T-bird can be used with the menu as I use an extension which adds it to indicator (and works well) but it would be better if we could make T-bird (or others) take over that email section in the menu rather than adding new entries.
Or better still, like I mentioned before, it would be a lot better to tie the menu to the accounts and not an app.
In fact the more I keep thinking about it the more this all makes sense to me.
A single configuration panel somewhere for setting up all mail and IM/Broadcast accounts which can be used by any related app.

---

### Post by x-shaney-x on 2010-04-19
Hmm, intruiging.

On closer inspection it seems you CAN make thunderbird take over the email section of the menu very easily (possibly even mail-notification, haven't looked into that yet).
So I could use the menu to open t-bird contacts and compose window or even add menu entries to open the calendar (if using lightning).

Can probably do the same with chat.

In fact, if I had some programming experience I could come up with some GUI me-menu editing tool and I wouldn't be suprised if somebody did come up with one in the near future.

---

### Post by x-shaney-x on 2010-04-19
Indeed, after a little playing I have managed to replace Evo with T-bird:

[IMG]http://i43.tinypic.com/210ll47.png[/IMG]

The compose and contacts entries listed there DO launch the thunderbird compose and addressbook windows, by the way.

Not sure how to move the entries up or down, I suspect it may possible be alphabetical based.
Also I haven't worked out how to get it to show new mail in the menu, the extension I use creates a new section in the menu which isn't ideal but I've got more poking around to do yet.
Suppose I could replace the broadcast entry with firefox launched straight to facebook or something :)

---

### Post by sayantandas on 2010-04-20
> **x-shaney-x said:**
> Indeed, after a little playing I have managed to replace Evo with T-bird:

[IMG]http://i43.tinypic.com/210ll47.png[/IMG]

The compose and contacts entries listed there DO launch the thunderbird compose and addressbook windows, by the way.

Not sure how to move the entries up or down, I suspect it may possible be alphabetical based.
Also I haven't worked out how to get it to show new mail in the menu, the extension I use creates a new section in the menu which isn't ideal but I've got more poking around to do yet.
Suppose I could replace the broadcast entry with firefox launched straight to facebook or something :)

could u give us a quick how-to on how to remove evolution and put t-bird?

---

### Post by x-shaney-x on 2010-04-20
Well removing evolution was simply a case of uninstalling it (I removed everything evolution related except "evolution-data-server-common" but just evolution will do.

To add the Thunderbird entry, I didn't really know what I was doing, it was more trial and error: 
I compared the evolution and thunderbird desktop files in /usr/share/applications and came up with the following, which I put into thunderbird.desktop file:```

[Desktop Entry]
Name=Thunderbird Mail
GenericName=Mail Client
Comment=Manage your email and contacts
Exec=thunderbird %u
Icon=evolution
Terminal=false
Type=Application
Categories=Application;Network;Email;
StartupNotify=true

X-Ayatana-Desktop-Shortcuts=Compose;Contacts

Name[en_GB]=thunderbird.desktop

[Compose Shortcut Group]
Name=Compose New Message
Exec=thunderbird mailto:
OnlyShowIn=Messaging Menu

[Contacts Shortcut Group]
Name=Contacts
Exec=thunderbird -addressbook
OnlyShowIn=Messaging Menu
```

I then added a text file in /usr/share/indicators/messages/applications called thunderbird which contained just the following: ```
/usr/share/applications/thunderbird.desktop
```

I think I logged out to make sure everything cleared and restarted and the menu showed as the screenshot in my above post.

As I mentioned before, this doesn't actually inform you of new messages but there is a thunderbird extension somewhere that adds this functionality.

The other downside is that future thunderbird updates would overwrite the .desktop file.
There should be a way of replicating it all inside your home directory so it doesn't get overwritten but I haven't had time to look into that yet.

Of course the best thing would be for the thunderbird devs to build it all in ;)

---

