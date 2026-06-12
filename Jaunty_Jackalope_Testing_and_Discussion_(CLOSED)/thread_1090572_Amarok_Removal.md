---
title: "Amarok Removal?"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jimbo99 on 2009-03-08
I wrote a lengthy write up some time ago about amarok 2.  I wasn't impressed and still am not.  I just installed jaunty off the kubuntu dvd iso.  I want to remove amarok 2. I would like to install the old amarok instead.

The new amarok is so far off base that I just can't see it gaining wide appeal.  The author was extremely arrogant.

Any simple procedure for removing Amarok 2 and replacing it with 1.4?

---

### Post by bapoumba on 2009-03-08
Moved to Jaunty.

---

### Post by Elfy on 2009-03-08
There are a couple of ppa's in here, post #21 and #36 [http://ubuntuforums.org/showthread.php?t=1084971](http://ubuntuforums.org/showthread.php?t=1084971)

I used one yesterday and then today put Amarok2 back.

---

### Post by dentaku65 on 2009-03-08
> **forestpixie said:**
> There are a couple of ppa's in here, post #21 and #36 [http://ubuntuforums.org/showthread.php?t=1084971](http://ubuntuforums.org/showthread.php?t=1084971)

I used one yesterday and then today put Amarok2 back.

...and why?

---

### Post by hockeyhead019 on 2009-03-08
i agree with you that amarok 2 isn't real great but i'm gonna stay with it to report bugs and try and make it better but the answer you are looking for is already posted haha in those threads

---

### Post by Elfy on 2009-03-09
> **dentaku65 said:**
> ...and why?

because I wanted to

---

### Post by dentaku65 on 2009-03-09
> **forestpixie said:**
> because I wanted to

Thanks for your answer.

But I would like to know a little bit better and in the sense of the thread (or, lets say, for everyone that reads here) which differences you get in Jaunty between the two versions and if your "final" choice belongs stability, performance, environment or just personal pleasure.

I just report that for me Amarok 1.4 is really far superior than Amarok 2 not only as a player but as a app in general.

But maybe this my choice is incorrect for Jaunty; I was asking you before something to report and wasn't "malicious" post.

---

### Post by Elfy on 2009-03-09
> **dentaku65 said:**
> Thanks for your answer...

OK - I started using Amarok2 in Intrepid, it took a while for me to get on with it - but I did. The features that I preferred Amarok1.4 for boiled down simply to it's playlist management - I use long shuffled playlists resuming from last played tune and I never got banshee/exaile/rhythmbox to work satisfactorily for me.

I then tried Amarok2 - yes it's different and crucially for me at the time it's playlist management was changed - I went back to Amarok1.4 in Intrepid.

I installed jaunty and with it Amarok2 - I had some issues with it at the time which meant that I couldn't use it [http://ubuntuforums.org/showthread.php?t=1066687](http://ubuntuforums.org/showthread.php?t=1066687)

So I have then been flip flopping between banshee/exaile/rhythmbox which I never got to work with my long shuffled playlists and cruciall - so at this point - other than the fact that amarok wouldn't work - all 4 players would leave me without my playlists resuming.

I got used to that fact - eventually

So eventually (I know not when) some update left amarok2 working as it should, so I installed it - always wanting to return to playlist management as it was in 1.4 - obviously something that isn't going to happen.

I then found the thread I linked to in this thread earlier and removed Amarok2 and installed Amarok1.4 - purely to get the playlist shuffle/resume I craved - but by this time I found that after being forced to use players without that ability it was no longer as important to me and I now preferred the look of version2 to 1.4.


Edit - just restarted amarok and it has conveniently forgotten yesterdays play list again and now won't start properly, I give up ...

---

### Post by cl333r on 2009-03-09
Just installed daily build of Jaunty and Amarok installs but can't start:
> 
fox@fox-desktop:~$ amarok
amarok(4426) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
amarok(4426) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
<unknown program name>(4425)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 


---

### Post by cl333r on 2009-03-09
Amarok starts ok after renaming /usr/share/nofity_osd to /usr/share/notify-osd as stated by chrisccoulson at
[http://ubuntuforums.org/showthread.php?t=1087402](http://ubuntuforums.org/showthread.php?t=1087402)

---

### Post by jimbo99 on 2009-03-09
How does this exchange help me remove Amarok 2?

I want to remove Amarok because it is, in my opinion, the wrong direction for it to take.  It is also buggy as hell.  I wrote a lenghty write up about it about 2 months ago, or rather, right after the official release.  It is just as bad and they haven't adjusted anything to make it work the way I want.  I'd much rather the old Amarok.

I was critical of KDE 4.x and disliked the idea of the desktop in a window.  They have given us the choice now.  That makes KDE a worthwhile desktop manager for me, though I would like to have the traditional desktop metaphor the default.

But Amarok is essentially way out in left field.  They have lost their way in my opinion.  You can probably read my write up if you look for my post on ubuntuforums.org.

I simply want to rid my machine of it and go back to the original which is/was very nice and capable.

---

### Post by Elfy on 2009-03-09
> How does this exchange help me remove Amarok 2?Did you read the posts I linked in post #5? This exchange followed the on form a post with the information you needed.

```
sudo apt-get purge amarok
```

Then add one of the ppa's and reinstall - check with those ppa's what you need to install.

---

