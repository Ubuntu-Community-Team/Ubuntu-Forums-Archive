---
title: "Upgrade to 12.04... messed up Unity themes"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by ausrick on 2012-09-30
Hello again Everyone!

I updated from 10.04 to 12.04.  I know, after reading the documentation that wasn't a recommended thing to do but at the time I was just happily computer-ing along and saw the update button in the software center... but I digress.

In 10.04 I was using a dark gray and blue theme, I think iirc I had picked one from the appearances and just tweaked it with the options given me.  Also I had used Compiz for the desktop cube and wobbly windows and windows catching on fire when you closed them and all of that good stuff.  I had actually used pretty much this same setup with not too much difficulty since 8.10 (original install) Going to 9 and 10 always messed some things up but I could stumble around and fix them after at most a day or two of messing around.  Not so this time I'm afraid.

First let me say that I've been searching around for several days on this issue.  What I keep finding are posts telling me to add different repositories but I find conflicting information, or outdated links, and I don't want to mess anything else up.  I'm also not sure I quite understand the differences between Gnome 3, Gnome 3.4.1, Gnome-Shell, and Unity so in that regard I don't know if some of the instructions I find are actually targeting what I want to accomplish.

That all being said, my problem pretty much seems as follows. It seems like some of the settings I had used on my previous theme are some how getting passed through to 12.04.  So when I choose "ambience" the background color of windows stays a dark blue gray, and text boxes and font colors and buttons stay to some what how I had them before... But some elements are changed, and so some things have become unreadable, etc. or some of my buttons are over to the right when in other fresh installs I see them on the left. etc.

I'm assuming there are some config files somewhere I have to remove or edit but I'm not really sure how to proceed.  Any advice?  below is a screen cap of my desktop showing what I'm talking about.

[IMG]https://dl.dropbox.com/u/54319871/Screenshot%20from%202012-09-30%2017%3A10%3A09.png[/IMG]

---

### Post by Sonsum on 2012-09-30
A big problem is that 10.04 was running Gnome 2, while 12.04 runs Unity, which is based on Gnome 3.

Probably the easiest thing to do would be to find a similar theme you like that is a GTK 3 theme.

---

### Post by ausrick on 2012-09-30
Thanks Sonsum.  It seems like some of those settings from 2 got moved into whatever it is exactly now and I can click on "Ambience (default)" all day long without it making the interface look like what a fresh install with "Ambiance (default)" selected looks like.

I'm not concerned so much with retaining the look I had in 10 as I am with getting it to act "properly"  And what it seems to do is take any value that's not expressly defined in "ambiance", for example, and lets whatever I had in 10 "show through"... so I can click on "High Contrast" for example, and it will change some of these oddities, but the second I change back to "ambiance" or "adwaita" it brings back these previous "poke throughs" from 10.

I'm guessing there's some config file somewhere that hopefully (wishful thinking) if I zap it it will make functionality return to normal... even then, outside of the handful of themes that comes with the distro... which one's would you add? would they say GTK3? 3+? 3.4.1? Unity? Nautilus? where would you get them?  I guess I don't understand the underlying fundimentals of the GUI Desktop environments that sit on-top-of the actual OS and command line interface or how they handle the assignment of colors and graphical elements (theme).

At least the good news is that after upgrading the way I did the system actually still runs.  I haven't *cough, knock on wood, ran into any other issues with my upgrade path yet.

---

### Post by ausrick on 2012-10-04
Update: Problem solved, maybe with a rusty crowbar rather than a scalpel, but solved none the less :)

in my user account's home directory did a Ctrl+H and trashed the following folders. log out, log back in and viola! no more weird hold overs from 10.04. Looks just like a new install, and faster too! Sure I had to reenter my wifi passphrase and repopulate and rearrange my dock but small effort to pay.

```
.gnome
.gnome2
.gconf
.gconfd
.cache
.compiz-1
.dbus
.gnome2_private
.mission-control
.prism
```

Why did I delete the above? According to Google(tm) they were all either outdated, or applied to Gnome2 user settings, or Gnome3 user settings, and several threads about resetting gnome desktops to a fresh state recommended these.

Also these searches mentioned removing .metacity .dmrc .thumbnails and anything .compiz ... Also saw some commands like "unity --reset" but many complaints that this did not work or had other side effects. Also there was a post by Jorge Castro over on askubuntu.com that is a little too intangible for me. It's quoted below.  Thankfully I had to do none of this and it worked like a charm just removing what I removed! :D

> The current answer(s) are out-of-date and require revision given recent changes.

Didrocks told me there's no easy way to do this in 12.10, however he gave me some information to figure it out, the ideal answer will script up something like this: "gsettings list-relocatable-schemas | grep compiz", then note down the relocatable schemas then gsettings reset-recursively <each schema from the list above>:/org/compiz/profiles/unity

---

