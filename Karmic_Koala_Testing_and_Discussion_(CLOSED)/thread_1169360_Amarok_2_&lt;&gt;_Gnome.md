---
title: "Amarok 2 &lt;&gt; Gnome"
date: 2009-05-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Roosje on 2009-05-25
I have finally got Amarok 2 producing sound, but.. There is no icon in the notification area (just a blank space that does function) and when i have it minimized to the not. area the play-list disappears?? Even repopulate will not bring it back (sigh) I know that is the risk of using an alpha, but it is kinda unsettling ;-) Any tips here?

Oh, before i forget to ask, anyone has temp sensors working on ASRock x58 deLuxe motherboard?

Thanks, Wilco

---

### Post by Josey on 2009-05-26
I'm still a step behind you trying to get it to produce sound.  How did you do this?

edit:  
> sudo apt-get install phonon-backend-xine libxine1-ffmpeg
fixed for me.

---

### Post by Darkshade on 2009-05-26
Why would you want to run Amarok 2 in Gnome? :-#

---

### Post by cl333r on 2009-05-27
I think because many people including me think that there's no better music player for Linux than Amarok. Most remarkably, decent drag and drop (and playlist viewer).

---

### Post by Darkshade on 2009-05-27
> **cl333r said:**
> I think because many people including me think that there's no better music player for Linux than Amarok. Most remarkably, decent drag and drop (and playlist viewer).

I could agree if you were talking about Amarok1.4 but "decent playlist viewer" in Amarok2? :confused:
I know it's not the place to start yet another discussion about Amarok2 but Amarok1.4, Exaile, Banshee, Listen and even Rhythmbox seem like better options, specially for Gnome.

---

### Post by seeker5528 on 2009-05-27
> **Roosje said:**
> I have finally got Amarok 2 producing sound, but.. There is no icon in the notification area (just a blank space that does function) and when i have it minimized to the not. area the play-list disappears?? Even repopulate will not bring it back (sigh) I know that is the risk of using an alpha, but it is kinda unsettling ;-) Any tips here?

Don't know, it's working fine for me.

If this was an upgrade I would rename the ~/.kde/share/apps/amarok directory and any amarok files in ~/.kde/share/config and configure the Amarok stuff from scratch.

Also you could open a terminal window and run it from there to see what output you get.

Later, Seeker

---

### Post by seeker5528 on 2009-05-27
> **Darkshade said:**
> I could agree if you were talking about Amarok1.4 but "decent playlist viewer" in Amarok2? :confused:
I know it's not the place to start yet another discussion about Amarok2 but Amarok1.4, Exaile, Banshee, Listen and even Rhythmbox seem like better options, specially for Gnome.

Don't know about that playlist viewer part either, it did improve in 2.0.96, but I haven't really looked at it much. Track/Album/Length what else do you need visible in your playlist? :p

Everything else is kind of Anemic compared to Amarok 1.4. The 2.1 beta (2.0.96) is much better than the earlier 2.0 releases.

I'd have a hard time going backward to Listen or Rhythmbox, neither of these provides much in the way of playlist management.

I'd have to try the other two but have not seen anything that would give me any indication they stand out any more than Rhythmbox.

Amarok is built around the playlist, you can't play anything that is not in a playlist, so good features revolving around the playlist management is a must.

Later, Seeker

---

### Post by Darkshade on 2009-05-27
> **seeker5528 said:**
> The 2.1 beta (2.0.96) is much better than the earlier 2.0 releases.
Agree with that. Amarok improved a lot with the 2.1 beta and I really believe that someday it will become an awesome music player but for now it still lacks a lot of functions and it's rather resource-heavy and buggy.

> **seeker5528 said:**
> I'd have a hard time going backward to Listen or Rhythmbox, neither of these provides much in the way of playlist management.
I have to agree once again and I could say the same for Banshee actually.

> **seeker5528 said:**
> Amarok is built around the playlist, you can't play anything that is not in a playlist, so good features revolving around the playlist management is a must.
Try Exaile :popcorn:

---

