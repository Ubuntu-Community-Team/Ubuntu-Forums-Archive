---
title: "IDEA: Replace Rhythmbox with Banshee for Intrepid Ibex"
date: 2008-06-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2008-06-02
I feel that Banshee 1.0 has become the most matured media player that the open source community has to offer, and (not that this is a requirement for a media player) has become the best replacement for iTunes on Linux. To highlight a few of its new great features, it has:
[LIST]
[*]AN EQUALIZER!!!!
[*]Better support for large databases
[*]Video Support with fullscreen playback
[*]Better bling and a more compact, refined look than Rhythmbox
[*]Integrated with Brasero, which is now the default CD burning app for Ubuntu
[*]Better support for storage devices, including video sync
[/LIST]

Check out the new features at [banshee-project.org]("http://banshee-project.org")

---

### Post by Flashgordon20 on 2008-06-02
If I could get it to work in Hardy, I would agree with you.

[http://ubuntuforums.org/showthread.php?t=816077](http://ubuntuforums.org/showthread.php?t=816077)

---

### Post by rockin_goliath on 2008-06-02
I'm not a code guy either, that's why I love apt-get and deb packages :)
There is a more recent version of Banshee, RC1, which has some Ubuntu repositories available.
[http://banshee-project.org/Releases/0.99.3]("http://banshee-project.org/Releases/0.99.3") This is the link for the latest version. Following the Ubuntu link will get you here. [https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive") They have some debian repositores listed here. Hope that works for you.

---

### Post by olskar on 2008-06-06
Wow! Tried it recently! Rhythmbox would lose the musicplayer-race if I was the judge!

If you try it, remember to install banshee-1 and not banshee

EDIT:
[http://arstechnica.com/news.ars/post/20080527-rock-out-on-linux-with-the-banshee-1-0-beta-2-media-player.html](http://arstechnica.com/news.ars/post/20080527-rock-out-on-linux-with-the-banshee-1-0-beta-2-media-player.html)

---

### Post by ikarus2k on 2008-06-06
I second that (banshee rocks, literally ;) )

---

### Post by dr.silly on 2008-06-06
+1

(amarok is best; it's just not gtk)

---

### Post by edd07 on 2008-06-06
Hey, I've just downloaded Banshee, and so far it seems really good. But one thing is driving me crazy...can it watch folders like Rythmbox can? Because if it can't, I'm afraid its a show-stopper for me

---

### Post by damoxc on 2008-06-07
Not yet, I've been thinking the same, it really wouldn't be massively hard to implement though due to the FileSystemWatcher class in .NET, which basically does what is required, just needs some thought. Might be able to be implemented as a plugin.

---

### Post by Joe_Bishop on 2008-06-07
It isn't a good idea, this player is soooo much buggy.

---

### Post by olskar on 2008-06-07
> **Joe_Bishop said:**
> It isn't a good idea, this player is soooo much buggy.

Please report those bugs ;)

[http://banshee-project.org/Bugs](http://banshee-project.org/Bugs)

---

### Post by Joe_Bishop on 2008-06-07
It's quite hard to me, I'm not fluent in english. And, to say, the player is too slow. The redraw is very slow - just take any window and move it over the opened banshee's window. Scroll songs list with many items (whole library, for example). And if this happened on my PC: core 2 quad q6600, gf 8800gtx, 4gb ram, fast hdd - samsung f1, 1Tb, what will happen on lower machines?

---

### Post by Joe_Bishop on 2008-06-07
But, of course, this player is very functional.

---

### Post by Metaleks on 2008-06-07
I like this idea very much.  However, I feel that Amarok is still a lot more mature than Banshee.  Banshee is getting there, though.  And since Amarok isn't an option for a default Ubuntu player, that leaves the Rhythmbox or Banshee to duke it out for top spot.  IMO Banshee as a whole is much better than Rhythmbox in many respects.  Video support, better interface, and in my experience it handles ANY device much better than Rhythmbox does.  (MTP, iPod, anything)

---

### Post by liquidfunk on 2008-06-07
Just compiled my own version, I LOVE IT!

 Looks really smooth, everything just glides. Imports all your music by just searching for it, gets cover art from the net, can play Videos too. 

 So good!

---

### Post by T_W on 2008-06-07
Its infected with mono which makes it a non-starter.

Please, keep the Microsoft tech away from my system.

---

### Post by olskar on 2008-06-08
Version 1 is released!

---

### Post by Joe_Bishop on 2008-06-08
After latest upgrady to 1.0 I totally make sure this player should not be default. There are a huge number of incompleteness, like showing many items from one album in album list: [ATTACH]73359[/ATTACH], saving tags of several tracks is totally breakes the HIG - [ATTACH]73361[/ATTACH], and many others. It reminds me WMP very much.

---

### Post by Joe_Bishop on 2008-06-08
And the worst thing I have found: it didn't watch for the music and video library folders. It suggests to add new tracks through its own interface, which is totally inconvinient and not clear. So, it is definetely a BAD idea to make this default player.

---

### Post by olskar on 2008-06-08
No it should not be default in its current state but is it final?

It says on their site:

DRAFT - Do Not Announce
Banshee 1.0
DRAFT - Do Not Announce 

So perhaps it is not done

---

### Post by tretle on 2008-06-08
In banshee's defense the hig was written 6 years ago and it has been said that a rewrite would happen soon. Of course this is necessary because when it comes to writing a music playing application the hig for gnome doesn't give very much choices.
Id really love to see some gnome developers take an active interest in updating the hig, I think the banshee devs and other devs like macslow would give allot of good input because they are the ones who actually understand the constraints with the hig.

---

### Post by olskar on 2008-06-09
> **tretle said:**
> In banshee's defense the hig was written 6 years ago and it has been said that a rewrite would happen soon. Of course this is necessary because when it comes to writing a music playing application the hig for gnome doesn't give very much choices.
Id really love to see some gnome developers take an active interest in updating the hig, I think the banshee devs and other devs like macslow would give allot of good input because they are the ones who actually understand the constraints with the hig.

Isnt hig v2.0 the new hig? Or is it the one that was written 6 years ago?

[http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/)

---

### Post by Metaleks on 2008-06-09
> **Joe_Bishop said:**
> After latest upgrady to 1.0 I totally make sure this player should not be default. There are a huge number of incompleteness, like showing many items from one album in album list: [ATTACH]73359[/ATTACH]...
This picture could have been caused by some really bad metatags.  It happens.  I really don't think Banshee is to blame for this one.

For those of you who are against Banshee, I assume that you're for keeping Rhythmbox.  I'd like to get your views on why Rhythmbox makes a better default player.  For me, I personally can't see it.  Banshee has a better interface, works with more digital players, and has some pretty neat features Rhythmbox lacks.  Oh, and it can play video.  Which really helps the whole "media management" idea.

---

### Post by olskar on 2008-06-09
> **Metaleks said:**
> This picture could have been caused by some really bad metatags.  It happens.  I really don't think Banshee is to blame for this one.

For those of you who are against Banshee, I assume that you're for keeping Rhythmbox.  I'd like to get your views on why Rhythmbox makes a better default player.  For me, I personally can't see it.  Banshee has a better interface, works with more digital players, and has some pretty neat features Rhythmbox lacks.  Oh, and it can play video.  Which really helps the whole "media management" idea.


According to this, banshee is to blame:
[http://bugzilla.gnome.org/show_bug.cgi?id=536059](http://bugzilla.gnome.org/show_bug.cgi?id=536059)

It also misses daap-support in 1.0.
It is only some kind of milestonerelease it seems..

And therefore I change my mind about it being default.

EDIT: And the equalizer has been left out cause it did not work apparently, so now I see no reason to replace rhythmbox with banshee.

---

### Post by qamelian on 2008-06-09
> **Metaleks said:**
> For those of you who are against Banshee, I assume that you're for keeping Rhythmbox.  I'd like to get your views on why Rhythmbox makes a better default player.  For me, I personally can't see it.  Banshee has a better interface, works with more digital players, and has some pretty neat features Rhythmbox lacks.  Oh, and it can play video.  Which really helps the whole "media management" idea.
I find Banshee extremely crash-prone. I have never been able to get any version of it, including the latest to play more than three or four songs before it starts to stutter after which it crashes hard. Rhythmbox has all the features I need in an audio player and has always been rock solid for me.

---

### Post by dmitrijledkov on 2008-06-10
I'd rather see Epiphany with WebKit backend polished and Empathy for IM. I really not that fussy whether it's Rhythmbox or Banshee for music.

Rhythmbox stable, Banshee not.

And here we come with the classic Ubuntu time release question. We know program B is better than A, but do we ship it now or +6 months or +12 months.

I would say Banshee in Ibex, but we'll have to play wait and see =D

---

### Post by animaniac on 2008-06-12
personally im more for Exaile, it seems to have better performance too.

---

### Post by bruce89 on 2008-06-12
> **dmitrijledkov said:**
> I'd rather see Epiphany with WebKit backend polished and Empathy for IM.

Good luck with our dream is all I can say.

---

### Post by atomkarinca on 2008-06-12
It seems very nice and has nice features, it even found my Jamendo cover arts but it just crashed and closed in the middle of the first song. If the devs can get it more stable then why not? (I don't buy that "No .Net applications because then we become sellouts" story).

---

### Post by bruce89 on 2008-06-12
> **atomkarinca said:**
> If the devs can get it more stable then why not?

Implementing new features is more fun than fixing bugs I suppose.

---

### Post by atomkarinca on 2008-06-12
> **bruce89 said:**
> Implementing new features is more fun than fixing bugs I suppose.

Well, I guess they should implement "actually playing songs", too then.

---

### Post by eragon100 on 2008-06-13
The video library feature doesn't work, and it only plays a video if you go to Media -> open location, and select it with the file browser. If they can solve that, I want it as the default player in 8.10, because it :guitar: (rocks)

---

### Post by Joe_Bishop on 2008-06-13
> **Metaleks said:**
> This picture could have been caused by some really bad metatags.
What? It just tells that banshee sucks. Rhytmbox shows only one album, Amarok shows only one album, Exaile shows only one album. It means banshee can't work with tags properly, not these songs has bad metatags (they have been created with Easytag).

---

### Post by bruce89 on 2008-06-13
The lack of file monitoring kills it for me. I also think F-spot is bad for not having the same thing.

---

### Post by qamelian on 2008-06-14
> **eragon100 said:**
> The video library feature doesn't work, and it only plays a video if you go to Media -> open location, and select it with the file browser. If they can solve that, I want it as the default player in 8.10, because it :guitar: (rocks)
I'm visiting a friend right now who prefers Banshee and the video library is working fine on his PC using Banshee 1.0.

---

### Post by eragon100 on 2008-06-14
What could be wrong? I used the .deb from launchpad :(

---

### Post by olskar on 2008-06-14
I tried another musicprogram recently, its called listen!
You gotta try it out, its in the repos :)

Really like it and a new version is coming soon!

---

### Post by Junk_head on 2008-06-15
No gapless no deal for me. Ive gotten use to Rhythmbox due to this feature alone, plus the killer Gnome-do integration which if i recall was also compatible with banshee. If banshee does gapless or crossfading playback I'd digg a switch, but im sure it doesn't yet.

---

### Post by zekopeko on 2008-06-16
my guess is that banshee is going to have all of this features and more before feature freeze for ibex

---

### Post by olskar on 2008-06-16
> **zekopeko said:**
> my guess is that banshee is going to have all of this features and more before feature freeze for ibex

I hope you are a good guesser :)

---

### Post by zekopeko on 2008-06-17
> **olskar said:**
> I hope you are a good guesser :)

well considering how quickly banshee-1 was developed... it think that it's a matter of weeks before we have sync, better video management etc.

---

### Post by eldragon on 2008-06-17
i like the fact that rhythmbox is light, and fast, and does just what it does.
i dont know how big your music library is, but ive got a quite extensive collection and it doesnt complain much about it. but maybe yours is bigger (we are still talking about databases, dont laugh :D )

i would love if rhythmbox could talk through a centralized database and allow all the lan's music to be available through it. but thats not a show stopper.

and ive tried banshee and it felt, slow, buggy, and quite mono.

---

### Post by olskar on 2008-06-17
> **eldragon said:**
> i like the fact that rhythmbox is light, and fast, and does just what it does.
i dont know how big your music library is, but ive got a quite extensive collection and it doesnt complain much about it. but maybe yours is bigger (we are still talking about databases, dont laugh :D )

i would love if rhythmbox could talk through a centralized database and allow all the lan's music to be available through it. but thats not a show stopper.

and ive tried banshee and it felt, slow, buggy, and quite mono.

Doesnt DAAP-plugin do that kind of?

---

### Post by rahulthewall3000 on 2008-06-23
Banshee-1 is a much better default media player IMO.

---

### Post by Zenze on 2008-06-23
I think that exaile would be better than either one of them.

---

### Post by smartboyathome on 2008-06-23
I like Rhythmbox a lot, haven't tried Banshee 1.0 yet, but will now.

---

### Post by olskar on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=816103](http://ubuntuforums.org/showthread.php?t=816103)

---

### Post by bapoumba on 2008-06-23
Threads merged.

---

### Post by durand on 2008-06-23
> **zekopeko said:**
> my guess is that banshee is going to have all of this features and more before feature freeze for ibex

It's not that banshee needs more features, it needs to be more stable. Though without Folder Watching, it really is a no-go...(though I won't switch from AmaroK anyway...)

> i would love if rhythmbox could talk through a centralized database and allow all the lan's music to be available through it. but thats not a show stopper.

Rhythmbox might support mpd...might (i haven't checked)

Oh and we have Totem for video, don't we? I'm not really one for organising video like audio so I don't see why a music player needs this. I'm not saying it's a bad thing but it just feels a bit pointless to me.

Actually, I might install banshee for my sister, does it support the latest ipod nano?

---

### Post by olskar on 2008-06-23
> **durand said:**
> It's not that banshee needs more features, it needs to be more stable. Though without Folder Watching, it really is a no-go...(though I won't switch from AmaroK anyway...)



Rhythmbox might support mpd...might (i haven't checked)

Oh and we have Totem for video, don't we? I'm not really one for organising video like audio so I don't see why a music player needs this. I'm not saying it's a bad thing but it just feels a bit pointless to me.

Actually, I might install banshee for my sister, does it support the latest ipod nano?

I found it to be good since I have a folder with musicvideos :) But Im not gonna use it for other movies.

---

### Post by smartboyathome on 2008-06-23
I haven't found anything which would make me switch, quite the opposite actually. It crashed on me once after importing my media, and then when I went in again, I found there was no way to use jamendo with it. That is one of my favorite plugins for rhythmbox. Its even more bloated than rhythmbox as well.

---

### Post by DJ_Peng on 2008-06-24
> **Zenze said:**
> I think that exaile would be better than either one of them.
I actually use Amarok or MPD most of the time because I find Exaile takes too bloody long to load. In the time I can load Amarok (or amarok-nightly), select an album and start playing it Exaile *might* be ready for me to browse my library. I love that Exaile is a better fit for GNOME but it just takes too long for me to be able to do anything in it.

---

### Post by Kougaiji on 2008-06-25
No, it cannot watch folders and doesnt have alternate skins, so i don't see the point of moving the default. Especially since it doesn't watch folders, this bothers me. I have a collection of over 40 thousand songs (i'm a dj) and I have to wait long enough to let it import the collection ONCE, let alone go through the effort of importing it again each time I get new albums and I don't remember what all they were or where i saved them all. I like the auto-cd-cover thing, and while it doesn't scroll through the library as fast as winamp would on windows, it seems faster than most linux alternatives.

---

### Post by durand on 2008-06-26
> **olskar said:**
> I found it to be good since I have a folder with musicvideos :) But Im not gonna use it for other movies.

Oh, didn't think about that though i never use music videos :)

---

### Post by olskar on 2008-06-26
> **Kougaiji said:**
> No, it cannot watch folders and doesnt have alternate skins, so i don't see the point of moving the default. Especially since it doesn't watch folders, this bothers me. I have a collection of over 40 thousand songs (i'm a dj) and I have to wait long enough to let it import the collection ONCE, let alone go through the effort of importing it again each time I get new albums and I don't remember what all they were or where i saved them all. I like the auto-cd-cover thing, and while it doesn't scroll through the library as fast as winamp would on windows, it seems faster than most linux alternatives.

Can you change skins in rhythmbox? :O

---

### Post by BCurtisWX on 2008-07-11
It seems that Rhythmbox has gone nowhere, and that Banshee is rising and has actually IMO surpassed Rhythmbox.  Do you think that Bashee with take over as the default music player for ubuntu in the upcoming Intrepid Ibex?  I think they look a lot alike, but it seems that the banshee devs are putting more work into it.

Edit: Sorry, I keep calling it Musicbox but its Rhythmbox........ <palm to face>

---

### Post by psyke83 on 2008-07-11
> **BCurtisWX said:**
> It seems that Rhythmbox has gone nowhere, and that Banshee is rising and has actually IMO surpassed Rhythmbox.  Do you think that Bashee with take over as the default music player for ubuntu in the upcoming Intrepid Ibex?  I think they look a lot alike, but it seems that the banshee devs are putting more work into it.

Edit: Sorry, I keep calling it Musicbox but its Rhythmbox........ <palm to face>

I recommend you take a look at the recent discussion on the ubuntu-devel-discuss mailing list, rather than rehashing all the points here: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-June/004484.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-June/004484.html)

---

### Post by BCurtisWX on 2008-07-11
> **psyke83 said:**
> I recommend you take a look at the recent discussion on the ubuntu-devel-discuss mailing list, rather than rehashing all the points here: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-June/004484.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-June/004484.html)

