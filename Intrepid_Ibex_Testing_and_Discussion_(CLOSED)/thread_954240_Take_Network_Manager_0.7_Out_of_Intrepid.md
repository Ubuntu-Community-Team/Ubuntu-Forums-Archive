---
title: "Take Network Manager 0.7 Out of Intrepid"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by american.swan on 2008-10-21
Poll:

Take NM 0.7 out of Intrepid...too many problems?

---

### Post by PinkFloyd102489 on 2008-10-21
Thank you for your elaborate, thought-provoking post. I'll be sure to trash my installation right away because of this shocking information.

*cruises right along with no problems*

---

### Post by dasunst3r on 2008-10-21
I've been cruising along just fine as well.  I don't see any reason why NetworkManager 0.7 should be taken out.  Perhaps you should elaborate on what problems you are encountering and what you have done to try and resolve them before writing something like this.

---

### Post by Jim March on 2008-10-21
I'm not sure I'd go so far as to say "rip it out" but, there are indeed problems.  In my case, trying to use my cellmodem connection (Verizon-based Kyocera KPC680) causes NM7 to crash so hard that only a restart will allow any networking at all.

But, it's OK for WiFi and it doesn't object to using a wvdial script to start the cellmodem if I first close any active WiFi connections.  So it's not TOO annoying.

I say leave it in, hope they fix it somewhere in Intrepid's life-cycle, meanwhile make sure instructions for Wicd installation are widely available.  The only reason I'm not running Wicd right this second is that I keep hoping each new NM7 update will fix it...

---

### Post by american.swan on 2008-10-21
> **dasunst3r said:**
> I've been cruising along just fine as well.  I don't see any reason why NetworkManager 0.7 should be taken out.  Perhaps you should elaborate on what problems you are encountering and what you have done to try and resolve them before writing something like this.

This thread is very informative to me.

" *cruises right along with no problems* 	"
The previous post before yours was the first time I had read anywhere of it working. The bug list as far as I have read is rather long.   PinkFloyd102489  	 		probably is using DHCP rather than Static, but of course I don't know.

I also am thinking of updating to 8.10beta and use static IP.  As you might imagine I am rather **nervous** to upgrade if I am going to loose my internet connection.  I am on a machine where I can't exactly afford to have many problems.  Maybe their needs to be a way to shut off NM, besides removing it.

Also my first post should have had a question mark instead of a period at the end of the comment.

Perhaps throwing 0.7 into Ubuntu is Ubuntu's way of "speeding up the slow development" of NM.

Either way I am sorry for upsetting anyone due to my fear of installing the beta right now.  If it weren't for NM I'd already have upgraded.

---

### Post by sloggerkhan on 2008-10-21
It certainly has a few issues, particularly if there are multiple networking devices. For example, if you have wireless and wired active in the same location, it will show both as active even when it only is using one.

---

### Post by Jim March on 2008-10-21
The good news is that Wicd 1.5.3 works like a champ in Intrepid, so you have a way out if NM7 blows up on you.

---

### Post by Eclipse. on 2008-10-21
Everybody wanted it in hardy, now that its in intrepid people want rid of it lol.

---

### Post by forcecore on 2008-10-21
just fix it because it is CRITICAL, now i can finally use ubuntu with full power with my broadband.

---

### Post by american.swan on 2008-10-21
> Jim March              **Re: Take Network Manager 0.7 Out of Intrepid**
         The good news is that Wicd 1.5.3 works like a champ in Intrepid, so you have a way out if NM7 blows up on you.
That is good to know.  So if I upgrade, I can remove the NM packages and use Wicd???

That is very informative.  Maybe Wicd should be the default Network manager then??

---

### Post by Gina on 2008-10-21
I recommend a fresh new install for trying (or using) a new version - in a dual (or multi) boot setup with the current version remaining available, just in case of any problems.  Then you can always boot into a tried and tested system that you know works for you.

