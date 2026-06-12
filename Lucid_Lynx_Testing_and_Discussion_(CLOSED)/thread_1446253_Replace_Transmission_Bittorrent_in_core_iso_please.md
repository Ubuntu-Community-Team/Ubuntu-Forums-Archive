---
title: "Replace Transmission Bittorrent in core iso please??"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zengeos on 2010-04-03
It seems, at least for me on my wireless connection, that when I try downloading via Transmission, that none of my other programs can access the Internet, or become so slow that they time out.

However, with QbitTorrent this does not seem to be a problem.  Has anyone else experienced this issue?  Is it a setting in Transmission I can adjust?

OR might Transmission be replaced by QbitTorrent (asuming room on the install CD?

---

### Post by mikewhatever on 2010-04-03
It most likely is you configuration of Transmission. Anyway, asking to replace it in the iso just because it doesn't work for you seems a little arrogant, don't you think?

---

### Post by emarkay on 2010-04-03
> **mikewhatever said:**
> It most likely is you configuration of Transmission. Anyway, asking to replace it in the iso just because it doesn't work for you seems a little arrogant, don't you think?

Aw, be nice, they are a "20 bean noob"  :)

Use system monitor to confirm your connection and data transfer amounts, and yes, check your Transmission settings - try settng the upload and download amounts insanely slow and see if your Internet returns.

---

### Post by splicerr on 2010-04-03
> **mikewhatever said:**
> Anyway, asking to replace it in the iso just because it doesn't work for you seems a little arrogant, don't you think?

Hahaha yes it does. What was he thinking?!?

@zengeos

There's absolutely no chance that's going to happen. If you want it included in an ISO, use something like UCK and build your own ISO.

---

### Post by Starks on 2010-04-03
I'm having the same problem and I'm rather annoyed that the question about settings hasn't been addressed.

---

### Post by zengeos on 2010-04-04
Suggestion wasn't meant to sound arrogant, nor was it intended to annoy the senior posters.

However, it doesn't belie the fact for me, at least, that having tried using Transmission with it's default settings on my typical 1megabit plus connection, it let few peers connect. In addition, as stated in my initial post, Qbittorrent just works.  400+kb/s in Qbittorrent, while multitasking in other web apps.

I honestly don't think it's a silly question. Neither do I think it's something that should be ruled out.

I even lowered the max connections in Transmission to 25 peers. That did not stop the near complete choking of my other internet connections.

Fix Transmission so it works, explain what settings are wrong or fix the default settings so they work.

Of course, Transmission isn't an Ubuntu specific program, but a bundled program, so the problem likely isn't something that can be fixed by Canonical, but must be fixed upstream. Which leads me BACK to my original suggestion...remove Transmission and switch to Qbittorrent or another Torrent app that works. KTorrent is fine. Azureus is ok tho a bit heavy.

---

### Post by cariboo on 2010-04-04
If there's a problem with Transmission, you should report a bug. If the devs don't know about a problem, they can't do anything about it.

I use Deluge, so I haven't seen the problem.

---

### Post by Linuxforall on 2010-04-04
Transmission is the best most easiest to configure client out there, I rate it better than uTorrent which in itself is an excellent client, you can reduce the number of conneciton in Transmission network, its your router which is unable to handle multiple connections.

Also Transmission makes fale IP blocking a breeze which no other client does, it downloads and updates IPBLOCKLIST automatically, it also automatically auto updates it.

---

### Post by kerry_s on 2010-04-04
the problem with transmission is the upnp, it's always sucked.
best thing is to turn that off & open a port in your router, after that it should be fine.

---

### Post by Mr. Picklesworth on 2010-04-04
> **Linuxforall said:**
> Transmission is the best most easiest to configure client out there, I rate it better than uTorrent which in itself is an excellent client, you can reduce the number of conneciton in Transmission network, its your router which is unable to handle multiple connections.

Also Transmission makes fale IP blocking a breeze which no other client does, it downloads and updates IPBLOCKLIST automatically, it also automatically auto updates it.

In addition, Transmission has an awesome upstream developer(s?) who is active in Launchpad :)
(And it has a considerably prettier, more consistent and Gnomey interface than the others).

Try using the Temporary Speed Limits option, or head to the Network tab and change the maximum number of peers per torrent. Chances are your other client has different defaults.

---

### Post by executorvs on 2010-04-04
I've never liked transmission all that much. That said, I must admit I have noticed it improving at a fair pace and keep an eye on it for that reason. my preferred client is deluge.

---

### Post by Starks on 2010-04-04
> **cariboo907 said:**
> If there's a problem with Transmission, you  should report a bug. If the devs don't know about a problem, they can't  do anything about it.

