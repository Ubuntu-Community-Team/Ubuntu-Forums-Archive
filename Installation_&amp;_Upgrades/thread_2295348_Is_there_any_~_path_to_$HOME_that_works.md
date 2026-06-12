---
title: "Is there any ~/ path to $HOME that works???"
date: 2015-09-17
forum: Installation &amp; Upgrades
---

### Post by artphotodude on 2015-09-17
Am trying to setup a universal build file and am getting killed by all the path-setup tomfoolary Linux requires.  Coming from OSX, am used to simply being able to put **~/** into any path and it automatically redirects to the home directory, but in Linux it instead seems to make a folder **(~)** inside of the user directory and writes to that.  Have had the same results with **pwd** and **$HOME**.  Is there ANY way to simply make a generic user-account path that will reliably work?  

Also, is there any way to get around the /media/UserName path problem????  /dev/USB seemed to work just fine before the change.

This all doesn't seem to benefit security at all, as it is a simple matter in a script to use pwd and then execute whatever one wants to do.  it just seems like a deliberate way to break portability of script and config files.

---

### Post by qamelian on 2015-09-17
Maybe you could provide a specific example. I have no problem with using ~ or $HOME to access or work in my home directory.

---

### Post by artphotodude on 2015-09-17
qamelian:  it relates to config files (Javascript?) in several apps I regularly configure, that won't connect within Linux, but do just fine in OSX.  Perhaps there is some less cooperative interconnection here that makes each be regarded as an absolute path rather than a sym/relative Link. Things like download location settings for Firefox and Chrome (I use a special configuration optimized for security) and always have to go into each app and manually set these links after installation, or they go nowhere (null). I think I will simply start using a .sh to pwd -> Sed them after installation with the username as this is a massive hassle each time I have to do it. It all reminds me of driving in Washington, DC.  Just when you think you are going in the obvious direction, you wind up at a dead end, or going the opposite way.

---

