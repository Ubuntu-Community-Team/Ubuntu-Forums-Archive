---
title: "Some internet sites won't load after upgrade to 9.10/10.04 -- maybe Flash or Java???"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by TracyO on 2010-11-01
Hello,

I upgraded from 9.04 to 9.10 a week ago.  After the upgrade, I didn't have an internet connection, and I ended up resetting my wireless router to get it back.  Once I had internet, some sites weren't working.  I upgraded to 10.04 a few days ago thinking it might be better with the LTS, but it is the same.  The pages time out.  Sometimes I can get onto a mainpage, but anything further than that times out.

Sites that work normally:
Gmail, hulu

Sites that do not work:
Ubuntuforums (my attempted postings time out), YouTube, DailyShow.com (Ads loop over and over again), facebook, Npr.org (mainpage comes up but my search doesn't load), various websites I need to pay bills on

This problem is equal in Chrome, Firefox, Seamonkey, and Epiphany.  

Is there something I could have messed with when I reset my wireless connection?  Is there something that needs to be updated (like Flash or Java)?  I attempted to update Flash for Mozilla through the Software Center, but nothing has changed.

I downloaded Lynx for a fresh install, and I tried running the Live CD to get a sense if that might help.  Same results from Facebook and NPR and other sites while on the live cd. The error message is usually that the connection was reset while the page was loading, or the pages just keep trying to load but never do.  Should re-installing 10.04 from the cd fix whatever this is?

I'm posting this from work, and I can at least see people's responses from home and through my email.  

I appreciate any thoughts.

Thanks.

---

### Post by Cavsfan on 2010-11-01
Firefox flash addon developed by a forum member **lovinglinux**
[[COLOR=blue]_FLASH-AID by lovinglinux_[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/161939/")

Instructions for checking your java version and another for installing the latest version if you do not have it 
are in my signature.

Hope this helps!

---

### Post by TracyO on 2010-11-01
Thanks for those links.  It looks like the problem is NOT Flash or Java.  Java is working, and I installed Flash-aid.  Everything is still the same, and I still have no idea what to do or what happened.

Got any other thoughts?

Thank you.
Tracy

---

### Post by TracyO on 2010-11-01
Ooh, I can reply to forums again!  Thanks for that much.  =)

Nothing else seems to have changed, though.  Still no NPR, Facebook, YouTube, etc.  Error messages appear.

I'll take whichever wins I can get.

---

### Post by Cavsfan on 2010-11-02
> **TracyO said:**
> Ooh, I can reply to forums again!  Thanks for that much.  =)

Nothing else seems to have changed, though.  Still no NPR, Facebook, YouTube, etc.  Error messages appear.

I'll take whichever wins I can get.

You could try the Firefox addon Noscript. You can control what websites are allowed to access your browser. 
It is sort of a pain to setup initially, but you will not have any popup ads that you don't allow. 
At the bottom right corner of the screen you can middle click on sites to view information about whether to 
grant access or not. Sometimes you just want to give temporary access. There are YouTube videos that show 
you to set it up once you have installed it. For example YouTube has 2 sites that need access to view videos and 
the rest are extraneous.

---

### Post by TracyO on 2010-11-02
I'm certainly up for trying it, but can you please explain a little more how it will help?  I'm missing that.

---

### Post by Quackers on 2010-11-02
I had a couple of problems after upgrading. Some sites would timeout or say the link was broken. I fixed it by adding those sites as exceptions in the pop-up blocker.
In the homepage go to Edit > Preferences > Content tab and on the pop-up blocker line click on exceptions then enter the website address.
I have had no problems since.

---

### Post by TracyO on 2010-11-02
Some things are working better but not consistently.  I won't have a chance to look into this further today, so I'll let you know once I figure out how this works out.

Thanks for what it's already helped.

---

### Post by efflandt on 2010-11-02
When I did a 9.10 to 10.04 upgrade, most recent version of flashplugin-installer appeared to be installed, but apparently did not appear in Firefox Add-ons and did not work.  Also **ubuntu-restricted-extras** had become uninstalled, but installing that (which should have included flash) did not restore flash.  I had to mark **flashplugin-installer** for **Reinstallation** and apply before it showed up in Firefox and worked.  So give that a shot.

---

### Post by Cavsfan on 2010-11-03
> **TracyO said:**
> I'm certainly up for trying it, but can you please explain a little more how it will help?  I'm missing that.

You should probably watch this tutorial before installing noscript. It will give you an idea about what it does. 

[[COLOR=blue]_Noscript tutorial from Cnet._[/COLOR]]("http://www.youtube.com/watch?v=GzBqnLgOzwM")

Once you have added it to Firefox, you can middle click the mouse on the websites listed with Noscript at the bottom of the screen 
and that will bring up another 
tab with 4 websites. The 1st one gives you information on how it is rated. The 4th website will give you info about in the 
past 90 days has anyone been infected by that site. You can use this info as to whether to allow temporary or permanent access.

Here is how to add it to Firefox:
Click on **Tools** > **Addons**. Then click on **Get New-addons** and enter "noscript" in the search box. Install it and it will ask you to 
restart Firefox.

It takes a little getting used to, but it is a great tool.

---

### Post by TracyO on 2010-11-08
Update:

I'm still having trouble with websites in Chrome and Firefox, though Firefox is behaving better of the two.  Thanks for the YouTube site.  I will look at it when YouTube finally works again.

I went to reinstall flashplugininstaller and to do so, it uninstalls Flashplugin.  I did that (just to see), and of course nothing worked.  I reinstalled flashplugin, and I'm at the same place I was prior to this endeavor.  

I reinstalled restricted extras, but it hasn't changed anything.

I've also been looking around on Google Chrome's help pages. It looks like this has been a somewhat common phenomenon, but I haven't found my solution yet.  

[http://www.google.com/support/forum/p/Chrome/thread?tid=13bd8aa2533edbe3&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=13bd8aa2533edbe3&hl=en)
[http://www.google.com/support/forum/p/Chrome/thread?tid=24045d5f3da4820e&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=24045d5f3da4820e&hl=en)

It may be a little late, but I'm starting my own log.

Chrome Preferences &#8594; under the hood, unchecked DNS Prefetching, restarted Chrome: Bank of America site won't load
Cleared Chrome cache: BA site won't load
Re-checked DNS Pre-fetching: BA site won't load
Chrome: couldn't post to Ubuntuforums

Restarted computer: Chrome BA site loads up to entering my passcode—ERR 324

Chrome Npr.org, searched Jon Stewart fresh air, saw search results, then "waiting for npr.org"
won't load direct page URL when pasted into another tab

Firefox: BA stuck on loading after entering passcode, clicked allow all in no script, entered passcode again; then stops loading 

Firefox: pasted direct Jon Stewart URL, and it loaded, AND downloaded the file; on the tab, the page is still loading

Chrome: Bank of America homepage Error 101 (net::ERR_CONNECTION_RESET): Unknown error.
Facebook: homepage: Error 101 (net::ERR_CONNECTION_RESET): Unknown error.
Electric company site: never-ending attempt to load after entering login info

Firefox: Electric company site:never-ending attempt to load atter entering login info
Facebook: loads, can look, attempts at posting do the never-ending attempt to load
BA: mainpage comes up while still appearing to load on the tab, can't get past attempt to login

Any thoughts on whether resetting my router will help?  Or other thoughts?

Thanks again.

---

### Post by Cavsfan on 2010-11-09
I don't have anything more to offer. Hopefully **lovinglinux** will see this and help you out.
Did you install **flashplugin-installer**? You can get it via Synaptic.
I think I got an update for it and it is on version 10.1.102.64ubuntu0.10.10.1.

It says it is for Firefox and Chromium and some others. Chromium is open source and can be gotten
via Synaptic. I believe it is just Chrome only open source. I haven't used it.

You can go to this site and [[COLOR=blue]_check the version of flash that is installed._[/COLOR]]("http://www.adobe.com/software/flash/about/")

---

### Post by TracyO on 2010-11-11
I did download the flash installer, which uninstalled flash, which I then reinstalled.

According to Adobe's site, I have version 10,1,103,19 installed.  

I tried Chromium a few days ago.  When I tested it and sites still didn't load, I just uninstalled it.

Thanks for the help you've given. I really appreciate it.

---

### Post by Cavsfan on 2010-11-11
> **TracyO said:**
> I did download the flash installer, which uninstalled flash, which I then reinstalled.

According to Adobe's site, I have version 10,1,103,19 installed.  

I tried Chromium a few days ago.  When I tested it and sites still didn't load, I just uninstalled it.

Thanks for the help you've given. I really appreciate it.

You are very welcome! Hope I was able to help some!

---

### Post by TracyO on 2010-11-12
Test to see whether I can post.  Now having trouble with launchpad.  No need to respond.

---

