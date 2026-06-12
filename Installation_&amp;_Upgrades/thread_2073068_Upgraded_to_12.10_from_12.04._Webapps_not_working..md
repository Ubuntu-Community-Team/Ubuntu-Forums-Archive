---
title: "Upgraded to 12.10 from 12.04. Webapps not working."
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by jondecker76 on 2012-10-18
I just upgraded my 12.04 box to 12.10.  I have a few problems:

1)  In 12.04 I added google's repo to install chrome.  Web apps are not working with chrome for me right now

2) I installed chromium from the software center.  Web apps are not working from chromium

3) I opened gmail from firefox.  It almost looked like webapps were going to work with firefox as I got a popup from gmail to enable desktop functionality.  However, I don't get a gmail icon in sidebar, and none of the webapp integration is present on my ubuntu!

4) I saw in a youtube video that gimp was integrated with unituy apps and that the dashboard would give me extra functionallity..  This isn't present in my install

How can I get the unity apps/ web apps to work?  This was the feature I was looking forward to the most!

---

### Post by jondecker76 on 2012-10-18
I just visited [http://developer.ubuntu.com/api/ubuntu-12.04/javascript/index.html](http://developer.ubuntu.com/api/ubuntu-12.04/javascript/index.html) and clicked on all the "Execute this code now" links a try and not a single one of them worked.  I'm obviously missing whatever package enables the unity API on my machine.  This is the absolute worse upgrade I've been through yet!

---

### Post by jondecker76 on 2012-10-18
I verified that unity-chromium-extension is installed... Another dead end...

---

### Post by FreedomOverdose on 2012-10-18
Same here, the webapps hud is not working (the only thing that I can get to work are shortcuts to gmail/twitter/etc)

---

### Post by eggsbenedict on 2012-10-19
I'm also one of many that seems to be having problems with (a few of) the web apps.  I have gotten Facebook and Twitter to function perfectly.  Gmail is still a problem.  I've installed it, it appears on my launcher and in the panel envelope.  BUT, it does not indicate any new unread emails in the inbox.  And, when clicked, it opens up an entirely new window to gmail even if there is another window signed into gmail...i'm using Firefox btw, dont know if this makes a difference.

I tired uninstalling and reinstalling the unity-webapps-gmail from Software Center.  It didn't do anything.  In fact, after uninstalling it (and before reinstalling it), I restarted my computer and the gmail indicator was still present in the panel envelope menu and on the launcher!  I'm not sure what is going on.  I reinstalled it, and still doesn't really work.

---

### Post by javierfh on 2012-10-19
> **eggsbenedict said:**
> I'm also one of many that seems to be having problems with (a few of) the web apps.  I have gotten Facebook and Twitter to function perfectly.  Gmail is still a problem.  I've installed it, it appears on my launcher and in the panel envelope.  BUT, it does not indicate any new unread emails in the inbox.  And, when clicked, it opens up an entirely new window to gmail even if there is another window signed into gmail...i'm using Firefox btw, dont know if this makes a difference.

I tired uninstalling and reinstalling the unity-webapps-gmail from Software Center.  It didn't do anything.  In fact, after uninstalling it (and before reinstalling it), I restarted my computer and the gmail indicator was still present in the panel envelope menu and on the launcher!  I'm not sure what is going on.  I reinstalled it, and still doesn't really work.

So have you tried if it works with chromium?
Anyway for me when I use chrome, nothing happens, but if I use firefox I get the message asking if I want to install "gmail" for extra features and faster access ( I didn't try to install it, since I don't understand these webapps very well and I am afraid that if I install it from firefox, will always open firefox as default for these webapps)

Also I was curious about the fact that you said you are tired of installing unity-webapps-gmail.. I have installed this morning a ppa for webapps, but I wonder if that is a ppa for all of them and what you are doing is configuring one by one. Do I need to also install unity-webapps-gmail? I guess answer is no, because when I tried to install I got a message saying that "if you install unity-webapps-gmail, future updates will not include new items in Unity Webapps Preview metapackage set. Are you sure you want to continue?" and then lists "unity webapp integration scripts and Unity webapps preview metapackage.

Any idea?

---

### Post by jondecker76 on 2012-10-19
Well, by some miracle I got it to work on my wife's login, but it refuses to work on my login.

Regarding the HUD - it was probably working all along for me (with gimp, etc).  I didn't understand that you had to invoke the HUD with the ALT button instead of clicking on the icon at the top of the sidebar.  So this part is working for me.

So as of now, everything is working on my wife's login.  My login, however, none of the web app features work - no webapp icons in the sidebar, chromium doesn't prompt me when i visit webapp enabled sites (Gmail, twitter, facebook, last.fm, etc).

---

### Post by jondecker76 on 2012-10-19
Ok, i thought I would get a fresh start, so I deleted the folowing configuration files:
~/.local/share/unity-webapps
~/.config/chromium
~/.config/google-chrome

Now I got last.fm to prompt for integration and it works.  But gmail, twitter and facebook still don't prompt or work.  How is this even possible???

---

### Post by jondecker76 on 2012-10-19
Even more strange behavior..  I go to launchpad to do a bug report on this, and  launchpad does in fact prompt for the integration, but the webapp extension crashes out.  I tried several times and closed chromium in between, but it crashes every single time.  Here is the error:

> The crashed program seems to use third-party or local libraries:

/home/jondecker76/.config/chromium/Default/Extensions/pmoflmbbcfgacopiikdcpmbiellfihdg/2.4.2_0/libunity_npapi_plugin.so

It is highly recommended to check if the problem persists without those first.

---

### Post by jondecker76 on 2012-10-19
created bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/1068662](https://bugs.launchpad.net/ubuntu/+bug/1068662)

---

### Post by jondecker76 on 2012-10-19
I linked this thread from the bug report.  I'm going to place the contents of the unity-webapps databases here in case it helps them find the problem:

```

jondecker76@main-desktop:~/.local/share/unity-webapps$ 
jondecker76@main-desktop:~/.local/share/unity-webapps$ ls
apps2.db  availableapps-v2.db  resources  resources.db
jondecker76@main-desktop:~/.local/share/unity-webapps$ sqlite3 apps2.db
SQLite version 3.7.13 2012-06-11 02:05:22
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> .tables
actions  apps   
sqlite> select * from apps;
last.fm|last.fm|http://www.last.fm/
sqlite> select * from actions;
sqlite> .quit
jondecker76@main-desktop:~/.local/share/unity-webapps$ sqlite3 availableapps-v2.db
SQLite version 3.7.13 2012-06-11 02:05:22
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> .tables
urls
sqlite> select * from urls;
https://read.amazon.com/*|unity-webapps-amazoncloudreader|AmazonCloudReader|read.amazon.com
http://chrome.angrybirds.com/*|unity-webapps-angrybirds|AngryBirds|chrome.angrybirds.com
http://www.bbc.co.uk/news/|unity-webapps-bbcnews|BBCNews|bbc.co.uk
http://*.cuttherope.ie/*|unity-webapps-cuttherope|CutTheRope|cuttherope.ie
http://apps.facebook.com/*/*|unity-webapps-facebookapps|FacebookApps|apps.facebook.com
https://apps.facebook.com/*/*|unity-webapps-facebookapps|FacebookApps|apps.facebook.com
http://www.facebook.com/*|unity-webapps-facebookmessenger|FacebookMessenger|facebook.com
https://www.facebook.com/*|unity-webapps-facebookmessenger|FacebookMessenger|facebook.com
https://mail.google.com/*|unity-webapps-gmail|GMail|mail.google.com
https://www.google.*/calendar/*|unity-webapps-googlecalendar|GoogleCalendar|google.com
http://www.google.*/calendar/*|unity-webapps-googlecalendar|GoogleCalendar|google.com
https://docs.google.com/*|unity-webapps-googledocs|GoogleDocs|docs.google.com
https://plus.google.com/*|unity-webapps-googleplus|GooglePlus|plus.google.com
http://grooveshark.com/#!/*|unity-webapps-grooveshark|grooveshark|grooveshark.com
http://www.hulu.com/watch/*|unity-webapps-hulu-player|hulu-player|hulu.com
http://last.fm/*|unity-webapps-lastfm-radio|lastfm-radio|last.fm
http://*.last.fm/*|unity-webapps-lastfm-radio|lastfm-radio|last.fm
https://last.fm/*|unity-webapps-lastfm-radio|lastfm-radio|last.fm
https://*.last.fm/*|unity-webapps-lastfm-radio|lastfm-radio|last.fm
https://*.launchpad.net/*|unity-webapps-launchpad|Launchpad|launchpad.net
https://launchpad.net/*|unity-webapps-launchpad|Launchpad|launchpad.net
http://alpha.libre.fm/*|unity-webapps-librefm|LibreFm|libre.fm
http://www.linkedin.com/*|unity-webapps-linkedin|LinkedIn|linkedin.com
http://www.linkedin.com|unity-webapps-linkedin|LinkedIn|linkedin.com
http://*.live.com/*|unity-webapps-livemail|LiveMail|mail.live.com
https://*.live.com/*|unity-webapps-livemail|LiveMail|mail.live.com
http://*.mail.ru/*|unity-webapps-mail-ru|mail-ru|mail.ru
http://mail.ru/|unity-webapps-mail-ru|mail-ru|mail.ru
http://newsblur.com/|unity-webapps-newsblur|Newsblur|newsblur.com
http://www.pandora.com/*|unity-webapps-pandora-com|pandora-com|pandora.com
https://www.pandora.com/*|unity-webapps-pandora-com|pandora-com|pandora.com
http://*.mail.qq.com/cgi-bin/*|unity-webapps-qq-mail|qq-mail|mail.qq.com
https://*.mail.qq.com/cgi-bin/*|unity-webapps-qq-mail|qq-mail|mail.qq.com
http://*.reddit.com/|unity-webapps-reddit|Reddit|reddit.com
http://reddit.com/*|unity-webapps-reddit|Reddit|reddit.com
http://*.reddit.com/*|unity-webapps-reddit|Reddit|reddit.com
http://tumblr.com/*|unity-webapps-tumblr|Tumblr|tumblr.com
http://*.tumblr.com/*|unity-webapps-tumblr|Tumblr|tumblr.com
https://tumblr.com/*|unity-webapps-tumblr|Tumblr|tumblr.com
https://*.tumblr.com/*|unity-webapps-tumblr|Tumblr|tumblr.com
https://twitter.com/*|unity-webapps-twitter|Twitter|twitter.com
http://vk.com/*|unity-webapps-vkcom|Vkcom|vk.com
https://*.wordpress.com/wp-admin/|unity-webapps-wordpress-com|wordpress-com|wordpress.com
http://*.wordpress.com/wp-admin/|unity-webapps-wordpress-com|wordpress-com|wordpress.com
https://*.wordpress.com/wp-admin/index.php|unity-webapps-wordpress-com|wordpress-com|wordpress.com
http://*.wordpress.com/wp-admin/index.php|unity-webapps-wordpress-com|wordpress-com|wordpress.com
http://*.mail.yahoo.com/*|unity-webapps-yahoomail|YahooMail|mail.yahoo.com
https://*.mail.yahoo.com/*|unity-webapps-yahoomail|YahooMail|mail.yahoo.com
http://news.yahoo.com/|unity-webapps-yahoonews|YahooNews|yahoo.com
http://mx.noticias.yahoo.com/|unity-webapps-yahoonews|YahooNews|yahoo.com
http://es.noticias.yahoo.com/|unity-webapps-yahoonews|YahooNews|yahoo.com
http://music.yandex.ru/*|unity-webapps-yandex-music|yandex-music|music.yandex.ru
https://music.yandex.ru/*|unity-webapps-yandex-music|yandex-music|music.yandex.ru
http://news.yandex.ru/*|unity-webapps-yandexnews|YandexNews|news.yandex.ru
https://news.yandex.ru/*|unity-webapps-yandexnews|YandexNews|news.yandex.ru
http://youtube.com/*|unity-webapps-youtube|YouTube|youtube.com
http://*.youtube.com/*|unity-webapps-youtube|YouTube|youtube.com
https://youtube.com/*|unity-webapps-youtube|YouTube|youtube.com
https://*.youtube.com/*|unity-webapps-youtube|YouTube|youtube.com
sqlite> .quit
jondecker76@main-desktop:~/.local/share/unity-webapps$ sqlite3 resources.db
SQLite version 3.7.13 2012-06-11 02:05:22
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> .tables
resources
sqlite> select * from resources;
1|fc87b27fe1c6598e2135b9179baffaf3|/home/jondecker76/.local/share/unity-webapps/resources/fc87b27fe1c6598e2135b9179baffaf3|1|1350655720
2|cae7f8d818cebfcd61bed50752127714|/home/jondecker76/.local/share/unity-webapps/resources/cae7f8d818cebfcd61bed50752127714|3|1350655808
sqlite> .quit
jondecker76@main-desktop:~/.local/share/unity-webapps$

```

---

### Post by joe1826 on 2012-10-19
Same problem here.  I upgraded for the webapps but they don't seem to do anything.  After I first upgraded there was an Amazon and Ubuntu Music Icon on the dashboard, but now they have both disappeared after a restart. The only part of the webapps process that seems to work is the notification to install the app after you go to a webpage that supports it.  After that, nothing.  No unity integration, no icon on the dashboard :(  Pretty much it looks like I upgraded solely for the benefit of being able to search amazon without opening a browser <---- sarcasm.  I hope someone finds a fix for this soon.:confused:

---

### Post by agualdino on 2012-10-20
Hi,

I have the same problem as described above.
So far the best i got was to get prompted to create the app when using Chromium (didn't work in Chrome) but then nothing else happens. no notifications, no tray integration and app opens inside chrome as a new window.

---

### Post by FreedomOverdose on 2012-10-20
I can get the icons to appear in the dashboard, but that's all webapps do for me. No integration with the HUD whatsoever

---

### Post by jondecker76 on 2012-10-20
I went into synaptic and reinstalled every web app that was already there (including Gmail, which I didn't even know was installed, but never worked anyways).  I also installed some that I thought would be cool like Cut The Rope and Angry Birds.


Even after doing this, I can't find Angry Birds or Cut The Rope in the dash.

I'd gladly let a developer connect via a VNC session so they could see this for themselves.

---

### Post by KieranS on 2013-01-10
Hello.

I also have the same problem.  I am prompted to install and I have icons appear but nothing else, no extra functionality.  One thing I did notice is that when I installed the BBC News app it worked for a few seconds (popping up notifications) but then stopped.

If anyone comes up with a sollution I'd be grateful. :)

---

### Post by c4c on 2013-01-26
Here's a tutorial I uploaded for our users to fix Chromium webapp creation on Lubuntu 12.10 - It's for the LXDE desktop environment, but hopefully this will lead you all in the right direction to get things working on whatever distros you use. [URL="http://computers4christians.org/Chromium-app-shortcut-fix-lubuntu.html"]http://computers4christians.org/Chromium-app-shortcut-fix-lubuntu.html
[/URL]

---

### Post by nick3499 on 2013-02-03
was having a problem with the pandora-webapp, but assuming that my solution could possibly help you, here is what I did.

1. went into the **Synaptic** package manager and did a *complete removal* of...```
unity-webapps-pandora-com
``` you could also try...```
sudo apt-get purge unity-webapps-pandora-com
```

2. rebooted OS

3. went into **Ubuntu Software Center** and reinstalled...```
unity-webapps-pandora-com
```...then the webapp worked like new.

note:

before the fix, I did notice (after running...```
about:plugins
```...in **Google Chrome**, click **+Details** in the upper right) that I had, along with the **Pepper API**, the...```
flashplayer-installer
```...dir .so, and a third...```
___flashplayer.so
```...in a mozilla dir that I had cp'd there myself. but even after disabling all but one...```
___flashplayer.so
```...I could not get the dog to hunt, which led to the suggested solution above.

---

### Post by for_serg on 2013-02-09
The same, I did fresh install of 12.10 and still Unity Web API is not working. Tried to reinstall many packages, no result.

---

### Post by JafoFubar on 2013-02-23
Here's what I had to do. I installed Synaptic Package Manager, ran it, searched for gmail, uninstalled (completely) unity-webapps-gmail and then reinstalled it via Synaptic. I tried uninstalling it via Synaptic and reinstalling it via the Firefox prompt several times and it would not work. Reinstalling it via Synaptic worked. 
Although ..... I'm not sure if it's working the way it's designed. I have to open and login to Gmail in Firefox to have the icon show me Inbox etc. I'm guessing it's that way because I have to be logged into gmail somehow and via Firefox is how to log in.

---