hey neat.  thanks!

---

### Post by olskar on 2008-07-12
> **BCurtisWX said:**
> It seems that Rhythmbox has gone nowhere, and that Banshee is rising and has actually IMO surpassed Rhythmbox.  Do you think that Bashee with take over as the default music player for ubuntu in the upcoming Intrepid Ibex?  I think they look a lot alike, but it seems that the banshee devs are putting more work into it.

Edit: Sorry, I keep calling it Musicbox but its Rhythmbox........ <palm to face>

And [http://ubuntuforums.org/showthread.php?t=816103](http://ubuntuforums.org/showthread.php?t=816103) :)

---

### Post by | MM | on 2008-07-12
While i currently use Banshee (because rb playback sometimes stops and rb tag support is fubar atm compared to banshee) and there is much to like about Banshee , i would not recommend Banshee for default installation.

Banshee is still quite slow in many cases compared to rb and shutdown is also slow. it does not 'watch' directories. its video playback is not as good as totems (fullscreen does not block the screensaver for instance). it doesn't think flv's are video like the rest of gnome. and banshee doesn't _obviously_ play internet streams.

Perhaps rb could instead be improved to the level of Banshee, with a visual refresh, i think that would be preferable.  Perhaps canononical could sponsor rb development, as i see MacSlow has an interest in some Mac-like plugins for rb.  a high-quality media player/manager is no doubt cruicial in the modern pc era.

---

### Post by puccaso on 2008-07-12
the only show stopper for me
is no genre listing
i mean whats the point of having id3 data and tags,
if i cannot play music by genre.. 

to not have that is dumb, i dont care what else they have.
not having an option to play by genre makes banshee as usefull as using mplayer for a full fledged music player

---

### Post by stijngysemans on 2008-07-13
a show stopper for me is not able to watch a folder also.

---

### Post by bapoumba on 2008-07-13
One thread merged in here.

---

### Post by MadsRH on 2008-07-13
61.19% says NO, yet all the posts in this thread seems to love Banshee.

:confused:

---

### Post by olskar on 2008-07-13
I love banshee but it is just not ready

---

### Post by Manosdoc on 2008-07-13
Ha, no worry.

If they don't do it, I'll do it myself rip off Rythmbox and add Banshee

Now I'm running it through PPA Launchpad source

---

### Post by uBeer on 2008-07-13
It's just not ready for the masses, it needs a little work like folder watching, better tag support, better cover art support (Rhythmbox rocks with that on my music collection!), stability (I used it for 2 weeks when 1.0 came out, had some crashes and found out that none of my new music was found and my phone wasn't detected (w800i)...)

Good things are nice interface and the video thing, looks really cool when you go from windowed to full screen mode :D
Too bad it doesn't feel snappy: the playlist doesn't react immediately... 

But I figure most of those things will be worked out, as I said: not yet ready for the masses.

---

### Post by tech0007 on 2008-07-13
I'll make the switch if banshee can serve my breakfast and fetch my paper every morning!

lol!!!

---

### Post by psyke83 on 2008-07-13
> **uBeer said:**
> It's just not ready for the masses, it needs a little work like folder watching, better tag support, better cover art support (Rhythmbox rocks with that on my music collection!), stability (I used it for 2 weeks when 1.0 came out, had some crashes and found out that none of my new music was found and my phone wasn't detected (w800i)...)

Good things are nice interface and the video thing, looks really cool when you go from windowed to full screen mode :D
Too bad it doesn't feel snappy: the playlist doesn't react immediately... 

But I figure most of those things will be worked out, as I said: not yet ready for the masses.

Rhythmbox may have its own flaws, but it uses half the resources compared to Banshee. Unless Mono (and Banshee) gets some serious optimization and reduced memory use, it's not appropriate to be included by default.

---

### Post by tech0007 on 2008-07-13
> **MadsRH said:**
> 61.19% says NO, yet all the posts in this thread seems to love Banshee.

:confused:

Not all voters wrote their comments. Do the math.

---

### Post by ronacc on 2008-07-13
well it looks like we are goimg to send another good app down the drain . I would much prefer single purpose apps that do one thing and do it well with no frills than one behemoth that does everything half a**ed. things I specificly have absolutley no use for are playlists especialy persistant ones and coverart or cutesy visualizations .I also don't want an app that insists on trying to import my music/vidieo/whatever collection that is a nusance that I will happily live without.

---

### Post by jjgomera on 2008-07-13
i prefer gmusicbrowser, the default music player in xfce, light and powerful

---

### Post by uBeer on 2008-07-13
> **psyke83 said:**
> Rhythmbox may have its own flaws, but it uses half the resources compared to Banshee. Unless Mono (and Banshee) gets some serious optimization and reduced memory use, it's not appropriate to be included by default.

