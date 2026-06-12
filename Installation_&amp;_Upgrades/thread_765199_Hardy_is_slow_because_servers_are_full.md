---
title: "Hardy is slow because servers are full?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Afkpuz on 2008-04-24
Hello.  I've switched to Hardy and it seems to be terribly slow.  Am I right to assume that it is just because it's opening day?  For example, I can't download the restricted drivers for my NVidia card.  It just stalls at the download bar.  I also can't get any updates.  Is this just high server load at the moment?

---

### Post by st0nedpenguin on 2008-04-24
Yup, servers are probably packed to the brim right now with people upgrading/pulling down new packages.

It's running slow as all hell here while I'm trying to slap dmraid on a fresh install so I can reboot then spend the better part of a month updating. :|

---

### Post by keithcleaver on 2008-04-24
I'm guessing so. AFIAK, everything runs off the single server (iso downloads, torrents, updates etc.)

Question while I'm thinking about this: is it a better idea to maybe use a server in a place that won't get as much traffic right now, eg the Australasian servers?

EDIT: To answer my own question, I'm using an Australian server now, and things are moving along at about three times speed of the European servers.

---

### Post by st0nedpenguin on 2008-04-24
GB server is so slow right now I may as well rewrite the apps myself and compile. :(

---

### Post by munky99999 on 2008-04-24
Just flying along at about...

[IMG]http://img520.imageshack.us/img520/4204/screenshotut2.gif[/IMG]

haha main server is being ddosed by everyone basically.

I'm usually connected to uofwaterloo or similar. It reset itself seemingly.

---

### Post by JustinJS on 2008-04-24
Well, my upgrade took a total of ~ 4 hours to Download and install. Now I trying to download some packets and its took 2:13 just to do a get-apt update.

---

### Post by oldgoatroper on 2008-04-24
> **keithcleaver said:**
> I'm guessing so. AFIAK, everything runs off the single server (iso downloads, ***torrents***, updates etc.)


There are torrents available? Where? 

I would think that a torrent would be far less likely to be affected by a slow server once several seeds had been established.

---

### Post by Haluci on 2008-04-24
> **oldgoatroper said:**
> There are torrents available? Where? 

I would think that a torrent would be far less likely to be affected by a slow server once several seeds had been established.

The torrents are available for the CDs, not for the updates.  You can find the torrents in the [release page]("http://releases.ubuntu.com/8.04/").

Oh, and if you think your speed is bad, just look at mine:

[IMG]http://img388.imageshack.us/img388/7060/screenshotdistributionutw7.png[/IMG]

---

### Post by keithcleaver on 2008-04-24
> **oldgoatroper said:**
> There are torrents available? Where?


[http://releases.ubuntu.com/releases/8.04/]("http://releases.ubuntu.com/releases/8.04/")

Link for torrents

---

### Post by oldgoatroper on 2008-04-24
> **keithcleaver said:**
> [http://releases.ubuntu.com/releases/8.04/]("http://releases.ubuntu.com/releases/8.04/")

Link for torrents

Thanks, guys...

Unless I'm blind, I didn't see a link to this on the main download page.

---

### Post by st0nedpenguin on 2008-04-24
After seeing the pics in this thread, I'm glad I grabbed the torrent for a fresh install. :x

For me it takes around 5 minutes to actually find the repo and start the download, then it crawls in at an amazingly slow speed.

WTB Thunderbird.

---

### Post by forkd on 2008-04-24
I didn't even bother trying to download from the server.  I set up my new FIOS on the torrent and had both the desktop and the alternate images in less than 45 minutes.  Of course I've left them on @ home uploading like mad to help people get their images downloaded.  

These are the days it really helps to participate in the torrent to give a little bit of bandwidth back to the community.  Tonight I will probably throttle down my torrent upload speed so I can surf the net myself. :)

have fun :)

---

### Post by JarG0n on 2008-04-24
> **Haluci said:**
> The torrents are available for the CDs, not for the updates.  You can find the torrents in the [release page]("http://releases.ubuntu.com/8.04/").

Oh, and if you think your speed is bad, just look at mine:

[IMG]http://img388.imageshack.us/img388/7060/screenshotdistributionutw7.png[/IMG]

Having the update system utilize bittorrents for future upgrades would be interesting.  Has anyone proposed this yet?

---

### Post by Onderstekop on 2008-04-24
> **keithcleaver said:**
> EDIT: To answer my own question, I'm using an Australian server now, and things are moving along at about three times speed of the European servers.

Works like a charm!

Edit: sort of.

---

### Post by thebigbluecan on 2008-04-24
Yup Slow Here... Download of .iso took an hour, normally 10 min or so...Got it installed took ten minutes to refresh Synaptic Package manager... Won't load nVidia driver... Hopefully this slowdown is why. so now I have a computer that is running at 800 X 600... :( Lol  Used to (1680 x 1050) And its hard to do stuff on such a low res screen. Some buttons at the bottom of the window are hard to get to.  (Got to do the alt click to move windows off the screen to get to the bottom settings.) Hopefully this Hiccup ends soon. :popcorn:

---

### Post by DROP on 2008-04-24
I wasn't able to connect to the US archive at all. I looked at the list of mirrors here:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

The Rochester Institute of Technology mirror is pretty fast for me.
There are lots of options to choose from though...

---

### Post by munky99999 on 2008-04-24
I lost connection or something because I just came back and it said failed to fetch stuff. So I just restarted :(

Fetching 1 of 15 and it's not going anywhere. :(

---

### Post by munky99999 on 2008-04-24
> **DROP said:**
> I wasn't able to connect to the US archive at all. I looked at the list of mirrors here:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

The Rochester Institute of Technology mirror is pretty fast for me.
There are lots of options to choose from though...

Sweet thanks I found one that's uptodate now and it's downloading well.

---

### Post by brodae on 2008-04-24
Yeah, I recommend going to a different server. It worked great for me.

---

### Post by HangukMiguk on 2008-04-24
Meh, unless I figure out how to change my mirror for the archive, I'll be waiting a few days to update i guess.

---

### Post by Cauda_Draconis on 2008-04-24
The slow servers wouldn't have anything to do with ```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-xcb1_1.1.3-1ubuntu2_i386.deb
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
``` when trying to reinstall compiz (or do almost anything), would it?

Edit: I was in Synaptic, but it happens in terminal and in update manager, too.

---

### Post by Hooya on 2008-04-24
This is all pretty funny.  I decided last week, without even knowing that an LTS was around the corner, that I would start migrating to Linux from Vista.  I decided on Ubuntu because word on the net had been favorable and I wouldn't know the difference right now.  So last weekend I picked up the release candidate and installed it on Monday.

Kinda glad I didn't wait.  I used the torrent download of the RC and it downloaded in about an hour and have had no issues installing software this week to get things going.  I'm just doing this as a test install to see how I like it and so far there are only a couple things keeping me from migrating completely.

I'm planning on doing a fresh Vista and Ubuntu install in a couple weeks when the insanity of the end of semester and of the 8,04 release cools off.

I have officially joined the bandwagon.

---

### Post by Cauda_Draconis on 2008-04-24
> **HangukMiguk said:**
> Meh, unless I figure out how to change my mirror for the archive, I'll be waiting a few days to update i guess.

Go to System>Administration>Software Sources, and on the first tab, at the bottom of the list of checkboxes, it says "Download from:" with a dropdown menu beside it. You can pick "other" and it'll take you to a big list of servers organized by country.

---

### Post by nmsu on 2008-04-24
Umm, this is bad.  I did a clean install of 7.1 because i like them for my web servers.  Now I can not get the thing any updated packages.  I got apache, but anything else coming from ubuntu is like not happening.  No updates from them today.  :(

---

### Post by HangukMiguk on 2008-04-24
> **Cauda_Draconis said:**
> Go to System>Administration>Software Sources, and on the first tab, at the bottom of the list of checkboxes, it says "Download from:" with a dropdown menu beside it. You can pick "other" and it'll take you to a big list of servers organized by country.

Killer (Hopefully).  Thanks.

---

### Post by thebigbluecan on 2008-04-24
Im getting it along now... Got my drivers installed and getting it going good now. Got compiz all configured and im not running at 800 x 600 res now :guitar: Now just getting things the way i want it.:popcorn:

---

### Post by CWaugh on 2008-04-24
Alright, I finally got it going and it is actually cruising along pretty well

[IMG]http://img114.imageshack.us/img114/3604/screenshotdistributionugi9.png[/IMG]

---

### Post by keithcleaver on 2008-04-24
> **keithcleaver said:**
> EDIT: To answer my own question, I'm using an Australian server now, and things are moving along at about three times speed of the European servers.

> **Onderstekop said:**
> Works like a charm!

Edit: sort of.

UPDATE: Everything went OK for me until about halfway through when the speed cut in half! The "55 Minute" download turned into a near 2 and a half hour slugathon, but hey, at least I finally have it.

---

### Post by Knertified on 2008-04-24
I used the method above to change my source to US MIT. I still had problems with the GUI updater so I ran "sudo apt-get update" then "sudo apt-get upgrade" from a shell and its moving along nicely. About 700k/sec.

---

