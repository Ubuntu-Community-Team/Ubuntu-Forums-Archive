---
title: "This audio stream stops..and refuses to play."
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-01-18
[http://kscs.com/article.asp?id=785764](http://kscs.com/article.asp?id=785764)

Anyone know why?  I have the restricted extras and all the gstreamer tools installed.

---

### Post by dino99 on 2010-01-18
> **sox fan Matt said:**
> [http://kscs.com/article.asp?id=785764](http://kscs.com/article.asp?id=785764)

Anyone know why?  I have the restricted extras and all the gstreamer tools installed.

i think it's due to rodeo time  :P

be carefull : this site immediatly freeze Firefox and all the system. :frown:

---

### Post by sports fan Matt on 2010-01-18
The rodeo is VERY popular...We have a whole area called the "stockyards"..it's a very neat area.  

Well, I may have to call up KSCS and inform them of this.  Or at least let one of the DJ'S know.  Thanks for looking into it.

---

### Post by cariboo on 2010-01-18
I would suggest calling the management, as most DJ's have no say about what and how things are done.

---

### Post by sports fan Matt on 2010-01-18
I just sent an email to Citadel (their company).  If UI get a response, i'll post it.

---

### Post by mc4man on 2010-01-18
I don't think it's the station as it works fine in karmic's firefox.

In lucid if you click on the little white arrow -> open in movie player that does work 
As does directly entering the url into a player like vlc, mplayer ect. or enter the url into firefox and choose application to open

```
mmsh://citadelcc-kscs-fm.wm.llnwd.net/citadelcc_KSCS_FM?MSWMExt=.asf
```

So atm the issue seems to be with lucid's firefox itself

---

### Post by gradinaruvasile on 2010-01-18
> **sox fan Matt said:**
> [http://kscs.com/article.asp?id=785764](http://kscs.com/article.asp?id=785764)

Anyone know why?  I have the restricted extras and all the gstreamer tools installed.

It just works in Chromium... It seems it uses the totem plug-in.

---

### Post by dino99 on 2010-01-18
> **mc4man said:**
> I don't think it's the station as it works fine in karmic's firefox.

In lucid if you click on the little white arrow -> open in movie player that does work 
As does directly entering the url into a player like vlc, mplayer ect. or enter the url into firefox and choose application to open

```
mmsh://citadelcc-kscs-fm.wm.llnwd.net/citadelcc_KSCS_FM?MSWMExt=.asf
```

So atm the issue seems to be with lucid's firefox itself

i was using Karmic32 when freeze happened, had to kill Firefox process as nothing else work

---

### Post by philinux on 2010-01-18
> **sox fan Matt said:**
> [http://kscs.com/article.asp?id=785764](http://kscs.com/article.asp?id=785764)

Anyone know why?  I have the restricted extras and all the gstreamer tools installed.

Works fine in karmic.

---

### Post by mc4man on 2010-01-18
checking out several other mms streams (that all play fine in karmic/firefox/totem-mozilla ), none will in lucid except if opening in totem if the option is present
And all will play directly in players as mentioned.

There seems to also be some other breakdowns in the firefox/totem-mozilla plugin, which for the most part works flawlessly in karmic ( there's always exceptions to something

---

### Post by sports fan Matt on 2010-01-18
So if I were to try mplayer, it could be an alternative?

---

### Post by sports fan Matt on 2010-01-18
it is a no go with mplayer as well.  I agree with mcman.  In Karmic is operated as is expected.  Mplayer just stops and quits as well.

---

### Post by mc4man on 2010-01-18
> So if I were to try mplayer, it could be an alternative? 
possibly though not the gecko-mplayer with it's default settings

As a test, this works
```
mplayer mmsh://citadelcc-kscs-fm.wm.llnwd.net/citadelcc_KSCS_FM?MSWMExt=.asf
```

This doesn't
```
gnome-mplayer mmsh://citadelcc-kscs-fm.wm.llnwd.net/citadelcc_KSCS_FM?MSWMExt=.asf
```

The error (seen with a -v option) is the same as when trying to play any file with smplayer
> ERROR: Unknown option on the command line: -***
ERROR: Error parsing option on the command line: -***


What you can do for gnome-mplayer is open the preferences and disable the a_s_s support under subtitles
Then the gecko plugin may work

As far as smplayer see[ here]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/508561") (bug  is not yet been confirmed - hint

edit 
if you try the gecko-plugin do remove the mozilla-totem one

---

### Post by Ibidem on 2010-01-18
The site is using .asf (a MS proprietary audio/video format); allegedly kmplayer can handle that.  See [here]("http://ubuntuforums.org/showthread.php?t=1346779").
That is a little old, but it's the first I found.

Ibidem

---

### Post by mc4man on 2010-01-18
While atm opening in a player seems better - 
If you install the gecko-mediaplayer plugin, remove the totem-mozilla plugin and edit the pref. of gnome-mplayer as noted than that station, ( and a few other mms streams will work from firefox

( though it does take about 15 secs for the cache to fill. ( totem-mozilla, when working is faster

so the issue atm is with the mozilla-totem plugin ( which I prefer myself, as seen here (karmic) with 'in  chrome browser' playback -( the same 'in browser' also with firefox
[http://ubuntuforums.org/showthread.php?p=8683448#post8683448](http://ubuntuforums.org/showthread.php?p=8683448#post8683448)

screen of lucid/gecko/station in question (mmsh stream

---

