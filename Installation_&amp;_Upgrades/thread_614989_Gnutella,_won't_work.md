---
title: "Gnutella, won't work"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Chappy7777 on 2007-11-16
I just installed Gnutella 96.3 because that is what's on 7.04  The last time I did this on a previous install of 7.04, it worked great. The difference being two different PCs, but more to the point, I think is the fact that I am now on Cable Modem instead of Dialup. Since I am brand new to hi-speed I'm having trouble setting Gnutella up. With dialup it seemed to pretty much connect itself. 

I went thru the preferences doing my best to fill in the blanks, but Gnutella isn't connecting. I am afraid I am going to mess up my connection to the net if I'm not careful.

So: two questions. 
1) help w/the setup of Gnutella

2) otherwise, how do I uninstall Gnutella, now that I have it installed. Do I just go to  Apps/Add Remove and figure. 

I have never uninstalled an App in Ubuntu. So far. I need to learn how. Obviously.

---

### Post by Chappy7777 on 2007-11-16
blump

---

### Post by santiagoward2000 on 2007-11-16
> **Chappy7777 said:**
> blump
We normally say *bump* :lolflag:

> **Chappy7777 said:**
> 2) otherwise, how do I uninstall Gnutella, now that I have it installed. Do I just go to  Apps/Add Remove and figure.

Well, I don't know how to configure it, but if you want to uninstall it, go to System/Synaptic Package Manager, There, look for the program, click on the box and select "Mark for Complete Removal" and then "Apply".
I hope someone can help you to configure it.

---

### Post by Chappy7777 on 2007-11-16
Thnx Santgia, I just finished doing that. Of all things I used the HELP files, and doing just what you said to do.

I would still like to get it working as I love music. Since I live in Canada I am not breaking the law, since the gov't has quite figured out what to do about the whole P2P thing. It's called a Grey area. We had the same thing with C band satellites years back. After most channels were blocked, my local newspaper was publishing weekly numbers to reset the code and get the channels again. I always thought that seemed weird.

There is a fairly good legal site w/a hefty number of MP3s at $.20 a song. S songs for $1 isn't a bad price, and it avoids all the scarey parts (especially in Windows) of file sharing. You start by giving them as little as $20 to start an account, and as you download songs they deduct from that. 

The site is called    [http://mp3skyline.com](http://mp3skyline.com)

---

### Post by santiagoward2000 on 2007-11-16
Well, you're welcome! Sorry I couldn't help you to get it running.

---

### Post by cbiere on 2007-11-18
Your best option is to upgrade to 0.96.4. The older version is now over a year old and will no longer bootstrap on its own. Thus if you scrap your ~/.gtk-gnutella directory (very bad idea), it will not know any peers to connect to, just hover there and you'll have to bootstrap it manually.

If you don't know anyone else using Gnutella you could connect to, you can visit **[http://gcachescan.jonatkins.com/](http://gcachescan.jonatkins.com/)** and pick any of the cache URLs. Append **?client=blah&version=1.0&hostfile=1** to it, load it in your web browser and you'll get a list of peer addresses. For example, **[http://gwc.eod.cc/skulls.php?client=blah&version=1&hostfile=1](http://gwc.eod.cc/skulls.php?client=blah&version=1&hostfile=1)**.
If it doesn't work immediately, just pick any of the others. You shouldn't have to do this again, if you use Gnutella at least every few days.

If the above does not work anymore, you can also use Google to find peers:
[http://google.com/search?q=gnutella+network+gnucdna](http://google.com/search?q=gnutella+network+gnucdna)

This should work with any Gnutella software. It may look somewhat complicated on first sight but with this in mind, you should never have a problem to get connections again.

---

