---
title: "Weird Issues: Karmic Beta+Firefox+Flash=Mouse Buttons Don't Work"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jcsteele on 2009-10-01
Hello All,

  Before I beat my head against the desk any longer trying to solve this problem, I thought I would simply write here to see if anyone else is having similar issues.


  I just downloaded and installed Ubuntu Karmic (9.10) AMD64 onto my new (literally just unpacked it!) HP Xeon Workstation.  Everything is working wonderfully!

However, this is an issue:  Flash videos in Firefox work fine...but I can't use the mouse.  Rollover works in hulu/youtube/etc. but clicking the mouse button does NOTHING.  I can even bring up the "settings" menu with a right click, but I can't modify anything inside of there - the left button doesn't work.

Any ideas?  Obviously, I have tested the mouse - it works perfectly fine everywhere else.  I am also using an NVIDIA Quadro FX video card as well, with the proprietary/binary-only drivers.  Flash was simply installed using the flash available in the ubuntu repos.

Any help would be appreciated...thx.

JCS

---

### Post by danns on 2009-10-01
I am noticing this too.  I have Karmic upgraded from Jaunty on two systems and both exhibit the same behavior.  Mouse buttons rarely seem to work.  On some videos I can get it to move on to the original site the video is on like blib.tv or viddler and the video will play, but I cannot do anything else.  

The right mouse button seems to work though.

---

### Post by dt_ on 2009-10-02
I have the exact same problem -- using the Chrome  browser though.. so it's not a browser issue, more of a plugin or OS related issue I imagine.    Sometimes clicking does work but most of the time it doesn't.. very annoying! :(

---

### Post by nhasian on 2009-10-02
did you install flash from the repos?  or did you get the 64 bit alpha flash plugin from labs.adobe.com?

---

### Post by Lazy123 on 2009-10-02
I have the same problem. In jaunty I had the 64bit plugin that worked well but upgrading to Karmic pulled 32bit version 10.0.32.18 (checked from [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)).

[EDIT]
OK, I removed 32-bit version and downloaded 64-bit version again and the buttons started working, but now Firefox crashes with certain sites. For example if I go to [www.openstreetmap.com](www.openstreetmap.com) and try to edit map it will crash the browser with error: Segmentation fault (core dumped)

---

### Post by Funnnny on 2009-10-02
The button sometimes works:
1. youtube's player, only the player in personally page. The players in video page is unclickable
2. game in facebook, I can click most of the flash game in facebook.
other flash is non-clickable

---

### Post by dt_ on 2009-10-02
> **nhasian said:**
> did you install flash from the repos?  or did you get the 64 bit alpha flash plugin from labs.adobe.com?

got it from labs.adobe.com.

---

### Post by fut21 on 2009-10-02
I have problems with mouse bottens all over firefox. Nothing works, not even in the menues nor the copy/paste funktions.

---

### Post by Leighman on 2009-10-02
I have this problem with Opera too, with flash from the repos.
I find that if you click outside the video before clicking any button,, that seems to work

---

### Post by ljrmorgan on 2009-10-02
Hey guys, I had this problem during the alpha testing on my AMD64. As well as the buttons not working, I also had problems with flash slowing down my browser and sometimes crashing it.

I installed the 64-bit flash using the script found [here]("http://ubuntuforums.org/showthread.php?t=1259102") (at least I think it was from here, otherwise just search the forum for install guides), and I haven't had any problems since then. The buttons have been working, and it seems more stable than the 32-bit version.

Try installing it and see if you still have any problems.

Edit: Fixed the link

---

### Post by Colonel Kilkenny on 2009-10-02
I would suggest skipping scripts like that. 

I had the same problem and it seems that I managed to solve it. Opera found 3 flashplugins (two R32 and one d20). First I removed package flashplugin-nonfree as there was also flashplugin-installer installed. That did nothing, Opera still had 3 plugins to use. Then I just deleted files /usr/lib/mozilla/plugins/libflashplayer.so and /usr/lib/mozilla/plugins/flashplugin-alternative.so

Now I only have /usr/lib/flashplugin-installer/libflashplayer.so and everything seems to be working. It would probably be okay to remove plugin brought by flashplugin-installer instead of the one which is in /usr/lib/mozilla/plugins/. 

Anyway, I'd suggest getting rid of flashplugin-alternative.so and all other unnecessary flash plugins. Of course your mileage may vary. My installation is updated from Jaunty instead of clean install.

edit. Remember that I have Opera and it searches plugins from different places than Firefox which is a mess when it comes to finding & configuring plugins. So these instructions may not work for Firefox (or Chrome, Epiphany, etc.) at all.

Edit #2. Sorry, the problem is back. Ignore all that I just said :)

---

### Post by ljrmorgan on 2009-10-02
Actually, just read the last page of the post I referenced earlier, there is a more recent version [here]("http://ubuntuforums.org/showthread.php?t=1259102") (Sep 2009) (I have now changed the original link too)

The script removes all the old versions of flash for you, and there is a lot of troubleshooting etc. there, so I personally think it's better than just trying to install it yourself.

---

### Post by Colonel Kilkenny on 2009-10-02
> **ljrmorgan said:**
> Actually, just read the last page of the post I referenced earlier, there is a more recent version [here]("http://ubuntuforums.org/showthread.php?t=1259102") (Sep 2009) (I have now changed the original link too)

The script removes all the old versions of flash for you, and there is a lot of troubleshooting etc. there, so I personally think it's better than just trying to install it yourself.

That script just tries to remove some packages, then deletes files and after that tries to manually install flash plugin. It may be suitable for some people but for an example it just assumes that user has Firefox. What about Opera, Epiphany, Konqueror, Chrome, Chromium, Midori, Arora, etc. ?
Okay, it might actually work with those browsers as they usually look for plugins from mozilla folders as well, but this Firefox-centric approach in Ubuntu and community is equally as stupid as IE-centric in Windows.

That script also installs flash for you once. It doesn't keep it updated or anything. So actually it might be worse for normal people who aren't familiar with system files and just want to have up to date plugin.

---

### Post by Amaranth on 2009-10-02
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/141494](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/141494)

