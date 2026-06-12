---
title: "KDE 4.3 released!"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-08-04
Looks amazing, can't wait to test it on Karmic!
[http://kde.org/announcements/4.3/index.php](http://kde.org/announcements/4.3/index.php)

Hope it won't take as long as Firefox 3.5 which for some reason is not yet in Karmic.

---

### Post by taavikko on 2009-08-04
Been waiting all day for the packages to build and dependencies to sort out.

I hope that; 
krfb mess is sorted out... where's the vncserver?
samba mess, does it still require chmodding and removing of files to make it work.

and finally, where the support for quicktime in browsers.... :(

---

### Post by Zorael on 2009-08-04
As far as I'm aware Krfb is still a mess. Until it becomes even remotely usable, I'm using x11vnc.

---

### Post by SuperSonic4 on 2009-08-04
I'm just waiting for it to come into the KDEmod repos instead of extra

---

### Post by ruik on 2009-08-04
So let's start waiting for 4.4. :)

---

### Post by wayne_cat on 2009-08-04
KDE is getting better with every version ... and Gnome ...well ... it is a sad story

---

### Post by phenest on 2009-08-04
> **wayne_cat said:**
> KDE is getting better with every version ... and Gnome ...well ... it is a sad story

Gnome is fine. Leave us Gnome users alone. It's not a competition. It's a preference.

---

### Post by wayne_cat on 2009-08-04
> **phenest said:**
> Gnome is fine. Leave us Gnome users alone. It's not a competition. It's a preference.

I'm using Gnome since 6 years .... so what is your point?

---

### Post by MacUntu on 2009-08-04
> **wayne_cat said:**
> KDE is getting better with every version ...

Considering its 4.0 state that's no surprise. :popcorn:

---

### Post by phenest on 2009-08-04
> **wayne_cat said:**
> I'm using Gnome since 6 years .... so what is your point?

The point is to not keep putting Gnome down at every chance. It gets tiresome.

---

### Post by caryb on 2009-08-04
> **phenest said:**
> The point is to not keep putting Gnome down at every chance. It gets tiresome.

I agree horses for courses as the old saying goes! I use Kubuntu but I respect Gnome users too. Heck 1/2 my install is Gnome apps, it's great to have such variety. How many Gnome users use k9copy & k3b gust like how many KDE users use synaptic? etc?


Cary

---

### Post by the8thstar on 2009-08-04
> **phenest said:**
> The point is to not keep putting Gnome down at every chance. It gets tiresome.

Agreed. Please, posters, don't get on with this. I use BOTH Gnome and KDE and they both are very good desktop environments.

---

### Post by wayne_cat on 2009-08-04
I'm not talking about the Gnome applications.

Look at the gnome history

```
Gnome 1 had a "kicker"

[http://www.gnome.org/images/screenshots/19991208-jrb-big](http://www.gnome.org/images/screenshots/19991208-jrb-big)
``````
Gnome 2 has panels:

[http://upload.wikimedia.org/wikipedia/commons/5/5b/Ubuntu.png](http://upload.wikimedia.org/wikipedia/commons/5/5b/Ubuntu.png)

``````
Gnome 3 will have a Gnome Shell

[http://live.gnome.org/GnomeShell/Screenshots](http://live.gnome.org/GnomeShell/Screenshots)

```I just don't have much trust in the Gnome Shell concept.

---

### Post by taavikko on 2009-08-04
One more thing, wish that kubuntu-devel will sort out the multimedia(video) mess.
Why there's kaffeine/dragonplayer side by side?

dumb the dragonplayer... Or was it KDE's upstream choice of video-content?
either way, dumb the other one.

---

### Post by phenest on 2009-08-04
For goodness sake wayne_cat, what is the thread title? Does it say 'What are your thoughts on Gnome'? Stay on topic, please.

---

### Post by wayne_cat on 2009-08-04
> **taavikko said:**
> One more thing, wish that kubuntu-devel will sort out the multimedia(video) mess.
Why there's kaffeine/dragonplayer side by side?

dumb the dragonplayer... Or was it KDE's upstream choice of video-content?
either way, dumb the other one.

dagonplayer is the the default player in kde 4.3

---

### Post by taavikko on 2009-08-04
> **wayne_cat said:**
> dagonplayer is the the default player in kde 4.3

thanks for this clarification.
Then devs should dump the kaffeine.

Yet another issue with kubuntu,
If arora is made default browser, then konq should be demoted.
Clicking any link in KDE will result in konqueror to launch.
(unless you've set links to open in arora)
But I personally prefer to open them based of the content of the link.

---

### Post by wieman01 on 2009-08-04
Please stop arguing about Gnome vs. KDE, otherwise I have do move this thread to "Recurring Discussions". We don't want that. Stay on topic please.

---

### Post by Regenweald on 2009-08-04
> **wieman01 said:**
> Please stop arguing about Gnome vs. KDE, otherwise I have do move this thread to "Recurring Discussions". We don't want that. Stay on topic please.

You would think there would be better things to talk about. but no, same old same old.

---

### Post by wayne_cat on 2009-08-04
The packages are already available for Jaunty:

[http://www.kubuntu.org/news/kde-4.3](http://www.kubuntu.org/news/kde-4.3)

---

### Post by Zorael on 2009-08-04
I wish rekonq was fleshed out enough to be a valid contender for the default browser spot. Obviously it's just the Nokia QtDemoBrowser proof-of-concept browser, but so is Arora. Arora further aims at being portable, so its KDE integration is largely nonexistent - at least currently. (By design it's not trying to integrate.)

Following the rekonq mailing list there have been some nice ideas thrown around, like reusing krunner as an awesomebar-like URL entry (kparts <3). Among the already available plugins there are a few that stand out as just suiting this perfectly. Assuming rekonq shares bookmarks and history with Konqueror, you would already be able to use those krunner plugins right off the bat. The "Konqueror Web Shortcuts" plugin would have to get OpenSearch click-to-add functionality added, and then you basically have an awesomebar done (normal url entry, history, bookmarks, "shortcuts"/accelerators/yubnub), with code shared with the (to-KDE) ubiquitous krunner.

&#7742;oreover, kget? (Is there a kgetpart?)

While rekonq aims toward being lightweight, I'd still prefer a plugins framework, letting people opt-in to get features *they* want without the main codebase growing too large for those that want it as slim as possible. Still a long way to go though, and I fear the Kubuntu default will have long since been decided on and set in stone for a good number of future releases.

---

### Post by buzzmandt on 2009-08-04
I thought we have been running 4.3

I don't get it?

---

### Post by wayne_cat on 2009-08-04
> **buzzmandt said:**
> I thought we have been running 4.3

I don't get it?

we have 4.2.96 on our systems at the moment .. a 4.3 testing version

```
root@macbook:~$ dpkg -l |grep kdebase-runtime
ii  kdebase-runtime                                4:4.2.96-0ubuntu2                         runtime components from the official KDE 4 release
ii  kdebase-runtime-data                           4:4.2.96-0ubuntu2                         shared data files for the KDE 4 base runtime module
root@macbook:~$ 

```

---

### Post by MacUntu on 2009-08-04
> **wayne_cat said:**
> we have 4.2.96 on our systems at the moment .. a 4.3 testing version

You should do an upgrade. :P

```
testuser@biteme:~$ dpkg -l |grep kdebase-runtime
ii  kdebase-runtime                            4:4.3.0-0ubuntu1
ii  kdebase-runtime-bin-kde4                   4:4.3.0-0ubuntu1
ii  kdebase-runtime-data                       4:4.3.0-0ubuntu1
ii  kdebase-runtime-data-common                4:4.3.0-0ubuntu1

```

---

### Post by wayne_cat on 2009-08-04
> **MacUntu said:**
> You should do an upgrade. :P

```
testuser@biteme:~$ dpkg -l |grep kdebase-runtime
ii  kdebase-runtime                            4:4.3.0-0ubuntu1
ii  kdebase-runtime-bin-kde4                   4:4.3.0-0ubuntu1
ii  kdebase-runtime-data                       4:4.3.0-0ubuntu1
ii  kdebase-runtime-data-common                4:4.3.0-0ubuntu1

```

well ... apt-get update is not worth a damn ... if you don't run apt-get dist-upgrade :biggrin:

```
root@macbook:~# dpkg -l |grep kdebase-runtime
ii  kdebase-runtime                                4:4.3.0-0ubuntu1                          runtime components from the official KDE 4 release
ii  kdebase-runtime-bin-kde4                       4:4.3.0-0ubuntu1                          core binaries for the KDE 4 base runtime module
ii  kdebase-runtime-data                           4:4.3.0-0ubuntu1                          shared data files for the KDE 4 base runtime module
ii  kdebase-runtime-data-common                    4:4.3.0-0ubuntu1                          shared data files for the KDE 4 base runtime module

```

---

### Post by Zorael on 2009-08-04
Phaw, aptitude safe-upgrade beats silly apt-get dist-upgrade. ;3

---

### Post by MacUntu on 2009-08-04
Whew, don't start aptitude vs. apt-get - I'm all outta popcorn. :D

---

### Post by georgegerm on 2009-08-04
i cannot wait for kubu karmic...
looks sweet
to bad i cannot configure it myself....

---

### Post by wayne_cat on 2009-08-04
> **georgegerm said:**
> i cannot wait for kubu karmic...
looks sweet
to bad i cannot configure it myself....

not root on your system?


@MacUntu ... really not?

```
root@macbook:~# apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
root@macbook:~#
``````
root@macbook:~# aptitude moo
There are no Easter Eggs in this program.
root@macbook:~#


```:biggrin:

---

### Post by vishalrao on 2009-08-05
> **SuperSonic4 said:**
> I'm just waiting for it to come into the KDEmod repos instead of extra

ah another arch user :) i dont use kdemod, yet to update via pacman though...

btw, kubuntu should really drop all media players and pick one, like VLC (it uses Qt i believe) to avoid some clutter. i dont run dragon/kaffeine whatever anyway. even though kubuntu aim to be "upstream focused" with as little modifications.

same thing about the kmenu/kickoff start menu icon, we should put a nice bling fancy kubuntu circle-of-friends icon in there. currently i have put the circle icon taken from kubuntu-bling svg logo (cut out just the circle by editing the svg xml in inkscape) :)

also, it will be sad if konqueror were replaced with another browser like arora. they should keep the browser but temporarily replace the KHTML engine with WebKit underneath til they can restore KHTML when its more stable.

in fact we should just keep KHTML so more users report bugs and install Firefox as well for those sites that need it. thats what i do.

but that discussion is ongoing in the kubuntu-devel mailing list...

---

### Post by caryb on 2009-08-05
Just in case you get the black screen & mouse only after login do this....

ctl + alt +F1
logon as self
```
sudo apt-get install kubuntu-desktop
```
reboot


All will be good.

Cary

---

### Post by taavikko on 2009-08-05
> **wayne_cat said:**
> 
@MacUntu ... really not?
```
root@macbook:~# apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
root@macbook:~#
``````
root@macbook:~# aptitude moo
There are no Easter Eggs in this program.
root@macbook:~#

```

hmmm.... <-Begin offtopic part->

```
devil@core7:~$ aptitude moo 
There are no Easter Eggs in this program.
devil@core7:~$ aptitude moo -v
There really are no Easter Eggs in this program.
devil@core7:~$ aptitude moo -vv
Didn't I already tell you that there are no Easter Eggs in this program?
devil@core7:~$ aptitude moo -vvv
Stop it!
devil@core7:~$ aptitude moo -vvvv
Okay, okay, if I give you an Easter Egg, will you go away?
devil@core7:~$ aptitude moo -vvvvv
All right, you win.

                               /----\
                       -------/      \
                      /               \
                     /                |
   -----------------/                  --------\
   ----------------------------------------------
devil@core7:~$ aptitude moo -vvvvvvv
What is it?  It's an elephant being eaten by a snake, of course.

```

---

### Post by PGHammer on 2009-08-05
> **taavikko said:**
> thanks for this clarification.
Then devs should dump the kaffeine.

Yet another issue with kubuntu,
If arora is made default browser, then konq should be demoted.
Clicking any link in KDE will result in konqueror to launch.
(unless you've set links to open in arora)
But I personally prefer to open them based of the content of the link.

Konqueror deserves demotion, but that's because Arora is that much better than Konqueror (all the more surprising because Konqueror was ground-up designed for KDE, and Arora is a straight Webkit browser, which is also available for other desktops, including GNOME and Windows).  I have Arora as my *lightweight browser* on my Windows 7 x64 partition, and my preferred browser in Kubuntu Karmic (replacing *Firefox*, not Konqueror, in that role)

---

### Post by PGHammer on 2009-08-05
> **Zorael said:**
> I wish rekonq was fleshed out enough to be a valid contender for the default browser spot. Obviously it's just the Nokia QtDemoBrowser proof-of-concept browser, but so is Arora. Arora further aims at being portable, so its KDE integration is largely nonexistent - at least currently. (By design it's not trying to integrate.)

Following the rekonq mailing list there have been some nice ideas thrown around, like reusing krunner as an awesomebar-like URL entry (kparts <3). Among the already available plugins there are a few that stand out as just suiting this perfectly. Assuming rekonq shares bookmarks and history with Konqueror, you would already be able to use those krunner plugins right off the bat. The "Konqueror Web Shortcuts" plugin would have to get OpenSearch click-to-add functionality added, and then you basically have an awesomebar done (normal url entry, history, bookmarks, "shortcuts"/accelerators/yubnub), with code shared with the (to-KDE) ubiquitous krunner.

&#7742;oreover, kget? (Is there a kgetpart?)

While rekonq aims toward being lightweight, I'd still prefer a plugins framework, letting people opt-in to get features *they* want without the main codebase growing too large for those that want it as slim as possible. Still a long way to go though, and I fear the Kubuntu default will have long since been decided on and set in stone for a good number of future releases.

Arora is an interesting lightweight browser option for *all* its platforms (while I originally ran into it in KDE, I also use it in *Windows* as an IE/Firefox alternative) because it *is* lightweight (and it doesn't use a different plug-in model; it shares the plug-in model of Firefox, which is likely why it functions better than Konqueror, which uses a different model for plug-ins).  I've been using it instead of both Konq and Firefox in Kubuntu, and as an alternative (not default) browser in Windows.

---

### Post by Zorael on 2009-08-05
> **PGHammer said:**
> Arora is an interesting lightweight browser option for *all* its platforms (while I originally ran into it in KDE, I also use it in *Windows* as an IE/Firefox alternative) because it *is* lightweight (and it doesn't use a different plug-in model; it shares the plug-in model of Firefox, which is likely why it functions better than Konqueror, which uses a different model for plug-ins).  I've been using it instead of both Konq and Firefox in Kubuntu, and as an alternative (not default) browser in Windows.
I just wish there was a Karora, if that makes sense. Platform-independent and consistent looks/functionality is one ideal (Arora's), and specific-platform/environment integration is another (rekonq's).

---

### Post by hanzomon4 on 2009-08-06
This is amazing!!!!

---

### Post by meborc on 2009-08-07
> **hanzomon4 said:**
> This is amazing!!!!

what is?

---

### Post by kpkeerthi on 2009-08-07
Congrats to the KDE devs.
> 
... from [http://kde.org/announcements/4.3/index.php](http://kde.org/announcements/4.3/index.php)
The KDE community has fixed over 10,000 bugs and implemented almost 2,000 feature requests in the last 6 months. Close to 63,000 changes were checked in by a little under 700 contributors. 

Thats phenomenal! (I'm much happy with GNOME. Not a KDE fan. Will wait for KDE 4.10)

---

