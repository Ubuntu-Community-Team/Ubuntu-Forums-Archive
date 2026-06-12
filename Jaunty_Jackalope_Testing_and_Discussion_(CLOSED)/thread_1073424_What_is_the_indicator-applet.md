---
title: "What is the indicator-applet?"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-02-18
I have done a dist-upgrade and a new package named indicator-applet was installed. What does it do??? Do you know?

---

### Post by tretle on 2009-02-18
Its designed to try and clean up the taskbar, currently it supports evolution. The idea behind it is that instead of having multiple applications use different icons to notify you of something you instead have one icon(mail icon) which is used for multiple apps like empathy, pidgin, evolution etc.)
Whats a bit more exciting is that macslow announced on his blog that the new notification system should be in today.

---

### Post by bruce89 on 2009-02-18
Once again, a fork that will have no hope of ever finding itself upstream. This and the new notification system is going too far.

I'm all for change, but only if it finds itself upstream. However, I don't know why a black rectangle is considered better than a nice balloon thing.

---

### Post by philinux on 2009-02-18
It's in synaptic but not installed on my system.

---

### Post by bruce89 on 2009-02-18
> **philinux said:**
> It's in synaptic but not installed on my system.

Count yourself lucky that you've disabled recommended packages being installed.

---

### Post by philinux on 2009-02-18
> **bruce89 said:**
> Count yourself lucky that you've disabled recommended packages being installed.

"Consider recommended packages as dependencies" is ticked. It's a default install. :confused:

---

### Post by bruce89 on 2009-02-18
> **philinux said:**
> "Consider recommended packages as dependencies" is ticked. It's a default install. :confused:

You can't have the newer ubuntu-desktop package installed then.

---

### Post by philinux on 2009-02-18
Alpha 4 64 bit clean install and fully updated or is there an update I'm missing?

---

### Post by bruce89 on 2009-02-18
> **philinux said:**
> Alpha 4 64 bit clean install and fully updated.

That doesn't mean anything. The output of

```
apt-cache policy ubuntu-desktop
``` does though.

---

### Post by philinux on 2009-02-18
Ok got the new ubuntu-desktop installed but notification area still there and indicator applet not visible. I can add it to a panel but it just looks like a divider.

---

### Post by pferraro on 2009-02-18
> **philinux said:**
> Ok got the new ubuntu-desktop installed but notification area still there and indicator applet not visible. I can add it to a panel but it just looks like a divider.

Open evolution, and you'll see a mail icon get added.  Doesn't seem to do anything though...

---

### Post by philinux on 2009-02-18
> **pferraro said:**
> Open evolution, and you'll see a mail icon get added.  Doesn't seem to do anything though...

Right, bit pointless. I dont use evo and Thunderbird has no integration.

---

### Post by Nullack on 2009-02-18
Phil if your using a source mirror, yo might try hitting main to not be behind like some mirrors are

---

### Post by philinux on 2009-02-18
Cheers nullack,

Default install was set to server for UK. I've changed it to main.

Wow it's a lot faster too.

---

### Post by tawmas on 2009-02-19
> **pferraro said:**
> Open evolution, and you'll see a mail icon get added.  Doesn't seem to do anything though...

Yep... It doesn't even have the contextual menu to move/remove it... So, how do you remove it from the panel?

---

### Post by castrojo on 2009-02-19
> **tawmas said:**
> Yep... It doesn't even have the contextual menu to move/remove it... So, how do you remove it from the panel?

There's a little grippy just to the left of it so you can move it around, remove it, etc.

---

### Post by olskar on 2009-02-19
> **bruce89 said:**
> I don't know why a black rectangle is considered better than a nice balloon thing.

It looks better ;)

---

### Post by tawmas on 2009-02-19
> **whiprush said:**
> There's a little grippy just to the left of it so you can move it around, remove it, etc.

