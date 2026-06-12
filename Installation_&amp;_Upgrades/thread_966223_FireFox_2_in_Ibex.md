---
title: "FireFox 2 in Ibex"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Qbert on 2008-11-01
I have ibex installed on my ThinkPad.  I dislike Firefox 3 and would like to remove it to install version 2.  How can I go about this?  I downloaded the package, but synaptic doesn't seem to know what to do with it.  I did this in hardy, but now can't remember how.  Thanks for any help.

---

### Post by steveydoteu on 2008-11-01
May I ask why? Have you not considered the possible security implications?

---

### Post by OrangeCrate on 2008-11-01
Frankly, FF2 is a dead duck, and likely won't be supported for much longer. You might as well learn to like FF3, or try one of the alternatives. Opera seems to be a popular option...

**&#8216;End of life&#8217; beckons for Firefox 2**

[http://blogs.zdnet.com/security/?p=2080](http://blogs.zdnet.com/security/?p=2080)

---

### Post by Qbert on 2008-11-02
I happen to like Firefox 2 better.

---

### Post by peakshysteria on 2008-11-02
It is possible to set up FF3 just like FF2 without much hassle. This is preferable to a roll back to an earlier version. Tell us the features or things you dislike ([my first guess is the terrible awesomebar. The first thing I removed from my own FF]("http://ubuntuforums.org/showthread.php?t=813553")). We might help you to set up FF3 just like you want it.

(if not there are ways to get FF2 up and running though it's not recommended: But there are reports of trouble regarding FF2 and Intrepid Ibex).

---

### Post by houstonbofh on 2008-11-03
> **peakshysteria said:**
> It is possible to set up FF3 just like FF2 without much hassle. This is preferable to a roll back to an earlier version. Tell us the features or things you dislike.
How about the fact that mjpeg streaming is broken in FF3, and never closes streams.  This is a major issue if you are using things like ZoneMinder [http://www.zoneminder.com](http://www.zoneminder.com) but it will still flood your net connection if you use any mjpeg streaming.

Also, how about the way is kicks you in the teeth if you use self signed certificates?  I have them on 75 firewalls, and I am sick to death of having to re-accept the cert every time I go to a remote location.

Can you fix that? :rolleyes:

Or how about how every request for FF2 leads mainly to admonitions, not instructions? ;)

---

### Post by peakshysteria on 2008-11-03
[SIZE="7"]**[mozillazine]("http://forums.mozillazine.org/index.php")**[/SIZE] seems to be your best bet. FF2 seems like a bad choice anyway. FF3.0.3 is by far the safest version (if your not into nightly builds). **[The Burning Edge]("http://www.squarefree.com/burningedge/")** might also help you.

---

### Post by jmail524 on 2008-11-09
I would also like to get Firefox 2 running under Intrepid (8.10).  Firefox 3 keeps crashing on some sites, doesn't always display javascript correctly and the print selection function doesn't work most of the time. (It generally prints out a blank page with a header and footer.)  I never had these problems with Firefox 2.

Thanks.

---

### Post by peakshysteria on 2008-11-09
As far as I found out so far it's not possible to run FF2 on Intrepid.

jmail524: Please post your setup (use [infolister]("https://addons.mozilla.org/en-US/firefox/addon/447") for your FF3 setup)

---

### Post by Qbert on 2008-11-13
I got a little sidetracked, but thanks for the replies so far.  There's a couple things I don't like about FF3.  In Hardy I figured out or someone helped me figure out how to remove the page bar from Firefox.  Since I'm mostly on a notebook I like as much resolution as possible.  I also want to remove the searchbox from the bookmarks sidebar becuase I like to get as many in there as I can.  Lastly, I dislike the unsorted bookmarks and other folders I have to have on the bookmarks sidebar because again I like to jam as many in there as I can.  If anyone knows how to fix those things, it would be greatly appreciated.  Thanks.

---

### Post by peakshysteria on 2008-11-13
I would suggest to don't use the bookmarks sidebar at all. But you might find some code to put in your [userchrome]("http://kb.mozillazine.org/UserChrome.js") to remove the search box from it at [mozillazine]("http://forums.mozillazine.org/index.php"). [Sidebar Autohide 1.0]("https://addons.mozilla.org/en-US/firefox/addon/6524") might also be to your liking if your looking to save some more space available. Userchrome code snippets are always most fun but addons are often the easiest way to go. Here's some nice [bookmarks sidebar addons]("https://addons.mozilla.org/en-US/firefox/search?q=bookmarks+sidebar&cat=all"). You might also like [Autohide]("http://www.krickelkrackel.de/autohide/autohide.htm"), Auto-Hide Your Firefox Bookmarks Toolbar, [http://lifehacker.com/software/firefox-tip/auto+hide-your-firefox-bookmarks-toolbar-316445.php]("http://lifehacker.com/software/firefox-tip/auto+hide-your-firefox-bookmarks-toolbar-316445.php"), or just use multiple bookmarks bars and/or the smooth art of [bookmarks keywords]("http://lifehacker.com/software/bookmarks/hack-attack-firefox-and-the-art-of-keyword-bookmarking-196779.php").

Also removing the name of the bookmark and placing it in the Bookmarks toolbar saves space and increases the accessibility:

[[img]http://bildr.no/thumb/286405.jpeg[/img]](http://bildr.no/view/286405)

---

### Post by Qbert on 2008-11-13
I know it's probably unusual, but I don't like tabbed browsing.  What I liked about the sidebar in FF2 is I could put in all my most used bookmarks on the side and put the rest in a folder.  That way I could just hit my regulars and go to the bookmarks menu when needed.  I have no need to search my bookmarks, but could use the extra space for more bookmarks.  For the same reason I don't like the extra folders I can't seem to get rid of.  I'd also like to get rid of the page bar cause I already know what page I'm on.  Thanks for the help.

---

### Post by peakshysteria on 2008-11-13
My point with the screenshot above where to show you the bookmarks bar (not the tab bar :)).

To remove the searchbar (if that's what you mean) right click the menu bar at the top (or any grey field) and choose **customize**. Then you can drag items you don't want into the pop up box (or back again). The Autohide addon I linked to above is also helpful with hiding the menubar, searchbar and so on..... keywords for bookmarks also helps you increase speed and efficiency (even without finding the bookmark itself). 

Not using tabbed browsing severely cripples your ability to powersurf. I must admit I never use only one page when I'm browsing. And having more than one browser window open seems very slow compared to tabbed browsing. I guess we all have our quirks and needs. But whatever you fancy, it's possible to make it happen with Firefox.

---

### Post by Otustelija on 2008-11-13
You could attempt to run the Windows version of FF2 using Wine. At least the portableapps.com port works perfectly. (Just tried.)

Ps. The latest version of FF2 is a couple of days old, so I wouldn't talk about security vulnerabilities just yet.

---

### Post by houstonbofh on 2008-11-13
I just downloaded the tar of FF2 from mozilla, and stick it in a firefox2 directory in my home.  I made a symlink to the binary on my desktop, and it runs fine.  However, not both at once, and I have to accept plugins after switching between versions.  A real PITA, but it works.  Kinda...

---

### Post by jmail524 on 2008-12-03
**peakshysteria:**  Thanks for the reply. (Sorry I was gone for so long.) Below is a copy of the output from the 'InfoLister' add-on.

```
Last updated: Thu, 04 Dec 2008 03:01:14 GMT
User Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.4) Gecko/2008111319 Ubuntu/8.10 (intrepid) Firefox/3.0.4
Extensions (enabled: 2, disabled: 0):

    * InfoLister 0.10
    * Ubuntu Firefox Modifications 0.6

Themes (1):

    * Default 3.0.4 [selected]

Plugins (6):

    * Default Plugin
    * Demo Print Plugin for unix/linux
    * DivX® Web Player
    * QuickTime Plug-in 7.2.0
    * Totem Web Browser Plugin 2.24.3
    * Windows Media Player Plug-in 10 (compatible; Totem)
```

Thanks.

---

