---
title: "Nuked again!!!! Configure Display applet"
date: 2008-07-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scradock on 2008-07-25
I fell victim to the problems with nautilus running with gksudo, and nuked my install (see related thread). After posting some hopefully helpful info on the launchpad bug report (#250021) I decided to re-install Intrepid from scratch. That done, I updated today, and saw a shiny new toy on the top panel - an applet marked "Configure Display", or something similar.

It showed a very limited display of information - on a laptop there isn't a lot to configure - but I was seduced by the offer to turn the display Left. After I clicked that my display died, and returned me to the login screen. Now every attempt to login, using all available graphical session options, fails. Console login is OK, but limited use.

Inspecting the logs, I see the error message 

"gdm: WARNING: gdm_slave_xioerror_handler: Fatal X error: Restarting X"

which of course fails.

Does anyone have any suggestions as to what I misconfigured, and how to get back to normal gdm behavior?

Or do I have to re-re-install? and learn not to try shiny new buttons?

PS the gdm log contains the message

EE Failed to load module "dri2" (module does not exist, 0)

Is this a clue? Am I supposed to have this module in Intrepid?

---

### Post by Trespasser on 2008-07-25
Humorously put. Yes, we've all been seduced by shiny new buttons before (I know I have...:)).

BTW, a similar thing happened to me today as well. I was unable to change my resolution to what I preferred...it kept kicking me back out to the login screen...so I thought I'd see if enabling compiz might help...well, it didn't. It kicked me back out to login, and, unlike before, it wouldn't let me pass this time. I reloaded Hardy and am up and going once again. Thank goodness for CloneZilla...a great utility.

---

### Post by mc4100 on 2008-07-25
"Configure display settings", I'm seeing this on my laptop too. When I click on it, however, "screen rotation" is grayed-out, so I can't reproduce your problem. 

But, it seems like a bad idea anyway:
Firstly, it's permanently living in the tray, (I need a neat tray, less=more sort of thing). 
Secondly, is it even useful?
As far as I can tell, it provides screen rotation (Which for me is gray;  would anyone use this anyway?) and a link to "Screen Resolution", which can already be found in System -> Preferences.

---

### Post by ronacc on 2008-07-25
I checked the gdm log(s) on my nuked install and its there ,

Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 17 22:05:51 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "dri2" (module does not exist, 0)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

infact I have 5 gdm logs all written during a span of 42 seconds imeadiately after the failure all the same . I'm going to install A3 later this evening and I'll remember not to try the "shiny new toy".

---

### Post by Nullack on 2008-07-25
So whos reported the bug :)

---

### Post by ronacc on 2008-07-25
scradock found this one he should file it , I still haven't had any response on the root nautilus one I filed 6 days ago , no  more info requests or anything except for the kind people that added comments , from the devs nothing !

---

### Post by Nullack on 2008-07-25
Ronacc I totally share your frustration with the lack of bug action my friend. Like you, I make a conscious effort to contribute to existing bugs that effect my system and to create new bugs not reported elsewhere.

It has been my experience Novell do a far better job with actioning bugs and engaging bug reporters.

Its clear that the free community for Ubuntu bug development is nowhere near the size it needs to be and that Canonical is not funding paid workers at any level near sufficient to get the quality right.

Sometimes too I have found when my lucky rain dance and salf throwing has by chance worked and has gotten developer attention the outcome has not been very good. For example an easily repeatable crash bug I raised was closed by a dev who felt there wasnt enough information, and when I went to the effort to totally and completely have all debug output in a new bug report, that bug report has been sitting there for many moons now with nothing happening. I even emailed the dev directly to advise him I had addressed all of his issues and that everything was now supplied, to no effect.

That said, I think it is a major function of us testers to be disciplined and keep raising and commenting on bugs. Its better than giving up.

---

### Post by scradock on 2008-07-25
> **ronacc said:**
> scradock found this one he should file it , I still haven't had any response on the root nautilus one I filed 6 days ago , no  more info requests or anything except for the kind people that added comments , from the devs nothing !

Yes, I'll do it - at the moment I'm trying to re-install Intrepid. I come to the forums first in case anyone has any bright ideas to fix stuff - this time it doesn't seem as if we do... 

I have to say that it seems ridiculous that I need to re-install after a one-click error. There HAS to be a config file somewhere that could be edited to get back to sweet Intrepid. But all the new ideas mean that no-one knows where those config files are any more.

