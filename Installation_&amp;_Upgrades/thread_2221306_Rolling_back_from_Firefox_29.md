---
title: "Rolling back from Firefox 29"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by dwlamb on 2014-05-01
[COLOR=#000000][FONT=Arial]I run Ubuntu 12.04 LTS and Firefox was upgraded to ver 29. I am not happy with it for changes to the interface, particularly lack of a status bar (may have been called something else) for plug-ins like synchronizing Xmarks and controlling the debug helper for Netbeans.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To rollback to a previous version, I found this article [http://www.liberiangeek.net/2012/04/download-and-install-firefox-manually-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/download-and-install-firefox-manually-in-ubuntu-12-04-precise-pangolin/)  but the paths are totally different. I found nothing in /opt or /usr/bin for Firefox. whereis yielded that Firefox is located in /usr/lib/firefox.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Is it safe to follow the steps for that tutorial, placing the rolled back Firefox ver. 28 in /usr/lib/firefox and creating symbolic links there?[/FONT][/COLOR]

---

### Post by 67GTA on 2014-05-01
I wouldn't follow that unless you originally installed firefox manually. This is the best way to downgrade software, and keep it from upgrading in the future. The only thing that will over ride this is a "dist-upgrade". [http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/](http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/)

---

### Post by dwlamb on 2014-05-01
Thanks for the reply but the solution you suggest won't work.  With Firefox 29 already installed, the only options presented in Synaptic is to lock the version at 29 or rollback all the way to 11 (what came with the distro).  I've manually removed 29 and will install 28 using the method suggested in the article I pasted a link to.

> **67GTA said:**
> I wouldn't follow that unless you originally installed firefox manually. This is the best way to downgrade software, and keep it from upgrading in the future. The only thing that will over ride this is a "dist-upgrade". [http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/](http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/)

---

### Post by fantab on 2014-05-01
Firefox 29 or the new 'Chrome wannabe' can be tweaked to look and feel like 'Classic' firefox with a couple of addons.
[http://www.dedoimedo.com/computers/firefox-disable-australis.html](http://www.dedoimedo.com/computers/firefox-disable-australis.html)

I suggest you cleanup all the old 'profiles' and settings by removing dot-mozilla [.mozilla] folder in your Home. It is a hidden folder you can reveal it with ctrl+H in nautilus.

We cannot forever use FF28; at some point in time we do need those critical security updates that come with newer versions of FF.
Its not a good idea to use outdated web-browser.

---

### Post by vasa1 on 2014-05-01
+1 to what fantab wrote. Just one extension, Classic Theme Restorer, will fix *most* Australis-induced issues.

---

### Post by fantab on 2014-05-02
> Just one extension, Classic Theme Restorer, will fix *most* Australis-induced issues.

True. I added just the '*Classic Theme Restorer*', that did most of what I needed....

---

### Post by claracc on 2014-05-02
> **fantab said:**
> Firefox 29 or the new 'Chrome wannabe' can be tweaked to look and feel like 'Classic' firefox with a couple of addons.
[http://www.dedoimedo.com/computers/firefox-disable-australis.html](http://www.dedoimedo.com/computers/firefox-disable-australis.html)

I suggest you cleanup all the old 'profiles' and settings by removing dot-mozilla [.mozilla] folder in your Home. It is a hidden folder you can reveal it with ctrl+H in nautilus.

We cannot forever use FF28; at some point in time we do need those critical security updates that come with newer versions of FF.
Its not a good idea to use outdated web-browser.

+1

Using an outdated web browser as firefox 28, is a security risk.

---

