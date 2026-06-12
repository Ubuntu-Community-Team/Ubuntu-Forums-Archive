---
title: "Firefox address and search bar not working after update to FF 11"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by ole1 on 2012-03-16
Hi,

The address bar and search bar in Firefox stopped working after I upgraded from FF 10 to 11 in ubuntu 10.04. Typing in URLs or search phrases is not followed by any FF activity. I can open URLs from bookmarks though.

Also, I cannot access "Manage search engines", the Add-ons-manager won't load and when trying to create this threat in Firefox, the following error message appears: "The following errors occurred with your submission: The message you have entered is too short. Please lengthen your message to at least 1 characters."

At first, the bookmarks menu remained blank, too. That changed when I brought up the classic Menu bar instead of the Firefox menu.

I have reinstalled Firefox both from the mozillateam and the ubuntu main ppa's, to no avail.

Any help or advice on how to do further troubleshooting would be appreciated.

Thanks

---

### Post by igortroy on 2012-03-16
looks like I'm not the only one to run into this issue. unfortunately, what you described is just the tip of the iceberg: none of my AddOns work. writing a complete address and clicking "go" or hitting Enter does nothing. no search engines. no AddOn manager. no back or forward buttons in case you actually went anywhere (from Bookmarks)...

I installed the FF10 -> FF11 update from the official Mozilla Firefox-Stable ppa, then tried to fix this by using Synaptic to completely reinstall all Firefox and Firefox-related packages - and nothing.
I am actually writing this reply from FF11 on Windows7 - since my FF11 on Ubuntu 10.04 is now completely useless.

if this is a bug with the Ununtu version of FF11, then it must be the unholy mother of all bugs.

Mozilla's obsession to compete with Google's Chrome-version-frenzy was bound to cause something like this sooner or later. there was nothing wrong with FF4.

---

### Post by Renshu on 2012-03-16
My upgrade didn't work either. After weeks of headaches with Firefox 10 with the constant crashes and now I couldn't even add a sentence in this forum with the firefox browser. I can either downgrade and work from there or just use something else, maybe Chromium since this is what I am using at the moment. 

Any advice would be most appreciated.

---

### Post by Renshu on 2012-03-16
I wonder if Mozilla is listening.

---

### Post by ubu_lin on 2012-03-16
Yeah, So I am not alone.. :D
I had installed 3 times deleting all old configuration, settings and cache, but no use. Can anyone tell me how to revert to firefox 10 ?

---

### Post by mwotsch on 2012-03-16
Same problem here. 
In the last few days I have been able to revert to FF10 by doing

```

sudo apt-get purge firefox
sudo apt-get install firefox=10.*

```

which now does not work anymore.
Any ideas?

---

### Post by darkod on 2012-03-16
> **Renshu said:**
> My upgrade didn't work either. After weeks of headaches with Firefox 10 with the constant crashes and now I couldn't even add a sentence in this forum with the firefox browser. I can either downgrade and work from there or just use something else, maybe Chromium since this is what I am using at the moment. 

Any advice would be most appreciated.

I still haven't tried FF11 but as far as FF10 is concerned I have been using it since it was released WITHOUT any crashes.

Do you guys maybe use some specific settings and changes made to FF which might not play nice with the new v11?

It is normal some add-ons to be disabled in a new version until an update of the add-on is released. But the core of FF should still work anyway.

Also when using the PPA to be able to have the latest version, make sure it is only the official and stable PPA and not some pre-release which might not be able for prime time.

Other than that, nothing springs to mind about such issues. FF has been stable ages ago, because of that I switched from IE even on windows. Have never seen it crash except when my GF opens 190 tabs. :)

---

### Post by mwotsch on 2012-03-16
This did the trick for me: I had the xul-ext-bindwood package installed for bookmark syncing. I never used it so I uninstalled it using the Synaptic package manager and now Firefox works as it should.

Maybe this will help a select few of you.

---

### Post by ubu_lin on 2012-03-16
> **mwotsch said:**
> Same problem here. 
In the last few days I have been able to revert to FF10 by doing

```

sudo apt-get purge firefox
sudo apt-get install firefox=10.*

```

which now does not work anymore.
Any ideas?

Thanks for that, I will try to revert to FF 10

> **darkod said:**
> 

...

