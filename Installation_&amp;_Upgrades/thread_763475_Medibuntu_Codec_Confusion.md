---
title: "Medibuntu Codec Confusion"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2008-04-23
In the Medibuntu page it says:
"Some software such as Amarok and Kaffeine are distributed through the main Ubuntu repositories but with certain functionalities taken away, again because of legal issues. Medibuntu distributes these kind of packages with those functionalities in place."

I would like to make sure I understand this.  

Is there any difference in the end result between:

1.  Uninstalling the default installs of Amarok (or Rhythmbox) & Kaffeine  (say) and reinstalling them from Medibuntu

Vs

Keeping the default installs of Amarok and Kaffeine (say) and
installing the w32codecs from Medibuntu and libxine1-ffmpeg for mp3 support?

Grateful for any light anyone can shed on this.

---

### Post by mgmiller on 2008-04-24
Interesting question.  

I have Ubuntu, but installed Amarok from the regular repos.  I then enabled the medibuntu repos as well as the backports repos.  When I look at what is available to me, it shows 3 versions of amarok. They are listed in this order:
2:1.4.8-0ubuntu3~gutsy1 (gutsy backports)
2:1.4.7-0ubuntu3+medibuntu1 (gutsy)
2:1.4.7-0ubuntu3 (gutsy)
 
Since synaptic will take the newest as default, it has me running from the backports version.  If you don't have backports enabled, I suspect it would automatically give you the medibuntu version, regardless of where it was first installed from.

---

### Post by undecidable on 2008-04-25
Yes, I guess backports would be the latest, but is unlikely to have things such as extra codecs. 

I will be clean installing kubuntu 8.04 (currently running K7.04, U7.04 and U6.06) - I never upgrade.  So for me the issue will come up in 2 separate ways:

a.  Amarok will be installed by default.  Should I uninstall and then reinstall from Medibuntu or should I just add the Medibuntu codecs?

b.  MPlayer wont be installed by default.  Should I install as normal then add Medibuntu codecs, or just install clean from Medibuntu?

With respect to your last point, I am not sure that adding the Medibuntu repos later will cause libraries that weren't initially installed to then be installed during a normal update.  The libraries are not going to be 'hard dependencies'.

---

### Post by mgmiller on 2008-04-26
> With respect to your last point, I am not sure that adding the Medibuntu repos later will cause libraries that weren't initially installed to then be installed during a normal update. The libraries are not going to be 'hard dependencies'.

That's true, they may not be hard dependencies, but if the libraries are also in the medibuntu repository and they have a more recent version of them, then I think they would also be updated automatically.

---

### Post by undecidable on 2008-04-27
Indubitably correct, but I think it is not relevant to this issue: the point is that if you had not installed from Medibuntu in the first place, there would be libraries that would not be installed (eg w32 codecs).  It is not a case of just different version numbers of libraries that would be installed, but that some libraries would not be installed if you installed without medibuntu enabled, and it is possible that some libraries may be 'different'.     

So, for example,  the key issue in my case a above, amarok, I may not know which additional libraries would have been installed if I had installed from Medibuntu, so would not be sure which to try to install when I (later) add the Medibuntu repo - and so my question.

---

### Post by mgmiller on 2008-04-27
I see your point.  Since you are planning a new install, perhaps the most logical course of action would be to enable the medibuntu repositories as soon as the install is finished, then install mplayer from medibuntu and do a reinstall of amarok.  A quick check in synaptic (or whatever the kde equivalent is) will tell you which repository the application is being installed from.  That way you have the medibuntu versions.  You could then fill in any other codecs you need from medibuntu.  

You gave the example of the w32 codecs.  I just checked my system and I have them installed from marillat.  This was done quite some time ago.  I no longer have the marillat repo enabled.  My system also shows them available from medibuntu, but seems to imply they are not as recent, as they are second on the list.  Looking at the version numbers, however, implies the marillat is from 2005 and the medibuntu is from 2007.  Perhaps I should switch.

marillat version:  1:20050412-0.4 (now)
medibuntu version: 20071007-0medibuntu1 (gutsy)

edit:  I have uninstalled the version from marillat and installed the medibuntu one.  I also discovered my ffmpeg was from marilatt and have brought that one up to date as well.  I used marilatt a few years ago to get all these things working before medibuntu existed.  I guess it's a good idea to prune a little "dead wood" before I upgrade to Hardy.  As you can see from my sig line, I have upgraded a lot.  I always learn something new when I do this and the system seems to remain stable.

What other codecs are you interested in?

---

### Post by undecidable on 2008-04-27
with respect to mplayer, I completely agree, esp given its independent structure (not using xine libraries, keeping everything internal).  

With respect to amarok, I am a little less sure about uninstallng the preinstalled vsn first, and am a bit more inclined to add the codecs. 

key point is that I dont have sufficient information to defend the decision either way, which of course was the point of the question.

Which codecs:  w32codecs (in particlar real and wma - I listen to a lot of finance conferences) 
and mp3 for podcasts that havent seen the ogg light yet.  
not interested in dvds- life already too short.  


On a separate note, I never upgrade - bad joss - though after testing I may individually copy across some config files assuming no major change in vsn numbers.  
On the other hand, I only do every 2nd vsn, though still have 1 machine on 6.06.

---