Exactly! Forgot to add that to my post ;)

---

### Post by furyy on 2008-07-14
[https://wiki.ubuntu.com/No-Mono-by-Default]("https://wiki.ubuntu.com/No-Mono-by-Default")

Anyway, i like C# , but you never know MS.

---

### Post by Gina on 2008-07-14
ATM the No's outnumber the Yes's by two to one exactly.

---

### Post by aamukahvi on 2008-07-14
Banshee 1.0 is a very nice player, however I can't stand the fact that I have to manually add every file, no FS watching.

---

### Post by Amaranth on 2008-07-15
Banshee is a very nice player (I use it) but it is currently not feasible to replace Rhythmbox with Banshee in the default install.

Banshee fixes a lot of problems with Rhythmbox and has more features but it also has it's own problems. We want better, not broken differently.

[list]
[*] Does not autoupdate when you add files to your music folder.
[*] Does not copy music to music folder when you import it. (neither does rhythmbox)
[*] Does not handle albums with multiple artists well. (neither does rhythmbox)
[*] Does not have any accessibility support. (show stopper)
[/list]
This is just a quick list off the top of my head of problems with Banshee. We don't want to trade one set of bugs for another, if we switch to Banshee it needs to do everything rhythmbox does and at least fix the problems we have with rhythmbox. I believe the file watching and album items will be fixed in the next release but we need the accessibility support to even consider it.

---

### Post by Gina on 2008-07-16
I'm quite happy with RB except for the poor handling of albums with multiple artists.  That really does need looking at.  Not a Ubuntu matter as such, I agree.  I doesn't seem that there is any app that does much better than RB at present.

---

### Post by hachaboob on 2008-07-27
Unfortunately Banshee version 1.0 crashes, it doesn't read the contents of my iPod at all and I can not subscribe to podcasts either. It is pretty much useless to me.

Rhythmbox works except for adding content onto my media player...

---

### Post by gnomeuser on 2008-07-27
> **Amaranth said:**
> 

[list]
[*] Does not autoupdate when you add files to your music folder.
[*] Does not copy music to music folder when you import it. (neither does rhythmbox)
[*] Does not handle albums with multiple artists well. (neither does rhythmbox)
[*] Does not have any accessibility support. (show stopper)
[/list]

* Coming in 1.2 which will be out very soon
* Absolutely and utterly untrue, just select the copy on import option in the preference dialog - this feature has been here since the very earliest glimpses of Banshee years ago.
* Already improved in SVN, will be included in 1.2
* Should have exactly the same a11y support as the rest of GNOME, what exactly is missing here?

Aside this a number of exciting features are coming, such as integration with MonoTorrent to allow downloading of bittorrent vod/podcasts. The amazing Mirage plugin is being ported, there's a guy doing a coverflow like plugin. In short Banshee is improving leaps and bounds every day and has a vibrant development community around to to bring us new features.

Oh and another cool thing, switching to Banshee from the users POV is painfree due to the Banshee developers taken time to do importers for major media player.

---

### Post by aamukahvi on 2008-07-27
> **gnomeuser said:**
> * Coming in 1.2 which will be out very soon
* Absolutely and utterly untrue, just select the copy on import option in the preference dialog - this feature has been here since the very earliest glimpses of Banshee years ago.
* Already improved in SVN, will be included in 1.2
* Should have exactly the same a11y support as the rest of GNOME, what exactly is missing here?

Aside this a number of exciting features are coming, such as integration with MonoTorrent to allow downloading of bittorrent vod/podcasts. The amazing Mirage plugin is being ported, there's a guy doing a coverflow like plugin. In short Banshee is improving leaps and bounds every day and has a vibrant development community around to to bring us new features.

Oh and another cool thing, switching to Banshee from the users POV is painfree due to the Banshee developers taken time to do importers for major media player.
I checked the GUADEC slides on their homepage and it does seem impressive. And 1.4 in September? Moving fast...

---

### Post by olskar on 2008-07-27
Yes Banshee development is indeed impressing. Anyone knows if there is a place where you can see when next version of rhythmbox is planned to come? Or at least a page where it says what new features next version will bring (if any)?

---

### Post by phenest on 2008-07-27
> **animaniac said:**
> personally im more for Exaile, it seems to have better performance too.

If Rhythmbox has to be replaced, then I second Exaile. Banshee has a long way to go yet. Horrible GUI too.

---

### Post by syxbit on 2008-07-28
one word. 
Mono
what were they thinking?????

---

### Post by Nullack on 2008-07-28
Whats wrong with Mono? It is an open standard. Yes it happens to be implemented on MS platforms. Its like saying VC-1 is evil because MS use that too when VC-1 is also an open standard.

---

### Post by RAOF on 2008-07-28
> **syxbit said:**
> one word. 
Mono
what were they thinking?????

Probably that it provides a managed, garbage collected, high-performance runtime for which it is extremely easy to integrate existing C libraries, with a large (and reasonably sane) standard library?

Sure, it could've been written in Python instead, but I'd guess people would be writing "OMG!!! PYTHON BLOAT" posts if they had.  I'm pretty sure Python's also somewhat slower (not that it really matters), and is more fiddly to get access to C libraries from.

C really isn't a particularly good language for writing a media library application in.

---

### Post by psyke83 on 2008-07-28
> **RAOF said:**
> Probably that it provides a managed, garbage collected, high-performance runtime for which it is extremely easy to integrate existing C libraries, with a large (and reasonably sane) standard library?

Sure, it could've been written in Python instead, but I'd guess people would be writing "OMG!!! PYTHON BLOAT" posts if they had.  I'm pretty sure Python's also somewhat slower (not that it really matters), and is more fiddly to get access to C libraries from.

C really isn't a particularly good language for writing a media library application in.

It's pretty clear that people have strong opinions about Mono, but let's not focus on Python vs Mono and instead look at the merits and shortcomings of the actual applications we're talking about.

As it stands, Banshee uses 2x the memory that Rhythmbox does - this is the issue that disqualifies it from getting included by default, in my eyes. I hope this situation improves, though - competition is good. Increasing Ubuntu's system requirements to "Vista capable" is not the solution to this (and similar) problems.

---

### Post by gnomeuser on 2008-07-28
> **psyke83 said:**
> 
As it stands, Banshee uses 2x the memory that Rhythmbox does - this is the issue that disqualifies it from getting included by default, in my eyes. I hope this situation improves, though - competition is good. Increasing Ubuntu's system requirements to "Vista capable" is not the solution to this (and similar) problems.

Interesting, on my machine Rhythmbox uses about 20-30% more memory for fewer and less complete features. I suspect you are runinng Banshee in debug by default, try checking that and if so it's a packaging bug which should be filed.

You may also want to unload extensions you are not using for such a comparison, e.g. it's hardly fair to load everything for Banshee and then compare it to a feature crippled Rhythmbox when declaring a winner.

Will Mono always add to memory usage, yes, by design that is the case but look at what you get in return in terms of fixes for potential bugs due to the managed nature of the entire framework. It is also very possible to do very memory efficient .NET programming, my cousin, who happens to work for Microsoft (yes we do call him the black sheep of the family), was involved in the development of a handheld scanner project for Microsoft where they implemented a complete ERP system that ran in 64 megs of ram. All managed code, it is about the tradeoffs you make in the design for the deployment. Let us work on improving Mono for low memory setups instead of doing this senseless dismissal upfront for what is a completely solvable issue.

---

### Post by gnomeuser on 2008-07-28
> **olskar said:**
> Yes Banshee development is indeed impressing. Anyone knows if there is a place where you can see when next version of rhythmbox is planned to come? Or at least a page where it says what new features next version will bring (if any)?

Rhythmbox unlike Banshee does not commit to a release schedule nor do they provide a list of future features. 

This presentation contains the feature goals for Banshee 1.2 and 1.4
[http://download.banshee-project.org/documents/GUADEC-2008-Banshee_Talk.pdf](http://download.banshee-project.org/documents/GUADEC-2008-Banshee_Talk.pdf)

Banshee 1.2 (coming very soon)
* Internet Radio
* Equalizer
* Multi-artist album support
* DAAP
* Recommendations
* Library directory watching/scanning

Banshee 1.4 in September
* MonoTorrent integration
* Podcast directory (Miro Guide)
* Playbin2 (gapless playback)
* UPnP
* Device playlist support
* Gnome Do support
* Better Last.fm community integration (new API)
* 3rd party extension browser

---

### Post by pt123 on 2008-07-28
Currently no but RB has been very slow with it's feature improvement recently. At one stage they were rolling out features rapidly. The plans to introduce a cover flow and Google like tags feature hasn't moved. 

While Banshee has been steam rolling ahead. A bit scary to compare the progress of mono and non-mono based apps.

---

### Post by psyke83 on 2008-07-28
> **gnomeuser said:**
> Will Mono always add to memory usage, yes, by design that is the case but look at what you get in return in terms of fixes for potential bugs due to the managed nature of the entire framework. It is also very possible to do very memory efficient .NET programming, my cousin, who happens to work for Microsoft (yes we do call him the black sheep of the family), was involved in the development of a handheld scanner project for Microsoft where they implemented a complete ERP system that ran in 64 megs of ram. All managed code, it is about the tradeoffs you make in the design for the deployment. Let us work on improving Mono for low memory setups instead of doing this senseless dismissal upfront for what is a completely solvable issue.

You had me right until the last sentence. What part of my message was a "senseless" dismissal? I made the observation that memory consumption was much higher than Rhythmbox, and I expressed hope that this situation would improve in the future (without senselessly jacking up Ubuntu's system requirements merely for a music player). 

Try being a little less defensive, perhaps. I wasn't attacking Mono or Banshee, just offering an observation.

---

### Post by ronacc on 2008-07-28
since we are talking about a default and space is always a concern on the install cd IMHO both Rhythmbox and Banshee are bloated and frill loaded , how about a "music player" that plays music period end of sentence . no "libraries " no "import any d**n thing" no "dancing fractals" just point it at a file and listen . on a fresh install of intrepid A3 rhythmbox pointed at and playing a single song (mp3) used 10% cpu and 31.5 mb memory  banshee under the same conditions used 11% cpu and 44 mb . 10 or 11% cpu on a system with an amd64 x2 4600 is absurd and even the 31.5 mb of mem that rhythmbox uses to play a 2.7 mb mp3 is criminal .

---

### Post by olskar on 2008-07-28
> **ronacc said:**
> since we are talking about a default and space is always a concern on the install cd IMHO both Rhythmbox and Banshee are bloated and frill loaded , how about a "music player" that plays music period end of sentence . no "libraries " no "import any d**n thing" no "dancing fractals" just point it at a file and listen . on a fresh install of intrepid A3 rhythmbox pointed at and playing a single song (mp3) used 10% cpu and 31.5 mb memory  banshee under the same conditions used 11% cpu and 44 mb . 10 or 11% cpu on a system with an amd64 x2 4600 is absurd and even the 31.5 mb of mem that rhythmbox uses to play a 2.7 mb mp3 is criminal .

I think many people nowadays need libraries, it's a good way to have order in a mp3/ogg-collection of 1000+ songs.

---

### Post by silkstone on 2008-07-28
Please do not replace rhythmbox. Have something else as an alternative, by all means, but leave rhythmbox as a simple, bling-free music player that really works.

I'm sure I not alone here - I like Ubuntu for its simplicity and freedom from bloat. I don't want 'skins', eye-candy or anything else that consumes resources and adds little or nothing to functionality.

Rhythmbox is a simple, efficient and easy-to-use application for playing music files. Let's keep it that way. Please.

P.S. I have a collection of over 5000 files/songs on rhythmbox, and it works perfectly.

---

### Post by ronacc on 2008-07-28
> **olskar said:**
> I think many people nowadays need libraries, it's a good way to have order in a mp3/ogg-collection of 1000+ songs.

I thought those were called "drectories" , IIRC there is one im my /home named MUSIC , why should a music player feel compelled to keep a seperate database . I understand that many people want playlists and visualizations etc but it is my belief that they should be handeled by "plugins" not by bloating the basic app .

---

### Post by silkstone on 2008-07-28
> **ronacc said:**
> since we are talking about a default and space is always a concern on the install cd IMHO both Rhythmbox and Banshee are bloated and frill loaded , how about a "music player" that plays music period end of sentence . no "libraries " no "import any d**n thing" no "dancing fractals" just point it at a file and listen . on a fresh install of intrepid A3 rhythmbox pointed at and playing a single song (mp3) used 10% cpu and 31.5 mb memory  banshee under the same conditions used 11% cpu and 44 mb . 10 or 11% cpu on a system with an amd64 x2 4600 is absurd and even the 31.5 mb of mem that rhythmbox uses to play a 2.7 mb mp3 is criminal .

You can do that with Totem, vlc or whatever. Just right-click the music folder and play with whatever you choose.

On my system, rhythmbox uses less than 5% CPU, and this is not a high-spec machine.

With regard to memory usage, mp3 and similar files are compressed and have to be uncompressed before they can be played, so they will take up more space in memory than the source file. The same applies to opening a JPEG image file in a photo editor - the memory usage may be several times the size of the compressed file.

---

### Post by ronacc on 2008-07-28
I may be wrong but I thought that decompression of mp3's was done "on the fly" rather than decompress then play . just to test that I fed rythmbox a 13.9 mb podcast and on that file it used the same cpu but only 29.1 mb mem , that indicates on the fly to me .

---

### Post by cariboo on 2008-07-28
I can confirm that mp3's are decompressed on the fly. I used to use my old AST Bravo as an mp3 player only, if it stopped to decompress an mp3 before playing it I wouldn't have seamless music 24 hours a day.

Jim

---

### Post by Nullack on 2008-07-28
Ronacc your solution is mplayer (ffmpeg) and gnome-mplayer for the front end. Best multimedia solution on Linux - fast, wide support, robust

---

### Post by ronacc on 2008-07-28
@ nullack thanks I always install mplayer , I was just being a gadfly and ranting against apps (including mplayer) that have delusions of omnipotents . I have an intense dislike of "one size fits all" .

---

### Post by BwackNinja on 2008-07-28
I like rhythmbox's interface better than banshee's but personal style probably affects these decisions too much :P. Probably the inability to detect changes in your library is the biggest problem. Rhythmbox is not quite so integrated as totem is so I guess it would be *possible* if/when banshee becomes better than rhythmbox at everything but I'd say that time isn't now.

@Nullack I'm really surprised that I haven't encountered even a failed project of a dedicated music player that uses mplayer as a backend. I've even searched for one. I wonder if there's any reason why mplayer wouldn't be suited for that...

---

### Post by Nullack on 2008-07-28
I disagree mate - the beauty of say ffmpeg in my view is that with libavcodec I have a very powerful, fast, robust library with which to decode many many types of standards. I dont want to have to trawl through 100+ different SVN trees to grab the latest decoders.

---

### Post by ronacc on 2008-07-28
@ BwackNinja while not a "music player" per se , the radio screenlet uses mplayer as a backend .

---

### Post by Nullack on 2008-07-28
Mplayer is very closely tied to ffmpeg - I think some audio apps use ffmpeg demuxers and decoders.

---

### Post by olskar on 2008-07-30
Banshee 1.2 is out!

New for 1.2 is an equalizer, support for internet radio, music recommendations, DAAP client support, compilation album support, and more.


[http://banshee-project.org/download/archives/1.2.0/](http://banshee-project.org/download/archives/1.2.0/)

---

### Post by aamukahvi on 2008-07-30
> **olskar said:**
> Banshee 1.2 is out!

New for 1.2 is an equalizer, support for internet radio, music recommendations, DAAP client support, compilation album support, and more.

[http://banshee-project.org/download/archives/1.2.0/](http://banshee-project.org/download/archives/1.2.0/)
Still no directory watching :/

---

### Post by olskar on 2008-07-30
> **aamukahvi said:**
> Still no directory watching :/

Nope, it was planned for 1.2 but will definitely be in 1.4.

And with this fast development, 1.4 will propably come pretty soon ;)



EDIT: Some interesting reading about the future of Banshee;
[http://download.banshee-project.org/documents/GUADEC-2008-Banshee_Talk.pdf](http://download.banshee-project.org/documents/GUADEC-2008-Banshee_Talk.pdf)

---

### Post by ronacc on 2008-07-30
> **olskar said:**
> Banshee 1.2 is out!

New for 1.2 is an equalizer, support for internet radio, music recommendations, DAAP client support, compilation album support, and more.


[http://banshee-project.org/download/archives/1.2.0/](http://banshee-project.org/download/archives/1.2.0/)
 
did you get this to build in intrepid ? my ./configure is erroring out at GNU gettext tools not found and I can't find that and some other depenencies in synaptic .

---

### Post by olskar on 2008-07-30
> **ronacc said:**
> did you get this to build in intrepid ? my ./configure is erroring out at GNU gettext tools not found and I can't find that and some other depenencies in synaptic .

Nope, but it should appear in [https://edge.launchpad.net/%7Ebanshee-team/+archive](https://edge.launchpad.net/%7Ebanshee-team/+archive) soon :)

---

### Post by ronacc on 2008-07-30
I noticed they have a link to an opensuse repository but none for us :(

---

### Post by olskar on 2008-07-31
1.2 is now in the repository I mentioned above, enjoy :)

---

### Post by ronacc on 2008-07-31
they must have pushed it right to the regular repos ! I updated a few minutes ago and banshee was updated to 1.2 and I don't have the launchpad repo enabled :)

---

### Post by NilsHG on 2008-07-31
although i would want to vote yes, i did not. banshee 1.2 is great, except for random crashes when switching from streaming audio to a mp3 file in the library... it is not stable enough.

personally i stick to amarok, but i am always hoping for a gtk player that can catch up to the kde player

---

### Post by Lokken on 2008-08-01
> **silkstone said:**
> 
Rhythmbox is a simple, efficient and easy-to-use application for playing music files. Let's keep it that way. Please.

P.S. I have a collection of over 5000 files/songs on rhythmbox, and it works perfectly.

See, perhaps with 5000 files/songs Rhythmbox holds up well.

I'm in the ~36000 song range (with a large portion of them being FLAC, bringing me around 580 GB), and I find that Rhythmbox chugs along with them (and I've experienced crashes in whatever version came with Feisty). I've tried Banshee and Exaile (though not too recently, but will give them another try soon).

So far, my favorite music player for the large library is Amarok with a PostgreSQL or MySQL backend.

That said, I do think Rhythmbox is a fine default for the time being.

---

### Post by ronacc on 2008-08-01
36,000 songs ? thats impressive ! at an avg of 2.5 min/song that 62.5 days of 24/7 music with no repeats.

---

### Post by plun on 2008-08-01
> **Lokken said:**
>  I've tried Banshee and Exaile (though not too recently, but will give them another try soon).

That said, I do think Rhythmbox is a fine default for the time being.


Well, Exaile from Launchpad/bzr just rocks....:guitar:

With kernel 2.6.26-5 and Pulseaudios equalizer enabled
its more then great....

So what is Rhythmbox and Banshee. ??? ..:)

---

### Post by olskar on 2008-08-01
> **plun said:**
> Well, Exaile from Launchpad/bzr just rocks....:guitar:

With kernel 2.6.26-5 and Pulseaudios equalizer enabled
its more then great....

So what is Rhythmbox and Banshee. ??? ..:)


What is Rhythmbox, Banshee and Exaile?

I heard the player Listen is soon out in a new version after long development and I heard it will be great ;)

---

### Post by bom28 on 2008-08-01
> **Lokken said:**
> See, perhaps with 5000 files/songs Rhythmbox holds up well.

I'm in the ~36000 song range (with a large portion of them being FLAC, bringing me around 580 GB), and I find that Rhythmbox chugs along with them (and I've experienced crashes in whatever version came with Feisty). I've tried Banshee and Exaile (though not too recently, but will give them another try soon).

So far, my favorite music player for the large library is Amarok with a PostgreSQL or MySQL backend.

That said, I do think Rhythmbox is a fine default for the time being.

Have you tried GMusicBrowser, it is designed with huge libraries like yours in mind. Although it lacks some features that some would consider essential (ipod, radio), it has a lot of great unique features, is **very** customizable and is very stable. It's a pity the default configuration doesn't show off the nice features :(
See the [screenshots page]("http://squentin.free.fr/gmusicbrowser/screenshots.html") and [contributed layouts]("http://squentin.free.fr/gmusicbrowser/contrib.html")
Some of the nice features :
-[Songtree]("http://squentin.free.fr/gmusicbrowser/screenshots/songtree_example.png")
-[weighted random modes]("http://squentin.free.fr/gmusicbrowser/screenshots/wrandom_example.png") :cool:
-labels (with icons)
-customizable window layouts
-"traytip" with buttons and everything, you can do a lot of things from there
-[cloud mode]("http://squentin.free.fr/gmusicbrowser/screenshots/cloud_example.png")
-click on the current song title to get the list of songs from the album, and enqueue with middle click
...

Don't forget to install libgstreamer-perl to use gstreamer and libgtk2-trayicon-perl to get the "traytip"

---

### Post by DarkW0lf on 2008-08-01
I wouldn't replace Rhythmbox.

It does what I need and it manages the music library well. The only thing I'd change is being able to reorder the columns displayed and the way titles are sorted (ie the priority should be Album Artist Song and not Artist Album Song; the first handles albums of various artists correctly, the second doesn't)

I don't need a music manager integrated with a cd burner and if you have so much music that you get database support issues maybe you should be looking into the database apps more and not music managers. A cd burner is just bloat, if you want to make cd's of your library, use Serpentine (which can use Rhythmbox playlists).

And I certainly don't need bling.

---

### Post by plun on 2008-08-01
> **olskar said:**
> What is Rhythmbox, Banshee and Exaile?

I heard the player Listen is soon out in a new version after long development and I heard it will be great ;)

Well, sounds great.

I have never heard of any mainstream user which likes Rhythmbox.

Its directly to find better alternatives,  so apparently something is wrong with Rhythmbox, IMHO.

---

### Post by syxbit on 2008-08-01
I loved 'listen'
but for OSS it has made very little progress in the last 2 years.
(it's just one dev, so you can't blame him)
i personally want software that advances more quickly, like rythmbox, exaile and amarok

---

### Post by Buzzdee on 2008-08-02
Banshee is definitely more advanced than Rhythmbox, but there are still some flaws that make it a bad choice for a default programme:
[LIST]
[*]No automatic scanning of the library
[*]Problems with playback order, sometimes it just repeats the first item of a folder
[*]Bad handling of compiled albums because it stores each title under the artist's name
[*]Editing tags doesn't work properly
[*]Random crashes in Hardy
[/LIST]

Those are the biggest ones I realised myself and I stopped reading the mailing list, so I can't tell how many other ones are out there, but chances are high there's quite a bunch. 
Let's have a look at 1.2 and see again, it should be released soon, I heard.

Basti

---

### Post by Swarms on 2008-08-02
I have never really used RB because I didn't find it good enough. I prefer Banshee but I do not think its quite there yet and ready for the masses, but with this rapid development (1.4 in September already), I think it should be reconsidered for the 9.04 release.

And yeah 1.2 rocks!

---

### Post by olskar on 2008-08-02
> **syxbit said:**
> I loved 'listen'
but for OSS it has made very little progress in the last 2 years.
(it's just one dev, so you can't blame him)
i personally want software that advances more quickly, like rythmbox, exaile and amarok

You want software that advances more quickly? :confused: Rhythmbox is like a dead duck compared with Banshee development

---

### Post by Buzzdee on 2008-08-02
So, 1.2 is out... I didn't get an update though, although I even have the backports enabled for Hardy. I guess, there have been quite some problems with the repositories when upgrading from gutsy. Can anyone please give me the repo line which enables me to get 1.2 via synaptic?
Thanks a lot

---

### Post by Swarms on 2008-08-02
> **Buzzdee said:**
> So, 1.2 is out... I didn't get an update though, although I even have the backports enabled for Hardy. I guess, there have been quite some problems with the repositories when upgrading from gutsy. Can anyone please give me the repo line which enables me to get 1.2 via synaptic?
Thanks a lot

Instructions here: [https://launchpad.net/~banshee-team/+archive](https://launchpad.net/~banshee-team/+archive)

---

### Post by Buzzdee on 2008-08-02
Thanks, installation worked flawlessly. The first thing I did was to crash the programme, though. I tried to connect to a shared library (a colleague shares some music with his mac) and programme closed. So much for default programme, then ^^

I would even think about adding amarok, although it's ugly as hell, it does its job quite nice.

---

### Post by plun on 2008-08-02
> **olskar said:**
> You want software that advances more quickly? :confused: Rhythmbox is like a dead duck compared with Banshee development

Well... a mainstream user which comes from Windows or OSX compares a media player with WMP or iTunes.

Rhythmbox is a "dead duck" compared to those for a new user which
knows more or less about different functions.

A mainstream user also finds it important that a player looks good, ie eye-candy...:)

Time for a Banshee test...

---

### Post by mitchellcipriano on 2008-08-02
I have been running Banshee for a while now. I had good luck with it until the upgrade to 1.2. The upgrade installed fine, but when I ran Banshee I clicked on the about box while the DB was rebuilding after the upgrade. This caused my entire system to hang. Once I got my notebook restarted Banshee would not load because of a corrupted DB. I deleted the DB file and restarted Banshee. It all seems fine now, but it caused me to loose some confidence in Banshee.

---

### Post by riftt on 2008-08-02
After seeing the rhythmbox replacement subject a couple of times before I decided to give banshee and exaile a try. After using banshee for about two weeks I still haven't found anything interesting to worth the switch: the video thing is useless since I have mplayer installed :), it feels slower and it is missing the lyrics display (at list I haven't find them). After 1.0 release it seems stable but still nothing special.