Oh, true! The grippy is practically invisible on a dark panel. :-(

---

### Post by hyperair on 2009-02-26
Alright, out of curiosity, I've backported the following to Intrepid in my PPA ([https://launchpad.net/~hyperair/+archive/ppa](https://launchpad.net/~hyperair/+archive/ppa)):
[list]
[*] evolution-indicator
[*] gobject-introspection
[*] indicator-applet
[*] notify-osd
[*] pidgin-libnotify
[/list]

I noticed pidgin-libnotify seems to depend upon indicator-applet, though I don't see it being used. As for evolution-indicator, it doesn't seem to have any effect either. I have the plugin installed and enabled, and all I see is "No Indicators". Perhaps I'm missing something here.

EDIT:
Backporting and installing indicator-messages seems to have solved the issue. Also, I've backported the patches from gnome-settings-daemon and gnome-power-manager as well as the new human-icons-theme.

---

### Post by Taiebot65 on 2009-02-28
The icon is showing up when i ve got a new email in my inbox via evolution...
It s good because it s over pop and was not working before.

There is still a bug as filtered email are not showing up as new email i think i will filled or look if one is existing or maybe there is an extra setting to do.

Edit yes there is an extra setting..

Preferences
>>preferences of email ( do not know exactly because it s in french) third choice from the top in the left menu

When new email arrives in.........
choose any folder

---

### Post by Kow on 2009-03-19
Can someone post screenshots of what this actually does? Besides seeing an envelope in the taskbar I don't see what it does besides cluttering up the taskbar even more.

[http://www.flickr.com/photos/kenvandine/3334176704/](http://www.flickr.com/photos/kenvandine/3334176704/) If this is all it does then wow what a waste of time and taskbar space.

---

### Post by hyperair on 2009-03-19
Actually yes, that's what it does. It's a place for applications to queue messages. However, evolution doesn't really use it properly yet, and Evolution's the one that would really benefit from this. Pidgin already has its blinking icon.

---

### Post by Kow on 2009-03-19
> **hyperair said:**
> Actually yes, that's what it does. It's a place for applications to queue messages. However, evolution doesn't really use it properly yet, and Evolution's the one that would really benefit from this. Pidgin already has its blinking icon.

Okay thanks. I'll remove it now.

---

### Post by rudenko_ruslan on 2009-03-19
Strange - I can't see indicator-applet on my GNOME panel, but System Monitor shows it's process running without any problems.

#-o

---

### Post by Halow on 2009-03-19
Yeah, for me - sometimes it's there, sometimes it isn't. I haven't figured out yet what's making it appear and disappear. And I really wish it worked with Evolution. :(

Edit: Wait, it *does* work with Evolution! Just got an email.

---

### Post by olskar on 2009-03-19
> **Halow said:**
> Yeah, for me - sometimes it's there, sometimes it isn't. I haven't figured out yet what's making it appear and disappear. And I really wish it worked with Evolution. :(

Edit: Wait, it *does* work with Evolution! Just got an email.

Does evolution need to be running for the applet to show you got new mail in evolution? If not, I upgrade as fast as possible :D

---

### Post by Halow on 2009-03-19
Evolution has to be open. :(

---

### Post by topyli on 2009-03-30
> **Kow said:**
> 
[http://www.flickr.com/photos/kenvandine/3334176704/](http://www.flickr.com/photos/kenvandine/3334176704/) If this is all it does then wow what a waste of time and taskbar space.

Actually, you can now disable Pidgin's perpetual icon from your notification area (persistet icons don't belong there anyway), because the indicator-applet takes care of your notifications, and you can handle your presence status from the user-switcher-applet seen on the far right. Evolution will no longer notify you about messages via a notification icon either.

Eventually when more apps support the new applet, it will potentially save lots of space. Right now it's not very useful except for people using Ubuntu's default apps.

---

### Post by TrueTom on 2009-03-30
> **topyli said:**
> Actually, you can now disable Pidgin's perpetual icon from your notification area (persistet icons don't belong there anyway), because the indicator-applet takes care of your notifications, and you can handle your presence status from the user-switcher-applet seen on the far right.

How do you open the contacts list then?

---

### Post by uBeer on 2009-03-30
If the applet is there and pidgin is running, there will be an envelope and if you click it you will see a drop down with one of the items being Pidgin.

That icon works the same as the notification area icon where you click once to hide the people list and click again to show it.

---

### Post by novafluxx on 2009-03-30
Glad it can be disabled :P

---

### Post by jlimon on 2009-04-10
Yeah, absolutely. I immediately removed it as soon as I noticed it..

Pidgin has its blinking icon and I use Mutt.. I have no use for this.

---

### Post by jlimon on 2009-04-10
Hm, second thought.

Why does /usr/share/gnome-panel/add-indicator-applet.py ship with gnome-panel and not indicator applet? The startup function remains after the applet is removed due to this.

---

### Post by danube on 2009-04-22
I actually don't think it's that much of a bad idea, that thing. The fact that it leaks of configuration AT ALL confuses me a bit, and that there is not a bit of any description what the application might be for.

I'd love to see it customizable and maybe skinable with having some documentation on it.

I'm using it with Pidgin (which works obviously pretty well) and Banshee notifications (I wonder!), but doesn't show Banshee in it's drop down list of apps. Also, Banshee tray icon can't be cleared without quitting it.

Tom

---

