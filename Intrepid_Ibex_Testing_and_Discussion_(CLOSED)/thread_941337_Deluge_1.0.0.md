---
title: "Deluge 1.0.0"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by talkingwires on 2008-10-08
Since there's so many posts from people requesting feature freeze exceptions for their favorite programs, I thought I'd throw mine into the mix. [Deluge]("http://deluge-torrent.org/"), an excellent GTK Bittorrent client (and in my opinion, would make a much better choice than the crippleware currently included), hit 1.0.0 back in September. Version 0.5.9.3 is the version in the repos.

[Here's]("https://launchpad.net/~deluge-team/+archive") the Launchpad PPA if you want to try it out.

---

### Post by u-slayer on 2008-10-08
agree

---

### Post by wolfie2x on 2008-10-08
I currently use 0.5.9.3. Have you tested 1.0.0? Is it stable? what are the new features? The only thing the change log says is "Complete rewrite", and I really don't like those since that means tons of new bugs!

---

### Post by sloggerkhan on 2008-10-08
deluge 1.0 is pretty stable.
The 1 thing that's temperamental (not unstable) is blocklist importing from the web.
It does take up a fair amount of memory, but I also have 13 torrents open, most of them seeding, 1 dling, my comp's been up for 13 days and it's using about 90 megs of RAM counting both the daemon and the GUI front end. That's about 1/2 what firefox is using. So obviously neither is particularly RAM efficient. But it could be worse.

---

### Post by sonicb00m on 2008-10-08
Deluge started out as a good bit torrent client that got gradually more and more unstable as time went on. It was so buggy I totally aborted using it, much to my despair.

V1.0 is still buggy and lacks basic features that were in older versions. I wouldn't touch it with a barge pole.

I use Transmission now because the thing JUST WORKS.

In the past I would have lobbied for Deluge to be the default BT client but I am glad this never happened. It's just not stable enough and way too experimental right now. Maybe one day.

---

### Post by lovinglinux on 2008-10-08
> **talkingwires said:**
> Version 0.5.9.3 is the version in the repos.

I use Deluge and I love it, but I disagree about including version 1.0 on Intrepid. In my opinion is premature to include it.

Deluge 1.0.x still hasn't most of the plugins that work pretty well on 0.5.x branch. For instance, the Blocklist plugin doesn't work at all. It is included in the 1.0 version, it loads the blocklists but it doesn't block any IP, which could give a false sense of protection. Apparently is due to an issue with libtorrent.

---

### Post by olavjunior on 2008-10-08
> **sonicb00m said:**
> 
I use Transmission now because the thing JUST WORKS.


Really!?? I can not agree with you on that one. The latest transmission versions have been very buggy! I have to restart Transmission a couple of times to get it to start downloading, if not it will hang as if it wasn't connected to the net. I've also noticed some other bugs like old torrents earlier deleted showing up again. 

Currently checking out Vuze. It's heavy, but a neat design

---

### Post by ShirishAg75 on 2008-10-08
I had a talk with some of the developers on the forum and they (i.e. the developers) agree that it would be wise till 1.01 comes out which would happen by the end of the month or something like that. Then give request for packaging.

---

### Post by taavikko on 2008-10-08
> **talkingwires said:**
> Since there's so many posts from people requesting feature freeze exceptions for their favorite programs, I thought I'd throw mine into the mix. 

Feature freeze exceptions needs to be reported on [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu)
not here ;)

IMHO transmission is "cool" app, but it lacks few features compared to 
deluge, e.g bandwidth throttle access in notification tray icon
which can be found in deluge and much of my surprise, Mac port of transmission, so it's just missing features in GTK.

---

### Post by sonicb00m on 2008-10-08
> **olavjunior said:**
> Really!?? I can not agree with you on that one. The latest transmission versions have been very buggy! I have to restart Transmission a couple of times to get it to start downloading, if not it will hang as if it wasn't connected to the net. I've also noticed some other bugs like old torrents earlier deleted showing up again. 

Currently checking out Vuze. It's heavy, but a neat design

I am also using Vuze. Actually, if you switch to the classic mode is uses less resources than Azureus 2.5.0.4

I also had problems with recent builds of transmission but the latest one is working just perfectly for me.

Linux GUI clients have been quite disappointing over the last year.

---

### Post by Lorenz on 2008-10-08
I would not include it. I have plenty of of problems with 1.0 (makes surfing impossible, locks up internet).

---

