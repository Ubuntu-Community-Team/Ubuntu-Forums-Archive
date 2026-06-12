---
title: "Deluge torrent worked fro 1 day,not anymore"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by BadaR on 2007-04-21
Hello guys,i am having problem with my Deluge Torrent client on my new Feisty Fawn.It worked yesterday,i left my pc at night.When i came back in the morning,pc lagged,so i did restart manually (the button),because i didn't had any choise.I am really beginner in linux,so here goes the log:

[B]max@max-h4ck:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)
max@max-h4ck:~$ 
[/B]

And screenshot
[IMG]http://i14.tinypic.com/44v56vq.png[/IMG]

P.S i installed from .deb on [http://deluge-torrent.org/](http://deluge-torrent.org/) . Please give me some advices to get my deluge back to life,i find it the best torrent client

---

### Post by iamtherealwoody on 2007-04-24
I am having the same exact problem.  Was working great this morning, added a new torrent, move one down to bottom and paused it, then one of my previous torrents werent showing up in the display.  I shut down deluge and restarted it, it wouldnt come up. Restarted the computer and I get the same error.

---

### Post by willskills on 2007-04-24
Same here guys; I tried this in Edgy, have also tried in Feisty - getting the same problem.

---

### Post by iamtherealwoody on 2007-04-24
found a fix here on this thread 
[http://ubuntuforums.org/showthread.php?t=383420&highlight=boost%3A%3Afilesystem%3A%3Afilesystem_error]("http://ubuntuforums.org/showthread.php?t=383420&highlight=boost%3A%3Afilesystem%3A%3Afilesystem_error")
This is what I did
> rm ~/.config/deluge/*.state
Deluge now opens up but all the torrents I had running arent running but I didnt lose any data, i renamed the folder i had everything downloading to just to be safe.  

matt

---

### Post by nphx on 2007-04-25
Dude forget deluge, use Transmission: [http://transmission.m0k.org](http://transmission.m0k.org)  IT IS AWESOME!!!

dowload the deb packages:

Edgy Eft:
[http://transmission.m0k.org/forum/viewtopic.php?t=1506](http://transmission.m0k.org/forum/viewtopic.php?t=1506)

---

### Post by iamtherealwoody on 2007-04-25
nphx,
Im trying out Transmission now, your link didnt work for me so I found the deb at getdeb.net.
Deluge just crashed again so its worth a try.

Matt

---

### Post by nphx on 2007-04-25
> **iamtherealwoody said:**
> nphx,
Im trying out Transmission now, your link didnt work for me so I found the deb at getdeb.net.
Deluge just crashed again so its worth a try.

Matt

getDeb has the older version .70, Transmission 0.71 just came out. Sorry about the link. 
I'll attach it to this post. 

**Feisty Fawn Transmission 0.71** attached:

---

### Post by iamtherealwoody on 2007-04-26
Thanks nphx,
been using transmission for one day now, seems very light weight, hasnt crashed once or suck up resources.  i think i can remove deluge now.

Matt

---

### Post by zvacet on 2007-04-26
I installed Transmission myself and i find it is very well torrent client.In fact best i ever run,but that is not answer to the people who want to run Deluge.If you want to fix your problems with feluge uninstall it and go to the hidden folders in your home directory.There you will find folder named .config and inside itis deluge folder.Delete it and install Deluge again.

---

### Post by kxs on 2007-05-07
nphx: thanks for the build :)

---

