---
title: "Nomachine (nx) problem in Maverick (10.10)"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by mhjacks on 2010-10-07
Hi everyone,

I use the nomachine thin client tools ([www.nomachine.com](www.nomachine.com)) and have noticed this issue using both the nomachine "free edition" .deb and the neatx-server deb from the freenx-team PPA.

My server (the nx server) is amd64.

Under gnome only, on the most recent Maverick, the nomachine Windows client does not display window decorations (borders and controls).  In KDE the window controls display just fine.  Using the Linux version of the nx client the window borders display just fine in gnome.

Does anyone have any ideas?

Thanks

---

### Post by simonhang on 2010-10-08
Yes, I have tried the exactly same thing. Looks like the nomachine nx client is not support some of the X extension.

Workaround:

You can select the following option in nomachine NX client, and the display will become normal again.

Display settings – Performance

    * Disable the render extension


I was also going to try use no visual effects. But no luck so far.

- Simon

---

### Post by mhjacks on 2010-10-08
Thanks, that worked perfectly.

---

### Post by sylaan on 2010-10-14
I have the same problem but unfortunately disabling the Render Extension does not help in my case :(

---

### Post by foobar0104 on 2010-10-14
Hi,

the "disable the render extension" does help with the window decorations. However now 
 1. window updates are really slow (but I could live with that)
 2. nautilus crashes after literally every 2nd click

Any other ideas?
I start to regret to have upgraded.

Markus.

---

### Post by florentnicoulaud on 2010-10-15
Same here, no improvement when changing the settings (even 'Disable the render extension').
Have tried to clean my home directory but no luck either.

---

### Post by nshupe on 2010-10-16
Thanks for the fix.  Worked like a charm for me.

---

### Post by damirl on 2010-10-18
I'm experiencing the same issue with Nautilus crashing when trying to open a file or folder by double clicking. The issue doesn't occur when using right-click/open with or when expanding the contents of the folder by clicking the little arrow next to it.

Thanks

---

### Post by foobar0104 on 2010-10-19
> **damirl said:**
> I'm experiencing the same issue with Nautilus crashing when trying to open a file or folder by double clicking. The issue doesn't occur when using right-click/open with or when expanding the contents of the folder by clicking the little arrow next to it.

Thanks

Yep - exactly. It somehow has to do with user settings. If I create a brand new user, all these issues are gone.
Wondering what setting causes these problems.

M.

---

### Post by foobar0104 on 2010-10-20
> **foobar0104 said:**
> Yep - exactly. It somehow has to do with user settings. If I create a brand new user, all these issues are gone.
Wondering what setting causes these problems.

M.

Very very strange - but I changed the theme for my user (from ambience to "Human Clearlook") and now all segfaults are gone.
I open the gedit "open file" dialogue and also nautilus doesn't crash any more on keyboard strokes.

M.

---

### Post by anf on 2010-10-21
The "Disable the render extension" work-around worked for me too, but this problem is not exactly solved.  Presumably, it would be more efficient to use the render extension, so it would be nice to know what the problem really is.

---

### Post by quoderat on 2010-10-23
Problem is definitely not solved. Disabling the render extension makes the window decorations return, but depending on the theme, it causes many apps to crash.

---

### Post by hellmet on 2010-11-03
> **anf said:**
> The "Disable the render extension" work-around worked for me too, but this problem is not exactly solved.  Presumably, it would be more efficient to use the render extension, so it would be nice to know what the problem really is.
This workaround doesn't work for me either. I've no special effects enabled.  This is "UNSOLVED".

---

### Post by sylaan on 2010-11-03
Another workaround I found, after reading some other threads, is to change the XServer config to use 16bit color depth, in the "Screen" section of xorg.conf. 

If I do this, then I see the decorations when I log in via NX. The bad thing is that when I log in locally, the quality is not so great and compiz is disabled, emerald is not working either. 

So yes, I would also say this is unsolved.

---

### Post by birty on 2010-11-07
To disable the render extension you have to close any existing sessions, then disable the extension and start a new session otherwise the setting does nothing

---

### Post by venik212 on 2010-11-08
My problem is a little different-- something (a recent update?) has made it impossible for me to log in using NX from Windows to my Ubuntu/gnome 10.10 (64 bits).  I am told of an error having to do with server configuration.  Updating the NX server, client and node did not make any difference.

===================================

SOLVED: my .Xauthority file was corrupted.  I deleted it and rebooted, and all is well.

---

### Post by birty on 2010-11-08
> **venik212 said:**
> My problem is a little different-- something (a recent update?) has made it impossible for me to log in using NX from Windows to my Ubuntu/gnome 10.10 (64 bits).  I am told of an error having to do with server configuration.  Updating the NX server, client and node did not make any difference.
the actual error message and the relevant parts of your logs may be a bit more helpful

---

### Post by Speed_D on 2010-11-12
Metacity's latest revision had some significant changes that cause problems with nx.

Downgrade metacity to 1:2.30.1-0ubuntu1 and then nx will work properly again with render extensions.

Disabling render extensions causes a lot of apps to become unstable, so I don't view that as a good workaround.

To downgrade, add the lucid lines back into your apt sources.list file.  apt-get update and then install the specific version (see apt-get manpage).  Then do a package hold on it.

---

### Post by rdoolen on 2010-11-12
Nomachine released a fix for the Windows client. This fixed things for me:

[http://www.nomachine.com/news-read.php?idnews=326](http://www.nomachine.com/news-read.php?idnews=326)

---

### Post by iluxa1 on 2010-11-18
After Nomachine NX client update window updates are still really slow.

---

### Post by florentnicoulaud on 2010-11-19
Another kind of workaround.
I installed xfce and use it for my remote sessions through nx.
No problem at all, fast and stable.

---

### Post by lz1dsb on 2011-04-20
> **rdoolen said:**
> Nomachine released a fix for the Windows client. This fixed things for me:

[http://www.nomachine.com/news-read.php?idnews=326](http://www.nomachine.com/news-read.php?idnews=326)

Thanks a lot for this hint. I installed the new NX Client version. The window manager issue is resolved. The windows are refreshing a bit slowly though. I think I can live with that.


Regards,
Boyan

---