Exaile it is in the quite early development stage but it shows real potential, especially for using the python language that I love. 

I know that competition is a good thing for rhythmbox so I really wish the rest of the players the best of luck, BUT for me there is no reason to change rhythmbox. If you are bored with this excellent player and feel the need to experiment, feel free to install anything you want but I think that such topics only make rhythmbox developer sad for no reason, no reason at all. Keep up the good work guys.

---

### Post by amano on 2008-08-02
And just keep in mind, that banshee requires the mono framework and together with mono wastes a lot of LIVE CD space which could be spent otherwise. Getting rid of Mono in the default install (= on the live CD) is one of the most requested things on Ubuntu Brainstorm.

---

### Post by w4tch0 on 2008-08-02
I am RB user, since I got used to it together with its little annoyances. Never found any particular reason to switch to banshee.

I tried banshee 1.0 and 1.2 and so far i figured:
- no folder watching (show stopper).
- no drag&drop support (what good is a play queue for if I can't drag a song from i.e. nautilus window into it?).
- uses twice as much resources compared to rhythmbox.
- what the hell is this micro mini short seek bar thing? How am I suppose to seek a song using that? We have wide screen displays for a reason nowadays, time to start using them effectively.
- the seek bar doesn't support "click to jump" behavior (well, not even RB has this implemented properly, I'd like a winamp-like seek bar behavior :( ).

Than there are things I miss in both Banshee and RB (compared to i.e. Amarok):
- automatically resume playback on player start from where it stopped when I turned the player off.
- a bit more configuration options (Banshee 1.x seems to be even worse than RB at this).

But there is one huge plus for Banshee compared to RB and that is really fast development and also Banshee's devs seem to listen more to community (RB was a personal project of its original author so I can't really blame him) ... maybe within a few months or a year Banshee will surpass RB, or even Amarok, but for now it has still a long way to go and I don't see any major reason to make it Ubuntu default audio player ... except maybe Banshee being more promising for the future.

