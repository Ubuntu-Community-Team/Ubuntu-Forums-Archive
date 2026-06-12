---
title: "What does it mean when it shows flash under about:plugins, but flash doesn't work?"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by steveyos666 on 2006-11-18
Kubuntu, upgraded from dapper to edgy, Firefox 2.0

(Typing this last, just remembered- What I mean by "doesn't work" is Firefox [2.0] drops the little menu at the top and says missing plugin or whatever it says, and of course you can't just install it from that little thing for reasons unknown)

Here's a screenshot [http://img453.imageshack.us/img453/8466/snapshot4mu8.png](http://img453.imageshack.us/img453/8466/snapshot4mu8.png)

I've tried using automatix2, I've tried downloading flash 9 off the beta site, I think I tried some other stuff, I think I'm out of ideas.

Everything worked fine in Ubuntu, what's the deal with Kubuntu? Is KDE harder to program for than Gnome or something? I used to like Gnome the best, but KDE grew on me and now I think it's pretty cool. The only thing is, when I tried to install KDE on Ubuntu, I couldn't get it to do what I wanted, but now with Kubuntu I can't get flash working, and everything else was trial and error, not just success.

](*,) Come on people I can't defend us Linux users when stuff like this happens, the Windows fanboys are killing me :-x

---

### Post by steveyos666 on 2006-11-18
By the way, I looked around a LOT before posting so don't get mad at me :D


Oh and while I'm at it, can anyone tell me how to remove old kernels with a little more detail than "synaptic linux-image obsolete"? I guess it's not that important, I don't wanna make another thread about it. But yeah, I search for linux-image and get maybe 15-20 things, and I'm not one to just randomly delete stuff.

---

### Post by steveyos666 on 2006-11-18
Oh man nothin? :(

---

### Post by Xamindar on 2008-01-24
I have a similar problem.  I installed the flash plugin but firefox doesn't see it.  How do you install the flash plugin in ubuntu without going to adobe's site and manually installing it?  

Forgive me, I am from gentoo where I do "emerge flash" and it just works. ;)

---

### Post by Xamindar on 2008-01-25
Man, no one?  Shouldn't this be a pretty important problem for the Ubuntu people to fix?  Flash has become pretty important to have these days.  Strange that Ubuntu would ignore fixing what is probably a simple fix.

---

### Post by AgentZ86 on 2008-01-26
> **Xamindar said:**
> Man, no one?  Shouldn't this be a pretty important problem for the Ubuntu people to fix?  Flash has become pretty important to have these days.  Strange that Ubuntu would ignore fixing what is probably a simple fix.

In Gutsy it use to install the plugin on it's own just like it should. go to a site that requires flash and the firefox plugin screen comes up and hit install plugin and that about it.

But anyhow you can do a couple things.

Install Gnash from the add/remove programs which will work for most flash sites and flash games etc. and utube, but I had a problem on yahoo video sites so I installed the one from adobe just do this:

But Read NOTES below at the bottom of my install instructions FIRST.

[LIST]
Downoad adobe flash to desktop [(click here)]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")[/LIST]
[LIST]
Then right click on the file and select extract here[/LIST]
[LIST]
Then open the folder and click the (flashplayer-installer)[/LIST]
[LIST]
Then select run in terminal[/LIST]
[LIST]
It will ask to install in something like /home/.mozilla select yes it won't hurt anything and not really sure if you need this step, it's the next step that is what you want[/LIST]
[LIST]
Sceen will ask if you want another install y\n etc. just select yes[/LIST]
[LIST]
Then it will ask for your plugin location and you will type /user/lib/firefox/plugins[/LIST]
you could also install perhaps in user/lib/mozilla/plugins as well shouldn't hurt anything either.


This will install for a user not all users I'm pretty sure but it works perfectly.
Just have to remember that your user firefox plugins are in the /user/lib/firefox/plugins
And my yahoo vids and most vids online work now.



**Before you install flash described above:**

NOTE: I would open synaptic and uninstall any Gnash, typically select Gnash-commons from within synaptic will unistall 2 other packages also.

**Additionally:** in synaptic I would install adobe flash - plugin- non free etc etc.

**And finally: be sure your browser is closed before you install flash**

I don't know if installing Gnash along with adobe flash will conflict or cause problems, I would like to know about that I may try it and post back on that topic as well.


I hope this helps.

---

