---
title: "Can STARTUP APPLICATIONS be minimzed by default? How ???"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by WinRiddance on 2010-07-25
Hi. I have items such as Tomboy, Gedit, and Thunderbird starting up by default after a reboot since I'm using the "save session on exit" feature. Gedit starts via the startup applications though since I added that in there. However, all of those apps start up in their default window size.

Is it possible to add an application to the startup list with the option to have it minimized by default. Since I use all 3 apps daily, but not in "their order of appearance" after a restart, it would be great for all of them to just be minimzed from the get go. Then I could pick and choose which application I need to begin with after the restart. Is there a command that I can add for this ... what would that be?

Also, is there a way to force an application to start in a second workspace? Another app that I use daily is used strictly on my second workspace. It would be great if I could have that start up minimized by default, but on workspace two ...
Thanks.

---

### Post by WinRiddance on 2010-07-26
B u m p . . .  :(

---

### Post by WinRiddance on 2010-07-27
N O B O D Y ? ? ?  :(

I found a wiki article that said the minimize or startup in a second workspace can be done manually ... but no instructions ... just an age old reference to devilspie from 2005 that might as well be written in chinese ???

---

### Post by davidmohammed on 2010-07-27
dont know about the workspace issue.  I use "alltray" to start an application minimized to the system-tray.

For the workspace thing - this article looks interesting (wmctrl) - does it work for you?

---

### Post by WinRiddance on 2010-07-28
Okay, perhaps I should try asking this differently?

When I open up the STARTUP APPLICATIONS it's possible to add command such as ...

firefox %u

... in order to have Firefox start up automatically anytime that I reboot my system. This is of course also a shell command because if I open up my terminal and type the above command, this too will cause for FF to start up. So I guess the question should be, how do I minimize an application from the shell? I'm assuming that the command for a startup application can be combined with the minimize function which would then result in a startup application being started ... minimized ... right?

---

### Post by WinRiddance on 2010-12-01
Another bump ... :confused:

---

### Post by WinRiddance on 2010-12-09
.

Well, sorry to say, but apparently the answer is ... **NO** !!!

I've searched on Google, Yahoo, and also general Linux, Fedora, Ubuntu, Linux Mint, plus other forums. The question about minimizing applications from within a terminal _has been asked many times_ during the past several years, but apparently this is one command that can't be applied by the general user. I find this to be almost unbelievable for two reasons ... ONE, because it only stands to reason that users who maximize applications via the command line, may also want to minimize applications in the same manner, and ... TWO, because there's obviously a function built into Linux, numerous distros, which does indeed permit users to minimize their GUI windows with the click of a mouse button. Consequently it also stands to reason that there would have to be some kind of a command which is translated into that mouse-click, no ???

Aaaaaahhh, the complexities of Linux for us Ex Windows users .... :rolleyes:

---

### Post by oldos2er on 2010-12-09
Have you tried devilspie? [http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)

---

### Post by WinRiddance on 2010-12-09
Thanks for the input, but the issue that I was talking about had to do strictly with being able to reboot the system, followed by having certain applications opened automatically ... in minimized windows ... and nothing else.

**Problem with devilspie** (there's another version with a GUI as well) is that it is far too complex for any average user and most especially a Windows user to comprehend. Metacity comes into play, Compiz comes into play, some settings won't work if this or that is being used, and so on. Also, sometimes Canonical is to blame for application changes from the command line i.e. when the .tomboy file locations were changed not too long ago (Karmic methinks) which then ended up with a different path reference as a result. Changes to grub/paths later on, etc. This issue (minimize via command line) is in my honest opinion something that should have been available as one of the first command settings to be enabled. According to one of the user comments from your devilspie link, this was possible with a Mac as far back as 1990. Kind'a makes 'ya think, doesn't it? Why wouldn't such an option be available in Linux ... ???

Everything that I do or try to figure out with Linux is done _from the point of view of a total noob or a senior_ who's never had a computer before. My Dad would benefit greatly from such minimize functions because he doesn't understand 90% of what he sees on the menu, which then makes using _anything_ a daunting, intimidating experience. He can't even relate to the names of things ... GIMP ... what on earth is that? BRASERO DISK BURNER ... say what? TOMBOY NOTES ... what does a tomboy and a computer have to do with one another? **Developers just don't think about things like that.** It's not much easier on my, going on 80, Mom with her Windows7 setup. Now if I were able to set up 3 or 4 key apps to just magically appear minimized on the panel after a restart, that would be very helpful to him, at least until he becomes more comfortable with the computer in the first place.

**There is a compromise solution** that's a lot easier to apply then devilspie if you have [UbuntuTweak]("http://ubuntu-tweak.com/downloads/") installed. With [UbuntuTweak]("http://ubuntu-tweak.com/downloads/") there's the option of remembering and saving your current desktop session when shutting down. The reason why I say that that's only a compromise solution is because I tried shutting down my system with three applications minimized ... but after a restart only FF actually remained minimized. One other application started in standard size mode and the third application was gone completely. But if UbuntuTweak will keep my FF, Thunderbird, Gedit, and Gimp minimized after a reboot then that would make me happy as a clam. ;)

Anyway, thanks again for your thoughts on that.

---

### Post by oldos2er on 2010-12-09
I agree with a lot of your sentiments that Gnome lacks or makes difficult some of its configurability. I came to Linux with a background in OS/2, where such configurations were straightforward and simple, so , yeah I miss that. I'm using KDE for the past month or so, which in my opinion is nicer than Gnome in that regard (but still wouldn't be obvious to a newbie probably).

---