---

### Post by gnomeuser on 2008-08-03
> **mitchellcipriano said:**
> I have been running Banshee for a while now. I had good luck with it until the upgrade to 1.2. The upgrade installed fine, but when I ran Banshee I clicked on the about box while the DB was rebuilding after the upgrade. This caused my entire system to hang. Once I got my notebook restarted Banshee would not load because of a corrupted DB. I deleted the DB file and restarted Banshee. It all seems fine now, but it caused me to loose some confidence in Banshee.

If it's not in bugzilla, it doesn't exist.. it's that simple, complaining on a forum, especially one the developers have no reason to visit, will not get your problem fixed. No software is flawless but expecting us to improve it when you don't even inform us about the flaws that may have gone undetected in testing.. that's just silly.

If you want software it improve, banshee or anything, tell us when it breaks.. and please tell us upstream not to the Ubuntu bugtracker, that will vastly increase the chance of getting things fixed.

---

### Post by grigio on 2008-08-03
+1 for Banshee

---

### Post by Polygon on 2008-08-03
i personally dont think this will ever be resolved. there are too many really good music players out there, i say just leave Rhythmbox in.... just because a ton of people install their favorite music player anyway.

---

### Post by ronacc on 2008-08-03
> **Polygon said:**
> i personally dont think this will ever be resolved. there are too many really good music players out there, i say just leave Rhythmbox in.... just because a ton of people install their favorite music player anyway.

this is true of most of the replace X with Y threads , no default will satisfy everyone .

---

### Post by mitchellcipriano on 2008-08-03
> **gnomeuser said:**
> If it's not in bugzilla, it doesn't exist.. it's that simple, complaining on a forum, especially one the developers have no reason to visit, will not get your problem fixed. No software is flawless but expecting us to improve it when you don't even inform us about the flaws that may have gone undetected in testing.. that's just silly.

If you want software it improve, banshee or anything, tell us when it breaks.. and please tell us upstream not to the Ubuntu bugtracker, that will vastly increase the chance of getting things fixed.

It was logged into bugzilla by me prior to my post here. The bug number is: 546000. I was not complaining here. I was simply stating my experience with Banshee in a thread about Banshee. Isn't this the purpose of the forum?

---

### Post by syxbit on 2008-08-03
> **ronacc said:**
> this is true of most of the replace X with Y threads , no default will satisfy everyone .

while true, i think ubuntu should pick a default player that fits most needs.
based on mark shuttleworth's recent comments, the ubuntu dev's should pick one that has bling, and is flashy.
exaile fits, and so does banshee. both need more work though, and may have more features than rhythmbox, but seem like they could use a bit more cleanup (and bug fixes)
just noticed some updates on exaile. check the dev's blog for info
[http://www.vimtips.org/28/](http://www.vimtips.org/28/)


the reason for exaile's speed is his reusing code from amarok, listen, and other music apps (which i think is commendable. that's the whole point of OSS)
i just hope he uses code from the unreleased Amarok 2. We really need a GTK+ amarok 2 :)

---

### Post by CloudFX on 2008-08-04
This idea has been posted many times on brainstorm.ubuntu.com, and they generally get shot down pretty quickly.  I personally prefer Banshee over any other music player, but at this point, I don't think it's quite ready.

---

### Post by boombox1387 on 2008-08-04
> **CloudFX said:**
> This idea has been posted many times on brainstorm.ubuntu.com, and they generally get shot down pretty quickly.  I personally prefer Banshee over any other music player, but at this point, I don't think it's quite ready.

I agree completely.  I absolutely love Banshee, and it easily does most things that I want a music player to do (though support for the sortartist tag and GTK-type-ahead searching would be nice improvements), but at this point it isn't quite ready to be the default player.  Maybe by the time Intrepid gets a bit closer, or definitely by Interpid+1, but for now it probably isn't worth the change.

---

### Post by mc4100 on 2008-08-04
Dunno about being shipped as default, due to mono (no comment), but either way it doesn't really matter. I use Rhythmbox, but also am a fan of Banshee, so I frequent the wiki to check how it's doing. I just tested 1.2:

Banshee's Pros

	Better mouse-over tray pop-up (Shows the progress slider), and better Tray Context-Menu 	(Repeat/Shuffle)
	Next-Song/Next-Random-Song button (Perhaps not useful, but IMO, this is a very nice touch) 		and has shuffle by Artist/Song/Album
	Right-Clicking on the Columns allows for easy change of visible Columns
	Superior Last-Fm integration (Right-Click tray has Love/Ban Track), and the UI is more 		intuitive (Indicates when buffering, and fetching first results)
	Stop playing when finished song
	Close to Tray (CON: enabled by default)
	Recommended Artists
	Search (Artists/Albums/Titles)
	Equalizer
	Cover Art fetching/Cover Art from the album folder
	Bookmarks (Saves your place in the current song: might be good for Audio books, but I 		disabled it)

Useful Extensions:
	Mirage! "Mirage analyzes your entire collection. When it's done, you add songs to a special 		playlist and Mirage automatically fills in songs acoustically similar to the ones you added."

