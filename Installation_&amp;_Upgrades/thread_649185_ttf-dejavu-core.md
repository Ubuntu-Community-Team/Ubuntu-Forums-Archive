---
title: "ttf-dejavu-core"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by Annigma on 2007-12-24
Hi.
I've searched for a solution to this problem to no avail. I'd be grateful if someone can help.

I stupidly succumbed to clicking the 'upgrade' button from Feisty to Gutsy a while back and something went wrong during install. I ended up with a blank blue (quite a nice, soft blue actually but anyway..) screen. Yesterday I decided to make a concerted effort to try and get it working again and used 'sudo apt-get update' then 'sudo dpkg --configure -a' which got my GUI back! Yay! 

I now have a working system, but had a few errors thrown at me including acpid, powermangement, ttf-dejavu and ubuntu-desktop. I sorted the first few but can NOT get rid of these package complaints:

ttf-dejavu-core
ttf-dejavu-extra
ttf-dejavu
ubuntu-desktop

I can surf, post, play mahjongg (lol), open the GIMP... play about with settings, use Synaptic, etc.... but the dejavu stuff still isn't right. It wasn't interfering much with anything I want/need to do yet, but then I tried to play some music in Rhythmbox and each track I tried to play got a 'no entry' sign next to it and refused to play. I can play stuff in Youtube, with sound, so my sound card must be okay... 
I went to Synaptic and tried to reinstall Rhythmbox, but I got errors about that bloomin font thing again! Why should a pesky font cause so much trouble..? I can't uninstall it because the desktop depends on it and I can't remove that... can I...?

Any help would be appreciated.

:)

---

### Post by Annigma on 2007-12-26
Any suggestions..?

---

### Post by Partyboi2 on 2007-12-26
I don't think uninstalling and then reinstalling these packages
ttf-dejavu-core
ttf-dejavu-extra
ttf-dejavu
is going to cause a system melt down :) I tested it out on my machine and the uninstall and reinstall went ok, except I had to reinstall vlc. When you go to remove the packages it will tell you what other packages will be removed as well. Just check what the other packages are before proceeding. If still not sure wait for another opion.

---

### Post by K.Mandla on 2007-12-26
ubuntu-desktop is just a metapackage, so it should be removable. If it's not, then something else you have installed is pointing at it, holding it in place.

I'm also surprised the Dejavu fonts gave you such a hard time. I manually removed those three from a Xubuntu machine and it worked, although it wanted to tear out xubuntu-desktop too. Try this from a command line and maybe it will fly.

```
sudo aptitude remove --purge ttf-dejavu ttf-dejavu-core ttf-dejavu-extra
```
Be aware that it might force the removal of a lot of other stuff; if that's the case and you don't like what it suggests, tell it to abort and nothing will be changed.

---

### Post by Annigma on 2007-12-28
Thank you for your replies.
I tried uninstalling them from synaptic - it's just easier: is there a difference..? - and accepted anything else that it suggested would be removed. It failed giving me the following (which I had to write down! :shock:):

/etc/defoma/hints/ttf-dejavu-core.hints: Unable to open, or empty
dpkg: error processing ttf-dejavu-core (--remove)
  subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
ttf-dejavu-core

I assume that was the 'remove' command. I then tried 'complete removal', which I assume is the 'purge' command..? It gave me virtually the same error. (had 'purge' instead of 'remove' I think..)

I can't get firefox to fire up in Ununtu now (though strangely I'm using Opera atm as Firefox wouldn't work in XP either. My other half's using Firefox on another machine though, so.. *shrug*). 

I tried one of my other startup options from the 'Gnome kernel'.........? - the screen where you choose which OS to load.. I seem to have an ever-growing choice of these.. would be nice to know what that's all about too.. I have:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic  (recovery mode)
Ubuntu 7.10, kernel 2.6.22-16-generic
Ubuntu 7.10, kernel 2.6.22-16-generic  (recovery mode)
Ubuntu 7.10, kernel 2.6.22-15-generic
Ubuntu 7.10, kernel 2.6.22-15-generic  (recovery mode)
Ubuntu 7.10, memtest86+

and XP (which I'm on now :( )

Since I didn't follow your instructions Mandla (though I'm guessing what I tried was the same..?), I'm off to try that now.

Thanks again for your help. Please don't hesitate to post other suggestions :D

EDIT: Nope, didn't make any difference. Gave same error. *pouts*

---

### Post by Annigma on 2007-12-29
Any ideas...?

---