---

### Post by american.swan on 2008-10-21
> **Gina said:**
> I recommend a fresh new install for trying (or using) a new version - in a dual (or multi) boot setup with the current version remaining available, just in case of any problems.  Then you can always boot into a tried and tested system that you know works for you.


Wouldn't that be similar to upgrading and then going back to a previously installed Kernal?  I could be way off.

---

### Post by Foaming Draught on 2008-10-21
Not only do I have no problems with wired (Broadcom 10/100 on an Acer Travelmate 3002WTMi, DHCP) or wireless (Intel 2200), but my Samsung A411 3G mobile which used to require a complicated script and pon/poff in terminal, is now picked up by NM 0.7 and connects at 1.3 ish mbps.

I'm a NM fan.

(Having posted this, I'm about to reboot after a NM update ..... ;)   )

---

### Post by Jim March on 2008-10-21
> That is good to know. So if I upgrade, I can remove the NM packages and use Wicd???

Yup.  Get ahold of the .deb file:

```
wicd_1.5.3_all.deb
```

...at:

[http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

Next, pull out all network-manager and knetworkmanager pieces via Synaptic.  Install that .deb file once NM is gone (just double-click it), and then go into System>Preferences>Sessions...unclick NM, and add a session startup item that does the command:

```
wicd-client
```

...and check it for startup.  Reboot and done.

> That is very informative. 

Thanks.  Tested it in 32bit mind you but it's supposed to work with 64 too.

> Maybe Wicd should be the default Network manager then??

The problem is, Wicd isn't (yet) as ambitious a project.  There's no attempt (yet) to support cellular modems internally and the "create a WiFi hotspot" stuff equivelent to NM7 is extremely primitive (WEP only fr'instance) if it works at all.

Where Wicd shines is the ability to do scripts specific to the startup of a given WiFi connection (by SSID).  I have a friend at a law office whose lappy connects to his office servers only if he's at work, not anywhere else.  Way cool.

Also: running NM7 and a cellmodem via WVDial script, there's this really annoying bug where since you're not connecting to the Internet via a connection known to NM7, Firefox will start up in "offline mode" because obviously, you're not connected to the Internet because NM7 doesn't think you are.  Even when you are.  Grrr.  With Wicd that boolsheet doesn't happen.

But issues aside, while buggier than an ant farm right now, NM7 has more potential than Wicd down the road, and it's very likely NM7's issues will get sorted out long before Jackass^H^H^Halope.

As long as the word is out that Wicd is a viable fallback position, NM7's initial bugs won't be killers.  
[B]
I think a case can be made that at least semi-official acknowledgement should be made of NM7's initial issues, and a pointer to Wicd as a backup be published in Ubuntu Weekly or something, and at Ubuntuguide:Intrepid.
[/B]
That's actually two different "fallbacks" I've run into.  As I type this, the only way I can get sound (due to a really freaky ALSA bug with Intel's HDA laptop sound in some systems) was to yank ALSA and Pulseaudio and put in OSS4...which works surprisingly well.

Linux is modular...remember that :).  If something is broke, sniff out an alternative subsystem...very few are impossible to replace with something else.  I'm a Gnome guy but I keep KDE around and working "just in case" Gnome pukes and dies.  Happened to me once early on with Linux (for me, two years ago, zero *nix experience going in!), bad font cache, got online with XFCE and figured out a quick fix.  *If you're playing with Alpha or even Beta variants, you need a backup desktop "just in case".*

---

### Post by american.swan on 2008-10-22
I followed Jim March's idea.  Upgraded.  I had to upgrade with the ISO though for some reason.  anyhoo I quickly uninstalled network-manager completely and installed wicd. 

Works great.  :)

---

### Post by Polygon on 2008-10-22
network manager 7 works fine for me.

---

### Post by klange on 2008-10-22
Frick no. It *was* fixed.
If you don't want it, remove it yourself.

---

