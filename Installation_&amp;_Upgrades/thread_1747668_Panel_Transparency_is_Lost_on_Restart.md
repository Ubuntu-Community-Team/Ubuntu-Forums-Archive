---
title: "Panel Transparency is Lost on Restart"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by kevinharper on 2011-05-02
I have searched all over for my specific problem and cannot find anyone who has the same issue, much less an answer.

I have had no issue with the panel's transparency in previous Ubuntu versions. This all started w/ Natty.

I set up transparency (right click on panel, Nav through Properties > Background, Check "Solid Color," slide bar to my preferred opacity, & click "Close."

The panel looks as follows:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190926&stc=1&d=1304388231[/IMG]

But when I restart the computer it goes grey:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190927&stc=1&d=1304388231[/IMG]

killall command doesn't work, I have moved the panel, I have created a new one. The "closest" I found were people complaining (back in December) that the theme switched to grey. But I don't think the panel is taking up another theme, it is simply not painting the transparent image.

I didn't like Unity so I disabled it (still installed).
I also removed indicator-me and indicator-messenger via synaptic as I have since Lucid Lynx. I removed the black bubble notifications and removed the shutdown/logout/restart confirmation/countdown prompt w/ a couple of code-hacks I found online as I have since Jaunty Jackalope.

I also tried to change the opacity though an option inside Compiz's "Opacity, Brightness and Saturation". This also made AWN icons transparent so I undid it.

I use the "Glossy P" theme w/ "Snow Apple" icons.

If you guys need any more information, please let me know.

Thank you.

---

### Post by kevinharper on 2011-05-03
:( 15 views in less than a day... Officially "bump"ing this.

I know this issue isn't something that prevents me from using Ubuntu, but it is frustrating me to no end (first because it's fuggly, second because I can't resolve it).

---

### Post by kevinharper on 2011-05-05
:D 34 views... :( No Replies...

BUT VERY GOOD NEWS! ISSUE RESOLVED!

Last night I was automatically logged out of Ubuntu. Boohm, out of the blue the screen flashed black and when color was restored, I was at an Ubuntu login screen.

Previous to the login, I had set the transparency as described on my original post.

After I logged in, I noticed the panel was still transparent. I shutdown for the night and this AM when I turned the laptop on, the panel was transparent.

Don't know what happened. I know there have been a lot of updates in the past few days and I installed every single on of 'em. Maybe something in them fixed the issue.

---

### Post by kevinharper on 2011-05-05
Nope... Never mind.

Problem continues.

---

### Post by cipherboy_loc on 2011-05-05
Isn't transparency and much of the GNOME-panel's config stored in gconf? Try checking which values are set. You could always set a script to change them back (via gconf) to transparent on start up.



Cipherboy

---

### Post by kevinharper on 2011-05-05
Yes... the transparency is controlled in gconfig.

I launched the editor and went to
apps > panel > toplevels > top_panel_screen0 > background

There are values for opacity and background. All values are set correctly.

I opened up a second terminal and executed
gconftool-2 --set --type string /apps/panel/toplevels/top_panel_screen0/background/opacity "35556"

the panel became transparent. The panel also became transparent if I changed the type from gtk to solid. So basically, I have to change either opacity or type values and then change them back to how they were on startup. Almost like I have to force Gnome to retrieve those values.

Grrr... A script seems like a really nice suggestion but I'm hesitant to write one up just for this, though.

---

### Post by kevinharper on 2011-05-05
> **kevinharper said:**
> ...Almost like I have to force Gnome to retrieve those values...

As soon as I said this I realized there is
apps > panel > default_setup

I checked it out and it had not been updated. I manually entered the values from my previous post.

The problem seems to be that the default_setup > top_panel > background settings do not get set if not set manually (command line or gconf-editor).

\o/ No script needed! Thank you for your help!

---

### Post by kevinharper on 2011-05-05
Seems almost like a permissions problem.

Now when I start up, panel is transparent only AFTER I enter my credential into keyring prompt (I have autologon enabled).

If I just cancel through the prompt, the panel stays grey, even if I enter the pwd into the keyring at a later time.

Please note, I only have one account.

:) Good thing I always plan on entering my credentials when prompted to do so.

UPDATE [May 06, 2011]
The problem persisted. Most of the time it would be transparent after logging in, as described above but not always.

And it was frustrating me to no end so I took cipherboy_loc's advise and hacked up a short script that executed at startup.

This is the script:
```
#!/bin/sh
clear
gconftool-2 --set --type string /apps/panel/toplevels/top_panel_screen0/background/type "gtk"
gconftool-2 --set --type string /apps/panel/toplevels/top_panel_screen0/background/type "color"
```

I saved the file as /etc/init.d/ForcePanelTransparency.sh

I then made it executable by running "chmod +x /etc/init.d/ForcePanelTransparency.sh" on a terminal.

And then linked by running "update-rc.d /etc/init.d/ForcePanelTransparency.sh defaults" on a terminal.

---

