---
title: "Playing DVDs in Totem on Intrepid Beta"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2008-10-03
I just grabbed the beta ISO and have been doing some testing. After installing libdvdcss2 and all that jazz, I still am unable to play DVDs in Totem the way I could in Hardy. Sometimes it returns the message "could not connect stream", sometimes it crashes, sometimes it just sits there, not having crashed but also not having played the movie. I installed vlc player and everything worked just fine. Totem does play regular video files. 

Anyone else having the same problem?

---

### Post by Ewingo401 on 2008-10-03
I had the same issue with totem.  I installed xine and it worked fine though.

---

### Post by UbuWu on 2008-10-03
Did you open a bug/look for an existing bug report?

---

### Post by UbuWu on 2008-10-03
Probably this bug:
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765)

---

### Post by mc4man on 2008-10-03
If you want a totem player that works go 
```
sudo apt-get install totem-xine
```

followed by 
```
sudo update-alternatives --config totem
```

choose 2 and you'll be set.

---

### Post by Nullack on 2008-10-04
I dont recommend using Xine because it has problems with other multimedia types that gstreamer handles no problems.

With gstreamer dvd playback its coming together as per the bug report. The issue will be if resindvd gets in or the older method user in hardy is done.

---

### Post by mc4man on 2008-10-04
> I dont recommend using Xine 
The Op was is wanting to play dvds with totem and in that use totem-xine is clearly better.(certainly ATM ) If there was or is a reason to leave totem-gstreamer as the default totem player, then fine, either don't  use update-alternatives or change it back.

