---
title: "64bit flash player: complaint and a fix"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jim March on 2009-08-15
For some reason Karmic's repos want to give you 32bit flash along with nspluginwrapper.  The results stink - lots of Firefox doing the "gray pause", sometimes the flash player crashing outright.

I've installed a real 64bit release-code flash player from Adobe and it's working great on a fresh install of Karmic Alpha4/64bit.  Here's what I did to make it run:

1) Get rid of any existing flash-crap at the command line:

> sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash nspluginwrapper swfdec-mozilla


2) Go get the real 64bit flash player:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

***Warning: for some reason this is actually a pain in the butt to even find.  Adobe's official flash download site doesn't include 64bit code for some reason, even though this is release gold stuff (not beta or even RC).  That suggests Adobe may not intend to support Linux 64bit?***

3) Unpack it:

> tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

4) Put the new player into the right place:

> 
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

NOTE: if there's an error there, make sure that directory exists...but if you had already put in Ubuntu's suggested flash player from the repos (or possibly Gnash) it will already exist.

Done!  Restart Firefox, Flash will be about as good as it ever gets :).

Sidenote on Gnash:

Prior to going this route I tried Gnash for a bit.  It's come a LONG ways, actually works fine for Youtube, but it fails on too many other things.  It's not ready yet for me, but GO GUYS GO!

---

### Post by phenest on 2009-08-16
> **Jim March said:**
> ...even though this is release gold stuff (not beta or even RC).

Version 10.0.32.18 is an alpha released on 30/7/09.

---

### Post by Jim March on 2009-08-16
OOPS!

Oh crap...OK, so where's the release code?  Or at least something later?

---

### Post by phenest on 2009-08-16
That *is* the latest.

---

### Post by Jim March on 2009-08-16
Ah.  That explains much.

Well still, this is the best Flash setup I've ever had running in Linux.

---

### Post by eyelessfade on 2009-08-16
> **phenest said:**
> Version 10.0.32.18 is an alpha released on 30/7/09.

and? Its still a thousand times better then stiching the 32-bit version togetther with the duct-tape called nspluginwrapper.

If flash-32bit is release, then it became pre alpha when combined with nspluginwrapper. In my book alpha > exprimental

---

### Post by Harper45 on 2009-08-16
thanks for sharing this great information..

---

### Post by Jim March on 2009-08-16
Yeah, I mean...I was able to figure out that this was the last one issued.  I thought it was release code because I recall reading about a Flash64 alpha a hell of a while back.  I just assumed they must have got it right by now.

Silly me.

Still, this does work.

---

### Post by eyelessfade on 2009-08-16
alpha is just a name. Look at google they had gmail in beta for 5 years. Was it stable Yes. And look at Windows Vista (just because I had one vista experience last week). Its been in stable for 3 years and its still not anything near stable.

Adobe have alpha label on x64 because they won't release a "stable" x64 to gnu/linux before windows and mac.

---

### Post by martijntje on 2009-08-16
I completely agree the 64-bit flash plugin is way better then the 32-bit with nspluginwrapper.

IMHO it should be shipped with Karmic.

---

### Post by xebian on 2009-08-16
The 64-bit version is FireFox code compiled in 64-bit.
The 32-bit version is FireFox code compiled in 32-bit.

Just like the 64-bit Ubuntu is to the 32-bit Ubuntu.

---

### Post by zenarcher on 2009-08-16
> **phenest said:**
> Version 10.0.32.18 is an alpha released on 30/7/09.

Looking here, [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) the latest version released was June 30, 2009.

Cheers,
zenarcher

---

### Post by xebian on 2009-08-16
> **zenarcher said:**
> Looking here, [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) the latest version released was June 30, 2009.

Cheers,
zenarcher

```
Update: .. an alpha refresh of 64-bit Adobe Flash Player 10 for Linux operating systems 
was released on 7/30/09 and is available for download. T...
```

---