Do you guys maybe use some specific settings and changes made to FF which might not play nice with the new v11?

...

I had disabled/deleted all the add-ons, deleted all the old settings by deleting .mozilla folder in home directory and installed again freshly. So I think that is not the problem

---

### Post by darkod on 2012-03-16
> **ubu_lin said:**
> Thanks for that, I will try to revert to FF 10



I had disabled/deleted all the add-ons, deleted all the old settings by deleting .mozilla folder in home directory and installed again freshly. So I think that is not the problem

Look at post #8, just posted. It might be something as trivial as that, something you even forgot about. Just guessing here...

---

### Post by ubu_lin on 2012-03-16
> **mwotsch said:**
> This did the trick for me: I had the xul-ext-bindwood package installed for bookmark syncing. I never used it so I uninstalled it using the Synaptic package manager and now Firefox works as it should.

Maybe this will help a select few of you.

yes, Thank you, This worked for me too.

> **darkod said:**
> Look at post #8, just posted. It might be something as trivial as that, something you even forgot about. Just guessing here...

Yes, I had installed that long back but forgot about that. After removing that, it works now. Thanks.

---

### Post by igortroy on 2012-03-16
Luckily, I had a backup image done 5 days ago so I'm writing this from Firefox 10 and Ubuntu 10.04 dated 11/3/12. it's Wubi, so the restoration process was just copying and replacing one giant file named "root.disk" in Windows.

as for reverting to FF10 from inside Ubuntu, I couldn't do what you guys mentioned since apparently my system was already broken before the FF11 update. maybe it's the recent Xorg update or something.

anyways, I won't be updating anything in Ubuntu for a couple of days at least. just going to ignore Update Manager when it pops-up.

---

### Post by ole1 on 2012-03-16
> **mwotsch said:**
> This did the trick for me: I had the xul-ext-bindwood package installed for bookmark syncing. I never used it so I uninstalled it using the Synaptic package manager and now Firefox works as it should.

Maybe this will help a select few of you.

This worked for me. Thanks.

> **darkod said:**
> 
Do you guys maybe use some specific settings and changes made to FF which might not play nice with the new v11?

It is normal some add-ons to be disabled in a new version until an update of the add-on is released. But the core of FF should still work anyway.

Also when using the PPA to be able to have the latest version, make sure it is only the official and stable PPA and not some pre-release which might not be able for prime time.

Just to give some context and to recap: FFv10 worked without problems. I upgraded from the mozillateam/firefox-stable PPA and when that gave these mixed results, I switched to ubuntu/main. So this is not a question of stable builds or not. Concerning extensions: temporary incompatibilities would be perfectly acceptable, but in this case core functions of FF ceased to work. Like navigating websites.

I have a question regarding etiquette, being new to the forums: should I tag this thread as solved since my initial problem is indeed solved, or do I leave it open another 24h since there seem to be other people having the same issues?

---

### Post by cbtengr on 2012-03-16
> **mwotsch said:**
> This did the trick for me: I had the xul-ext-bindwood package installed for bookmark syncing. I never used it so I uninstalled it using the Synaptic package manager and now Firefox works as it should.

Maybe this will help a select few of you.

Thank you.  That fixed the problem for me.  Really had me stumped, the update was working fine on my laptop with Linux Mint 11, but not on my desktop Ubuntu machine.

---

### Post by ubu_lin on 2012-03-16
I had filed bug report for this, and a developer replied on launchpad. They are now removing bindwood package, as it is not maintained and useless. So may be soon an update come up and solve this problem for all whoever installed that package.

---

### Post by ierotheo on 2012-03-16
The removal of xul-ext-bindwood did it for me too.
Thank you mwotsch

---

### Post by chrisccoulson on 2012-03-16
Do any of you have the addon compatibility reporter installed?

---

### Post by mwotsch on 2012-03-16
Glad this bindwood extension removal seems to work for quite a few of us.

> **chrisccoulson said:**
> Do any of you have the addon compatibility reporter installed?

When Firefox updates itself, it runs that check. However, it only complained about a dictionary not being compatible. No mention of the bindwood extension.

---

### Post by chrisccoulson on 2012-03-16
> **mwotsch said:**
> Glad this bindwood extension removal seems to work for quite a few of us.