You can leave totem-gstreamer as the default totem player and quite easily set totem-xine as the default choice for dvd playback. (or have both versions available as choices,  from preferences -> media -> Dvd Video (autoplay), and / or the right click 'open with' on the dvd movie icon.

---

### Post by steeleyuk on 2008-10-04
Anybody got any idea when the DVD navigation is going to make it into a release of Gstreamer? I know the plugin has been worked on but haven't seen anything about it being released to the general public.

---

### Post by damoxc on 2008-10-04
There are updated packages in that bug report that apparently have working dvdnav. Have yet to try them for myself.

---

### Post by | MM | on 2008-10-04
An interim option is also VLC.  Currently working very nicely on my system.

---

### Post by Nullack on 2008-10-04
Intrepids vlc build uses an old ffmpeg and as a result isnt as good as what it could be.

---

### Post by Gina on 2008-10-05
I couldn't get a DVD-video to play in Intrepid with totem-gstreamer or totem-xine or even kaffeine - which generally works when others don't.  I had to go back to Hardy to play it.  DVD is 8mm DVD-RW (JVC) formatted as DVD-video and finalised, from my camcorder.

---

### Post by rockin_goliath on 2008-10-05
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765")

That is the bug entry that was mentioned earlier. It looks like some good people are on this issue. Hope to see it fixed by the final release.

---

### Post by amano on 2008-10-05
At the moment VLC is the only option that works for me. Even (Gnome) Mplayer refuses to play any DVD.

Does Mplayer work for somebody?

---

### Post by mc4man on 2008-10-05
As far as the usual dvd media players, all seem to perform well with a few minor issues. (don't consider totem-gstreamer a dvd video player

Totem-xine works fine (needs libxine1-ffmpeg

Vlc works fine  (with recent change to the %f launch command, calling vlc from a video_ts dir. the exception

mplayer, gmplayer work well (except with dvd-protect titles with repo ver.

Smplayer and gnome mplayer front ends also work fine 

kaffeine works okay in ubuntu as long playback is initiated from inside the gui (needs the dvd device to be set to /dev/scd[COLOR="Red"]x[/COLOR], right click on the icon or autoplay are a no go

xine-ui works fine also

as far as ones to set for autoplay (if desired) totem-xine and vlc work fine as is. 
Gmplayer and xine-ui need a 2nd .desktop with specific launch commands

Lack of playback or quality of such would be due to same causes as previous ubuntu releases.

@ amano
can you describe what happens, error mess., pop up, partial playback?

---

### Post by Nullack on 2008-10-05
An SVN compile of mplayer together with an svn compile of the gnome mplayer frontend is the most powerful multimedia solution available on Linux. Together with libdvdnav / read DVDs work well. it doesnt work for you, its user error.

Xine only allows for DVD menu playback, but it comes at the expense of other multimedia features breaking over gstreamer.

Intrepid's VLC doesnt work fine because it uses an outdated version of ffmpeg.

---

### Post by mc4man on 2008-10-06
> Xine only allows for DVD menu playback, but it comes at the expense of other multimedia features breaking over gstreamer.

you do realize that some of the people in this post and others are looking to play back DVD MOVIES using a player of either their choice or in some cases any player that works. (for them 
Or is it your contention that installing and using any of these other "nonsupported" players **for dvd playback** somehow "breaks" the install?

> An SVN compile of mplayer together with an svn compile of the gnome mplayer frontend is the most powerful multimedia solution available on Linux. Together with libdvdnav / read DVDs work well. 


I can agree that building your mplayer is the better way though again for many people it's unnecessary and or something they don't want to do. As far as a front end that's a matter of choice. I seriously doubt that the majority of posters in the next several weeks are looking for "the most powerful multimedia solution available on Linux", they just will want their media to play back and look and sound good. 

> it doesnt work for you, its user error.

As I mentioned all the players worth using work, so that could be true or it may be any number of other causes. Stating blanket facts or opinions isn't all that useful in solving local issues.

Note ; Gnome mplayer also works fine for dvd playback as long as your not using the the 'open with dvd menus' option with the repo ver. of mplayer. 
Smplayer also has no issues of note. (check  website for updated versions

---

### Post by Nullack on 2008-10-06
mc4man, show me where users can get svn compiles of mplayer for ubuntu with the external svn compile of the dvd menu library so that people dont need to compile their own, including compilation with specific tuning for their particular cpu. Then I wont need to compile like you claim....

If amano cant get mplayer working under that context, it is user error.

Anyway slomo has brought in the new gstreamer base binaries which will resolve the current issue with totem. Its a shame about the resindvd revision in Intrepid but hopefully itll be an unsupported update post production once resindvd has new releases.

---

### Post by rockin_goliath on 2008-10-06
We need to focus on getting totem-gstreamer working with DVDs, because that is what is ultimately going to ship with the final release. I encourage everyone to head over to the Launchpad page mentioned above and post their experiences with totem-gstreamer there so developers have as much as possible to work with.

Totem-gstreamer *should* be able to play DVDs, at least without menus, so let's run with that. I understand from the bug report page at Launchpad that there have been some updates to the Gstreamer base package. Has anyone else tried them?

---

### Post by Nullack on 2008-10-06
I agree goliath. Testing the latest updates on totem gstreamer results in errors and no DVD playback.

---

### Post by finite9 on 2008-10-08
this is a bit disheartening.  Totem has been able to playback DVDs with libdvdcss2, but excluding menus and navigation, since dapper drake.  That menus and or navigation still does not work with gstreamer indicates that development is ultra slow on gstreamer or this issues is like last on the list of things to do.  That simple dvd playback with totem-gstreamer is now broken is a catastrophe.  It's like 2 steps backwards.

By the way, I came to this thread, because I make home videos and I create the dvd structure with dvdauthor and then make an iso with mkisofs, but totem-gstreamer refuses to play them, whereas VLC and mplayer both play the ISO just fine (other DVD ISOs work fine in Totem).

Anyone got any tips?

I create with the following commands:

```
ffmpeg -i $infile -threads 2 -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd /tmp/$outfile

         dvdauthor -o /tmp/DVD/ -t --video=720x576+pal+16:9 --audio=ac3+en --file=/tmp/$outfile

         dvdauthor -o /tmp/DVD/ -T

         mkisofs -dvd-video -o "$infile2"iso /tmp/DVD/
```

---

### Post by zombiepig on 2008-10-08
> **finite9 said:**
> this is a bit disheartening.  Totem has been able to playback DVDs with libdvdcss2, but excluding menus and navigation, since dapper drake.  That menus and or navigation still does not work with gstreamer indicates that development is ultra slow on gstreamer or this issues is like last on the list of things to do.

DVD playback is messy - the company that handles the majority of gstreamer development, Fluendo, is unable to work on dvd navigation development because of legal obligations. So, it's left to volunteer coders to get this up to scratch :(

---

### Post by Gina on 2008-10-08
I have a camcorder that uses 8cm DVDs and I use the DVD-Video format and they play fine on DVD players. In Ubuntu I find I have to play DVDs as root. I get a message "You don't have permission..." But by invoking Totem (GStreamer) as root (or using **gksu nautilus**) they will play.

As an aside... I'm looking for an editor app that will take DVD-Video off my camcorder DVDs to edit.

---

### Post by finite9 on 2008-10-08
> **Gina said:**
> I have a camcorder that uses 8cm DVDs and I use the DVD-Video format and they play fine on DVD players. In Ubuntu I find I have to play DVDs as root. I get a message "You don't have permission..." But by invoking Totem (GStreamer) as root (or using **gksu nautilus**) they will play.

As an aside... I'm looking for an editor app that will take DVD-Video off my camcorder DVDs to edit.

I tried starting a shell with ```
sudo bash
``` and then starting totem and playing the file but get the following:

```
root@everest:~/movies# totem legoclip.iso

** (totem:3387): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
** Message: Error: Could not open resource for reading.
vcdsrc.c(421): gst_vcdsrc_start (): /play/source:
system error: Inappropriate ioctl for device
```

Seems like bigger problems with dbus integration than simple permissions

---

### Post by philinux on 2008-10-08
Add your errors to the bug report.
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/260765)

---

### Post by finite9 on 2008-10-09
its not the same bug, as the bug you refer to is about playing ISO DVD copies with resindvd, but my home-made ISO files made from mpg files have never played in totem, so I created a new bug: Bug #280664.

---

