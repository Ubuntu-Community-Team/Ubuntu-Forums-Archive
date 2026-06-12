---
title: "Ubuntu 9.10 Alpha 3"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by marsdend on 2009-07-21
Hi all,

Can anyone tell me what we can expect to see in the Alpha 3 of Ubuntu 9.10

Thanks,
Dan

---

### Post by calrogman on 2009-07-21
Whatever is frozen now will remain the same until the final release.

What is not frozen now will continue to change, apart from that, those of us who don't subscribe to mailing lists don't know much.

Try looking around the wiki.

---

### Post by MaxIBoy on 2009-07-21
I'm currently running Karmic.

[LIST=1]
[*]Sound sucks. VLC seems to stutter and squeak a lot. (Gnome Mplayer works, but seriously, who uses that?) In games that use openAL, sound will routinely stop working after a few minutes until you restart that game, and even when it does work, sounds get cut off before they should and some sounds get dropped altogether.
[*]The new GDM screen can only be customized by entering in some console commands (or by fumbling around in gconftool's menus.) ```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename "/name/of/background/file"
``` ```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/gtk_theme "theme which must be in /usr/share/themes for some reason" 
``` But since I just told you the code, I doubt you'll have a problem with it.
[*]Besides those two hiccups, everything is AWESOME! I even got fglrx working with a 2.6.31-rc3 kernel!
[/LIST]

---

### Post by marsdend on 2009-07-21
Thanks, can i expect to see any big changes when its finally released. I was quite disapointed when i found out they were not going to be updating the desktop with a new look.

Dan

---

### Post by MaxIBoy on 2009-07-21
...Because it's so freakin' difficult to change the theme...

---

### Post by Stan_1936 on 2009-07-21
> **MaxIBoy said:**
> ...Because it's so freakin' difficult to change the theme...

Well said.  The annoying posts, about a brown default theme that can be changed in LESS than 1 MINUTE, by half the people on here is just really pathetic.

Let't face it, Windows XP wasn't tbhe best looking OS ever but it still made it to the top of the pile.

The VLC thing sounds more serious though.

---

### Post by stwschool on 2009-07-21
Obviously a lot of upstream work will appear including the newer kernel which I'm told has the realtime patch baked in. This should be good news for musicians among others. Presumably the latest firefox and OO will appear too as you'd expect. Every release is a subtle improvement of the last. I think this one's primarily going to be an under-the-hood release.

---

### Post by bodhi.zazen on 2009-07-21
Moved to development (from the cafe).

If you want accurate information use these forums and the various mailing lists. If you need assistance with the mailing lists, wiki, or launchpad just ask.

The cafe is not really the best source of accurate information.

---

### Post by Sub101 on 2009-07-21
Grub 2 should work with systems with more than one OS. 

For me that is an important change.

---

### Post by froggyswamp on 2009-07-21
> **Stan_1936 said:**
> Well said.  The annoying posts, about a brown default theme that can be changed in LESS than 1 MINUTE, by half the people on here is just really pathetic.

Let't face it, Windows XP wasn't tbhe best looking OS ever but it still made it to the top of the pile.

You don't give credit where credit is due, defaults matter, even Canonical recognized it and is considering moving away from brown AND adding a few NICE wallpapers (finally).
Also, in my experience, when I decided to load a **beautiful** theme from the internet (Gnome's site) - more than a half (actually almost ALL) of those themes  were broken or didn't look/work as expected, that sux.

---

### Post by HappyFeet on 2009-07-21
> **marsdend said:**
> Thanks, can i expect to see any big changes when its finally released. I was quite disapointed when i found out they were not going to be updating the desktop with a new look.

Dan

They *are* going to be changing the default theme from what I've heard. Plus, they are changing the start up screen to something that will be very nice looking and glitch free.

---

### Post by ELD on 2009-07-21
We haven't even had the first artwork drop yet so who knows.

August 27th - [Feature Freeze]("https://wiki.ubuntu.com/FeatureFreeze") & [Artwork First Drop]("https://wiki.ubuntu.com/ArtworkFirstDrop")

Bear that date in mind ladies and gents.

---

### Post by bodhi.zazen on 2009-07-21
> **ELD said:**
> We haven't even had the first artwork drop yet so who knows.

August 27th - [Feature Freeze]("https://wiki.ubuntu.com/FeatureFreeze") & [Artwork First Drop]("https://wiki.ubuntu.com/ArtworkFirstDrop")

Bear that date in mind ladies and gents.

There are , however, proposals on the wiki ;)

---

### Post by ELD on 2009-07-21
Exactly my point, just proposals, no one knows what will realllyy happen until it does :P

---

### Post by andrewabc on 2009-07-21
> **marsdend said:**
> Hi all,

Can anyone tell me what we can expect to see in the Alpha 3 of Ubuntu 9.10

Thanks,
Dan

Hopefully the first 'stable' alpha, for me at least (where I plan on doing testing). I downloaded a daily image couple weeks ago and it wouldn't run, but alpha2 did fine.

Dunno what your exact question is. Alpha 3 compared to alpha2? GDM is probably biggest difference.

Lots of tech improvements over jaunty.

There better not be any VLC issues with karmic! I am using PPA of vlc 1.0 and it is working very good (best I've ever seen it) on jaunty.

---

### Post by andrew.46 on 2009-07-21
Hi andrewabc,

> **andrewabc said:**
> There better not be any VLC issues with karmic! I am using PPA of vlc 1.0 and it is working very good (best I've ever seen it) on jaunty.

I will admit that I was a little puzzled at that previous comment about vlc. I am running vlc with the bleeding edge Karmic and I have not seen any problems at all. You may already know that as a bonus Karmic is shipping with vlc 1.0.0 straight from the repository?

All the best,

Andrew

---

### Post by Slug71 on 2009-07-21
Alpha 3 will be out in a couple of days.

---

### Post by inportb on 2009-07-21
About the VLC comments -- the audio pretty spotty at best; while it works on some machines, on others (like my laptop) it stutters. I've taken to using Kaffeine or Dragon because they just work.

---

### Post by pw_f100_220 on 2009-07-21
> **MaxIBoy said:**
> I'm currently running Karmic.

[LIST=1]
[*]Sound sucks. VLC seems to stutter and squeak a lot. (Gnome Mplayer works, but seriously, who uses that?) 

I USE MPLAYER!!!!  but i see you're point.

---

### Post by Macchia on 2009-07-21
i expect pulseaudio will be just an option, if i dont want it, i must be able to remove it and switch to alsa/esd whatever i like/need.

---

### Post by Kareeser on 2009-07-21
I experience the VLC audio stuttering as well. A bit of a deal-breaker, as now I have to use Totem (*shudder*) when I want to watch something.

I've already [submitted a bug report for it](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/402018), though nothing has happened yet.

---

### Post by alphacrucis2 on 2009-07-21
VLC 1.0 mostly works ok for me on both Jaunty & Karmic. Under Jaunty, I do notice that VLC has some sort of performance problem when desktop effects are enabled with ati's fglrx driver, whereas Totem is fine. Of course I can't test this on karmic until a version of fglrx is available that works with Karmic's kernel.

---

### Post by Regenweald on 2009-07-21
> **Kareeser said:**
> I experience the VLC audio stuttering as well. A bit of a deal-breaker, as now I have to use Totem (*shudder*) when I want to watch something.

I've already [submitted a bug report for it]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/402018"), though nothing has happened yet.

I was experiencing crackling and whatnot also. I did ```
 sudo rm rf .pulse 
``` then log out/in which gave me back decent audio. My problem is now very low volume at maximum output, so i'm patiently waiting for some pulse updates :)

---

### Post by psyke83 on 2009-07-21
> **Regenweald said:**
> I was experiencing crackling and whatnot also. I did ```
 sudo rm rf .pulse 
``` then log out/in which gave me back decent audio. My problem is now very low volume at maximum output, so i'm patiently waiting for some pulse updates :)

Be careful with that command! You need to be in the home directory for that command to work, and a mistype coud cause all your files to be deleted.

You should have written:
```
$ rm -r ~/.pulse
```

---

### Post by bodhi.zazen on 2009-07-21
-i ftw :twisted:

rm -ri $HOME/.pulse

That way you will get confirmation , it is only when we get lazy and we do not wish to review what we are doing that we use -rf , in which case we suffer from our typos :-

---

### Post by Regenweald on 2009-07-21
> **psyke83 said:**
> Be careful with that command! You need to be in the home directory for that command to work, and a mistype coud cause all your files to be deleted.

You should have written:
```
$ rm -r ~/.pulse
```

> **bodhi.zazen said:**
> -i ftw :twisted:

rm -ri $HOME/.pulse

That way you will get confirmation , it is only when we get lazy and we do not wish to review what we are doing that we use -rf , in which case we suffer from our typos :-

Indeed, you are both right and apologies on my carelessness
I suppose i'm comfortable since i know that by default commands are executed in /Home and I'm cool once there are no infamous '/' in the command :) the thought DID cross my mind when i executed it last week :) What a horrible way to loose root!

Thanks :)

---

### Post by alphacrucis2 on 2009-07-21
> **bodhi.zazen said:**
> -i ftw :twisted:

rm -ri $HOME/.pulse

That way you will get confirmation , it is only when we get lazy and we do not wish to review what we are doing that we use -rf , in which case we suffer from our typos :-

Reminds me of the old joke. 

> Confucius say: "Man who play in root, eventually kill tree". :)

---

### Post by bodhi.zazen on 2009-07-22
That is an awesome quote :)

---

### Post by ranch hand on 2009-07-22
> 
 Originally Posted by Stan_1936
Well said. The annoying posts, about a brown default theme that can be changed in LESS than 1 MINUTE, by half the people on here is just really pathetic.

Let't face it, Windows XP wasn't tbhe best looking OS ever but it still made it to the top of the pile.


> **froggyswamp said:**
> You don't give credit where credit is due, defaults matter, even Canonical recognized it and is considering moving away from brown AND adding a few NICE wallpapers (finally).
Also, in my experience, when I decided to load a **beautiful** theme from the internet (Gnome's site) - more than a half (actually almost ALL) of those themes  were broken or didn't look/work as expected, that sux.

I am 100% with Stan_1936 on this.  There are millions of images on the web.  Gimp is on by default.  In 30 minutes you can have several wallpapers.

My hope is that the people whining about this are folks that have never installed a MS OS on a computer.  You spend hours, after a long install, to get everything to have drivers.

In the time difference between installing Ubuntu and Winwhatever, you can find images and learn to get them to fit your box the way you want them in Gimp.  I am speaking of people that are participating in testing and this forum, if you can update apt and upgrade your OS in xterm on boot you can change your wallpaper pretty much in your sleep.

I really am a ranch hand.  We are not noted for real fancy.  In the last year (almost) that I have used Ubuntu (all MS before that - back to MSDos) I have collected or made a collection of about 80 wallpapers.  This is not something that is hard or I could not do it.  It is not time consuming or I wouldn't do it.  It is fun.

Try it, it beats whining.

HAVE FUN

---

### Post by Marat89 on 2009-07-22
> **alphacrucis2 said:**
> VLC 1.0 mostly works ok for me on both Jaunty & Karmic. Under Jaunty, I do notice that VLC has some sort of performance problem when desktop effects are enabled with ati's fglrx driver, whereas Totem is fine. Of course I can't test this on karmic until a version of fglrx is available that works with Karmic's kernel.

I heard fglrx is now available in Karmic.
Just try.

---

### Post by ronacc on 2009-07-22
and if they are too lazy to resize their own wallpapers , check out gnome-look.org and kde-look.org . There are literaly 100 s of wallpapers there , many in several sizes , also themes and iconsets enough to satisfy any tase .

---

### Post by QwUo173Hy on 2009-07-22
With respect, I think what people are asking for is beyond 'just' a wallpaper. They want a cohesive look that spans bootup, login and desktop. I visit [www.gnome-look.org](www.gnome-look.org) regularly and the vast majority of the content there is either incomplete or not practical for long term usage. And that's being kind - there is in fact a lot of garbage there too.

The Human theme is an excellent example of a cohesive look. The icons, including those used in menus, dialogs and buttons etc. are clear, attractive and communicative. The colours blend well and text is always legible.

I think people are looking for this level of quality to be repeated. And there's nothing wrong with people asking for this surely? Just as there's nothing wrong with the release team deciding whether or not it's a priority.

---

### Post by Regenweald on 2009-07-23
Alpha 3 in a few hours, wonder what it will bring....

---

### Post by scheuri on 2009-07-23
> **Regenweald said:**
> Alpha 3 in a few hours, wonder what it will bring....

Surely nothing new if you have updated regularly...:)

---

### Post by Craigy90 on 2009-07-23
<snip>

No official announcement yet. :popcorn:

---

### Post by GeorgeVita on 2009-07-23
EDITed to a question:


[B]Where is the mirror for Europe/Greece for alpha versions?
[/B]
Thanks in advance,
George

---

### Post by 23meg on 2009-07-23
> **Craigy90 said:**
> 
No official announcement yet. :popcorn:

Which means it's not out.

Please don't download images you may see on the server before the release announcement; they're likely to be incomplete, and downloading prematurely may slow down the syncing of the mirrors.

---

### Post by andrewabc on 2009-07-23
Yep cdimage has alpha 3 listings. But wait until release announcement to make sure you have correct version. No point in taking chance of downloading non alpha 3 version. And the mirrors should be faster download anyways.

Someone will make a thread pointing to the release announcement etc once it is released.

---

### Post by Craigy90 on 2009-07-23
Ah, sorry about that.

---

### Post by xens on 2009-07-23
its out :)

---

### Post by infamousrev on 2009-07-23
[http://www.ubuntu.com/testing/karmic/alpha3](http://www.ubuntu.com/testing/karmic/alpha3)
**Sorry, the page you are looking for was not found**

---

### Post by andrewabc on 2009-07-23
> **xens said:**
> its out :)

Provide a link to the announcement if you think it is out...

---

### Post by ranch hand on 2009-07-23
<snip>

---

### Post by Hairy_Palms on 2009-07-23
> Gnome Mplayer works, but seriously, who uses that?
been my main video player since intrepid :p

---

### Post by andrewabc on 2009-07-23
> **ranch hand said:**
> <snip>

That is not announcement and may not be final version (but it probably is).
Wait until announcement to be sure.

Did anyone read the thread and what 23meg said?

---

### Post by Craigy90 on 2009-07-23
It's like, deja vu all over again. What have I wrought through my ignorance? #-o](*,):-#:twisted:\\:D/:cry::redface:

---

### Post by taavikko on 2009-07-23
Just a reminder folks, no need to install the alpha3 over previous releases to have the latest release. Unless you're testing the installer.

If you've been upgrading regulary, you'll already have the latest what the repos have to offer.

Alpha releases are just a "current snapshot" of the state of repositories.

---

### Post by Nickedynick on 2009-07-23
What are the main bugs (I assume there are some remaining) with 9.10 at the moment? I read about VLC and media issues on this thread, but was wondering what else is broken.

I'm thinking of upgrading on my desktop from 9.04 to check out new features, etc. but want to make sure I'd still be able to use it first.

<snip>

---

### Post by infamousrev on 2009-07-23
> **taavikko said:**
> Just a reminder folks, no need to install the alpha3 over previous releases to have the latest release. Unless you're testing the installer.

If you've been upgrading regulary, you'll already have the latest what the repos have to offer.

Alpha releases are just a "current snapshot" of the state of repositories.


My experience is that reinstalling every release works better then doing apt-get dist-upgrade.

For some reason some updates will not work without reinstalling.


> What are the main bugs (I assume there are some remaining) with 9.10 at the moment? I read about VLC and media issues on this thread, but was wondering what else is broken.

I'm thinking of upgrading on my desktop from 9.04 to check out new features, etc. but want to make sure I'd still be able to use it first.

You could try installing the newest realease in virtualbox, that was you can try it, but you wont risk wrecking your computer.

---

### Post by 23meg on 2009-07-23
Please wait until the release announcement, which will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce").

---

### Post by Nickedynick on 2009-07-23
> **infamousrev said:**
> You could try installing the newest realease in virtualbox, that was you can try it, but you wont risk wrecking your computer.

I would ordinarily, but I'm waiting for my laptop to be repaired atm and my desktop is 6 years old and can't really handle a Virtualbox install.

---

### Post by andrewabc on 2009-07-23
> **23meg said:**
> Please wait until the release announcement, which will be posted to the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce").

done
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000594.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000594.html)

Maybe you can create new 'alpha 3 released' thread and sticky it for a while?

---

### Post by keplerspeed on 2009-07-23
Excellent. I havnt played with Karmic since alpha 1, so im looking forward to giving it a try.

---

### Post by PRGUY85 on 2009-07-23
Downloading now.  Didn't know it had ubuntu one built in.

---

### Post by ranch hand on 2009-07-23
> **taavikko said:**
> Just a reminder folks, no need to install the alpha3 over previous releases to have the latest release. Unless you're testing the installer.

If you've been upgrading regulary, you'll already have the latest what the repos have to offer.

Alpha releases are just a "current snapshot" of the state of repositories.
This is the theory that I believed.  I am not too sure now.

The 32bit karmic that I have started as A1 that I update daily.  It still uses grub .97.  Has never been offered grub2.

I have 2 A2-64bit, one on 2 partitions and the other on 1.  They get slightly different updates some days (I can't figure that one out at all).  I have gone back to the one I did first to check to see if it has new stuff (in 15 minutes or so) and it has not.

Well, I better split and do some work before it gets too hot to breath.

---

### Post by GeorgeVita on 2009-07-23
> **keplerspeed said:**
> Get it here [http://cdimage.ubuntu.com/releases/karmic/alpha-3/](http://cdimage.ubuntu.com/releases/karmic/alpha-3/) (Ubuntu)
...and it is the same with the 'snipped':
> **Craigy90 said:**
> <snip>

No official announcement yet. :popcorn:
and it is 6 hours closer to me!

[IMG]http://acomelectronics.com/GeorgeVita/kk_a3.jpg[/IMG]

Regards,
George

P.S.: please excuse me for the .jpg, but sometimes is painful to get a 'testing' iso.

---

### Post by psyke83 on 2009-07-23
> **GeorgeVita said:**
> and it is the same with the 'snipped':

and it is 6 hours closer to me!

[IMG]http://acomelectronics.com/GeorgeVita/kk_a3.jpg[/IMG]

Regards,
George

P.S.: please excuse me for the .jpg, but sometimes is painful to get a 'testing' iso.

If there is no release announcement, they don't want everybody downloading the .iso - regardless of whether it exists in the proper place. The mirrors need time to seed the image (although it seems the release announcement for alpha 3 is out).

You could download with Bittorrent (may be faster, and will ease the load on the HTTP servers).

---

### Post by GeorgeVita on 2009-07-23
> **psyke83 said:**
> If there is no release announcement, they don't want everybody downloading the .iso - regardless of whether it exists in the proper place. The mirrors need time to seed the image.

You could download with Bittorrent (and ease the load on the HTTP servers).

Please let me know, I am trying to get it just to test it. I did not want to 'load' anybody. If you feel that my 20KB/s is a 'load' somewhere I must stop immediately the download. I just followed the instructions that where to the page: [http://cdimage.ubuntu.com/releases/karmic/alpha-3/](http://cdimage.ubuntu.com/releases/karmic/alpha-3/)

George

---

### Post by descendent87 on 2009-07-23
so much for "dual booting will be fixed by alpha 3" still doesn't find any of my other installs (arch and feroda 11)

---

### Post by tjeremiah on 2009-07-23
wait wait wait. So if I have been updating every day since Alpha 1 to 2, all I have to do is update again via manager and ill be bump to Alpha 3? This thread is confusing me, sorry. Also, how and where do I check to see what version im under and all the other version numbers?

---

### Post by infamousrev on 2009-07-23
Just booted into alpha 3. but its pretty slow,

It was supposed to give a performance boost for intel graphics right?

---

### Post by descendent87 on 2009-07-23
I'm using the radeon driver and getting pretty sluggish performance, moving windows around is really slow

---

### Post by taavikko on 2009-07-23
> **ranch hand said:**
> This is the theory that I believed.  I am not too sure now.

The 32bit karmic that I have started as A1 that I update daily.  It still uses grub .97.  Has never been offered grub2.

I have 2 A2-64bit, one on 2 partitions and the other on 1.  They get slightly different updates some days (I can't figure that one out at all).  I have gone back to the one I did first to check to see if it has new stuff (in 15 minutes or so) and it has not.

Well, I better split and do some work before it gets too hot to breath.

Please read the release notes: [https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview](https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview)
where it clearly states, that upgrades from jaunty will be using grub(0.97) and new install after alpha2 are using grub2

---

### Post by xebian on 2009-07-23
> **Regenweald said:**
> Indeed, you are both right and apologies on my carelessness
I suppose i'm comfortable since i know that [COLOR="Red"]**by default commands are executed in /Home **[/COLOR]and I'm cool once there are no infamous '/' in the command :) the thought DID cross my mind when i executed it last week :) What a horrible way to loose root!

Thanks :)

You are wrong again. Very.

---

### Post by Craigy90 on 2009-07-23
> **descendent87 said:**
> so much for "dual booting will be fixed by alpha 3" still doesn't find any of my other installs (arch and feroda 11)

It says here
[http://www.ubuntu.com/testing/karmic/alpha3#Known%20issues](http://www.ubuntu.com/testing/karmic/alpha3#Known%20issues)
that installing alongside windows, it may not show up. Look at the threads on grub2 for how to set up multi-boot.

> **tjeremiah said:**
> wait wait wait. So if I have been updating every day since Alpha 1 to 2, all I have to do is update again via manager and ill be bump to Alpha 3? This thread is confusing me, sorry. Also, how and where do I check to see what version im under and all the other version numbers?

I don't think there is a number for the alpha you are running, it is simply a matter of whether you have the latest updates.

---

### Post by descendent87 on 2009-07-23
I've read all the threads on grub2 and nothing has worked, just have to manually add the entries for arch and fedora in which is a pain

---

### Post by andrewabc on 2009-07-23
> **tjeremiah said:**
> wait wait wait. So if I have been updating every day since Alpha 1 to 2, all I have to do is update again via manager and ill be bump to Alpha 3? This thread is confusing me, sorry. Also, how and where do I check to see what version im under and all the other version numbers?

If you are up to date (via update manager or whatever) you have latest version. No need to download alpha 3 images. You would be running 'alpha 3' (aka karmic with latest updates).

---

### Post by jocko on 2009-07-23
> **tjeremiah said:**
> wait wait wait. So if I have been updating every day since Alpha 1 to 2, all I have to do is update again via manager and ill be bump to Alpha 3? This thread is confusing me, sorry. Also, how and where do I check to see what version im under and all the other version numbers?

Alpha 3 is just a snapshot of the development, there is no version number or anything like that. If you installed from an alpha 1 cd and installed the updates as they came, you were in fact testing the developing alpha 2 until alpha 2 was released, at which point you started to test the developing alpha 3 and so on. As alpha 3 was made from the packages that were in the repo before alpha 3 was released, you probably already had alpha 3 yesterday.

If you continue to keep the same installation updated until the final release of 9.10, you will have the final version without having to download the final cd or doing any huge update. The final version will be made from the packages that are produced during the development.

---

### Post by Regenweald on 2009-07-23
> **xebian said:**
> You are wrong again. Very.

Rather than a poor attempt at being elitist, why not correct me so that others may benefit. You are wasting space otherwise.

---

### Post by tjeremiah on 2009-07-23
Thanks guys for clearing that up :)

---

### Post by Sub101 on 2009-07-23
> **descendent87 said:**
> I've read all the threads on grub2 and nothing has worked, just have to manually add the entries for arch and fedora in which is a pain

I dual boot with Vista (rarely use it but like knowing its there). For me the Vista option did not appear in Grub2 when booting for the first 3 times. After that however, it appeared as it did with Grub1.

 I know its an unusual fix, and no doubt impractical, but may be useful to other users.

---

### Post by Coolaaron88 on 2009-07-25
Well it took three hours but I finally have the karmic koala installed on my machine. And I wish I could do more with it but as others have addressed it is VERY slow and I bet there is no quick fix for it. I guess I will have to wait for something to remedy this.

---

### Post by andrew.46 on 2009-07-25
Hi Coolaaron,

> **Coolaaron88 said:**
> Well it took three hours but I finally have the karmic koala installed on my machine. And I wish I could do more with it but as others have addressed it is VERY slow and I bet there is no quick fix for it.

I am running Karmic in a VM and on this reasonably limiting setting it is in fact *very* fast.

>  I guess I will have to wait for something to remedy this.

Or even better investigate why it is so slow on your system and file a carefully considered bug-report.

Andrew

---

### Post by Coolaaron88 on 2009-07-25
Hi Andrew

I wanted to know wether you installed koala as an I upgrade from jaunty or as a fresh intall. Thank you.

---

### Post by andrew.46 on 2009-07-25
Hi Coolaaron,

> **Coolaaron88 said:**
> I wanted to know wether you installed koala as an I upgrade from jaunty or as a fresh intall.

My installation is a fresh install of Alpha 2 with subsequent updates and upgrades.

Andrew

---

### Post by Coolaaron88 on 2009-07-25
I would love to see what the problem could possibly be but the os is so slow I can't even really move around through windows. Have any recommendations.

---

### Post by Gina on 2009-07-25
Check what applications are running (eg. look in System Monitor).  Is anything running the CPU 100%? - this is something we've had before.  Or is anything using all your RAM and spilling over into Swap?  On the same point, is your system finding all the RAM? - a memory module could have become unseated.

I guess it's possible that something went wrong when installing - you could try re-installing.

I'm running Alpha 3 and it's very fast - Ubuntu seems to be getting faster all the time.  But for Karmic, I can only report on the 64 bit version running on my AMD64 X2 machine - that is the only machine I'm testing on ATM.

---

### Post by Coolaaron88 on 2009-07-25
Well Gina here is the thing. I ended up booting up into Windows7 and unistalling ubuntu. I burned karmic koala onto a cd and did an install of karmic which went well until the attempted boot up of ubuntu which was stopped by the error no wubildr. After that error my computer reboots and starts up to the boot screen where the same thing happens again so I have that issues at the moment. I also run a 64 bit machine too with AMD as well. I really wanna get it running. Thanks for your input.

---

### Post by Digital Hick on 2009-07-25
**Karmic Alpha 3 Experience**

Downloaded LiveCCD and tried on my laptop.  System loads, the kernel is there, but I have no GUI at all.  It says GDM is working but I don't see how.  Jaunty was the first one that worked with my laptop.  Given that hardware is being migrated away from HAL I guess we are in the breakage stage and some things have regressed.  

Tried that LiveCD on my desktop.  Got a GUI but it is still somewhat broken.  Will not properly align with screen.  What I could do from there left me with the following thoughts:

>>>I spent three weeks configuring Jaunty's Release version to iron out most of the bugs in it.  I am not doing that with an Alpha of Karmic.  Will wait till Alpha 4 before I try to use it.

>>>Still no significant work on improving the theme.  Shuttleworth wanted to do something for 9.10 but said getting a team together was hard.  Apparently VERY hard.  Balanzan is what I am using on 9.04, they should start with that and work from there.  I made some changes to that and have a nice looking desktop now.  If you are going to do a brown/orange theme, do it with a touch of style.

>>>Stuff is moving around, I guess it will be good.  One thing nice about Ubuntu is that through 11 releases things have not moved that much.  Not compared to Windows anyway.  The shutdown options have moved, had to hunt for them.  They subdivided the games menu, good.  They should do the same to the System>Preferences and System>Administration menus.

>>>I have a feeling this is going to be a rough release, not because of the state of Alpha 3, but just given what is going on.  The transition to GNOME 3, EXT 4, GRUB 2, Boot Screen Stuff, fixing Pulse Audio, moving away from HAL, and the never ending battle with Xorg.  

I skipped 8.10, I hope I don't have to skip 9.10.  

Then there is the fact that the next LTS may be delayed given Canonical is trying to sync with what other projects are doing.  9.10 seems like it is going to be a transition release with lots of potential breakage.  This may be our Vista.:shock::shock:

Are they still going to put the Android socket in Karmic so we can run Android apps or has that been cancelled?

---

### Post by andrewabc on 2009-07-25
Why didn't firefox 3.5 become default for alpha 3?
What are they waiting for?

---

### Post by 23meg on 2009-07-25
> **andrewabc said:**
> Why didn't firefox 3.5 become default for alpha 3?
What are they waiting for?

The tasks listed [here]("https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition") to be completed. The more people help, the quicker it will happen.

---

### Post by bodhi.zazen on 2009-07-25
Thank you [23meg]("http://ubuntuforums.org/member.php?u=11472") for such a clear and concise answer.

andrewabc: as suggested, getting involved with the Ubuntu community tends to be more productive then posting on the forms asking when it will happen.

If you need assistance getting to know the greater community (LP, wiki, MOTU, etc) we would be happy to direct you.

---

### Post by 23meg on 2009-07-25
> **bodhi.zazen said:**
> Thank you [23meg]("http://ubuntuforums.org/member.php?u=11472") for such a clear and concise answer.

You're welcome; the question comes up pretty often and I (as well as the Ubuntu Mozilla team) would appreciate it if people spread this bit of information in other places (outside the forums) where it comes up as well.

---

### Post by dicairo on 2009-07-25
hi everyone , i tested it with live cd for a couple of hours and it seems good and  my intel card work well i can say that all the hardware work good , the  control center is a good idea **_and finally we have the bug work flow_** now u dont have to login to the lanuchpad to report a bug and a normal usrer (newppy) can report a bug in seconds.

 I hope that they creat an application to configure the new login screen and i dont know why they the delet the shutdown . restart comand fro the user switcher ??? but i dont care about this because i use gnome do.
so at the the i didnt have problems with karmic :P

---

### Post by jerrylamos on 2009-07-25
> **dicairo said:**
>  I hope that they creat an application to configure the new login screen and i dont know why they the delet the shutdown . restart comand fro the user switcher ??? but i dont care about this because i use gnome do. :P

Do Ctrl-Alt-Del which will give you the shutdown & restart options.

Jerry

---

### Post by ranch hand on 2009-07-25
Or ad "Shut Down" to your panel.

---

### Post by JOHNNYG713 on 2009-07-25
I run 9.10 alpha on one of my test machines, And all (as far as the normal operations)was the same, to the average user there would be no difference, Just upgraded code and such, (For the teckie a treat ), Until the last update, Now, the login window manager is gone, The standard type login window, That you can change[FONT=Arial] in the login window manager,  Is gone, and replaced with a small glassy looking black box, like a small themed gdm, with the users name, click the name and it animates to the password, enter the password and it animates away, tThe back ground is a default standard background[/FONT], And at this time I find no way of customizing it, I have heard that they are going to do away with usplash and gdm, And opt for a program called "plymouth", That puts the usplash and GDM into one program, Fedora uses this, As it is still alpha, There are more updates on the way, I am told that "plymouth" is totaly customizable, But I have yet to see the GUI. Other than that 9.10 appears to be unchanged at this point, Except for internal things. :)

---

### Post by buzzmandt on 2009-07-25
and also shut down options in the system menu

---

### Post by Nburnes on 2009-07-25
Been using it for a couple days and can say that it definitely is faster on boot up and shut down as well as the over all system, and my ATI X1250 graphics compatibility with Compiz has improved, as it does not have lines that appear when using the Cube.

Cannot wait till the final release :P

---

### Post by Gina on 2009-07-26
I'm running Karmic and finding little to grumble about now.  I agree the restart and shutdown are a little less convenient but as things are still in a state of flux I haven't felt it worth mentioning - rarely restart anyway.

It's certainly getting faster :)  And now my nvidia graphics card (GeForce 9400 GT)runs perfectly out of the box - no need to install the proprietry driver any more :)

I have no new bugs to report.

---

### Post by andrewabc on 2009-07-26
> **dicairo said:**
> 
 I hope that they creat an application to configure the new login screen and i dont know why they the delet the shutdown . restart comand fro the user switcher ???

I agree. With past two versions they put shutdown/restart/standby etc etc at far top right corner in user switcher. Now when testing alpha 3, I keep clicking on top right corner expecting to shutdown from there, but no option there. I did find the option under system menu.

Why was this moved/removed? Is it going to stay like this? I thought having the options where they were for 8.10 and 9.04 were good.

---

### Post by aamukahvi on 2009-07-26
> **andrewabc said:**
> Why was this moved/removed? Is it going to stay like this? I thought having the options where they were for 8.10 and 9.04 were good.

The user switcher is not yet compatible with the new gdm. The options should make a return.

---

### Post by leandromartinez98 on 2009-07-26
I've booted Karmic on a Asus eeePc 1008HA and on a Vaio NR11Z/S from a USB-stick. My first impresions are really good:

1 - Both machines have intel graphic cards. Now they work, very well indeed. The system is extremely responsive and compiz works with OpenGL applications for the first time due to UXA and DRI2. This is a great improvement, really. 

2 - Boot was faster than my Jaunty hard-drive instalation.

3 - They incorporated the Sound control redhat developed for Fedora 11, where volume can be set independently for each running application. Looks good and I hope will help me to fix my Skype sound problems. 

4 - OpenOffice 3.1 has antialising, so everything looks nicer. With the graphic card working, it is a great improvement (I had it installed on Jaunty, but with the flacky intel graphic performance the new graphic features ran bad).

---

### Post by dicairo on 2009-07-26
> **jerrylamos said:**
> Do Ctrl-Alt-Del which will give you the shutdown & restart options.

Jerry

> **ranch hand said:**
> Or ad "Shut Down" to your panel.

> **buzzmandt said:**
> and also shut down options in the system menu

thanks for all your replay and i know all that i was just saying that itsn't convenient
to remove the shutdown command from the user switcher that is it. :)

---

### Post by xx58 on 2009-07-27
:rolleyes:Be happy what you have. Karmic is just amazing. You can click on right mouse button and put SHUT DOWN the COMPUTER button where you want, customize....

---

### Post by andrewabc on 2009-07-27
So now that my computer illiterate parents have learned that shutdown is top right corner, they are now expected to look elsewhere? They don't know how to add shutdown to panel. Now I'm gonna have to explain to them and several others that it has moved to system. I don't want to have to customize yet another item after install for users.

No one has explained if the change is permanent (why is logout at top right corner but not shutdown etc like before), or any reason for doing so.

Yes us people posting at forum can easily deal with it, but computer illiterate people will have more difficult time finding out why stuff is being moved around. "Where'd it go!? Why?" 

What are the benefits of doing so? In 8.10 it had shutdown at top right and in system menu. Then in 9.04 they got rid of shutdown in system menu. Now in 9.10 they are getting rid of shutdown in top right corner and only having system menu? Stop moving stuff around! I think it was best when it was in system menu and top right corner. That way no one complained where it was at, because it was available in two locations.

---

### Post by Gina on 2009-07-27
Andrew - Don't take me wrong but why are computer illiterate people using a developmental system?  Al least give them a stable version like 9.04 - aka Jaunty.  This may well be a temporary thing like so much in development.

---

### Post by andrewabc on 2009-07-27
> **Gina said:**
> Andrew - Don't take me wrong but why are computer illiterate people using a developmental system?  Al least give them a stable version like 9.04 - aka Jaunty.  This may well be a temporary thing like so much in development.

No, I'm saying when 9.10 is released and I install it they will wonder why shutdown menu is moved. They are using 9.04 now.

And I have had them using 9.04 dev as wireless worked, and 8.10 would not boot at all (8.04 too old this spring). So yes there is a good reason to have them using dev version when normal version does not work.

---

### Post by taavikko on 2009-07-27
> **andrewabc said:**
> 
No one has explained if the change is permanent (why is logout at top right corner but not shutdown etc like before), or any reason for doing so.


AFAIK the fast-user-applet isn't yet compatible with new gdm.
When it get's sorted out, it will be brought back...

---

### Post by Copernicus1234 on 2009-07-27
> **Stan_1936 said:**
> Let't face it, Windows XP wasn't tbhe best looking OS ever but it still made it to the top of the pile.


Windows XP was a huge graphical improvement over Windows 2000 and Windows 98. Its looks was probably why most people started using it over older versions.

Gnome can be made to look pretty so its idiotic of Shuttleworth to not focus on it. I guess he likes throwing his money away.

---

### Post by ranch hand on 2009-07-27
> **Copernicus1234 said:**
> Windows XP was a huge graphical improvement over Windows 2000 and Windows 98. Its looks was probably why most people started using it over older versions.

Gnome can be made to look pretty so its idiotic of Shuttleworth to not focus on it. I guess he likes throwing his money away.
We have no idea what 9.10 is going to look like at this point.  At least not according to the release schedule in the wiki.  FIRST artdrop just after the release of A4 and only after that will they start to work that in.

They may be thinking that since they have several new paths to the art, it might be a good idea to make that stuff (like GDM) work before screwing with this.

---

