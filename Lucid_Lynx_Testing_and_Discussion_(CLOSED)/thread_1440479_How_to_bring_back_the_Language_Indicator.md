---
title: "How to bring back the Language Indicator?"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by trymyluck on 2010-03-27
Dear Ubuntu users,

I have removed the Language Indicator from the Ubuntu panel by mistake. Now i don't know how t bring it back :(
In the the following link [http://ubuntuforums.org/showthread.php?p=9017613](http://ubuntuforums.org/showthread.php?p=9017613) I have found out that I should have language-support, so I reinstalled it but it did not work.
So, how can I bring the Language Indicator back to the Ubuntu panel?

Regards.

---

### Post by MichaelSammels on 2010-03-27
I'm not sure what you mean by Language Indicator? There is a Keyboard Indicator which can change your system language. To add this back right click your panel, add to panel and type "Keyboard" (without the quotes) in the search bar. You should see Keyboard Indicator. Drag and drop this on your panel.

---

### Post by trymyluck on 2010-03-28
Thank you for you reply.
Unfortunately there is no Keyboard Indicator in the Add To Panel in Ubuntu 10.04 :-(
Any other ideas?

---

### Post by overdrank on 2010-03-28
Moved to Lucid Lynx Testing and Discussion

---

### Post by mdurham on 2010-03-28
try Preferences->iBus preferences, I'm not to my computer at the moment but I 'think' there is a check-box in there. Have a look.

---

### Post by kurros on 2010-03-28
The keyboard indicator applet was removed for gnome 2.30. 

The switching function is part of the notification area if you have more than one input method configured in IBus Preferences.

---

### Post by trymyluck on 2010-03-29
Guys,
thank you for your replies. I will try the Ibus when I get back home.
Have a nice day,
T.

---

### Post by McDuff on 2010-03-29
You don&#8217;t need iBus. The language indicator should appear automatically when you add a second keyboard layout in preferences > keyboard.

---

### Post by trymyluck on 2010-03-29
Guys,

I have tried to remove my extra languages and then installed them back again. But it did not help.
As I wrote in my first post, I removed the keyboard indicator by right clicking on it and selecting remove from panel. There should be a place, so where in Ubuntu, where I can choose to add the keyboard indicator back. Where is it?

Right now I have two languages installed.

---

### Post by 23meg on 2010-03-29
Try adding "Notification Area" to your panel, if you've removed it.

---

### Post by trymyluck on 2010-03-29
still no luck guys...

---

### Post by pressureman on 2010-03-29
You need to have two or more *keyboard layouts* configured, to see the "language indicator" (which is actually a keyboard layout indicator).

Adding additional language support packs will not influence this. Also, as was stated previously in this thread, the keyboard indicator applet is gone for good, as it is now integrated in the notification area... it should appear automatically when you add a second keyboard layout.

---

### Post by jcoles on 2010-04-05
In Karmic, I have seen the input method interface change before my eyes. When I first installed the PinYin input method, I also installed English iSpell (which does nothing). I had a menu in the notification area from which I could choose No input method, English iSpell or PinYin. 

Unfortunately, my Lightning add-on to Thunderbird got messed up and I reinstalled it. Then the input method menu was gone. 

Also, the selection menu for Chinese characters disappeared. Now I get a different character appearing as I type more of the PinYin word. I prefer the menu interface. 

Where are all the settings? Karmic has really dumbed down the settings available through Gnome. The settings that remain are often ineffective:

The "Keyboard input method system" setting in Language Support does not persist between logins and appears to be ignored anyway.

Some settings in iBus Preferences are ignored: "Show language panel", "Show input method name on language bar", and "Candidates orientation" at least. 

There's probably some sort of package conflict. I have not been able to get back to the functionality I got after the initial Language support / PinYin method install but before the first logout.

---

### Post by trymyluck on 2010-04-06
Guys,

my solution for this problem was simply - Microsoft method :-) I reinstalled Ubuntu and now I have a **keyboard indicator **in the **indicator notification**.
But, you should fix this, because we don't want fixes in the Microsoft method.

T.

---

### Post by jcoles on 2010-04-06
I wouldn't call "reinstall the OS" a solution. This morning, I booted up and the PinYin input is not there at all! My only remaining way to activate it, Ctrl-Space, does nothing. 

How do I get a menu or toolbar icon that let's me switch between two languages? 

I think the developers should do fewer but better releases. Karmic is the sloppiest Ubuntu yet. Sure it boots fast, so much is missing!

---

### Post by jcoles on 2010-04-06
I tried a less radical version of trymyluck's solution. I removed and reinstalled Simplified Chinese support. 

Everything worked fine again...until I logged out! When I logged back in, I was back to no input method icon, but Ctrl-Space activates a lame input method that doesn't present a menu. Sometimes the right character comes up as you enter the word in PinYin, sometimes it doesn't and there's nothing you can do about it. Poor!

Now I'll have to find out how to remove the SOLVED flag from a thread. This is a bug.

There is certainly a conflict between Simplified Chinese support and the Lightning add-on for Thunderbird. When I first installed Chinese, Lighning disappeared. When I removed Chinese, Lightning disappeared again.

---

### Post by jcoles on 2010-04-07
I might have a solution. 

(I have just read the intro to the forum and realize that this is a Lucid topic, while I've been talking about Karmic. Sorry if that's been disruptive. I'm going to risk being disruptive again by offering a solution from Karmic. Even if it doesn't work as-is, perhaps it will help someone figure out the solution for Lucid.)

The ibus-daemon, and the PinYin candidate panel tool have to be running and it seems that they are not started automatically. You can add them to the Start Applications list in Gnome. Go to System > Preferences > Startup Applications. You can add the following items on the Startup Programs tab.

IBus daemon  /usr/bin/ibus-daemon
PinYin candidate panel  /usr/lib/ibus/ibus-ui-gtk

Log out. Log back in. You should have the Language Indicator, although it's not called that any more.  
[INDENT]
Note: The candidate panel is deprecated in Karmic, so it might not even exist in Lucid. I see a message:
DeprecationWarning: Use the new widget gtk.Tooltip

Finding out how to start gtk.Tooltip is my next task.
[/INDENT]
Good luck.

---