I use Deluge, so I haven't seen the problem.
Also affects Deluge for me in case you were wondering and I have 100Mbit college connection.

---

### Post by mikewhatever on 2010-04-04
> **zengeos said:**
> ...

Fix Transmission so it works, explain what settings are wrong or fix the default settings so they work.

Of course, Transmission isn't an Ubuntu specific program, but a bundled program, so the problem likely isn't something that can be fixed by Canonical, but must be fixed upstream. Which leads me BACK to my original suggestion...remove Transmission and switch to Qbittorrent or another Torrent app that works. KTorrent is fine. Azureus is ok tho a bit heavy.

Well, what if the defaults of one of the programs you suggested don't work for someone else? Should that person demand it removed from the iso? And if that's not silly, then what is? There are lots of bittorrent clients in the repositories, and if you absolutely can't make Transmission work, you can easily remove it and install you one you like. If you want help with the settings, start by posting your upload/download speeds, as provided by the ISP.

---

### Post by mikewhatever on 2010-04-04
> **Starks said:**
> Also affects Deluge for me in case you were wondering and I have 100Mbit college connection.

Many colleges don't allow bittorrent, and other file sharing protocols, as it gets them in trouble with copyright owners and puts a strain on their networks.

---

### Post by Linuxforall on 2010-04-04
> **mikewhatever said:**
> Many colleges don't allow bittorrent, and other file sharing protocols, as it gets them in trouble with copyright owners and puts a strain on their networks.

That means you are firewalled and therefore no inbound so files can't be shared so most trackers ban you and you have slow speed.

---

### Post by Linuxforall on 2010-04-04
> **kerry_s said:**
> the problem with transmission is the upnp, it's always sucked.
best thing is to turn that off & open a port in your router, after that it should be fine.

UPnP never gave me an issues here with netgear and dlink routers, UPnP is also dependent on router firmware itself and some routers are notoriously flaky closing ports on their own.

---

### Post by Dayofswords on 2010-04-04
> **Linuxforall said:**
> That means you are firewalled and therefore no inbound so files can't be shared so most trackers ban you and you have slow speed.

you need to enable encrytion to get past that (i needed the iso for school... so i learned how)

---

### Post by JCoster on 2010-04-04
Limit the upload speed.  If I let the uploads max out on my connection it throttles my download speeds.

---

### Post by blackSP on 2010-04-04
I like Deluge better so I always replace Transmission. No big deal...

---

### Post by cb951303 on 2010-04-04
I had the same problem with my wireless router but didn't care much since I almost always use a wired connection.

---

### Post by WakkiTabakki on 2010-04-15
> **zengeos said:**
> It seems, at least for me on my wireless connection, that when I try downloading via Transmission, that none of my other programs can access the Internet, or become so slow that they time out.

However, with QbitTorrent this does not seem to be a problem.  Has anyone else experienced this issue?  Is it a setting in Transmission I can adjust?

OR might Transmission be replaced by QbitTorrent (asuming room on the install CD?

+1 Arrogant or not, I don't care - I want something that works... 
I've had precisely the same problem with Transmission from day 1 - many different computers, many ubuntu versions and on different networks. As soon as Transmission start downloading anything (even 0.5 kb/s) anything else on the comp accessing the net grinds to a complete halt and times out.

Capping up or downloads in transmission makes no difference at all, nor does reducing the number of connections. I've gone through the settings backwards and forwards many times over a long period to no avail. I've read many posts and bug reports with similar sentiment, though none provide any workaround or even suggests a reason for it happening (if I have missed any such report or post: please let me know, I would love so find a solution this!).

As a result, I run wine+uTorrent. Which in itself is a small pain as it doesn't integrate well in Gnome desktop.  With uTorrent, a similar problem occurs, but only when the upload  speed approaches the max bandwidth of my connection; setting the upload  cap to about 80% of my upstream bandwidth fixes that problem. I guess when you guys say "check your Transmission settings" this is the problem you're referring to, however, that is not the issue I'm having (and other with me, I assume).

Just my 2 &#8364;-cents. 
Cheers
/N

---

### Post by dudude on 2010-04-15
Just reiterating what JCoster said, throttling Transmission's upload speed makes all of my bandwidth/network problems that are related to Transmission go away.

Throttling the download speed has very little affect on the performance of other programs that need network/internet access.

---

### Post by kabloink on 2010-04-15
I had similar problems with transmission. It was basically killing my router. Nothing else could access the internet. In my case it turned out to be dht. Disabling DHT solved the problem for me.

---

### Post by Longinus00 on 2010-04-16
DHT will basically spam a bajillion UDP connections once it's up and running. Many routers aren't able to deal with this for one reason or another but this is just how DHT works so if it gives you problems feel free to turn it off.

---

