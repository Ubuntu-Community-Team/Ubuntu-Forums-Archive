---
title: "Help needed: Using Pearson's ePen with Oracle Java in Linux"
date: 2017-06-27
forum: MINT
---

### Post by tom-literaryconnections on 2017-06-27
Last year, like the poster on this helpful thread, **[Can I make ePen/Internet Explorer work?]("https://ubuntuforums.org/showthread.php?t=2320077")** I managed to make Pearson's ePen online marking system work in Firefox on Linux Mint. It was so much better than struggling with IE on my Windows laptop, which (amongst other aspects) constantly complains I need to update Java when we have to stick to a specific older version. However, that method no longer works, as **[Firefox version 52 upwards no longer supports Oracle Java]("https://www.java.com/en/download/help/firefox_java.xml")**, which is demanded by ePen. One workaround, though only temporary, appears to be to use the Firefox Extended Support Release (ESR) edition. 

Instead, I picked up a suggestion to try **[SeaMonkey]("https://www.seamonkey-project.org/releases/")** instead, and this *does* work with Java. It means I can continue to use the latest Firefox for normal browsing and keep SeaMonkey for this specific task. I needed to **Install Oracle Java** - [I found this guide to doing through PPA helpful]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"). (It doesn't matter whether you install Java or the browser first.) **Install SeaMonkey** - it doesn't seem to be in the standard repositories either, but it's easy to add it. I followed [these instructions on Ubuntuzilla]("https://sourceforge.net/p/ubuntuzilla/wiki/Main_Page/#installation"). You can **check** Java works in SeaMonkey [here on the Oracle site]("https://www.java.com/en/download/installed.jsp"). You probably need to add the ePen site(s) to the Java exceptions list. *Hidden feature*: to call up the **Java Control Panel** to do this, you have to type **[FONT=courier new]ControlPanel[/FONT]** in a terminal window. 

But although this gets me into the ePen system, there are still problems, and I'd love to hear from anyone who's got this to work:

[LIST]
[*]The browser health check still says 'This browser is not supported. You must use Internet Explorer 11.' This may not matter, if the system works despite the warning, but good to kill it. 
[*]The ePen practice site blocks any use with the same message - that's more annoying, as I can't check properly. 
[*]**I can log into the system** for my own work but until the system for my unit goes live, I can't see if it's actually working fully (I need to see the scanned items displayed on screen, not just access the admin side). 
[/LIST]
Hence my call for anyone actually using it successfully, or someone with more skill to take what I've done so far and suggest ways to solve the final problems.

Thanks!

*[Linux Mint 18.1, based on Ubuntu 16.04]*

---

### Post by howefield on 2017-06-27
Thread moved to the "*MINT*" forum.

---

### Post by slickymaster on 2017-06-27
Have you checked this thread on AskUbuntu: [How can I use Pearson's ePEN java applet on Ubuntu?]("https://askubuntu.com/questions/764815/how-can-i-use-pearsons-epen-java-applet-on-ubuntu")

---

### Post by tom-literaryconnections on 2017-06-27
Thanks - I'd not found that recent post, despite searching a few days ago! Will report back.

*Moved to Mint forum*: Fair enough, I suppose, though this is an issue that affects Ubuntu users and derivatives too. ;)

---

### Post by tom-literaryconnections on 2017-07-14
Thanks to the link from **slickmaster** above, I can report that **ePen now works**, at least the bits that I actually need. Once [these instructions]("https://askubuntu.com/questions/764815/how-can-i-use-pearsons-epen-java-applet-on-ubuntu") are followed, both Firefox ESR and Sea Monkey work with live ePen marking. 

I've settled on Sea Monkey, to avoid confusing my two versions of Firefox (they both use the same profile, which is mostly handy but means I can't readily tell which is in use). Sea Monkey still fails the browser check and on practice site because even with User Profile Switcher the ePen site detects I'm not using IE version 11. But all marking features seem to work, bar one glitch so minor I'm not even sure it's not a fault in the ePen system anyway. 

So thanks!

---