Example - a few crashes ago, back in Hardy-as-development, I found that the sort of X-crash I have now could be overcome by deleting a sessions file - I think it was in ~/.gnome2. There aren't any sessions files there now; in Hardy they live in ~/.config/metacity/sessions, and in Intrepid in ~/.config/metacity - or is it the other way round? And they have a fancy new name ending in .ms, which sounds as if the Redmond hordes are taking over....

And it isn't them anyway - those particular files, I mean - because after the first crash there were none dated for the last ten days or so. So I'm stumped.....

---

### Post by scradock on 2008-07-25
I've reported the bug. Let's see if anyone is listening...

---

### Post by ronacc on 2008-07-25
@ Nullack  thanks for your kind words I'm glad to see that I'm not the only one who sometimes gets frustrated , and I have also had experience with some bugs that I have filed .

@ scradock  I'm also reinstalling interpid A3 right now  on a new partition since I'm still keeping the screwed up install avaiable incase the devs want me to try something , fortunately intrepid was the first install on a 320gb drive so there is pleanty of room .

---

### Post by razmakati on 2008-07-26
I made the mistake of trying a different screen resolution with this new applet.
Every log in just returned me to GDM. I had to boot into previous kernel to adjust display setting back.

---

### Post by scradock on 2008-07-26
> **Trespasser said:**
> Humorously put. Yes, we've all been seduced by shiny new buttons before (I know I have...:)).

BTW, a similar thing happened to me today as well. I was unable to change my resolution to what I preferred...it kept kicking me back out to the login screen...so I thought I'd see if enabling compiz might help...well, it didn't. It kicked me back out to login, and, unlike before, it wouldn't let me pass this time. I reloaded Hardy and am up and going once again. Thank goodness for CloneZilla...a great utility.

I've just about got Intrepid back the way I want it - except for the "interesting" dark theme, of course - so I'll try Clonezilla before I mess it up again. Thanks for the hint - I had tried partimage and found it a royal PITA - just the worst combination of CLI and GUI for my taste.

---

### Post by scradock on 2008-07-26
The new "Configure display settings" is apparently an applet calling a capplet, the Screen Resolution component of gnome-control-center. But it has no name, cannot be removed from the panel, and I cannot for the life of me find out what actually installs it - probably an extra item in gnome-applets, but there is no change to the list of components to confirm that. So I think we're stuck with it on the panel - sorry, folks.

gnome-control-center is also interesting: it is no longer accessible through the menus; you have to invoke it from a terminal, apparently. I find that a shame, as it looked like a sensible collection of control capplets to give access to all sorts of things. Maybe I'll have to make a launcher for it...

Which leaves us with the problem that it is an old and familiar part of the gnome-control-center that is crashing X for some of us, not an untested new widget. I will update the bug report to point to gnome-control-center: screen resolution capplet, and see if there is some attention.

*****

PS No such luck. Launchpad informs me that gnome bugs have to go to Bugzilla, and that as there is no-one listed as maintainer of gnome-control-center I shouldn't hold my breath. Bugzilla says I should report via Bug-buddy, or else I have to submit a Stack trace - that's more than I can deal with tonight. How does one invoke Bug buddy from a crashed system? Or recover a Stack trace, for that matter?

G'night all...

---

### Post by ronacc on 2008-07-26
@ scradock on my crashed system I was able to get into recovery mode and set a root password from there and then I am able to start an xsession as root without gdm or network .

---

### Post by marijus on 2008-07-26
hello,

i think i found a solution... or at least i got my gnome-session working again... 

i played around with the new configure-display-settings applet and couldn't log in anymore after trying to rotate the screen...

[COLOR="Red"]the solution:[/COLOR]
go to /home/username/.config and rename or delete the file monitors.xml
that's the place where things were stored... after next login there was a new monitors.xml with default options and i could log in again....

i hope this will help you...
regards marijus

---

### Post by scradock on 2008-07-26
> **marijus said:**
> hello,

i think i found a solution... or at least i got my gnome-session working again... 

i played around with the new configure-display-settings applet and couldn't log in anymore after trying to rotate the screen...

[COLOR="Red"]the solution:[/COLOR]
go to /home/username/.config and rename or delete the file monitors.xml
that's the place where things were stored... after next login there was a new monitors.xml with default options and i could log in again....

i hope this will help you...
regards marijus