### Post by Hairy_Palms on 2008-10-08
i love transmission personally, i used it well before it was the default, lightweight, stable, and i never found any bugs. even has individual file prioritys, something only it and azureus had when i started using em.

---

### Post by SledgeHammer_999 on 2008-10-08
I love deluge but I am staying with 0.9.5.4. The 1.0 version has speed problems and there are quite a few complaining in the deluge forums.

---

### Post by Golgoth on 2008-10-08
I dropped deluge since it froze my web access.

I use now transmission (getdeb package) which is lightweight and stable.

---

### Post by Delvien on 2008-10-08
+1 I agree, Deluge is great. Maybe suggest it for Jaunty ?

---

### Post by Saneless on 2008-10-08
> **Lorenz said:**
> I would not include it. I have plenty of of problems with 1.0 (makes surfing impossible, locks up internet).

Hmm, I had surfing issues, thought it was just someone on my router but it hasn't happened until I did Deluge 1.0.  Guess I'll use something else.

---

### Post by DarkDancer on 2008-10-08
I love Deluge, but had to drop back to an earlier version. The 1.0.0 version swamped my bandwidth and I couldn't make it stop.

---

### Post by meastp on 2008-10-08
Some (but not all) of the speed problems in Deluge 1.0 is caused by the default settings. E.g connections per second and total connections are both set to unlimited. If they could choose sane defaults... :)

---

### Post by talkingwires on 2008-10-08
> **wolfie2x said:**
> I currently use 0.5.9.3. Have you tested 1.0.0? Is it stable? what are the new features? The only thing the change log says is "Complete rewrite", and I really don't like those since that means tons of new bugs!Here's the proper changelog:[LIST]
[*]Core/UI split allowing Deluge to run headless as a daemon
[*]A redesigned GTK interface
[*]Migration to the upcoming libtorrent 0.14 release
[*]Stability improvements across the board
[*]New codebase which will allow for growth and less bugs
[*]A much improved queuing system
[*]New bugs for you to find
[/LIST]I like the last one. It's like an Easter egg hunt.

I've been using the new version for a couple of days now, and haven't had any problems with it. Few plugins have been ported though, so if you depend on a specific plugin, I'd hold off.

---

### Post by talkingwires on 2008-10-08
> **Saneless said:**
> Hmm, I had surfing issues, thought it was just someone on my router but it hasn't happened until I did Deluge 1.0.That was me, sorry. Why pay for Internet access when your neighbors leave their routers open?

---

### Post by sloggerkhan on 2008-10-09
I had no idea blocklists weren't working with the latest deluge even though they claim to load.

---

### Post by lovinglinux on 2008-10-09
> **sloggerkhan said:**
> I had no idea blocklists weren't working with the latest deluge even though they claim to load.

From Deluge's forum:

[quote="markybob"]
yes.  we've discussed this with libtorrent's developer and he's looking into it.  we'll get a fix out when we can[/quote]

---

### Post by canabal on 2008-10-09
This looks like a great program, much better than transmission, but if all the problems that are reported are true then stay away.

I personally hate transmission, there are not enough options anywhere.

I was using utorrent in wine up until I installed the 8.10 beta, then I switched to ktorrent as the beta installed the libraries anyway, I figured I may as well try it out.

Ktorrent works well, but it would be nice to have a fully functional torrent client of the like in gnome (hopefully deluge gets fixed up).

---

### Post by lovinglinux on 2008-10-10
> **canabal said:**
> This looks like a great program, much better than transmission, but if all the problems that are reported are true then stay away.

The versions (0.5.x branch) included in Hardy/Intrepid repositories are very stable and you can use them without fear. The problem is with version 0.9.x and 1.0.0, since Deluge is a complete rewritten application on those branches and thus expected to have bugs.

---

### Post by Golgoth on 2008-10-10
> **canabal said:**
> This looks like a great program, much better than transmission, but if all the problems that are reported are true then stay away.

I personally hate transmission, there are not enough options anywhere.

I was using utorrent in wine up until I installed the 8.10 beta, then I switched to ktorrent as the beta installed the libraries anyway, I figured I may as well try it out.

Ktorrent works well, but it would be nice to have a fully functional torrent client of the like in gnome (hopefully deluge gets fixed up).

and which option is missing in transmission?!

---

### Post by ugm6hr on 2008-10-10
> **sonicb00m said:**
> V1.0 is still buggy and lacks basic features that were in older versions. I wouldn't touch it with a barge pole.

