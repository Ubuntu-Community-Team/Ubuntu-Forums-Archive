---
title: "Access to BBC radio &amp; iPlayer in the UK via Jaunty"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Scunnered on 2009-04-10
I have been looking at the Jaunty beta and liking very much what I see.  When I attempted to set up a wireless connection in 8.10 it was hell but working with a live CD in Jaunty was simplicity indeed.  Identify the network and enter the required password was all it took to have immediate access to the web.

I had hoped for better with working with the BBC as with 8.10 I can access all the BBC output in the UK easily.  This time I am being asked to load Real Player for radio and I get nothing on the iPlayer. 

Backtracking my posts I was told that totem would work perfectly with the BBC in 8.10 and I find that it is one of the default settings in Jaunty.  I was also told to install via Synaptic Ubuntu restricted extras but don't seem be be able to find them in Jaunty.  Is this because it is in beta or have they found yet another way to confuse me ?

If it is a case of patience then tell me so otherwise can anyone throw any light on where I may be going wrong this time.

---

### Post by gandaran on 2009-04-10
all you need for BBC iplayer is adobe flash for the videos, for the radio service use the real player or install the mozilla-mplayer plugin, forget totem it only works with wmv/audio not real audio or video

---

### Post by SuperSonic4 on 2009-04-10
You might have to enable the medibuntu repo for restricted-extras

---

### Post by ibizatunes on 2009-04-10
You need to type ```
sudo apt-get install realplayer
```

make sure you have the repos from medibuntu
im runninng 9.04 and the bbc site work fine :-)

---

### Post by Scunnered on 2009-04-10
My thanks to you all for your assistance.

I had a look for the items that were suggested other than Real as I do not like how they work.  Searching in Synaptic brought up nothing on Flash, Mozilla or Medibuntu repo could this be as I am currently experimenting as a Live Session User?

Just when I thought that I could stop banking my head against the wall, here we go again.

Can you please offer more guidance.

Thanks again

---

### Post by gandaran on 2009-04-10
> **Scunnered said:**
> My thanks to you all for your assistance.

I had a look for the items that were suggested other than Real as I do not like how they work.  Searching in Synaptic brought up nothing on Flash, Mozilla or Medibuntu repo could this be as I am currently experimenting as a Live Session User?

Just when I thought that I could stop banking my head against the wall, here we go again.

Can you please offer more guidance.

Thanks again
are you using the live cd?
for flash get it [here]("http://get.adobe.com/flashplayer/") download the .deb package for ubuntu.
the mozilla-mplayer plugin package should be in synaptic, type mozilla-mplayer in the search box.
the adobe flash packages in synaptic are named flashplugin-nonfree or adobe-flashplugin.
click the reload button in synaptic before searching to fetch the package list.

---

### Post by Scunnered on 2009-04-11
gandaran

Many thanks for your assistance.  There is something very wrong as I am totally unable to access anything.  I accepted your link to Adobe only for it to display an Error: Wrong Architecture i386.

I then went into Synaptic and cut and pasted the details that you posted.  Mozilla threw up 2 items being Mozilla-devscripts and Mozilla-Thunderbird.  There was a Totem-Mozilla marked as being installed. Strangely in this area there were items which did not follow the usual alphabetical sequence but I can only assume this was related to the installed / latest lists.

Seeking the flashplugin / adobe again none of these displayed.

I am not sure what is going on but as I can still work away with 8.10 I shall be patient and wait on Jaunty arriving.  Once the servers have been given a chance to cool down I will do a full install and start over again.

Once again my thanks

PS.  I am writing this post from Jaunty as a Live Session User.

---

### Post by gandaran on 2009-04-11
Scunnered
> Error: Wrong Architecture i386
this error is due to your ubuntu is 64-bits and you where trying to install a 32-bits package.
get the 64-bits flash [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") download to desktop and extract/unpack the package then move the libflashplayer.so file to either /home/'user'/.mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins, thats all you have to do to install flash. 
I'm not sure if it works with the live cd, even if it does you'll have to install it every live session

---

### Post by freeman2000 on 2009-04-11
[QUOTE=Scunnered;7047824]
Backtracking my posts I was told that totem would work perfectly with the BBC in 8.10 and I find that it is one of the default settings in Jaunty.  I was also told to install via Synaptic Ubuntu restricted extras but don't seem be be able to find them in Jaunty.  Is this because it is in beta or have they found yet another way to confuse me ?
QUOTE]