### Post by Wangberg on 2009-05-28
I realized after about 20 seconds of using Amarok 2.0, i was using the biggest piece of crap player i've ever seen.  I am still asking how the devels can take 1.4, and without totally deficating on it, could produce and release something as horrendous as 2.0.  

No offense to the devels, and i've been a 3 year fan of 1.4, but amarok 2.0 SUCKS.  

this leads me to ask:

is there any way to install 1.4 on Ubuntu 9.04.  i've worked with exaile, rhythmbox, and VLC (which i use for video) and none are anywhere close to what amarok 1.4 is in the audio player world.  

please help...how can i downgrade to 1.4?????

---

### Post by cb951303 on 2009-05-28
> **Darkshade said:**
> 
I have to agree once again and I could say the same for Banshee actually.


what about smart playlist? it looks pretty powerful to me

---

### Post by Darkshade on 2009-05-28
> **Wangberg said:**
> please help...how can i downgrade to 1.4?????

[https://launchpad.net/~bogdanb/+archive/ppa](https://launchpad.net/~bogdanb/+archive/ppa)

---

### Post by seeker5528 on 2009-05-29
> **Darkshade said:**
> Try Exaile

Took another look at the music players.

Listen actually does have stuff in it to help in playlist creation by artist, genre, track length, etc... it's got quick access to things in the center panel, and able to use Last FM in it's dynamic mode to select upcoming tracks to play, the dynamic mode was the original reason I tried it some moons ago. I would put it higher on my list than Banshee. It would be a toss up for me between Listen and Exaile. Exaile looks like it is probably the most competitive with Amarok.

For my personal usage Amarok still outshines the others, I'm only dealing with my local collection and scrobbling to Last FM. I rarely have any saved playlists. I am almost always using the current playlist and switch to dynamic and define what characteristics I want, usually with no defined characteristic so it will play from the entire collection, or I set it to static and add stuff, remove stuff, and move stuff around while I am listening.

95+ % of the stuff I used smart playlists for in 1.4 I can do by setting the playlist to dynamic, defining some characteristics, and letting the bias resolver add new/remove played stuff on the fly.

With the changes to the way the context pane works in 2.0.96, it seems to work better, and I've gotten kind of attached to it.

And one of my personal favorites, that I didn't notice if the other players do or not, you can right click the current track or an upcoming track and tell Amarok to stop playing after that track ends.

Also didn't note which of the other players let you select more than one music directory and how they handle importing and organizing.

I have one music directory I point Amarok to where the majority of the stuff has been piled up over the years and another music directory where I have subdirectories for stuff that came from riffage, besonic, last.fm, etc... and point Amarok to these subdirectories,  currently have Amarok pointing to 6 or 7 places all together. When I import or organize, I can choose to send the music to any of these.

Later, Seeker

---

### Post by Roosje on 2009-05-31
> **Josey said:**
> I'm still a step behind you trying to get it to produce sound.  How did you do this?

edit:  sudo apt-get install phonon-backend-xine libxine1-ffmpeg 

fixed for me.

Indeed, was away for a while, but that turned up in a thread in i think the amarok forum ;-)

---

### Post by Roosje on 2009-05-31
> **Darkshade said:**
> Why would you want to run Amarok 2 in Gnome? :-#

Because i want to know how far it has come. I want it to become at least as good as 1.4 (on my Jaunty, my main music program) 
I always use alpha/beta partition to experiment with as much programs as possible to see where they are going development wise, and i am a lazy git, don't want to install Kubuntu ;-)

Wilco

---

### Post by Vanishing on 2009-05-31
It seems you are missing the oxygen icon set.. install it in synaptic will solve your problem..i think
and to no sound.. you need the phonon xine backend..samething, install it in synaptic..

---

### Post by dentaku65 on 2009-08-02
> **Darkshade said:**
> [https://launchpad.net/~bogdanb/+archive/ppa](https://launchpad.net/~bogdanb/+archive/ppa)

The Bogdan PPA has changed
[https://edge.launchpad.net/~bogdanb/+archive/amarok14/](https://edge.launchpad.net/~bogdanb/+archive/amarok14/)
The series it is only avail for Jaunty
...but it works quite well for Karmic too :-)

---

