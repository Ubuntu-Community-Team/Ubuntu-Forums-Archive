---
title: "installing adobe flash player v10.3.183.90 on 12.04 LTS"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by churka on 2013-06-24
Hi
I just realised that adobe flash player v11 is not gonna work on my system. 
So i decided to download latest adobe fp  v10.3.183.90 released  June/11/2013 from adobe:
[helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html]("http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html")

running installer script from the download ended with error that glibc is older than 2.3 .
glibc on my comp is 2.15 
Latest stable glibc is 2.17 !!!!
Any idea how do I get v10 flash player installed on Ubuntu12.04?
Thanks

---

### Post by churka on 2013-06-26
looks like i have found an easy workaround courtesy french!!! will update once I have tried it out.

---

### Post by churka on 2013-06-26
Ok, its insane posting reply to myself but forget it, here is the **[COLOR=#ff0000]biggest thing: Shumway[/COLOR]** - project by Mozilla to to run SWF content without Adobe Flash Player! Shumway will render swf content if you have JavaScript and HTML5 support in your xyz browser.
[https://blog.mozilla.org/research/2012/11/12/introducing-the-shumway-open-swf-runtime-project/](https://blog.mozilla.org/research/2012/11/12/introducing-the-shumway-open-swf-runtime-project/)

Workaround Update - it works as I said in prev post.

The problem I faced is like an epidemic - affecting all those having old CPU not having SSE2. For example AMD athlonXP , Sempron Intel Pentium III Coppermine, Intel Pentium III Tualatin, Intel Celeron Mendocino, Intel Celeron Coppermine-128, Intel Celeron Tualatin-256, Intel Pentium M etc are victims.

If you are facing the same problem, steps mentioned here will sort you out:
[http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/getting-flash-plug-in-to-work-with-older-cpus-4175420481/](http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/getting-flash-plug-in-to-work-with-older-cpus-4175420481/)

If you know French, figureout the steps to get v10 Flash Player here:
[http://doc.ubuntu-fr.org/flashplayer](http://doc.ubuntu-fr.org/flashplayer)
look at  section 3.4 -Arrêt inopiné de FlashPlayer avec les anciens processeurs AMD

---

### Post by Frogs Hair on 2013-06-26
Thanks for posing the solution. If you are a Firefox user you may want to install this translator extension.   [https://addons.mozilla.org/en-us/firefox/addon/google-translator-for-firefox/](https://addons.mozilla.org/en-us/firefox/addon/google-translator-for-firefox/)

---

### Post by churka on 2013-06-28
Wow this extension exists! useful in many cases. Thanks.
On second thoughts of layman in comps like me, is it possible to convert SSE2 instructions to SSE and then pass it on to CPU? Context is Adobe Flash player compiled with SSE2 which renders all old SSE cpus stranded.

---

### Post by cigtoxdoc on 2013-06-29
An additional trick may be necessary on some installations.  After I downloaded and extracted v10.3.183.90 and copied it to the correct places, I rebooted and much to my surprise, the current version of flash player had taken over.  I write-protected v10.3.183.90 and then copied it to /usr/lib/adobe-flash-plugin and /usr/lib/firefox-addons/plugins.  I have survuved several reboots, etc.

John

---

### Post by churka on 2013-07-01
Wow! you hav to write protect it! thats strange stuff to hear :rolleyes:.I extracted libflashplayer.so from the download and copied it to existing directory : /usr/lib/flashplugin-installer . Basically replaced libflashplayer.so (v11). It is working. Yes, I used sudo privilege to copy so no need to change any existing permissions.

---