When Firefox updates itself, it runs that check. However, it only complained about a dictionary not being compatible. No mention of the bindwood extension.

I think you misunderstood my question. Do you have the Addon Compatibility Reporter addon installed?

If not, where did you install bindwood from? If you installed it from our archive, then did you manually edit /usr/share/xul-ext/bindwood/install.rdf at some point? The reason I ask is that the version of Bindwood in our archive for Ubuntu 10.04 is marked as incompatible with current Firefox versions unless you have installed the Addon Compatibility Reporter (as the version of bindwood in our archive has a maxVersion of 3.6.*)

---

### Post by mwotsch on 2012-03-16
> **chrisccoulson said:**
> I think you misunderstood my question. Do you have the Addon Compatibility Reporter addon installed?

If not, where did you install bindwood from? If you installed it from our archive, then did you manually edit /usr/share/xul-ext/bindwood/install.rdf at some point? The reason I ask is that the version of Bindwood in our archive for Ubuntu 10.04 is marked as incompatible with current Firefox versions unless you have installed the Addon Compatibility Reporter (as the version of bindwood in our archive has a maxVersion of 3.6.*)

My apologies. I don't have the Addon Compatibility Reporter Addon installed.

To be honest, I don't remember how I installed bindwood. That was a while ago. Sorry for not being more helpful there.

---

### Post by chrisccoulson on 2012-03-16
> **mwotsch said:**
> My apologies. I don't have the Addon Compatibility Reporter Addon installed.

To be honest, I don't remember how I installed bindwood. That was a while ago. Sorry for not being more helpful there.

It's ok. We've just pushed an update to automatically remove bindwood in any case

---

### Post by ole1 on 2012-03-16
> **chrisccoulson said:**
> I think you misunderstood my question. Do you have the Addon Compatibility Reporter addon installed?

If not, where did you install bindwood from? If you installed it from our archive, then did you manually edit /usr/share/xul-ext/bindwood/install.rdf at some point? The reason I ask is that the version of Bindwood in our archive for Ubuntu 10.04 is marked as incompatible with current Firefox versions unless you have installed the Addon Compatibility Reporter (as the version of bindwood in our archive has a maxVersion of 3.6.*)
I don't have the Addon Compatibility Reporter addon installed. I am not sure from where I installed bindwood. But I am quite certain that I never edited the .rdf file and that I installed bindwood after upgrading from FF 3.6. Sorry that I can't be more precise.

---

### Post by stevenc296 on 2012-03-16
Looks like many of us are having this problem.  The update to FF 11 was just installed this evening on Ubuntu 10.04.  I even went so far as uninstalling FF, renaming the hidden ".mozilla" folder to ".mozillaOld", and then did a new install.

After FF11 started up, the address and search bar worked once and did not work after that. I shut down and restarted FF and still the problem continues.

Ubuntu or Mozilla ... are you listening... this update is not working. A fix is needed and fast!!!!   (Good thing I have Chrome installed too or I would not be able to access the internet period.)

---

### Post by darkod on 2012-03-17
> **stevenc296 said:**
> Looks like many of us are having this problem.  The update to FF 11 was just installed this evening on Ubuntu 10.04.  I even went so far as uninstalling FF, renaming the hidden ".mozilla" folder to ".mozillaOld", and then did a new install.

After FF11 started up, the address and search bar worked once and did not work after that. I shut down and restarted FF and still the problem continues.

Ubuntu or Mozilla ... are you listening... this update is not working. A fix is needed and fast!!!!   (Good thing I have Chrome installed too or I would not be able to access the internet period.)

Did you try removing the bindwood package? Did you see that few people have reported the FF11 problem solved after they removed that package that is not used anyway?

---

### Post by AntiBodies on 2012-03-17
This is also happening to me

on 10.04 using the mozillateam PPA - recent update has borked Firefox

I do not have the bindwood package installed. 

Is there a bug been reported to launchpad for this??

---

### Post by mcdragon on 2012-03-17
Hi

did not have access to the internet for the last few weeks and upgraded my Ubuntu last night. Apparently the xul-ext-bindwood package was still there and my Firefox did not work. Removing it manually did the trick.

Thanks guys. Just another reason why even if there are problems with linux is still the best system around, for me at least :-)

Martin

---

### Post by realStargazer on 2012-03-17
Removing xul-ext-bindwood with synaptic manager did firefox to work again. Thanks:lol

