---
title: "Install Streamtuner (yet another n00b)"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by nickx on 2005-04-05
Hi Guys, 

I'm completely new to linux. I bought myself a macmini and I decided to delete all Windows Software on my 2 laptops and start from scratch.

As already mentioned i'm a newbie and I don't get the hang of it yet. I played with apt-get learned about sudo and settings rights on folders and so on. 

No I found a package on the internet Streamtuner. I would like to install it. In windows you have setup .. run install done. 

Here i have some dificultys. I only see the following installation files:

	Type
source distribution (signature)	official
patch fixing crash with PyGTK 2.5/2.6 (signature)	official
Fedora Core 3 i386 package (signature)	unofficial, contributed by Matthias Haase
Fedora Core 3 source package (signature)	unofficial, contributed by Matthias Haase
Fedora Core 3 i386 devel package (signature)	unofficial, contributed by Matthias Haase
Fedora Core 3 AMD64 package (signature)	unofficial, contributed by Curtis S Netterville
SUSE 9.2 i586 package (signature)	unofficial, contributed by Sébastien Corot
SUSE 9.2 source package (signature)	unofficial, contributed by Sébastien Corot

How can I install this and which one should I choose. Can please tell someone how to install this in a proper way? Or is it just dificult :) I downloaded RPM but then totem would like to open it :) ???

Thnx guys

---

### Post by nickx on 2005-04-05
I found the way to do it via Synaptic. But let's say I don't want to install it via that way (dunno way, but just to get things to know)

I downloaded the Sources and red the follwoing:

3. Instructions

	streamtuner uses the GNU build system. Hence, the following
	familiar sequence should satisfy most users:

		$ ./configure
		$ make
		<get root privileges, if needed>
		$ make install

	The ./configure script options are documented below. They are
	enabled by default and automatically disabled if a requirement
	is not met, so you probably do not need to use them.


I'm sorry but I'm completely lost. Can someone describe a littble bit about what it's saying here.


--> Some other strange thing...

Yes it installed, Synaptic says it has been installed but I can't see any application??? Very strange.

---

### Post by Nano on 2005-04-05
Well, I just installed it via apt and it works pretty well...
if it works why fix it?

---

### Post by nickx on 2005-04-05
[QUOTE=Nano]Well, I just installed it via apt and it works pretty well...
if it works why fix it?[/QUOTE]

True True. If it aint broke don't fix it. : ) 

Do you know how to open it with a other music player, now it opens with xmms?

---

### Post by Nano on 2005-04-05
[QUOTE=nickx]True True. If it aint broke don't fix it. : ) 

Do you know how to open it with a other music player, now it opens with xmms?[/QUOTE]
 Sure.
Open the program, open menu->Edit->Preferences
In "Applications" tab modify the commands in the right column replacing XMMS with your fav. app. I have it set to beep-media-player.

Cheers

---

### Post by benkorkor on 2005-04-09
I changed the command to "beep-media-player" but now it just opens beep but doesn't play a song. Am I forgetting something in the command?

*Edit. Oops, forgot to add %q to both stream and m3u. Working now :)

---

### Post by Gary Powers on 2005-04-10
Using either beep-media-player or xmms, after the player sets up the buffer, it freezes.

Any thoughts on what might be causing this "overload" ?

Gary

---

### Post by iminj on 2005-04-13
[QUOTE=Gary Powers]Using either beep-media-player or xmms, after the player sets up the buffer, it freezes.

Gary[/QUOTE]

I have the same problem. I tried Streamtuner with "xmms %q"; and also beep-media-player %q" ... and both failed. The app's open, but there is no sound - and xmms locks up completely (I have to force quit).

On the other hand - **when I set up "musicplayer %q", the GNOME Music Player loads and plays. ** Try it .. maybe it will work for you too.

I don't understand why xmms and beep crash.

-iminj

---

### Post by iminj on 2005-04-13
Gary:

 I posted this problem in another forum, and a fellow ubuntu user (Astrophobos) responded with a suggestion that **worked**  for me!! 

[B]Originally Posted by Astrophobos
For xmms, try to set the audio output plugin to esound in preferences
[/B]

Gary .. u can also try setting the esound plugin in beep as well - it also works for me. Good luck.
-iminj

---

### Post by Gary Powers on 2005-04-13
Thanks much, guys.  I was able to locate a smooth jazz stream and could hear it using Gnome Music Player, tho all I could hear was the invitation to subscribe to "live365", but that's a step in the right direction.  I have subscribed but still can't figure out how to listen via music player.  Gotta say .... iTunes sure is easier.  

Ah well, one step at a time.

And thanks again for the support!

Gary

---

### Post by Gary Powers on 2005-04-14
[QUOTE=iminj]On the other hand - **when I set up "musicplayer %q", the GNOME Music Player loads and plays. ** Try it .. maybe it will work for you too.

I don't understand why xmms and beep crash.

-iminj[/QUOTE]

Gnome Music Player works great!  I copied the URL's I wanted out of Streamtuner and badaboom, I have my internet radio.  Thanks!

Gary

---