I've found it to be pretty stable, but I agree that it has taken a step backwards on the features list :(

Most of the 0.5 plugins have not been written for the 1.0 versions, which is a shame.  I stuck with the previous version until recently (when I figures it was time to upgrade), but have decided to either go back to 0.5 or try something else.

Definitely not one as a default app on any distro.

---

### Post by meastp on 2008-10-10
Deluge 1.0.1 is out, and apparently, they have fixed what I found annoying. It should solve most speed issues.

---

### Post by likemindead on 2008-10-10
Deluge 1.0.1 will not work for me. When I try to add a torrent.... nothing happens. I haven't had any problems with 1.0.0 though. Guess I'll stick with it for now.

---

### Post by lovinglinux on 2008-10-10
> **meastp said:**
> Deluge 1.0.1 is out, and apparently, they have fixed what I found annoying. It should solve most speed issues.

Blocklist plugin still doesn't work.

---

### Post by Kokesh on 2008-10-10
The same here: Intrepid 1.0.1 ignores any added Torrents.

---

### Post by Starks on 2008-10-10
Deluge 1.0.0 cannot create torrents which really blows.

---

### Post by olskar on 2008-10-10
Deluge 1.0.0 is not mature enough to be in Intrepid. There are a lot of options that where in older versions that is missing and it is crashy. It actually crashed the first time I used it and that has never happened to me with older versions.

But I do think it will be a great client when it is ready.


Intrepid+1 :)

---

### Post by Starks on 2008-10-10
Motion for Intrepid+1

---

### Post by TenPlus1 on 2008-10-10
Deluge 1.0 is pretty sweet, works fine on my system, is easy to use and fast to download with...  No problems...

---

### Post by jojoman02 on 2008-10-10
deluge 1.0 is great, please remember that it just came out... plug-ins will follow, just bug some of the plug-in devs, lol, j/k of course... i think rss plug-in is most important (after blocklist which is already included in 1.0).


another thing to note, deluge daemon is crashing after installing it on latest intrepid, Oct 10, 2008 3pm AST w/ latest updates. this is why people are reporting that torrents don't get added, because the daemon is not running in the BG. someone please check on this, just run 1.0.1 on latest intrepid. i had to uninstall 1.0.1 and install 1.0.0 to get deluge functioning again.

---

### Post by mallegonian on 2008-10-10
@jojoman02
If you look at the daemon log file it says that it can't load or update the state file because of an out of range array or something to that effect.
I ran 'mv ~/.config/deluge/state ~/.config/deluge/state.old; touch ~/.config/deluge/state' and 1.0.1 is working for me now.

Yay!

Edit: After that command, you'll need to start deluge and re-add the torrents from ~/.config/deluge/state.old , then let it recheck the files.

Edit2: Damn. I restarted it and it is doing the same thing. *headdesk*

Edit3: Deluge 1.0.2 was released this morning, the post talks about fixing a bug preventing sessions from being loaded properly.

---

### Post by DPic on 2008-10-11
1.0.2 is out, can we plz have
kthxbai

---

### Post by mvoncken on 2008-10-17
> **Starks said:**
> Deluge 1.0.0 cannot create torrents which really blows.

It's in the future 1.1 : [http://dev.deluge-torrent.org/browser/trunk/ChangeLog](http://dev.deluge-torrent.org/browser/trunk/ChangeLog)


The blocklist is fixed in 1.0.3 :
[http://dev.deluge-torrent.org/browser/branches/1.0.0_RC/ChangeLog](http://dev.deluge-torrent.org/browser/branches/1.0.0_RC/ChangeLog)

---

### Post by likemindead on 2008-10-17
Yep, thankfully the 1.0.2 update fixed everything for me.

^_^

---

### Post by IGITIHI on 2008-10-19
There's definitely at least one major problem that wasn't fixed. I am now using Deluge 1.0.3 and I am still facing it: when deluge tries to check big incomplete torrents (larger than 1 GB or so), it just says "checking" or "checking 0,00%" for ever. Even if I remove and re-add the torrent, the same thing happens. There doesn't seem to be a way to make the torrent continue downloading.

Is there a fix or a workaround? This problem is serious and I may be forced to use another client :cry:

---

### Post by fjf on 2008-10-19
That is why I dont use it anymore.  That, and the fact that it gives "error" if you close the program or the system before ending the download.

Install ktorrent, make the incomplete downloads folder the one where you have the incomplete torrent and open the torrent file with ktorrent.  It will check it and go on.

---