The Medibuntu repository is available for Jaunty.  Go to Terminal and type in the following string:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list


Then go to Synaptics and search for:

ubuntu-restricted-extras


Mark & download (apply).  This should hopefully get you all the plugins/dependencies that you need.  Good luck.

NOTE--  do not underline anything!  The forum tools are not working properly for me right now.

---

### Post by jmmL on 2009-04-12
I'm told that flash on 64bit now works pretty well. You can install it by typing:
```
sudo apt-get install flashplugin-nonfree
```

You'll need the medibuntu repos enabled.

---

### Post by JohnJackson on 2009-04-12
You do not need the medibuntu repository to install flash or restricted extras. You have to enable the multiverse repository in software sources as they are restricted by copyright.

[http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras]("http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras")
[http://packages.ubuntu.com/jaunty/flashplugin-nonfree]("http://packages.ubuntu.com/jaunty/flashplugin-nonfree")

> **Scunnered said:**
> Strangely in this area there were items which did not follow the usual alphabetical sequence but I can only assume this was related to the installed / latest lists

This is because you used the quick search, use the search button instead. I don't know how the quick search is ordered but I find it confusing personally.

---

### Post by Scunnered on 2009-04-14
**Another fine mess I have got my self into **!  Going against my religon - DEVOUT COWARD,  I decided to load Jaunty to my hard drive this morning.  Initially things looked good but now I can't access my wireless connection.  When working with the Live DVD all I had to do was click on the icon and enter a passwork and a connection was made.  Now it shows up as disabled and no matter what I do it will not effect a connection.  Left clicking on the icon only shows the wired network and nothing else. This was the one feature of Jaunty that I was very pleased to see.

Now the question is how will I get rid of this troublesome Jaunty ?  This is a dual boot with 8.10.

Your kind assistance will be appreciated.

PS.  For the hell of it I returned to the Live session user mode and would you believe it I am back on line without any messing about.  Left clicking on icon displays 4 networks and all the options and everything works.

PPS Discovered that I could delete the partition rather easily. Did fresh install and everything worked OK.  Now following your guidance to set up the various connections that I seek.

---

### Post by Scunnered on 2009-04-16
My sincere thanks to everyone for all their assistance.

I have now installed all the required items to ensure my continued enjoyment of the BBCs output

---

### Post by capnthommo on 2009-04-19
Hi scunnered
a couple of points.
first, that really good howto at [http://ubuntuforums.org/showthread.php?t=766683&highlight=multimedia+howto]("http://ubuntuforums.org/showthread.php?t=766683&highlight=multimedia+howto") talk stickies is now updated for jaunty.  i dont know if you knew, i only found out by chance today.  but this has the correct repos details etc and when i activated them the loading really flew compared to intrepid (at least it did for me).
if you have gotten iplayer running properly can you tell me how you did it?  it works fine for most bbc radio (what i want mostly) but one or two programs give the stupid 'download real player' message when i try to listen.  odd really because most work fine its just one or two of my favourites (i'm talking 'listen again' rather than live streaming).
gods, this bbc thing can be a real pain in the donkey cant it?
cheers
nigel
;)

---

### Post by lerrup on 2009-04-19
the other thing worth knowing is that you don't need realplayer any more even for live streams on iplayer.  If you sign up as a labs tester then the live streams are via flash as well; and are better quality sound as well.

---

### Post by Scunnered on 2009-04-19
**capnthommo**

I am able to use all the BBC national and Local radio programmes + the iPlayer having folowed the guidance offered.  From memory having decided to rip out my initial Jaunty install and re-installing I followed the guidance offered by  JohnJackson and downloaded the restricted extras. 

Everything now works a treat and I can't want until the servers cool down to download the final Jaunty.

I intend to start everything afresh so I will follow your link and see what happens. I appreciate you posting this information as things seem to keep changing between issues.   I hope that you will be able to fully access your choices and hope that Jaunty will be of great benefit to us all. 

**lerrup**  

Many thanks for the heads up on Realplayer.  This will be of assistance to all.  I avoid Realplayer like the plague as they seem to want everything from you with regard to personal data.  I am totally surprised that they have not requested my inside leg measurement and my grannys date of birth as they seem to have managed to ask for everything else.  I suppose we will not have to watch this space and see if the ask for the foregoing.

Once again my sincere thanks to all who assisted in this matter

---

