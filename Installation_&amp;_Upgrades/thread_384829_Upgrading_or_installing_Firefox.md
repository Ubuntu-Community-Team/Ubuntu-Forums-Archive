---
title: "Upgrading or installing Firefox"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by Chappy7777 on 2007-03-14
The good news is that I finally got Ubuntu and my modem working together. Using the version of FFox that came w/Ubuntu 5.10, I downloaded the newest Firefox version 2.0.0.2 tar.gz

I need some help in how to install a tar.gz download, in this case, Firefox. So, can someone please tell me how to get this done? I did manage to download FFox w/out losing it, so I don't have to do a search.

When I clicked on the download, I got a box that was somewhat similar to a Winzip extractor. But I am not sure what to do next. My guess is create a file and extract the tar.gz file into it.
Am I close. 

I tried clicking on the "check for updates" in preferences, but it came back with "there are none. I suppose this is because my version of Firefox is so old.

I need some help, please, as the version of Firefox I am using is a tad out dated. Version 1.0

Another quick question re:Opera. I was using Xandros for a short while, but was having a ton of trouble w/it, so I switched to Ubuntu. In the XN forums there's a lot of talk about using Opera. I haven't seen it mentioned yet in this Forum. Is there a reason for that? I kind of like Opera on XP. I wouldn't mind using it w/Ubuntu if there isn't a reason not to.

Thnx alot,

Chappy

---

### Post by aysiu on 2007-03-14
This script will help you out:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by DJ_Peng on 2007-03-15
Actually no script is needed to run Firefox from Mozilla. Just right click on the file and select "Extract Here", then run the ```
firefox
``` file from the archive. You'll need to tale care of some plugins manually, but if you're comfortable doing that you can find that running Firefox 2 (or Thunderbird) straight from Mozilla is a remarkably pain free experience.

---

### Post by aysiu on 2007-03-15
> **DJ_Peng said:**
> Actually no script is needed to run Firefox from Mozilla. A script is not a terribly complicated thing to run, and it takes care of all the plugin linkage for you.

If you're using Ubuntu, you just right-click the script, go to Properties, mark it executable, then double-click the script, and choose to run it in the terminal.

That's it.

The script does everything for you--checks to see what the latest version of Firefox is, downloads it from the Mozilla website, checks the integrity of the download, allows you to choose the locale, and installs it fully so that *firefox* launches Mozilla Firefox and *firefox.ubuntu* launches Ubuntu Firefox. All the plugins are linked.

---