Thank you! That would probably have saved my bacon. In the event I did the re-install using the alpha 3 LiveCD, but if I get the same sort of problem again I'll know where to look.....

I have to say the ingenuity of the developers is impressive - all the cunning ways they find to store configuration data and make sure that things just work. Except when they don't, and we don't know where to fix what is broken because THERE IS NO DOCUMENTATION!!!

*****

PS  Grrrrr!   I checked; there is NO file monitors.xml in my .config folder! In fact there is no file monitors.xml anywhere in my Intrepid system - only a huge database of monitor specs. Now what? And why not?

---

### Post by ronacc on 2008-07-26
I don't have a monitors.xml file either , but I thought that was because I trashed my system with "copy as root" not the display config thing . anyway I always hand edit my xorg.conf file , the only way I've found to get it right .

---

### Post by hugmenot on 2008-07-26
Gconf-editor: ```
/apps/gnome_settings_daemon/plugins/xrandr/active
```, untick

---

### Post by faxmaster on 2008-07-26
> **scradock said:**
> <snip>The new "Configure display settings" is apparently an applet calling a capplet, the Screen Resolution component of gnome-control-center. But it has no name, cannot be removed from the panel, and I cannot for the life of me find out what actually installs it...
I was able to remove it, and in doing so removed Network Manager and the battery applet.  I can't get Network Manager to show up on the panel again, but it's set to load on startup.  When I run nm-applet from the terminal, I get:

** (nm-applet:5978): WARNING **: <WARN>  hal_net_physdev_cb(): dbus returned an error.
  (org.freedesktop.Hal.NoSuchProperty) No property net.physical_device on device with id /org/freedesktop/Hal/devices/net_(removed mac address)


** (nm-applet:5978): WARNING **: <WARN>  hal_net_physdev_cb(): dbus returned an error.
  (org.freedesktop.Hal.NoSuchProperty) No property net.physical_device on device with id /org/freedesktop/Hal/devices/net_(removed mac address)

---

### Post by scradock on 2008-07-26
> **hugmenot said:**
> Gconf-editor: ```
/apps/gnome_settings_daemon/plugins/xrandr/active
```, untick

Well found! That removes the applet from the panel....

One small step forward...

---

### Post by ronacc on 2008-07-26
good find ,thanks !

---

### Post by scradock on 2008-07-27
> **hugmenot said:**
> Gconf-editor: ```
/apps/gnome_settings_daemon/plugins/xrandr/active
```, untick

With this clue I have checked the xrandr program that should be called by this plugin. Using xrandr --prop gives me a sensible list of display properties.

Running ```
xrandr --screen 0 -o inverted
``` inverts the display (!!!)

and running ```
xrandr --screen 0 -o normal
``` sets it back the right way again.

Running ```
xrandr --screen 0 -o left
``` turns the display 90 degrees to the left - what I was expecting the Rotate | Left button to do in the plugin.

and running ```
xrandr --screen 0 -o normal
``` puts it back the way it was. (Phew!!)

So it seems that the underlying program xrandr is working fine, and so is my display adaptor. The original problem must be in the plugin.

But now maybe I know how to recover my display by using xrandr --screen 0 -o normal ....

No need for sudo or root, so I shouldn't run into the root privileges problem....

I'm going to try it - run the applet again, ask it to rotate display left, and see if I can recover......

****

PS Well, that was a bit scary! The display crashed again on clicking Apply after selecting Left in the Rotation menu. The usual behavior - wouldn't recreate the desktop after login. I logged in to Failsafe Terminal and tried xrandr --screen 0 -o normal, but it didn't seem to do any good the first time. I thought of checking the permissions on /, but ls -la wouldn't show them on the small terminal screen.

The second time I tried logging in using the Failsafe Terminal I did the following:

repeated xrandr --screen 0 -o normal;

started gconf-editor (which came up as a GUI object!) and set /apps/gnome_settings_daemon/plugins/xrandr/active to off;

ran sudo chmod 755 / - just for luck.

The next attempted login succeeded, returning me to the normal desktop. I don't know which of the three (one or more) did the trick, but it worked, in case I find myself in the same situation again.

It does seem that there is a bug in the xrandr plugin, rather than the actual xrandr program, so I'll update the bug report accordingly.

---

### Post by ronacc on 2008-07-27
good trouble shooting ,that will help the the devs.

---