---

### Post by trigity on 2012-03-17
Okay! Firefox issues that are causing problems after updates to 11.0. To fix the issues of search engines, url bars and bookmarking after update. 

After all other options failed. I just went to synaptic pkg mgr and removed the xul-ext-bindwood and restated firefox.

Problem solved - for now!

---

### Post by funcrunch on 2012-03-17
> **mwotsch said:**
> This did the trick for me: I had the xul-ext-bindwood package installed for bookmark syncing. I never used it so I uninstalled it using the Synaptic package manager and now Firefox works as it should.

Maybe this will help a select few of you.

Thank you so much! Removing that bindwood package (which I also was never using) fixed my completely screwed-up FF 11 upgrade as well.

---

### Post by AntiBodies on 2012-03-17
Thank you forum of awesome

My firefox is now fixed.. ah so it was the package xul-ext-bindwood  .. I did have that installed now removed and fixed problem.

```
sudo apt-get remove xul-ext-bindwood
```

Is your friend

---

### Post by SivArt on 2012-03-17
I had the same issue and it was caused by the UbuntuOne bookmark sync service **xul-ext-blindwood** **,** removing the app fixed it.

Thanks!

---

### Post by SivArt on 2012-03-17
I just created a launchpad bug report for xul-ext-blindwood:#958304             [xul-ext-bindwood makes firefox 11 unusable]("https://bugs.launchpad.net/ubuntu/+source/bindwood/+bug/958304")

[https://bugs.launchpad.net/ubuntu/+source/bindwood/+bug/958304](https://bugs.launchpad.net/ubuntu/+source/bindwood/+bug/958304)

It should be automatically  removed after upgrading to FF 11 or patched.

---

### Post by yelbetan on 2012-03-20
> **darkod said:**
> Look at post #8, just posted. It might be something as trivial as that, something you even forgot about. Just guessing here...

Yes I did just that and it solved the problem and everything works fine:

$ sudo apt-get remove xul-ext-bindwood

or remove it from synaptic.

It seems xul-ext-bindwood has a compatibility problem with the new firefox 11

---

### Post by SivArt on 2012-03-21
> **yelbetan said:**
> Yes I did just that and it solved the problem and everything works fine:

$ sudo apt-get remove xul-ext-bindwood

or remove it from synaptic.

It seems xul-ext-bindwood has a compatibility problem with the new firefox 11

As of ubuntu 11.10, xul-ext-blindwood is no longer supported, so the package was not mantained or updated (see: [http://voices.canonical.com/ubuntuone/2011/10/17/putting-bookmark-sync-to-bed/]("http://voices.canonical.com/ubuntuone/2011/10/17/putting-bookmark-sync-to-bed/")) at this point Canonical ya goig to makean empty package for xul-ext-bindwood in order to fix this issue (see bug [958304]("https://bugs.launchpad.net/ubuntu/+source/bindwood/+bug/958304")).

---

### Post by Flywaver on 2012-03-23
same issue here, xul-ext-bindwood is not even installed. Can't restore default search as it's greyed out!
Tried to purge ff, delete all traces of it, reinstalled and still no google search. :(

Edit: It worked by installing ff from the firefox-next PPA (12.0b2)

---

### Post by arahmanpbd on 2013-03-28
To search on the address bar with google ( to any version of firefox ) 
  1. In the default google bar, search any word
           like **bangladesh**
  2. You will see the address bar with corresponding url. 
           Mine _**[http://www.google.com/search?client=ubuntu&channel=fs&q=bangladesh&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=bangladesh&ie=utf-8&oe=utf-8) **_
      copy the url untill  your word comes
            like _**[http://www.google.com/search?client=ubuntu&channel=fs&q=](http://www.google.com/search?client=ubuntu&channel=fs&q=)**_
     * if yours link differ with mine dont bother. *
  3. Now go to address bar clicking new tab. Then type and enter
           **about:config**
  4. search with **Keyword.URL** 
  5. Now double click and paste the copied url
  6. Now you can search on your address bar with google.


You can choose your search engine with step 1. I chosed google, you can choose yahoo or others.

@author: [EMAIL="arahman_pbd@yahoo.com"]arahman_pbd@yahoo.com[/EMAIL]

---