---

### Post by dinxter on 2009-10-02
[https://edge.launchpad.net/~sevenmachines/+archive/flash]("https://edge.launchpad.net/%7Esevenmachines/+archive/flash")
should work for all that the repository 32 bit one supports
[EDIT] Though 64 bit has bugs too

---

### Post by ljrmorgan on 2009-10-02
> **Colonel Kilkenny said:**
> That script just tries to remove some packages, then deletes files and after that tries to manually install flash plugin. It may be suitable for some people but for an example it just assumes that user has Firefox. What about Opera, Epiphany, Konqueror, Chrome, Chromium, Midori, Arora, etc. ?
Okay, it might actually work with those browsers as they usually look for plugins from mozilla folders as well, but this Firefox-centric approach in Ubuntu and community is equally as stupid as IE-centric in Windows.

That script also installs flash for you once. It doesn't keep it updated or anything. So actually it might be worse for normal people who aren't familiar with system files and just want to have up to date plugin.

Well, firstly, the subject mentions using firefox, so this ought to be fine. Also, as you said, other browsers will probably look in those folders. I agree about not keeping it up to date, etc. though the thread seems up-to-date, and I imagine it will be updated when a new version comes out. Installing the alpha manually wouldn't keep it up to date either, and I think most people would rather use an alpha that isn't automatically kept up to date than to use a version which doesn't work properly. If they would rather use the automatically kept up to date but broken version, then they wouldn't run the script.

---

### Post by Colonel Kilkenny on 2009-10-02
> **ljrmorgan said:**
> Installing the alpha manually wouldn't keep it up to date either, and I think most people would rather use an alpha that isn't automatically kept up to date than to use a version which doesn't work properly. If they would rather use the automatically kept up to date but broken version, then they wouldn't run the script.

Yes, but in this case the problem apparently is in Compiz. The file you get from repos is probably exactly the same that you get from Adobe (as long as it's the r32 version).

I hope they really realise in launchpad that it cannot be a problem in nspluginwrapper as Opera for an example doesn't have anything to do with the nspluginwrapper. And if everything works okay with metacity then the problem is obviously in compiz. It has to have something to do with window management as flash recognises just fine the first click when I switch the focus to another window and then back to browser with plugin running.

---

### Post by SilverDrake11 on 2009-10-02
Hello, I have the exact same problem. That is, nothing is clickable in flash. For example, I try to watch a youtube video and I can't move the slider or click on HQ or pause the video.

I'm running karmic beta 64bit, and the flash I have is the one that is part of the restricted extras. I prefer not using scripts (im afraid itll make so I cant get any flash updates) or anything like that, so I guess I will have to wait until the flash is updated.

---

### Post by Prometheus7 on 2009-10-03
I too have this issue. It occurs even after using the script.

---

### Post by dt_ on 2009-10-03
That this bug has resurfaced and was originally reported in 2007 makes me a bit sad, haha :D

---

### Post by danns on 2009-10-04
I'm noticing this in Arora in Debian SID.  On both my karmic system and sid I am using Fluxbox on both system so that would rule out compiz too.

---

### Post by Colonel Kilkenny on 2009-10-04
Okay, what else could it be? X? Flash itself? Drivers (I'm using Nvidia 185.18.36)?
I've seen embedded youtube videos that work just fine. Some flash players work also without any problems.

---

### Post by joey-elijah on 2009-10-04
chiming in with "me too". 

Keyboard shortcuts work fine if you're desperate!

---

### Post by jcsteele on 2009-10-05
Well, it's nice to see that I am not the only one.  I reverted to using Jaunty on my nice new shiny HP Xeon Workstation - works wonderfully (flash included)...flash is definitely one of those apps that is required in this day in age...I wish it wasn't so though.

Even on Jaunty though, flash is sometimes quirky (64bit of course), but a lot less so than Karmic.  I do experience problems with firefox slowing down, and sometimes even going non-responsive.

---

### Post by bpickel on 2009-10-07
i know this thread references Firefox specifically however, I was wondering  if anyone has had any luck with Chromium ?   Firefox is working but no Chromium ? They use the same plugin........

---

### Post by Maharifu on 2009-10-07
Hi, I'm having the same problem. I'm using firefox, on 64bit Karmic upgraded from Jaunty.

I noticed that if you right click on the flash application, the options menu pops up. Then, if you left click on the app, the left click works, but only once!!!

EDIT: You do have to left click twice, one for the menu to go away, and another one on the app...

---

### Post by Nirro on 2009-10-07
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

The known workaround is to install an alpha version from adobe site (related to 64bit version)

---

### Post by Prometheus7 on 2009-10-09
The problem does not appear to be the flash (I think that we all have Adobe Flash 10 installed from the Adobe Labs site). Compiz seems to be the problem. When I kill compiz, I am able to interact with no problems. When I bring compiz back, no interactivity. Several others have mentioned this.

---

### Post by gurpal2000 on 2009-10-14
> **Prometheus7 said:**
> The problem does not appear to be the flash (I think that we all have Adobe Flash 10 installed from the Adobe Labs site). Compiz seems to be the problem. When I kill compiz, I am able to interact with no problems. When I bring compiz back, no interactivity. Several others have mentioned this.

Is something like this likely to be fixed before go-live ? for some Flash is entirely necessary to be working properly (eg. web designers)

---

### Post by Amaranth on 2009-10-14
It does happen for some people with metacity (and other WMs) which points to either a flash problem or a change in the libraries flash uses (GTK+, X, etc).

---

### Post by null_pointer_us on 2009-10-19
This problem appeared on my computer this morning, possibly after an update to firefox yesterday. Specifically, the **right** mouse button would not work anywhere inside the firefox window. I had the 64-bit flash 10 alpha from adobe's site. Redownloading the same plugin (into /home/*your-user-name*/.mozilla/plugins) appears to have fixed it (for now).

EDIT:

fcomp says the two plugins (old and new) are identical:

```
****@****:~/Desktop$ fcomp -BIN libflashplayer-old.so libflashplayer.so
Files "libflashplayer-old.so" and "libflashplayer.so" are identical
```

Now I'm really confused. All I replaced was this one file. How could that have fixed anything?

---

### Post by gurpal2000 on 2009-10-19
> **null_pointer_us said:**
> This problem appeared on my computer this morning, possibly after an update to firefox yesterday. Specifically, the **right** mouse button would not work anywhere inside the firefox window. I had the 64-bit flash 10 alpha from adobe's site. Redownloading the same plugin (into /home/*your-user-name*/.mozilla/plugins) appears to have fixed it (for now).

Do you have to uninstall anything else first? do you just get the adobe beta and put into the location you mention? thx

---

### Post by null_pointer_us on 2009-10-19
> **gurpal2000 said:**
> Do you have to uninstall anything else first? do you just get the adobe beta and put into the location you mention? thx

No, I didn't need to uninstall anything, but your system may be different.

It looks like package flashplugin-installer will do things a little more safely, though. I recommend trying that first. Your browser will need to be closed and restarted before it notices the plugin.

FYI, go to this address in your browser to see which plugins are active:

```
about:plugins
```

Note that it wasn't an updated plugin that solved my problem; it was reinstalling the same version. So maybe firefox has some sort of plugin-related cache or database that got messed up. If this guess is correct, uninstalling the plugin, opening and closing the browser, and then reinstalling the same plugin should fix this mouse button issue.

---

### Post by stereo_1999 on 2009-10-20
I have this problem with flash too, but I found out that if i hold down the middle or the right mouse button and click the left mouse button i can click the buttons....Its annoying but at least it will work until the problems fixed.

---

### Post by danatup on 2009-10-22
> **stereo_1999 said:**
> I have this problem with flash too, but I found out that if i hold down the middle or the right mouse button and click the left mouse button i can click the buttons....Its annoying but at least it will work until the problems fixed.

I can confirm this behavior and workaround.
uname -a
Linux cu-nim 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

Plugin version as installed from the karmic repo:
"You have version 10,0,32,18 installed"
as given by [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

---

### Post by Eversmann on 2009-10-22
Same problem here, hope it gets resolve before release date.

---

### Post by tychocity on 2009-10-23
same problem here amd64 flash 64 bits

---

### Post by DodgeV83 on 2009-10-23
> **Prometheus7 said:**
> The problem does not appear to be the flash (I think that we all have Adobe Flash 10 installed from the Adobe Labs site). Compiz seems to be the problem. When I kill compiz, I am able to interact with no problems. When I bring compiz back, no interactivity. Several others have mentioned this.

Agreed.  I hope this is fixed before official release.  Many people use Compiz and they will simply see this as "Ubuntu sucks!" instead of "Compiz sucks!"  I almost left for Windows until I realized disabling Compiz brings full flash functionality back.

---

### Post by Skerit on 2009-10-27
So, any word on this?

---

### Post by bkuhns on 2009-10-27
I'm also having this issue on my new Dell Inspiron 1545 :(

---

