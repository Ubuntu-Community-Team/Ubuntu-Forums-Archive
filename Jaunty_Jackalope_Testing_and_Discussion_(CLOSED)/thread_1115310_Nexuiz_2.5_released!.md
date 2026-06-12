---
title: "Nexuiz 2.5 released!"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-04-03
Official:
[http://alientrap.org/forum/viewtopic.php?t=4448](http://alientrap.org/forum/viewtopic.php?t=4448)

The article on phoronix:
[http://www.phoronix.com/scan.php?page=article&item=nexuiz_25&num=1](http://www.phoronix.com/scan.php?page=article&item=nexuiz_25&num=1)

Looks like it has many enhancements I'd really like it to land into Jaunty..

---

### Post by binbash on 2009-04-03
Second

---

### Post by Progressive on 2009-04-03
me wants packages

---

### Post by andrewabc on 2009-04-03
Probably won't happen until debian updates it. Then ubuntu will have to get it. Hopefully possible since it is not a default installed app.

---

### Post by tommcd on 2009-04-05
If you want to play Nexuiz 2.5, you don't have to wait for the Ubuntu repos to update to 2.5. Just download the nexuiz-25.zip file to your home directory and unzip it. 
[http://sourceforge.net/project/downloading.php?groupname=nexuiz&filename=nexuiz-25.zip&use_mirror=voxel](http://sourceforge.net/project/downloading.php?groupname=nexuiz&filename=nexuiz-25.zip&use_mirror=voxel)
Then from the terminal, cd into the Nexuiz directory that is created when you unzip it and run:
```
./nexuiz-linux-sdl.sh
```
or
```
./nexuiz-linux-glx.sh
```
Use which ever one runs better. I use the nexuiz-linux-sdl.sh on Slackware 12.2. It works great.
This will choose the correct binaries whether you are running 32 bit or 64 bit Ubuntu. See this:
[http://www.alientrap.org/nexuiz/faq.php#How%20do%20I%20install%20Nexuiz?](http://www.alientrap.org/nexuiz/faq.php#How%20do%20I%20install%20Nexuiz?)
[http://www.alientrap.org/nexuiz/faq.php#How%20can%20I%20place%20a%20shortcut%20to%20Nexuiz%20on%20my%20Linux%20desktop?](http://www.alientrap.org/nexuiz/faq.php#How%20can%20I%20place%20a%20shortcut%20to%20Nexuiz%20on%20my%20Linux%20desktop?)

---

### Post by vandorjw on 2009-04-05
is there a way to download source code only and compile it myself?
it would save bandwidth

---

### Post by Polygon on 2009-04-05
> **cc7gir said:**
> is there a way to download source code only and compile it myself?
it would save bandwidth

not very much as the majority of the size is content (maps/textures/sounds)

---

### Post by Polygon on 2009-04-05
opinion of game:

some maps look terrible

the UI is also terrible.  Flashing colors on all sides and the fact that Every message has to have at least two colors in it just makes it an eyesore

the game does not tell you what weapon you were killed with

i actually was lagging in a few parts (with my nvidia 9800 gtx? um.....)

the 'hook' is stupid, i played a few maps where the games lasted less then 2 minutes because the veterans just hooked all around the map and got 7 captures.

 i ended up with like -26 points one round, either because it was subtracting points from me every time i die, or someone suggested i lost the flag a lot...either way, its either buggy/bad design. No game should punish you for dying or dying while having the flag.

on ctf maps, its hard to tell what team your on. I guess you have to look at the weapons, but some of them don't have much color on them, so its hard to see if its red / blue

I lagged out and i was just stuck at the console and i could not rejoin the server, im not sure what was happening there

all in all, its just another generic deathmatch clone , with the same weapons every other quake/unreal/deathmatch game or clone has, and provides nothing new or interesting, besides that stupid hook. Just becuase a game is open source does not automatically make it a good game....sorry =/

---

### Post by tommcd on 2009-04-05
> **Polygon said:**
> opinion of game:
some maps look terrible
the UI is also terrible.  

Hmm, I've always thought the graphics in Nexuiz were pretty good. I have not seen all the maps; but the maps I have seen looked fine.
> **Polygon said:**
> 
i actually was lagging in a few parts (with my nvidia 9800 gtx? um.....)

Nexuiz 2.5 runs fine on my nvidia geforce 6200. I run it 1024x768 resolution with a lot of the effects turned down a bit from their defaults. 
> **Polygon said:**
> 
on ctf maps, its hard to tell what team your on. I guess you have to look at the weapons, but some of them don't have much color on them, so its hard to see if its red / blue
I agree with this one. Glad I'm not the only one who has trouble seeing who is on which team. I never play the ctf games though. I only play on the death match games. I just like to run around and shoot stuff!

> **Polygon said:**
> 
all in all, its just another generic deathmatch clone , with the same weapons every other quake/unreal/deathmatch game or clone has, and provides nothing new or interesting..
I agree that there are quite a lot of online death match clones out there in the open source world. I've always thought that Nexuiz does a better job with this genre than most of the others though.

---

### Post by ene_dene on 2009-04-06
I love that game, it would be very nice if version 2.5 was in Jaunty Jackalope repositories.

---

### Post by mikeize on 2009-04-06
Nexuiz is great!  Re: hook-- yes, I hate it too, but it's not enabled on all servers--usually the server name says "hook" in it.  
Re: scoring, yes, they are still working out the points system I think--it's changed a bit lately.
Re: graphics, it IS a free game, so it doesn't look like Crysis, but I think it is more than adequate.

Nexuiz really shines in terms of physics and movement.  Also, the community of players is generally much nicer than some proprietary game communities.

Turn your settings down a bit, and give it another try on a non-hook server.

---

### Post by Polygon on 2009-04-06
> **mikeize said:**
> 

Turn your settings down a bit, and give it another try on a non-hook server.

you don't seem to understand...i have a nvidia 9800gtx. with my monitor (Only a 15 inch one, that runs at 1024x768) i can MAX out every graphics setting in crysis in windows. I have 4 gb of ram, 3 ghz core 2 duo and my 9800, there is no reason this game should be lagging.

Also, i tried it again, In some spots, i get over 400 fps, but then i still see it tank in certain spots with lots of actions, to the point where i am lagging noticeably. 

and with these kinds of games, you take what you can get. When i played, there were only two ctf servers, one was full, the other one had the hook. So.....its not as easy as saying 'join another server'....i'm sure it will be even harder after the 'wow' factor of the new release settles and everyone stops playing

---

### Post by ene_dene on 2009-04-06
> **Polygon said:**
> you don't seem to understand...i have a nvidia 9800gtx. with my monitor (Only a 15 inch one, that runs at 1024x768) i can MAX out every graphics setting in crysis in windows. I have 4 gb of ram, 3 ghz core 2 duo and my 9800, there is no reason this game should be lagging.

Also, i tried it again, In some spots, i get over 400 fps, but then i still see it tank in certain spots with lots of actions, to the point where i am lagging noticeably. 

and with these kinds of games, you take what you can get. When i played, there were only two ctf servers, one was full, the other one had the hook. So.....its not as easy as saying 'join another server'....i'm sure it will be even harder after the 'wow' factor of the new release settles and everyone stops playing
It is possible that nVidia drivers are not good for that card. I played Nexuiz with constantly good framerate on my 8600GT.
However, when I changed the card to 9800GTX+, I have the same problems that you do. It must be the drivers. I have 3d acceleration but something must be out of place.
However I can't be sure, was it my fault, because I had to change drivers to enable CUDA (I'm running gpugrid project). I guess I'll find out when new Ubuntu release comes.

---

### Post by mikeize on 2009-04-06
*shrug*

I have an 8500GT, and it works great (on low settings).  I get up to 250 fps, which is good enough for me.  Some of your lag may be caused by the server itself.  Again, since there's no commercial money behind this game, or it's servers, sometimes the bandwidth is just too expensive.

I never play hook, and I play A_LOT_, for the last few years.  During peak times, you may have to wait a bit to get into the server you want, but you'll get in.  Also, you can bind "connect ipaddress" to a key, so when u are in one server, you can occaisionally hit that hotkey to try to sneak in when someone drops out.

I mean, if you don't like it, you don't like it... but I really think you should give it more of a chance.

---

### Post by Asraniel on 2009-04-06
nexuiz has and always had certain graphics options that are present, but that you don't want to turn on because they simply use too much resources.

Nexuiz uses darkplaces as an engine, which always had some next gen features, that you can't really use but that are in anyway.
Now you can argue if they should be shown to the user or not, but i prefer yes. And you can actualy disable quite a few things and it still looks good. or make it look realy bad and you can play it on a eeepc

---

### Post by ene_dene on 2009-04-22
You can download Nexuiz 2.5 for Jaunty Jacalope now from [http://www.getdeb.net](http://www.getdeb.net)

---