Banshee's Cons

	Video playback was rather buggy -- it's a very nice feature, but not one I expect to use.
	*Tiny* progress slider (With a -crappy- "Seek to position" addition) (Show Stopper, 		seriously, how can *anyone* use this -- what were they thinking?!)
	No directory watching (Show Stopper, but allegedly planned for next release, yay)
	Larger memory footprint (~50 megs vs Rhythmboxes' ~20 megs, whatever, if you're not using 		it, you're probably wasting it)
	More CPU Cycles than Rhythmbox (I can handle this, I mean, it's not *that* much more)
	The furthest-right column isn't flush like the others (Minor inconsistency issue)
	The UI is cluttered, with many things being grouped in corners (Art, Controls, etc., and 	free space is wasted (However, from their wiki: "The lower-left cover art and the ability to 	set cover art are still being worked on.")
	"Write CD..." is under the Edit Menu, and not "Media" which is odd. (Minor issue)
	No Crossfading/Gapless playback (Show Stopper)

Rhythmbox's Pros

	Near instant load time!
	Less CPU cycles (Meh. CPU's are fast; but if you need lightweight, I suppose it's essential)
	Lighter Memory Footprint (Meh. Memory is cheap, but if you need it...)
	Stability
	Search (Artists/Albums/Titles)
	Nicer length of 'seek-to' slider (My favourite feature by far, much more accurate)
	Nicer side bar groupings (benefits lighter themes ...  I use Aurora Midnight, lol)
	UI has less clutter; it uses available space better (Album Art in Sidebar)
	Close to Tray (not enabled by default)
	Crossfading/Gapless playback (with some useful options)
	Cover Art fetching/Cover Art from the album folder

Useful Plugins, to match Banshee functionality:
	Equalizer
	In the Mood (Picks the next song, based on the 'mood' of the currently playing one, 		essentially, Mirage for Rhythmbox)
	Music Recommendations from Last.fm -- almost identical to Banshee's, but I like this one 		better.

Rhythmbox's Cons

	Missing: stop playback when the current song ends. (Minor issue, but it would be nice)
	Doesn't fade-out when quit (Amarok does this, it's nice)
	No Video playback (As I said, doesn't really bother me.)

Misc.

	No matter how much I try to ignore it, Banshee (Or any other player, for that matter) sounds better than Rhythmbox; I don't even think this it possible (It's the same back-end!) but I swear I can hear a difference. Am I just crazy? -
	No, don't answer that.

	That Banshee is a good player is clear, in fact, I think it's excellent. And although I found it harder to configure than Rhythmbox, it's certainly an easy to use player. Yes, it does lack some much needed things, apart from that it's nearly feature complete. But Rhythmbox can be made to have identical functionality. And it doesn't have the same shortcomings.
So, why switch to Banshee? What's holding it back?
For me, it's the small (but not infinitesimal) UI imperfections and, for others, the bloat (which to be fair, can't really be helped). I'm not sure if this is enough to stop it being the default choice but, for me, I'm back to Rhythmbox. Banshee was so close to being my new, favourite music player; I'm sure there will be a time (seemingly soon; they are pushing new versions all the time) when I can put up with the bloat and sluggishness -- only when the features mature and the UI is polished to a glossy shine.
Maybe then, it will be ready -- for me, and for Ubuntu. But as I said, I like them both, and I definitely like where Banshee is headed. Problem is, it's not quite there...

---

### Post by supernovus on 2008-08-15
I've used dozens of different music/media players, and stuck with Banshee for quite a while, but there were some bugs that made me go hunting for a replacement. Then with (I think) Feisty, I switched to Rhythmbox, and haven't looked back. It "just works" and has features like "folder watching" and "gapless playback" which I would find hard to live without.

I vote to keep Rhythmbox as default, but ensure that all of the other choices are still there, as in everything, it's a matter of personal taste.

---

### Post by sicofante on 2008-08-24
> **gnomeuser said:**
> If it's not in bugzilla, it doesn't exist.. it's that simple, complaining on a forum, especially one the developers have no reason to visit, will not get your problem fixed. No software is flawless but expecting us to improve it when you don't even inform us about the flaws that may have gone undetected in testing.. that's just silly.

If you want software it improve, banshee or anything, tell us when it breaks.. and please tell us upstream not to the Ubuntu bugtracker, that will vastly increase the chance of getting things fixed.
Wow, what a great list of "what a developer should not do".

1. If a developer has no reason to go to a forum where their users hang out, s/he's not a real developer. S/he's just having fun with him/herself.

2. Never ask your users to work for you. If you want feedback, make it simple. Don't say "upstream" or "bugzilla" or any other geek-only word. If you don't want feedback, you're developing just for yourself. Go to 1.

3. Never call your users silly for expressing an opinion wherever they please. It makes you look silly...

4. Your users don't owe you s**t. Don't talk to them like you're making them a favour.

Have a nice day.

PS: I vote for Rythmbox for now. Ubuntu shouldn't jump to different defaults on each release unless there's a really powerful reason to do so. Current status of Banshee, while nice, doesn't justify the change.

---

### Post by durand on 2008-08-24
> Your users don't owe you s**t. Don't talk to them like you're making them a favour.

They owe the developer a thanks for using their software for free...and their cooperation and help.

---

### Post by ghindo on 2008-08-24
> **mc4100 said:**
> Dunno about being shipped as default, due to mono (no comment), but either way it doesn't really matter.Why would Mono be a problem?  Don't F-Spot and Tomboy use Mono?

---

### Post by mc4100 on 2008-08-25
> **ghindo said:**
> Why would Mono be a problem?  Don't F-Spot and Tomboy use Mono?
You're right, they do, but, and I could be totally wrong, I think Banshee uses more mono packages due to it being a more full featured app, which means more space would be needed on the CD so other stuff would need to be removed. Does anyone know if installing Banshee requires extra packages not shipped by default (mono or otherwise)?

---

### Post by Exsecrabilus on 2008-08-25
Ehh, replying the the first post without reading the rest of the replies:

OpenSUSE uses Banshee, and (I know some of you are gonna oppose and say "What's wrong with that?" but,) Ubuntu has its own pride too and it doesn't want to copy another distro (*waits for flame*) and use their default application.

Other than that, Rhythmbox sucks *** and Banshee > you.

---

### Post by psyke83 on 2008-08-25
> **Exsecrabilus said:**
> Ehh, replying the the first post without reading the rest of the replies:

OpenSUSE uses Banshee, and (I know some of you are gonna oppose and say "What's wrong with that?" but,) Ubuntu has its own pride too and it doesn't want to copy another distro (*waits for flame*) and use their default application.

Other than that, Rhythmbox sucks *** and Banshee > you.

At the risk of engulfing us all in flames, I would imagine there's a certain bias towards Mono apps in OpenSUSE, considering the Novell-Microsoft interoperability deal.

---

### Post by darthkhamul on 2008-08-25
Mono is a problem because the more mono applications you got in a distro, the more difficult it well be to remove it when microsoft asks the money.
Cause Suse can use mono, and push it only because they pay microsoft for no being sued. I think nobody want that ubuntu be ransomed by microsoft for the use of their technologies.
So why not use mono apps if you want, but please don't put it in the core of a distro.

---

### Post by mc4100 on 2008-08-25
> **darthkhamul said:**
> Mono is a problem because the more mono applications you got in a distro, the more difficult it well be to remove it when microsoft asks the money.
Cause Suse can use mono, and push it only because they pay microsoft for no being sued. I think nobody want that ubuntu be ransomed by microsoft for the use of their technologies.
So why not use mono apps if you want, but please don't put it in the core of a distro.
It's not really the problem that mono apps are shipped by default, it's as easy to remove as sudo apt-get remove (--purge, if you're feeling particularly vindictive), nor is mono actually that bad, it *is* free and open source software (LGPLv2 + MIT, I think), it's just that there's so much hostility due to the fact that by entering into a cross-licensing with Microsoft, Novell thereby validated their claims, that would otherwise have been resisted until they gave up, or FOSS devs coded around the issues.

---

### Post by Hairy_Palms on 2008-08-26
banshee should NOT be default, its far from mature and stable, its buggy, radio streams crash it most of the time for a start, it uses 3 times as much ram and cpu as Rhythmbox, largely due to its mono roots. weve had this thread for the past 2 releases, and the situation still hasnt changed.

---

### Post by damoxc on 2008-08-26
> **Hairy_Palms said:**
> banshee should NOT be default, its far from mature and stable, its buggy, radio streams crash it most of the time for a start, it uses 3 times as much ram and cpu as Rhythmbox, largely due to its mono roots. weve had this thread for the past 2 releases, and the situation still hasnt changed.

Evidence to backup these arguments...?

I just checked using the 2 versions in intrepid, Banshee was only using 5-10mb more. Hasn't crashed when playing a radio stream.

---

### Post by sicofante on 2008-08-26
> **Hairy_Palms said:**
> banshee should NOT be default, its far from mature and stable, its buggy, radio streams crash it most of the time for a start, it uses 3 times as much ram and cpu as Rhythmbox, largely due to its mono roots. weve had this thread for the past 2 releases, and the situation still hasnt changed.
The situation has definitely changed a lot since the past two releases. The thread makes sense for every release, especially since Banshee is developing very fast.

I still voted no because I'm on the conservative side and would change defaults only if they'd radically improve the distro. IMO Banshee is, at this point, level with Rythmbox, more or less (each has its pros and cons). It might have solved the "watch folders" issue by Intrepid Ibex release time, which would eliminate its biggest con, but even then, it's not a really huge step from Rythmbox.

However, unless Rythmbox devs take care, by 9.04 Banshee will definitely be that huge step and it might be worth the change.

---

### Post by MaX on 2008-08-26
> **damoxc said:**
> Evidence to backup these arguments...?

I just checked using the 2 versions in intrepid, Banshee was only using 5-10mb more. Hasn't crashed when playing a radio stream.

The "Works for me!" evidence isn't all that great either... Since Banshee started making a fuss on Planet Gnome (around 1.0) I've had it on my disk.
But without Watching a folder I won't use it. 

I'd rather sort my Music by, Genre and Artist than just Artist and Album.
It has no play queue. Pressing radio makes it crash.

It's Last.fm implementation seems better though.

---

### Post by damoxc on 2008-08-26
> **MaX said:**
> The "Works for me!" evidence isn't all that great either... Since Banshee started making a fuss on Planet Gnome (around 1.0) I've had it on my disk.
But without Watching a folder I won't use it. 

I'd rather sort my Music by, Genre and Artist than just Artist and Album.
It has no play queue. Pressing radio makes it crash.

It's Last.fm implementation seems better though.

Oh I know it's not, I just don't think it's fair to slander a programs reputation with nothing backing up your statements.

It does have a play queue.

Are you using the latest version available (1.2.1 off the top of my head)?

---

### Post by boombox1387 on 2008-08-26
Yeah, there's definitely a play queue.  I thought that was in all of the 1.x releases, but maybe it was new in 1.2.  I definitely think that Banshee will be ready to replace Rhythmbox by Intrepid+1.

---

### Post by Hairy_Palms on 2008-08-26
> Evidence to backup these arguments...?

Here you go, 55.9mb to rhythmbox's 19.0mb

playing same song with the exact same music library imported, this is hardy with the PPA package, not intrepid but i dont use intrepid day to day, only to test it, but its the same version of banshee.

I thought banshee 1.x had promise, im not just mindlessly slandering a program, but it unfortunately has many of the same issues that plagued 0.13.x, no easy way to provide evidence for the radio bug, but MaX said it happens to him, so its not only me.

---

### Post by damoxc on 2008-08-26
Ok that's fair enough.

[ATTACH]82899[/ATTACH]

That's showing RB vs B in my copy of Intrepid. I'm guessing the newer copy of mono (which I think has had quite a lot of memory reductions since novell hired people specifically for that task) may have affected the results.

I did have the radio bug before but it now all seems very well behaved.

---

### Post by gmclachl on 2008-08-26
I do like Banshee, but I don't think it should be included. In my experience it crashes (core dumps) whenever I try to transfer to an ipod.

I still think it's a step in the right direction to having an itunes like contender.

What I really want is an app in which I can sort my music, download podcasts and sync them with my device, and apart from amarok there is nothing else close just now. 

George

---

### Post by Hairy_Palms on 2008-08-28
i see youve only got 4 albums imported into each app, maybe banshee scales less well than rhythmbox using more memory for a larger library, whereas RB stays the same.

---

### Post by MaX on 2008-08-28
What I want is a media library that handles all my music/movies/tv-series/music videos/audio books/movie clips
Then we could have different interfaces thowards that library. The library would handle the folder watching and tagging stuff in correct labels, the interfaces just queries the library for audio etc...

The play queue (that I actually found now) is not as accessible in Banshee as in Rhythmbox though, and it still crashes randomly

---

### Post by boombox1387 on 2008-08-28
And if I'm not mistaken, in Rhythmbox you can add the Play Queue to the sidebar so you can simply drag songs to the side, which is a handy feature that I don't think Banshee has.

The more I use both players, the more I realize that neither one does exactly what I want but a combination of the two would be perfect.  While I wait for both to improve, I'll keep using my iPod as my music player and booting up Windows every now and then to sync it with iTunes. :(

---

### Post by BwackNinja on 2008-08-28
@MaX

Basically you're talking about MPD, only with support for videos. MPD is by far my favorite music player. Sonata, mpc, and ncmpc are great to have with it too.

---

### Post by frup on 2008-08-29
I like rhythmbox and don't understand why some people hate it so much.

---

### Post by Manosdoc on 2008-09-12
Banshee 1.3 is out!:)

---

### Post by boombox1387 on 2008-09-12
According to the features list ([http://download.banshee-project.org/banshee/banshee-1-1.3.0.news]("http://download.banshee-project.org/banshee/banshee-1-1.3.0.news")), it looks like Banshee can now do Library Rescanning: "Banshee can now detect newly added, removed, and relocated files and update its collection."  Sounds like drag and drop with Nautilus should work now too.  Those are some BIG pluses.  Can't wait until I get home from work so I can test it out.

---

### Post by gnomeuser on 2008-09-12
> **boombox1387 said:**
> According to the features list ([http://download.banshee-project.org/banshee/banshee-1-1.3.0.news]("http://download.banshee-project.org/banshee/banshee-1-1.3.0.news")), it looks like Banshee can now do Library Rescanning: "Banshee can now detect newly added, removed, and relocated files and update its collection."  Sounds like drag and drop with Nautilus should work now too.  Those are some BIG pluses.  Can't wait until I get home from work so I can test it out.

I compiled SVN on my Fedora x86_64 box earlier.. man is it sweet, they have taken the first steps to get the incremental portable player syncing working again (the best feature in the pre 1.0 Banshee) and it's being polished up a whole lot with new fancy functionality. 

It's rocking and the development pace is absolutely fantastic.

---

### Post by Anubis on 2008-09-12
For Banshee started to stall above 5000 mp3s. Rhythmbox kept on chugging along. RB has no problem finding lyrics or album covers. RB works with my Creative ZEN without me having to use Gnomad2. I like Banshee, but I wish it'd get stable, and do what RB does before we talk about replacements.:popcorn:

---

### Post by boombox1387 on 2008-09-13
Hmm... I'm having a hard time getting Banshee 1.3 up and running on Hardy.  Running ./configure seems to work up until the point where it tells me this:

```
No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found

```

I know I have gstreamer 0.10 installed, but Banshee can't find any packages with that name.  I'd really like to give 1.3 a shot, so if anyone has any pointers, let me know.  Sorry if this is too far off topic.

---

### Post by gnomeuser on 2008-09-13
> **boombox1387 said:**
> Hmm... I'm having a hard time getting Banshee 1.3 up and running on Hardy.  Running ./configure seems to work up until the point where it tells me this:

```
No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found

```

I know I have gstreamer 0.10 installed, but Banshee can't find any packages with that name.  I'd really like to give 1.3 a shot, so if anyone has any pointers, let me know.  Sorry if this is too far off topic.

You'll need the development packages, I believe debian/ubuntu system append -dev to their name. Then it should chug along nicely. You might also be able to find packages in the banshee PPA but I haven't checked, however they are normally on top of things.

---

### Post by mattduckman on 2008-09-13
> **boombox1387 said:**
> I know I have gstreamer 0.10 installed, but Banshee can't find any packages with that name.  I'd really like to give 1.3 a shot, so if anyone has any pointers, let me know.  Sorry if this is too far off topic.

finding all the packages you need can be a real bitch.
```
sudo apt-get build-dep banshee
```
will get you everything you need, quick and easy

---

### Post by olskar on 2008-09-13
You will need ipod-sharp from the SVN according to the banshee IRC-channel, it's on their webpage. However I didn't manage to compile it..

---

### Post by Hairy_Palms on 2008-09-13
i tried compiling the 1.3.0 tarball and the svn, both fail with an error about GConfSchemaExtractor

---

### Post by gnomeuser on 2008-09-13
> **olskar said:**
> You will need ipod-sharp from the SVN according to the banshee IRC-channel, it's on their webpage. However I didn't manage to compile it..

You just need 0.8.1 which was released along side banshee 1.3.0

---

### Post by zekopeko on 2008-09-13
when was 1.3.0 released?

---

### Post by boombox1387 on 2008-09-13
> **zekopeko said:**
> when was 1.3.0 released?
September 11, but it isn't a public update.  I think it's just a developer release in the path toward 1.4.  You can read about it and build it from source here [http://download.banshee-project.org/banshee/]("http://download.banshee-project.org/banshee/").

Thanks for all the help with building it.  I skipped ipod-sharp for now.  I can probably live without my ipod until 1.4 comes out.  Or I'll try to get ipod-sharp working if I find some free time.

---

### Post by Hairy_Palms on 2008-09-13
when i try to compile 1.3.0 it configures fine, then gives me this message under make

> mike@Mikes-Desktop:~/Desktop/banshee-1-1.3.0$ make
make  all-recursive
make[1]: Entering directory `/home/mike/Desktop/banshee-1-1.3.0'
Making all in build
make[2]: Entering directory `/home/mike/Desktop/banshee-1-1.3.0/build'
Making all in pkg-config
make[3]: Entering directory `/home/mike/Desktop/banshee-1-1.3.0/build/pkg-config'
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-core.pc.in > banshee-1-core.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-hyena-gui.pc.in > banshee-1-hyena-gui.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-hyena.pc.in > banshee-1-hyena.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-lastfm-gui.pc.in > banshee-1-lastfm-gui.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-lastfm.pc.in > banshee-1-lastfm.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-mono-media.pc.in > banshee-1-mono-media.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-musicbrainz.pc.in > banshee-1-musicbrainz.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-services.pc.in > banshee-1-services.pc
sed "s,\@VERSION\@,1.3.0,g; s,\@prefix\@,/usr,g; s,\@libdir\@,/usr/lib,g" < banshee-1-thickclient.pc.in > banshee-1-thickclient.pc
make[3]: Leaving directory `/home/mike/Desktop/banshee-1-1.3.0/build/pkg-config'
Making all in m4
make[3]: Entering directory `/home/mike/Desktop/banshee-1-1.3.0/build/m4'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mike/Desktop/banshee-1-1.3.0/build/m4'
make[3]: Entering directory `/home/mike/Desktop/banshee-1-1.3.0/build'
no -out:gconf-schema-extractor.exe GConfSchemaExtractor.cs
/bin/bash: no: command not found
make[3]: *** [gconf-schema-extractor.exe] Error 127
make[3]: Leaving directory `/home/mike/Desktop/banshee-1-1.3.0/build'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mike/Desktop/banshee-1-1.3.0/build'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Desktop/banshee-1-1.3.0'
make: *** [all] Error 2
mike@Mikes-Desktop:~/Desktop/banshee-1-1.3.0$ 

anyone got any ideas?

---

### Post by mattduckman on 2008-09-13
> **Hairy_Palms said:**
> when i try to compile 1.3.0 it configures fine, then gives me this message under make


anyone got any ideas?

if you're building from SVN, you have to run autogen.sh instead of configure. i don't know if that's the case for the 1.3 release or not

---

### Post by Hairy_Palms on 2008-09-13
ive tried the tarball and the SVN, autogen works fine, as does configure on the tarball, but its make that then fails

---

### Post by olskar on 2008-09-13
Love new Banshee, and I love the fast pace of the development!

---

### Post by phenest on 2008-09-13
So, can I assume that Banshee will not replace RhythmBox for II, seeing as the poll shows most have said 'No'.

I tried Banshee. Hmmm. I'm not sure whether I prefer Banshee or Exaile.

---

### Post by MALEADt on 2008-09-13
> **phenest said:**
> So, can I assume that Banshee will not replace RhythmBox for II, seeing as the poll shows most have said 'No'.

I tried Banshee. Hmmm. I'm not sure whether I prefer Banshee or Exaile.

Same feeling in here, Banshee doesn't convince me, although I like the idea of an all-in-one **media**player.
When talking about musicplayers, I'd be happier using Exaile. I'm looking forward to Exaile 3.0 (now with gapless playback), if it will be as good as I hope it might be a good competitor for Rhythmbox in ibex+1.

---

### Post by zolookas on 2008-09-13
Personally there are few things i don't like about bashee ( tested 1.0):
1. Song's seek bar is too short for me (i tend to listen long sets 2hrs+). Rhythmbox has very long one, so i like it better. I know i can open new window with seek bar and then expand, but it is very inconvenient way.
2. Banshee uses more cpu resources compared to Rhythmbox (sometimes about 30% when playing .mp3)

---

### Post by Buffalo Soldier on 2008-09-13
> **frup said:**
> I like rhythmbox and don't understand why some people hate it so much.

same goes here :)

---

### Post by mernen on 2008-09-14
Because of this thread, I tried Banshee for the last two days.

It has some nice features, mostly UI-wise (didn't find any actual feature Rhythmbox lacks I liked), but it's definitely unusable to me.

[LIST]
[*]Poor DAAP support. Wikipedia says I should be able to open my Banshee library from iTunes, but that didn't happen. Banshee is not announcing its own library, and lists both iTunes' and Rhythmbox's, but can't connect to either. Meanwhile, I can play my Rhythmbox songs on iTunes just fine (the other way doesn't seem to work, but I don't personally need it, fortunately).
[*]No directory tracking. Seriously, this alone makes it an absolute no-go to me, and I oppose it becoming the default player without this. Users should be able to throw new files into their Music folder without extra fuss. Worse than that is how you have to manually hunt all files you remove. I have just moved around about four hundred songs into a better directory structure. Rhythmbox handled it fine, and gave me a listing of all missing references (making it easy to remove them all at once). Banshee is now full of dead references.
[/LIST]

---

### Post by phenest on 2008-09-14
The idea that Banshee also plays videos is quite neat (although it can't handle .flv files). But, I'm not sure that's something I require. It's gonna take something real special in Banshee to get me off Exaile.

But I can't help thinking that Banshee does look promising.

And, yeah, the seek bar needs to be way longer.

---

### Post by boombox1387 on 2008-09-14
Which version of Banshee are you using?  1.3 is supposed to do folder watching and handle deleted tracks much better.

---

### Post by phenest on 2008-09-14
> **boombox1387 said:**
> Which version of Banshee are you using?  1.3 is supposed to do folder watching and handle deleted tracks much better.

I'm using 1.2.1 from the repos.

---

### Post by olskar on 2008-09-14
> **phenest said:**
> I'm using 1.2.1 from the repos.

Yea, 1.3 supports folderwatching and daap works for me in that version, bansheedevelopers are the fastest I know :KS

---

### Post by boombox1387 on 2008-09-14
> **olskar said:**
> Yea, 1.3 supports folderwatching and daap works for me in that version, bansheedevelopers are the fastest I know :KS

It's true, the development pace is outrageous.  It'll be interesting to see the results of this poll when it comes up for  Jaunty in a couple months.

---

### Post by Swarms on 2008-09-14
Exactly what I said long time ago in same thread. It is not ready yet, but 1.4 could very well be it!

Kudos to the developers for doing a great job!

---

### Post by phenest on 2008-09-14
I haven't read this entire thread, so I don't know if it's been mentioned already.

Why is there no stop button?

---

### Post by gnomeuser on 2008-09-14
> **Swarms said:**
> Exactly what I said long time ago in same thread. It is not ready yet, but 1.4 could very well be it!

Kudos to the developers for doing a great job!

1.4 is slated for release in a few weeks if I understand the mailing list correctly.

---

### Post by gnomeuser on 2008-09-14
> **phenest said:**
> I haven't read this entire thread, so I don't know if it's been mentioned already.

Why is there no stop button?

What is the use case for a stop button, the pause button does the same thing plus it retains positional data for the file 

I would be honestly interested in the functional difference between the two in actual use.

---

### Post by phenest on 2008-09-14
> **gnomeuser said:**
> What is the use case for a stop button, the pause button does the same thing plus it retains positional data for the file 

I would be honestly interested in the functional difference between the two in actual use.

On my laptop, I have an array of media buttons at the front of the laptop, and Banshee does react to the stop button. Just wondered why it didn't have one on the GUI.

---

### Post by mernen on 2008-09-14
> **gnomeuser said:**
> What is the use case for a stop button, the pause button does the same thing plus it retains positional data for the file 

I would be honestly interested in the functional difference between the two in actual use.

That's exactly the problem. What if I *don't* want to retain positional data? The most common situation arises for me when I want to restart the song from the beginning. On those players without a stop button, you either have to manually move the seeker to the beginning (error-prone, takes more dexterity than it should, plus various issues depending on the player), or you have to double-click the song again (which might not even be on the screen anymore &#8212; if I recall, Banshee does not automatically jump to a song when it starts playing it, making matters worse).

There are also other possible scenarios (listening to a song from a removable media and you want to free it, Internet radio), but these depend on the circumstances and the player.

Removing the stop button from a media player feels to me much like removing the stop button from the web browser, or combining the several quit options (shutdown, restart, sleep, hibernate, lock, logoff, switch user...) into a simple, tiny set: works great in many scenarios, but there are those particular times when you *need* a specific option. :)

---

### Post by BwackNinja on 2008-09-14
depending on how the previous track button works, you may not need a stop button or have to drag the slider. though I think its silly that banshee accepts a stop button but doesn't show one

---

### Post by RAOF on 2008-09-14
> **BwackNinja said:**
> depending on how the previous track button works, you may not need a stop button or have to drag the slider. though I think its silly that banshee accepts a stop button but doesn't show one

I'm fairly sure Banshee treats the keyboard's "stop" button as the same as 'pause'.  I seem to remember writing or reviewing or applying a patch to that effect :).

---

### Post by phenest on 2008-09-15
> **RAOF said:**
> I'm fairly sure Banshee treats the keyboard's "stop" button as the same as 'pause'.  I seem to remember writing or reviewing or applying a patch to that effect :).

Nope. Hitting Pause, keeps the song title, etc, at the top. Pressing Stop, and it disappears, and the slider resets.

These things should be at least optional, regardless of whether some don't want it.

---

### Post by phenest on 2008-09-15
It would be nice to have 'Bitrate' as one of the columns.

I think I'm slowly getting sold on Banshee.

Will they add folder watching? Or have they already?

---

### Post by olskar on 2008-09-15
> **phenest said:**
> It would be nice to have 'Bitrate' as one of the columns.

I think I'm slowly getting sold on Banshee.

Will they add folder watching? Or have they already?

They already have folder watching :)

---

### Post by phenest on 2008-09-15
> **olskar said:**
> They already have folder watching :)

I have version 1.2.1 and it doesn't seem to work. Could I be missing something?

---

### Post by boombox1387 on 2008-09-15
> **phenest said:**
> I have version 1.2.1 and it doesn't seem to work. Could I be missing something?

Banshee 1.3 has it, but it's only available if you build it.  I believe the tar files are at [http://www.banshee-project.org/files/banshee]("http://www.banshee-project.org/files/banshee")

If you're willing to wait, Banshee 1.4 should be coming in a couple weeks.  (I wasn't wiling to wait :)  )

---

### Post by MaX on 2008-09-15
What happened to the Banshee PPA?

---

### Post by boombox1387 on 2008-09-15
> **MaX said:**
> What happened to the Banshee PPA?

I think PPA only offers regular public releases.  As far as I know, 1.3 is only a developer release building up to 1.4.

---

### Post by phenest on 2008-09-18
I'm trying to install version 1.3. It's asking for package gdk-x11-2.0. I can't find it in Synaptics. Can someone help please?

---

### Post by olskar on 2008-09-18
There is no folderwatching in 1.3 :(

---

### Post by boombox1387 on 2008-09-18
> **olskar said:**
> There is no folderwatching in 1.3 :(

Shoot, you seem to be right.  What else would this mean:

>       * Library rescanning - Banshee can now detect newly added, removed,
        and relocated files and update its collection


---

### Post by mc4100 on 2008-09-18
> **olskar said:**
> There is no folderwatching in 1.3 :(
If they say it's there, it probably is, however, this is not a public release -- it's quite possible there is not yet a prefernce for this. You might try gconf-editor just in case...

---

### Post by boombox1387 on 2008-09-20
So I mistakenly let my hopes get the best of me.  When I read about rescanning the music library, I hoped for folder watching, which isn't what "rescanning" is at all.  The option for rescanning in 1.3 is under Tools > Rescan Music Library.  This simply runs through your ~/Music folder (or wherever you've told Banshee that you keep your music files) and adds new files to the Banshee library.  It doesn't happen automatically and it takes a pretty long time.

It's a step in the right direction, though.

---

### Post by MadMan2k on 2008-09-20
> **boombox1387 said:**
> So I mistakenly let my hopes get the best of me.  When I read about rescanning the music library, I hoped for folder watching, which isn't what "rescanning" is at all.  The option for rescanning in 1.3 is under Tools > Rescan Music Library.  This simply runs through your ~/Music folder (or wherever you've told Banshee that you keep your music files) and adds new files to the Banshee library.  It doesn't happen automatically and it takes a pretty long time.
wtf? they added this after their **1.0** release? This was the first feature I added to my own player. And rhythmbox notices files added during runtime.
COme on you cant be serious with replacing it with something that cant get even the basic things right.

---

### Post by mark0978 on 2008-09-30
Why not replace it with listen instead?  It's already in the repositories and it works much better than Rhythmbox.

Rhythmbox has so many problems, it isn't worth the time it takes to TRY to load your media into it.  It only reads part of your files, crashes.  Not worth the time to even look into.

listen just works.  The name sucks, hard to google for, but the player is solid and it is VERY fast at loading all my media.

---

### Post by olskar on 2008-09-30
> **mark0978 said:**
> Why not replace it with listen instead?  It's already in the repositories and it works much better than Rhythmbox.

Rhythmbox has so many problems, it isn't worth the time it takes to TRY to load your media into it.  It only reads part of your files, crashes.  Not worth the time to even look into.

listen just works.  The name sucks, hard to google for, but the player is solid and it is VERY fast at loading all my media.

... and a brand new version with lots of new features is coming soon

---

### Post by mihai.ile on 2008-10-01
I don't get it.. all this work to to the same thing, reinventing the wheel every time.
I know it's open source, freedom and so on but now when I start a new project I really think if I should improve a started one instead of building from zero.
That's why instead of creating my music player with my specific feature I end up helping with rhythmbox plugins...

For me Rhythmbox just works, but banshee is full of unpleasant surprises.

---

### Post by yelo3 on 2008-10-01
Could you list them?

---

### Post by Delvien on 2008-10-01
Rhtthmbox is not very user friendly. +1 for this.

---

### Post by SeanHodges on 2008-10-01
Voted Rhythmbox for default. Works great, very stable, and easy to use.

I use (and prefer) eXaile personally, but as a default Rhythmbox meets the general audience better than most others. Banshee is great, but it has no significant advantages over Rhythmbox as the default player. 

Also, shouldn't the thread be suggesting for inclusion to Jaunty Jackalope? Intrepid is in feature freeze, seems unlikely we could transplant the default music player at this stage! [https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule)

---

### Post by Delvien on 2008-10-01
> **SeanHodges said:**
> 

I use (and prefer) eXaile personally, but as a default Rhythmbox meets the general audience better than most others. Banshee is great, but it has no significant advantages over Rhythmbox as the default player. [/url]


Better library management, better internet radio, better last.fm implementation, cover art that is controllable, equalizer etc. etc.

Rhythmbox is kinda of plain jane in comparison. It's good, but not what I want. I uninstall it every time.

---

### Post by gnomeuser on 2008-10-01
> **Delvien said:**
> Better library management, better internet radio, better last.fm implementation, cover art that is controllable, equalizer etc. etc.

superior podcast support, much nicer iPod (and other portable player) handling at least when 1.4 drops where the sync option will be brought back from the pre 1.0 days. Nicer bling (smooth animations, glittery graphics), a much saner extension model. Also we are getting support for downloading torrent based podcasts which personally I find to be a killer feature. The whole thing is very scriptable and well designed for doing new interfaces or experimenting with new ways of doing things (e.g. you can overload the shuffle function with your own model) - this is also why one Banshee developer was able to implement the Muine interface on top of Banshee in a matter of days during hack week.

This is not even mentioning the additional plugins which are out of tree like the amazing Mirage. 

I don't really understand the library monitoring as being so important, it's not really what I want. I want my files represented in my player, on my fs they should be layed out in a sane consistent manner - all automatically. For this, something like having an indexer feed the database seems like a much better option. For now I am very happy having the manual copy on import.

---

### Post by Swarms on 2008-10-01
1.4 sure looks like its going to be the version for me!

---

### Post by go7Ul1ai on 2008-10-01
I am 1.4

---

### Post by gnomeuser on 2008-10-01
oh and a community developer is porting the Rhythmbox importer to the new codebase so with 1.4 hopefully you should have painfree import of your existing database with all it's rating and such.

---