### Post by eyelessfade on 2009-08-16
from [http://labs.adobe.com/technologies/flashplayer10/faq.html]("http://labs.adobe.com/technologies/flashplayer10/faq.html")

> 
We expect to provide native support for 64-bit platforms in an upcoming major release of Flash Player. Windows, Macintosh and Linux players will ship at the same time.

So until they start working on a Windows and Mac port, there will be no final 64-bit plugin for *NIX at least not in name

---

### Post by phenest on 2009-08-16
> **eyelessfade said:**
> So until they start working on a Windows and Mac port, there will be no final 64-bit plugin for *NIX at least not in name

If that's true, then maybe we should decide if it's ready for release in Ubuntu rather that waiting for Adobe. And seeing as so many users have confirmed it to be stable, then perhaps we should petition Canonical to replace the 32 bit in Karmic.

---

### Post by Jim March on 2009-08-16
> Looking here, [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) the latest version released was June 30, 2009.

Yeah, that's the code I'm using right this moment.  Like I said: BEST Linux flash I've ever seen or even heard of.  By far.

As one example: there's this really huge flash-based game I sometimes play:

[http://www.casualcollective.com/#games/the_space_game](http://www.casualcollective.com/#games/the_space_game)

Playing that towards the end of a big round, it bogs HARD.  It was impossible to watch Hulu (or even youtube) on one screen while that was in another.

Until now, with Flash64...

> If that's true, then maybe we should decide if it's ready for release in Ubuntu rather that waiting for Adobe. And seeing as so many users have confirmed it to be stable, then perhaps we should petition Canonical to replace the 32 bit in Karmic.

YUP.  Seriously.

---

### Post by Jim March on 2009-08-16
One more thing: you'll sometimes see references to running this 64bit flash inside of NSPluginwrapper.  DON'T.  Don't even have NSPlucinwrapper around.  You don't need it anymore with flash64.

---

### Post by gnomeuser on 2009-08-16
> **Jim March said:**
> One more thing: you'll sometimes see references to running this 64bit flash inside of NSPluginwrapper.  DON'T.  Don't even have NSPlucinwrapper around.  You don't need it anymore with flash64.

sure you do, it contains crashes in plugins.

---

### Post by martijntje on 2009-08-16
In my experience it rather creates problems with plugins than contain them.

---

### Post by CoreyB. on 2009-08-16
I think one of the reasons that it is not included in the repos is that it does not get regular security updates like the 32-bit one does.

---

### Post by eyelessfade on 2009-08-16
> **CoreyB. said:**
> I think one of the reasons that it is not included in the repos is that it does not get regular security updates like the 32-bit one does.

How did you come to that conclusion? There has been 3 version of flash 10, windows 32-bit and there has been 3 versions for linux x64. The last one 10.0.32.18 came out on the same day for all platforms.

---

### Post by CoreyB. on 2009-08-16
I don't know, I thought I read that in a previous thread on the same subject in this forum, I could be wrong though.

---

### Post by macros on 2009-08-16
For me the 64bit version crashes the browser when I open gmail.

---

### Post by miegiel on 2009-08-16
> **eyelessfade said:**
> ...

Adobe have alpha label on x64 because they won't release a "stable" x64 to gnu/linux before windows and mac.

My thoughts exactly :twisted: conspiratory thoughts :rolleyes:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) is the permanent link to the 64bit alpha flashplayer (since the .tar.gz url changes every next version).

For lazy people, check this post :
[http://ubuntuforums.org/showthread.php?p=7717588#post7717588](http://ubuntuforums.org/showthread.php?p=7717588#post7717588)
> **Rody said:**
> I just modifed a script i found on the forms to install the new version, it is not as clean as a .deb but it works great.

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

---

### Post by Giwex on 2009-08-16
Thanks Jim! Worked perfectly.

---

### Post by novafluxx on 2009-08-16
[http://labs.adobe.com](http://labs.adobe.com)

Its easy to find there because thats the sight for development. The 64-bit is still considered to be in the Alpha stage by Adobe. This is why it is not/will not be included in the repos. Also its very easy to install the plugin if you know what you're doing. If you don't...search these forums!

---

### Post by dinxter on 2009-08-17
i put together an amd64 package here for testing [https://launchpad.net/~dinxter/+archive/test](https://launchpad.net/~dinxter/+archive/test)

---

### Post by rajeev1204 on 2009-08-17
> **novafluxx said:**
> [http://labs.adobe.com](http://labs.adobe.com)

Its easy to find there because thats the sight for development. The 64-bit is still considered to be in the Alpha stage by Adobe. This is why it is not/will not be included in the repos. Also its very easy to install the plugin if you know what you're doing. If you don't...search these forums!

Then canonical need to review their policy.In any case,they believe its alpha because adobe tells them that.THey have no control over how the flash plugin works nor do they ship security fixes because they cant until adobe does,the reason being its closed source.

The 64 bit plugin incidentally is same version as the  release versions of adobe 32 bit.

It works a million times better in reality,and even theoretically speaking its an obviously neater solution than wrapping 32 flash around some hack called nspluginwrapper.

Its high time the ubuntu devs make alpha flash 64 bit the default in karmic.

---

### Post by miegiel on 2009-08-17
> **dinxter said:**
> i put together an amd64 package here for testing [https://launchpad.net/~dinxter/+archive/test](https://launchpad.net/~dinxter/+archive/test)

Sorry I can't test it :( I just installed 32bit karmic on a different partition and I still need to figure out how to get grub2 to boot my 64bit karmic.

[COLOR=lightgray]Flash does run a bit better in 32bit and my hibernation times are 25% faster too.[/COLOR]

---

### Post by whistlerspa on 2009-08-17
:( I have found this 64bit version of flashplayer to be buggy. It frequently freezes up the whole system, requiring a system reboot, and does not support full screen video feeds, I'm stuck with the default size within the web page.

It needs major improvement in my opinion.

---

### Post by miegiel on 2009-08-17
> **whistlerspa said:**
> :( I have found this 64bit version of flashplayer to be buggy. It frequently freezes up the whole system, requiring a system reboot, and does not support full screen video feeds, I'm stuck with the default size within the web page.

It needs major improvement in my opinion.

Are you sure you have the 64bit flash player? What you're describing sounds exactly like how the 32bit player runs in a wrapper on 64bit linux.

---

### Post by Jim March on 2009-08-17
Yeah, second that!  I'm getting the BEST full-screen flash I've ever had out of the 64bit version sans nspluginwrapper.  It's been a long time since I tried 64bit Linux at all and Karmic Alpha4 is running great that way.

---

### Post by whistlerspa on 2009-08-17
OK i think it is the 64 bit version but I'll uninstall it and try again:)

---

### Post by Eclipse. on 2009-08-17
Guys aslong as its alpha you surely cant expect this to be packaged into a gold release.Karmic needs to be stable and reliable.Alpha software falls into neither of those.Adobe would not like it one bit either if their development software was released in such a way and would probably ask for it to be removed.

---

### Post by miegiel on 2009-08-17
> **Eclipse. said:**
> Guys aslong as its alpha you surely cant expect this to be packaged into a gold release.Karmic needs to be stable and reliable.Alpha software falls into neither of those.Adobe would not like it one bit either if their development software was released in such a way and would probably ask for it to be removed.

Sure if it really is an alpha, the thing is, it probably isn't really an alpha. My suspicion is that adobe just calls it an alpha to avoid antagonising microsoft and apple, who won't be happy to see linux having a 64bit flashplayer while they don't. The official (32bit) flash player has serious performance issues in full-screen (on 64bit linuxes). Alpha or not, the 64bit flashplayer runs a lot better. Also, they both have the exact same version number [10.0.32.18]. I really think the only difference is that the "alpha" is (almost) the exact same code compiled for 64bit.

That said, I don't think this is something ubuntu should fix for us. A better strategy would be for medibuntu to add it to their repo. But [_**dinxter**'s deb_]("http://ubuntuforums.org/showthread.php?p=7800146#post7800146") is a good start.

---

### Post by lean on 2009-08-18
I think everyone can agree that the 64bit alpha runs better than the 32bit wrapped flash player.
But Ubuntu can not ship the 64bit, since they do not know if security issues will be fixed in an alpha version.
My suggestion is that ubuntu packages both version, and advanced users can install the 64bit version. I really don't see that it shold be necassary to hunt for a ppa or manually download to get the 64bit version.

If a security issue is found, then it is just a matter of apt-get install flash-plugin-nonfree-32, and wait until a fixed 64bit is released.

Seems like the sensible solution, right?

---

### Post by xebian on 2009-08-18
> **lean said:**
> ...
But Ubuntu can not ship the 64bit, since they do not know if security issues will be fixed in an alpha version.
...

Seems like the sensible solution, right?

Since when does Ubuntu ships the FlashPlayer from Adobe?

These are just scripts that download and install the Flash from Adobe.

---

### Post by Jim March on 2009-08-18
> Since when does Ubuntu ships the FlashPlayer from Adobe?

These are just scripts that download and install the Flash from Adobe.

Since when does the user know about (or care about) the difference?

Look at what happens: user installs new Ubuntu, pulls up Youtube, Ubuntu-designed page pops up and says "you need..." and then fetches and installs the needed bit.  Who cares where it came from?  What matters is, is it right?

What's being "served" now for 64bit users is a steaming turd.  Whose fault is that, when something better is available?

---

### Post by miegiel on 2009-08-18
> **Jim March said:**
> Since when does the user know about (or care about) the difference?

Look at what happens: user installs new Ubuntu, pulls up Youtube, Ubuntu-designed page pops up and says "you need..." and then fetches and installs the needed bit.  Who cares where it came from?  What matters is, is it right?

What's being "served" now for 64bit users is a steaming turd.  Whose fault is that, when something better is available?

evil thoughts :
When I got that *install add-on* popup last time I could choose from 3 different flashplayers. Imagine there would be a 4th in that list labelled *alpha* and *unstable*. And imagine the furry unleashed by all the users who discover that the *unstable alpha* to crash less and play more fluently.




 :twisted:

---

### Post by Jim March on 2009-08-18
> And imagine the **furry unleashed** by all the users who discover that the unstable alpha to crash less and play more fluently.

Ummm...yeah, the term "furry unleashed" has some really horrid connotations.

:guitar:

---

### Post by BobJ on 2009-08-18
> **Jim March said:**
> For some reason Karmic's repos want to give you 32bit flash along with nspluginwrapper.  The results stink - lots of Firefox doing the "gray pause", sometimes the flash player crashing outright.

I've installed a real 64bit release-code flash player from Adobe and it's working great on a fresh install of Karmic Alpha4/64bit.  Here's what I did to make it run:

1) Get rid of any existing flash-crap at the command line:


2) Go get the real 64bit flash player:



***Warning: for some reason this is actually a pain in the butt to even find.  Adobe's official flash download site doesn't include 64bit code for some reason, even though this is release gold stuff (not beta or even RC).  That suggests Adobe may not intend to support Linux 64bit?***

3) Unpack it:



4) Put the new player into the right place:



NOTE: if there's an error there, make sure that directory exists...but if you had already put in Ubuntu's suggested flash player from the repos (or possibly Gnash) it will already exist.

Done!  Restart Firefox, Flash will be about as good as it ever gets :).

Sidenote on Gnash:

Prior to going this route I tried Gnash for a bit.  It's come a LONG ways, actually works fine for Youtube, but it fails on too many other things.  It's not ready yet for me, but GO GUYS GO!


Really nice of you to help us - hope you got LOTS thank yous - Just one small thing - URL that give 404 errors REALLY don't help much. 

Thanks a lot - hope someone helps you the same way soon
BobJ

---

### Post by graaant on 2009-08-18
> **dinxter said:**
> i put together an amd64 package here for testing [https://launchpad.net/~dinxter/+archive/test](https://launchpad.net/~dinxter/+archive/test)

Do I need to uninstall all my other stuff first?

```
Selecting previously deselected package flashplugin64-installer.
dpkg: regarding .../flashplugin64-installer_10.0.32.18ubuntu0~dinxter1_amd64.deb containing flashplugin64-installer:
 flashplugin64-installer conflicts with flashplugin-nonfree
  flashplugin-installer provides flashplugin-nonfree and is present and installed.
dpkg: error processing /home/grant/Downloads/flashplugin64-installer_10.0.32.18ubuntu0~dinxter1_amd64.deb (--install):
 conflicting packages - not installing flashplugin64-installer
Errors were encountered while processing:
 /home/grant/Downloads/flashplugin64-installer_10.0.32.18ubuntu0~dinxter1_amd64.deb
```

---

### Post by dinxter on 2009-08-19
> **graaant said:**
> Do I need to uninstall all my other stuff first?

```
Selecting previously deselected package flashplugin64-installer.
dpkg: regarding .../flashplugin64-installer_10.0.32.18ubuntu0~dinxter1_amd64.deb containing flashplugin64-installer:
 flashplugin64-installer conflicts with flashplugin-nonfree
  flashplugin-installer provides flashplugin-nonfree and is present and installed.
dpkg: error processing /home/grant/Downloads/flashplugin64-installer_10.0.32.18ubuntu0~dinxter1_amd64.deb (--install):
 conflicting packages - not installing flashplugin64-installer
Errors were encountered while processing:
 /home/grant/Downloads/flashplugin64-installer_10.0.32.18ubuntu0~dinxter1_amd64.deb
```

flashplugin-nonfree and flashplugin-installer are packages for the 32bit wrapper and should be uninstalled if trying to install flashplugin64 using 'dpkg'. 
they should be automatically uninstalled by the flashplugin64-installer package if your using 'apt-get' or apt frontends like synaptic

---

### Post by quazi on 2009-08-19
I've been experiencing some flash madness recently.

Firefox was crashing and I found out the only way to fix this was to disable flash (I even tried deleting .adobe and .macromedia).  So I entered the following:
```

sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
sudo aptitude install flashplugin-installer
firefox (to let firefox realize that the older flash is now installed)
sudo aptitude purge flashplugin-installer
firefox
sudo cp ~/libflashplayer.so /usr/lib/mozilla/plugins/libflashplyer.so

```

Magically it stopped crashing.

Then after I ran chromium for a bit, it started up again.  After chromium updated to being 64-bit, flash wouldn't work in it either.  I did the 'fix' again and everything's peachy.  

Is it possible that a 32-bit and 64-bit flash being used interchangeably caused borkage?

---

### Post by Jim March on 2009-09-18
I just realized something - because I had "quote" around the wget line, it was truncating the URL.  It wasn't that I had a bad URL, it was the forum software chopping it.  I just switched to "code" instead of "quotes", that's fixed it.

---

### Post by Nickedynick on 2009-09-18
Dinxter - thanks! Installed flashplugin-installer from your PPA and it works great now! Had to restart after I installed, but that's a minor setback.

---

### Post by dinxter on 2009-09-18
i've added chromium-browser to the flash 64 bit package i've been using in the ppa [here]("https://launchpad.net/%7Edinxter/+archive/test"), i'll upload it in a bit if anyone finds it useful. it works with chromium here for what thats worth :)

flashplugin64-nonfree (10.0.32.18ubuntu0~dinxter3) karmic; urgency=low
  * debian/postinst: added chromium-browser variant
  * debian/prerm: added chromium-browser variant

---

### Post by dinxter on 2009-09-18
> **Nickedynick said:**
> Dinxter - thanks! Installed flashplugin-installer from your PPA and it works great now! Had to restart after I installed, but that's a minor setback.
shouldnt need any restart but glad it works for you!

---

### Post by Nickedynick on 2009-09-18
Yeah, for some reason Firefox was crashing repeatedly after the install but it's working like a charm now :)

---

### Post by pulpo69 on 2009-09-18
i had flashplugin-installer64bit installed dinxter's ppa. all worked fine (within firefox).
today i did a dist-upgrade one of upgraded packages was the flashplugin-installer64bit installer.
upgrade always returned an error code.

---

### Post by pulpo69 on 2009-09-18
2009-09-18 22:11:10 (7.30 KB/s) - `./libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz' saved [3727613/3727613]

Download done.
Flash Plugin installed.
update-alternatives: error: unable to make /usr/lib/chromium-browser/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/chromium-browser-flashplugin: No such file or directory
dpkg: error processing flashplugin64-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin64-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dinxter on 2009-09-19
> **pulpo69 said:**
> 2009-09-18 22:11:10 (7.30 KB/s) - `./libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz' saved [3727613/3727613]

Download done.
Flash Plugin installed.
update-alternatives: error: unable to make /usr/lib/chromium-browser/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/chromium-browser-flashplugin: No such file or directory
dpkg: error processing flashplugin64-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin64-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
sorry about that, i'll fix that or remove chromium support in the next hour or so and update ppa

---

### Post by dinxter on 2009-09-19
a classic friday mistake by me, should be fixed when ppa builds

flashplugin64-nonfree (10.0.32.18ubuntu0~dinxter4) karmic; urgency=low
  * debian/dirs: added /var/lib/chromium-browser/plugins

[EDIT] there may be a delay, seems to be an outage on upload server

---

### Post by Visceral Monkey on 2009-09-19
NM, wrong download. DOH!

---

### Post by dinxter on 2009-09-19
> **Visceral Monkey said:**
> Dinxter, I tried your flash fix and it removed the older versions just fine, but I know have *no* flash at all.

i'm having trouble with the ppa, i'll attach the new package if anyones in a rush

---

### Post by Amaranth on 2009-09-19
Last I heard we're actually not allowed to ship anything that installs any alpha or beta flash versions and since this counts as alpha to adobe...

---

### Post by dinxter on 2009-09-19
> **dinxter said:**
> a classic friday mistake by me, should be fixed when ppa builds

flashplugin64-nonfree (10.0.32.18ubuntu0~dinxter4) karmic; urgency=low
  * debian/dirs: added /var/lib/chromium-browser/plugins

ppa server has recovered from its saturday morning hangover so this should now be fixed, let me know if not

---

### Post by ELD on 2009-09-19
> **Amaranth said:**
> Last I heard we're actually not allowed to ship anything that installs any alpha or beta flash versions and since this counts as alpha to adobe...

Even if the other option is much worse? After all a label is simply a label.

---

### Post by 23meg on 2009-09-19
> **ELD said:**
> Even if the other option is much worse? After all a label is simply a label.

You'll have to talk to Adobe about that.

---

### Post by pulpo69 on 2009-09-19
thanks  dinxter, now  all works fine.

---

### Post by dinxter on 2009-09-19
> **pulpo69 said:**
> thanks  dinxter, now  all works fine.
good to hear, its amazing how easy it is for me to make stupid mistakes on a friday, i might set the computer to refuse to boot on those days and protect me from myself :)

---

### Post by screaminj3sus on 2009-09-19
This sucks, the 32 bit one worked alright for me, this crashes firefox isnantly on the colbert report and daily show sites.

---

### Post by dinxter on 2009-09-19
> **screaminj3sus said:**
> This sucks, the 32 bit one worked alright for me, this crashes firefox isnantly on the colbert report and daily show sites.
perhaps adobe were right to mark it alpha after all...

---

### Post by rtalcott on 2009-09-19
I just tried it also....instant crashes....removed it and went back to what I had before and Firefox is stable again...wish I could tell you why...I certainly appreciate your efforts!
rt

---

### Post by dinxter on 2009-09-19
wish i could offer some advice but its running solid as a rock here, with or without nspluginwrapper installed which i thought might be an issue. all i can offer is maybe checking for any other flash64 plugin installations you may have done, in ~/.mozilla/plugins for example, and get rid of them. i doubt its that to be honest, i suppose its an alpha thing after all, some people do much better than with the 32 bit wrapper, others get nasty crashes

---

### Post by rtalcott on 2009-09-19
Thank You for the tip...I'll see what else is installed and maybe give it another try!
rt

---

### Post by pulpo69 on 2009-09-19
i only can repeat to confirm, since today here it runs very stable.
otherwise tanks dinxter

---

### Post by FunkyRes on 2009-09-20
For what it is worth, I've been using the 64-bit "alpha" plugin on CentOS for a very long time (since it first became available).

One of the first things I did after installing Ubuntu was try to install flash. When I saw it wanted to bring in ndis-wrapper, 32-bit firefox, and a whole lot of 32-bit support library bloat - of course I backed out.

The "alpha" 64-bit plugin works well with stock FireFox, Shiretoko, Google Chrome, Epiphany webkit, Midori, and Opera on Ubuntu Jaunty.

I haven't been playing with any other browsers.

If you are not going to package the 64-bit plugin over the use of the word "alpha" then you should remove the ndiswrapper install of the 32-bit plugin, it causes problems in 64-bit. Serious problems, even though it is not "alpha".

Just my thoughts.

---

### Post by Faelan on 2009-10-05
Thanks for the post Jim.

Firefox however crashed lots until I performed the instructions on this page ([http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)).

It turns out that if you have an older 64 bit CPU like my Athlon 64, flash will crash when it tries to send a LAHF instruction to your CPU. The problem is that these older CPUs do not recognize that instruction, and hence the crash.

Hopes this helps others with the same problem.

---

### Post by tuxxy on 2009-10-05
I think the alpha should be in the repos without a doubt its very stable much better than using 32-bit apps.

---

### Post by Roger E Critchlow Jr on 2009-10-09
Doesn't work for firefox or google chrome under Karmic as of today.

Firefox gets blown right out of existence.  Google Chrome puts up an sick face in place of video and fingers libflashplayer.so by name.

-- rec --

---

### Post by Jim March on 2009-10-10
Still working fine for me with all Karmic updates, Firefox and Chrome.

---

### Post by gunnar123 on 2009-10-12
> **Faelan said:**
> Thanks for the post Jim.

Firefox however crashed lots until I performed the instructions on this page ([http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)).

It turns out that if you have an older 64 bit CPU like my Athlon 64, flash will crash when it tries to send a LAHF instruction to your CPU. The problem is that these older CPUs do not recognize that instruction, and hence the crash.

Hopes this helps others with the same problem.
Thanks, this lead me to take a deeper look into this AMD issue; I commented on it here:
[http://ubuntuforums.org/showthread.php?p=8092243#post8092243](http://ubuntuforums.org/showthread.php?p=8092243#post8092243)

---

### Post by FrancoNero on 2009-10-12
works great in both jaunty and karmic. go 64bit!

too bad it overheats my laptop badly if i watch flash things in fullscreen, like youtube videos. but that's both an adobe and a general linux problem of inadequate laptop-handling

---

### Post by waffen on 2009-10-16
Hello!
Working for me perfect! Thanks!

---

### Post by tjeremiah on 2009-10-16
ive had the 64bit flash since its release and no matter what, it always lags/stutters when watching some flash videos in HD. For a test, can anyone tell me if it lags/stutters while watching this?

[http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0](http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0)

---

### Post by zika on 2009-10-16
> **tjeremiah said:**
> ive had the 64bit flash since its release and no matter what, it always lags/stutters when watching some flash videos in HD. For a test, can anyone tell me if it lags/stutters while watching this?
[http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0](http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0)Yes.

---

### Post by tjeremiah on 2009-10-16
> **zika said:**
> Yes.

:? I thought I was the only one.

---

### Post by miegiel on 2009-10-16
> **tjeremiah said:**
> ive had the 64bit flash since its release and no matter what, it always lags/stutters when watching some flash videos in HD. For a test, can anyone tell me if it lags/stutters while watching this?

[http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0](http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0)

As a reference, on 32bit karmic with the 32bit player 1.4GHz core 2 duo mobile. It's a bit boring without sound (there is sound, it's just so soft you can't really hear anything). I get stutters when the guy on the left in the interview parts waves his hands. I get white flashes where the game and interview scenes are welded (probably not the correct term). Other then that playback is fine.

---

### Post by jejones3141 on 2009-10-25
Here's what I've run into: I did an upgrade to Karmic Koala Release Candidate, and then installed the 64-bit flash player. Some things work, e.g. YouTube. Others don't, e.g. [www.instapundit.com](www.instapundit.com) and mail.google.com (the latter after I sign on); they make Firefox crash with a segmentation fault in libflashplayer.so.

The odd part: I thought it might be something in my profile, so I created a new user, logged in under that account, and fired up Firefox. No problem. Log out, log back on as me, do a "mv .mozilla .mozilla.bak", and start up Firefox... and it dies on gmail and instapundit.com just as before.

What about the totally new account would be different, as far as Firefox is concerned, from an account for which I moved .mozilla out of the way so it would create a new ~/.mozilla directory? I am puzzled.

---

### Post by zika on 2009-10-25
> **jejones3141 said:**
> Here's what I've run into: I did an upgrade to Karmic Koala Release Candidate, and then installed the 64-bit flash player. Some things work, e.g. YouTube. Others don't, e.g. [www.instapundit.com]("http://www.instapundit.com") and mail.google.com (the latter after I sign on); they make Firefox crash with a segmentation fault in libflashplayer.so.

The odd part: I thought it might be something in my profile, so I created a new user, logged in under that account, and fired up Firefox. No problem. Log out, log back on as me, do a "mv .mozilla .mozilla.bak", and start up Firefox... and it dies on gmail and instapundit.com just as before.

What about the totally new account would be different, as far as Firefox is concerned, from an account for which I moved .mozilla out of the way so it would create a new ~/.mozilla directory? I am puzzled.Where is libflashplayer.so? Put it, being sure it is the latest version from alpha repository, only, as /home/jejones/.mozilla/plugins/libflashplayer.so (of cource change Your username here for Your username on that machine). If that does not work then we could think about some other options ...

---

### Post by jejones3141 on 2009-10-25
> **tjeremiah said:**
> ive had the 64bit flash since its release and no matter what, it always lags/stutters when watching some flash videos in HD. For a test, can anyone tell me if it lags/stutters while watching this?

[http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0](http://www.gametrailers.com/episode/gametrailers-tv/74?ch=1&sd=0)

I don't see lag or stutter, even in fullscreen mode--though it fell out of fullscreen mode three times on me. When it did, it went back to playing in the original window with no trouble, and would switch back to fullscreen if I clicked on the icon for it.

UPDATE: I do see some flickering on [www.speedtest.net](www.speedtest.net) when the test is running.

---

### Post by jejones3141 on 2009-10-25
> **zika said:**
> Where is libflashplayer.so? Put it, being sure it is the latest version from alpha repository, only, as /home/jejones/.mozilla/plugins/libflashplayer.so (of cource change Your username here for Your username on that machine). If that does not work then we could think about some other options ...

I retrieved the .tar.gz file again (from the link in the first post in this thread), and extracted it. The libflashplayer.so has a timestamp of July 17, 2009, 23:04, and is 9560488 bytes long, cmp shows it's identical to the file I have in /usr/lib/mozilla/plugins by that name.

I put it in ~/.mozilla/plugins, and got the same result as before.

UPDATE: It's forehead slapping time; I deleted the copy in /usr/lib/mozilla/plugins, and made sure there's one in /usr/lib64/mozilla/plugins, since after all it is 64-bit code. Does it assume things in /usr/lib/mozilla/plugins are 32-bit? I could see that breaking... in any case, instapundit.com is happy now.

---

### Post by bruno9779 on 2009-10-26
It works like a charm

---

### Post by philinux on 2009-10-26
I only have one copy of libflashplayer.so and it's in ~/.mozilla/plugins. Works just fine.

---

