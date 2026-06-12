---
title: "Trying to get Linux set up - Having some sound issues."
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2006-07-19
I got Linux running again. I was installing some of the plugins needed and I came to the audio plugin and ran into some trouble.

First of all, when I try to play audio files in Totem I get this error about the MPEG 1 Layer 3 CBR file missing.

When I go into Amarok, the file doesn't play, but I don't get an error. If I hit play, it'll "act" like it's playing for literally 1/3 of a second, then stop as if I actually hit STOP when I didn't.

What's wrong? :(

---

### Post by Qwerty_ on 2006-07-19
I think that you need to install the correct codecs to fix this problem i am experiencing it as well.

---

### Post by Dr. Nick on 2006-07-19
have you installed the mp3 codecs yet? By default ubuntu doesnt support mp3 due to license

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Roasted on 2006-07-19
Nick, help me out here. I've been shown that site before but I don't know what to do. Am I supposed to type each one (copy/paste) individually into the terminal? Should I make it a command like sudo aptitute (insert mp3 codec here) or what?

I'm just unsure of what to do with that information...

---

### Post by Dr. Nick on 2006-07-19
yeah 
```

sudo aptitude install  gstreamer0.10-ffmpeg   gstreamer0.10-pitfdll gstreamer0.10-plugins-bad  gstreamer0.10-plugins-bad-multiverse  gstreamer0.10-plugins-ugly  gstreamer0.10-plugins-ugly-multiverse
```

or just search for each in synaptic and mark them for installation

---

### Post by Roasted on 2006-07-20
Although I'm just going to copy and paste the line you gave me, how would I do the 2nd part? I'm new, if you didn't figure that out. Trying to learn and understand as much as possible, though! How would I get into Synaptic and mark them for installation?

---

### Post by Roasted on 2006-07-20
I just installed that line you posted. Everything went okay, except after doing a sudo aptitude update I got this at the very end.

Reading package lists... Done
W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems
jason@Linux:~$

I did run a sudo apt-get update, and it still said this.

Is this bad? Also, my music doesn't work yet. And like I said, I installed the line you posted above.

---

### Post by TripleE on 2006-07-20
> **Roasted said:**
> Although I'm just going to copy and paste the line you gave me, how would I do the 2nd part? I'm new, if you didn't figure that out. Trying to learn and understand as much as possible, though! How would I get into Synaptic and mark them for installation?

In the "Before You Start" section of the RestrictedFormats site, you need to enable the Universe and Multiverse repositories.  Here is the link ([https://help.ubuntu.com/community/Repositories/Ubuntu)](https://help.ubuntu.com/community/Repositories/Ubuntu)).  Another good source for Ubuntu noobs is [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper).

---

### Post by Dr. Nick on 2006-07-20
that gpg error shouldnt keep them from installing, though on a fresh install I wouldnt expect to see it :confused: what it means is that the packages are not "signed" so they cannot verify if they are coming from the correct source.

If you enabled the universe repo like the before you start section then just go to System - Administration - Synaptic package manager and search them package names and you can then mark them for install then click the "apply changes" button

---

### Post by Roasted on 2006-07-20
I went here.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then, I went to the step where you add the repository and are supposed to hit reload. When I hit reload, I got this error.

W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3

---

### Post by Roasted on 2006-07-20
> **Dr. Nick said:**
> that gpg error shouldnt keep them from installing, though on a fresh install I wouldnt expect to see it :confused: what it means is that the packages are not "signed" so they cannot verify if they are coming from the correct source.

If you enabled the universe repo like the before you start section then just go to System - Administration - Synaptic package manager and search them package names and you can then mark them for install then click the "apply changes" button


What am I searching for? All of these?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Dr. Nick on 2006-07-20
yep, all of them to get most formats to play, though when installing alot the command line is easier,

I hope you get some more help, I have to go as it is lightening like crazy outside and I need to power off my system

Good luck

---

### Post by Roasted on 2006-07-20
Let me get this straight...

It's easier to install from the command line. You gave me the proper command. Yet, I got an error. So if I'm getting an error the easy way, what's to say the harder way will yield a more positive result?

---

### Post by Roasted on 2006-07-20
What's this mean?

jason@Linux:~$ sudo aptitude install  gstreamer0.10-ffmpeg   gstreamer0.10-pitfdll gstreamer0.10-plugins-bad  gstreamer0.10-plugins-bad-multiverse  gstreamer0.10-plugins-ugly  gstreamer0.10-plugins-ugly-multiverse
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jason@Linux:~$

---

### Post by Dr. Nick on 2006-07-20
did you happen to have synaptic open when you ran the last command and got a error? If you did then you need to close it before trying the command again

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

means that it cant run simply because something else is using it at the time

When I menat that command line is easier to install the the synaptic way, i just meant that it is easier to type or copy/paste all that you need to get installed on a singe line as opposed to searching for all the packages in a gui and marking them each seperately for isntallation, The gui can be easier if you are not sure exactly what you are looking for

EDIT

If you would post the termial output of 
[B]
cat /etc/apt/sources.list
[/B]
up here then I could check and make sure everything that is neded is enabled

---

### Post by Roasted on 2006-07-20
jason@Linux:~$ cat /etc/apt/sources.list
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricteddeb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## Dapper PLF
## only uncomment it if you need it
## deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
## deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype (official)
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
jason@Linux:~$

---

### Post by Roasted on 2006-07-20
Okay. I'm raging. Someone, for the love of God tell me why I keep getting this error anytime I try to reload or update something in Synaptic.

W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3

---

### Post by Roasted on 2006-07-20
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Dr. Nick on 2006-07-20
ok, I went to that site and tried to import his authencition key, but was unsuccessfull :( All the packages you are installing should be hosted on one of the other repositories though, so you could disable the cipherfunk.org one by adding a # infront ot the 2 lines. using

sudo gedit /etc/apt/sources.list

then re run apt-get update or hit refresh in synaptic and you shouldnt see it

Having it their should not stop installation though, it wil only mean that the source can not be "validated"

---

### Post by Roasted on 2006-07-21
Why would I want to disable anything? It should work, and should be fine.

---

### Post by Dr. Nick on 2006-07-21
With the gpg error you will still be able to install software from that source, you would just have to live with the error message. I have no trouble getting other gpg imported from other sources to supress the messages, but for some reason couldnt get the one from cipherfunk to work.

I mentioned diabling cipherfunk only because all the packages you are installing I beleive are hosted in other sources you have so the cipherfunk may not be necessary.

---

### Post by Roasted on 2006-07-21
I got XMMS to work just fine. I think it's a little qwirky though. Is the XMMS player supposed to be SMALL as hell and have a little teeny tiny itzy bitzy little button to open the options menu?

But hey, it plays music. Wonder why I can't get that to happen with Totem or Amarok.

---

### Post by Dr. Nick on 2006-07-21
yeah, xmms can be a bit small, It also has a built in mp3 decoder so it will play them "out of the box" I forgot about that.

Just out of curiousity, have you restarted since getting them all installed? I am not sure if that would help or not.

---

### Post by Roasted on 2006-07-21
How can I make XMMS my default player?

Yes. I restarted just now. I was in Windows when I read this post, rebooted, tried again, and nothing helped.

---

### Post by Roasted on 2006-07-21
Also, maybe I'm stupid. But right now the only way I know how to open programs is by hitting ALT F2 then typing the name in. In Windows, you hit start, program files, etc. Does Linux have that? For example, if I wanted to find XMMS without using ALT F2, how would I do it?

---

### Post by Dr. Nick on 2006-07-21
xmms would probably be under this menu Applications -> Sound and Video

to make it your default player just right click a mp3, hit properties then go to open with tab and select xmms.

All that assumes you use gnome (regular ubuntu)

---

### Post by Roasted on 2006-07-21
Hm. I have a music video here. I double click it, Totem opens. I see the video play flawlessly, yet no audio. When I try to play MP3s in Totem that's where I get the MPEG 1 Layer CBR3 error. :(




Also, in XMMS, when I hit MAIN WINDOW, it like... disappears? What can I do to get it back? :confused:

---

### Post by Roasted on 2006-07-21
:confused: :(

---

### Post by Dr. Nick on 2006-07-21
I havent used xmms enough to know why it disapperars, pressing alt+tab may let you get back to it.

As far as totem goes, Videos have a seperate stream for audio and video, It appears like all the video codecs you need are installed, but totem lacks the audio codec that was used in the video , probably a mp3 codec that was used.

---

### Post by Roasted on 2006-07-21
Okay. Soooo what audio codec do I get... That's what I don't get, things just don't be as easy to get installed. Maybe it'll just take time though. ](*,)

---

### Post by Dr. Nick on 2006-07-21
ok, lets try something here.

Open synaptic up and search "gstreamer" 

Make sure totem-gstreamer is installed, along with gstreamer0.10-ffmpeg , gstreamer0.10-fluendo-mp3 , and the gstreamer good/bad/ugly ones are installed aswell. Make sure to mark the .1 vers not .8.

Also have you installed the w32codecs?

---

### Post by Roasted on 2006-07-21
I don't know about the W32codecs. See, this is what bothers me. I've just been trying to find a site that's like "Okay, if you want this this this this and this installed, here's what you do" but I haven't found anything like that. I've just gathered bits and pieces here and there and after 6 days finally am able to listen to music. :( 

How can I install the W32codecs?

Here's what I have.
[IMG]http://i2.photobucket.com/albums/y36/Roasted/dfsdfsd.png[/IMG]

---

### Post by Roasted on 2006-07-21
Okay, a few questions. I got automatix and a lot more is working. Music videos I hear audio + video.

Questions are this.

In Amarok, does Amarok not play videos? I played a music video and I heard audio, but I saw no indication, no window or anything, for the video part of it. No big deal, just curious.

When I try to open the same music video in XMMS, it gives me this screen. When I highlight the music video (Keith Urban on the right side) and hit play, it just disappears and nothing happens. Here's the screen shot.

[IMG]http://http://i2.photobucket.com/albums/y36/Roasted/xmmsscreenie.png[/IMG]

Also, is there anywhere that I can read up on this stuff more? Any books anybody recommends? I find it fascinating how automatix worked however I'd like to learn the hard way as well. I'd also like to learn how autoamtix even works. 

Another thing, when automatix was done, is it normal for it to reset my resolution?

edit - one more question. I never realized this but now I was like oh hey let's see how much hard drive space I'm using. In windows of course start-mycomputer-right click hard drive/properties. Bam, done. How do you do it here? Sorry I asked like 9 questions this time.

---

### Post by Dr. Nick on 2006-07-22
Well Glad you got some of it working, I guess I will start recommending automatix to people in the future, sorry I didnt think of it  for your sake, I used it once along time ago when it was still being worked on and didnt have the greatest success, Looks like it has gotten much better though.

Automatix just uses regular apt-get and synatic to install needed files, It is not uncommon for it to add extra repositories automatically that has the needed packages. I dont know of any books put out specifically for ubuntu and stuff like automatix, It all evolves so fast it would be hard to keep the book updated. Their is probably a few threads scattered in the forums talking about it. Have you glanced at the howto section of forum at all? It can teach you alot.

As far as I know neither amarok or xmms are video players, xmms may have a plugin somewhere to play videos, but not sure. I am 99% sure amarok wont play videos

For videos I would stick with totem, or look in synaptic at mplayer or vlc. All 3 are pretty decent players for video.

Not sure on the resolution issue with automatix, Were you able to get your old res back using System - Prefrences - Screen Resolution?

To see your free disk space go to System - Administarion - System Monitor and look at the devices tab. 

Some of the links in my signature may give you a place to start if you want to learn a few things about how parts of ubuntu work

---

### Post by Roasted on 2006-07-29
Sorry. I been away for a week and just got back. Looking over some things now with the problems I had, it seems like mplayer IS indeed playing videos now in mozilla. Interesting. Before I just had sound. *shrugs*

Well whatever. Only question I have right now is about the player used in mozilla. Am I stuck with just using mplayer on web sites to play videos? This one web site I used to watch videos on in Windows had Windows Media Player embedded in the site. How is this different? Does mplayer just convert it to a linux friendly format to play for me to see? Orrrrr what? Just trying to figure out how it works.

Can I change mplayer? Can I make it so totem is what plays the embedded videos on web sites?

EDIT - 

Cancel that. On another site where I used to use windows media player, I hear just sound. :(

---

### Post by Dr. Nick on 2006-07-30
I forget what all has been covered so far in this thread lol, but if you are getting just sound on a stream meant for windows media player then I would think that the w32codecs are not installed, I am not sure if automatix can install these or not, if you just search google and download the ubuntu .deb. for them then all you have to do is install them by double clicking and maybe typing in your password.

Mplayer works pretty good for all I do, plays the embedded wmp streams fine aslong as they are not made using the newest wmp codec which most arent. Last i knew their was 1 wmp format that w32codecs+mplayer couldnt handle.

you can switch between mplayer/totem/vlc for mozilla firefox by installing/uninstalling the plugins in synaptic. ex mplayer-mozilla etc.

their is also a firefox extension called "media player connectivity"
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
it allows you to launch a external player for embedded video.

I would look into getting w32codecs going, you just click and install the deb, you wont see any new menus,icons etc. all the players that can use them should find them automatically. I imagine the sound is a codec you have while the video isnt which would explain what you say.

I struggled getting streaming working when i did it the first time, it gets easier the more you do it though,

---

### Post by Roasted on 2006-07-30
Uh... err... uh...

sudo apt-get install w32codec

?? :confused: 

This is where I suck. Trying to figure out these commands.

---

### Post by Dr. Nick on 2006-07-30
no, that would be the right command but w32codecs isnt in the repos so you cant do it that way.

search google for w32codecs and their should be a .deb file that you can download, then click on it to install.

w32codecs has some legality issues in some countries so I cant post a direct link for you :(


EDIT

search google for 
"w32codecs" and the first link should have instructions for ubuntu, skip to almost the bottom and thier is a link posted that will tell you where you can always get the codecs, copy/paste the link to the address bar and look at the 2nd file from the bottom in the list, should be about 12-13mb, download that to the desktop then click to install.

You could also add the repository if you wanted like they say, then 

sudo apt-get install w32codecs would work

---

### Post by Roasted on 2006-07-30
Before going further with this, I wanted to ask this. I just downloaded them and double clicked on the icon to extract the files. In bright red letters under STATUS it says "Error: A Later Version Already Installed."

Seems like no matter what I do I can't get the install button to leave the grayed out and unclickable stage. :confused:

---

### Post by Dr. Nick on 2006-07-30
well if you open synaptic and search it for w32codecs does anything show up?

maybe they got installed while you were doing something else.

If thats the case then it may be one of them obscure cases where thier is no support for that file type in linux

---

### Post by Roasted on 2006-07-30
One item is listed. Below, it says the following:




win32 binary codecs
This package contains audio and video codecs for many popular proprietary
formats which are not natively supported by free or open implementations
under GNU/Linux.

The current release contains codecs to support:

 ATI VCR-2 video codec.
 Cinepak video codec
 DivX ;-) video codec, ver. 3.11
 DivX ;-) video codec, ver. 4.x
 Indeo Video 3.2/4.1/5.0/4.1 quick/5.0 quick codecs.
 Intel 263 video codec.
 Microsoft MPEG-4 video codec, beta version 3.0.0.2700
 Morgan Multimedia Motion JPEG video codec.
 QuickTime
 RealAudio
 RealVideo 8
 RealVideo 9
 Windows Media Audio 9
 Windows Media Video 9




Hmm. Let's try something here.

Go here.

[http://video.google.com/videoplay?docid=-2287291950564269771&q=sexy+zombie](http://video.google.com/videoplay?docid=-2287291950564269771&q=sexy+zombie)

I see video, but hear NO audio. What about you?

---

### Post by Dr. Nick on 2006-07-30
I hear audio, but that is a flash video and w32codecs isnt needed for that type.

Thier is a lot of threads here about people not getting audio in flash player, Are you using firefox? Ill see if I can dig up a thread.

EDIT

from termial type

killall esd 

then close and reopen firefox and try again

also look here
[http://www.ubuntuforums.org/showthread.php?t=180702a](http://www.ubuntuforums.org/showthread.php?t=180702a)

EDIT 2

Look at this aswell
[http://ubuntuforums.org/showthread.php?t=204022](http://ubuntuforums.org/showthread.php?t=204022)

---

### Post by Roasted on 2006-07-30
Thanks for the links. Unfortunately I didn't try them. I did some searching myself and found this in one of the threads:



The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
Code:

ln -s /tmp/.esd-1000 /tmp/.esd

to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.



I did just that. The particular video from google that I posted above has audio now. Now I gotta check out everything else and make sure it works, but tomorrow is another day.

---

### Post by Dr. Nick on 2006-07-30
Glad you got it, I think that those same/or similar instructions are posted in my 2nd edit. I followed that thread to fix mine. A quick serach turns up a ton of these threads about flash sound not working. It really seems to come from a variety of sources, no solution fixes them all.


gald you are making progress. I just realized its almost 2am and i have work today lol

Good luck

---

### Post by Roasted on 2006-07-30
I'm still trying to take in and understand what fix I just did. Did that little string of a "hack" that I put in (posted above) basically act as a translator between english and spanish or something?

---

### Post by Dr. Nick on 2006-07-30
I think what it basically did was create a link between 2 places.

flash for linux is not really specific to each distrobution, If you had been using fedora,mandrive,suse or any other distro you would still have the same flash player.

But the way ubuntu organizes its files is slightly different then some others. ESd sounds for esound daemon which is  aprogram in charge of controlling sounds. flash was looking at /tmp/.esd/socket expecting to find what it wanted to play sound, while ubuntu has macromedias desired file located at /tmp/.esd-1000.

the ln command is a link, similar do a windows desktop link. What you did was make a link so that when flash goes looking for the sound is it routed to where ubuntu stores it.

---

### Post by Roasted on 2006-07-30
Ah, I see. Thanks Nick!! :D

---

### Post by Roasted on 2006-07-31
Roasted is having another problem with Flash.

My buddy linked me to this site and I wanted to see the video. 

[http://videos.streetfire.net/video/82CB29BB-CDD0-4B88-B311-37D1A3ADC45B.htm](http://videos.streetfire.net/video/82CB29BB-CDD0-4B88-B311-37D1A3ADC45B.htm)

It says I need Flash 8. When I click the link to download it, it directs me to this section of Adobe to download Flash... but I noticed under "version" it says 7.0.63.0.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Does Linux basically not support Flash 8? Am I out of luck to see this video?

---

### Post by Dr. Nick on 2006-07-31
sorry to say but ive wanted to see vids their aswell.

flash 8 isnt done for linux yet :( not sure of a tenative release date either.

At this point all linux users are out of luck with flash 8 I believe

---

### Post by Roasted on 2006-07-31
k, just wanted to make sure. I figured that was the case, being it said CLICK HERE FOR FLASH 8! I click, and it says 7 under "version". 

Think it'll be a while till Flash 8 is out? Isn't there ANY way 7 can do the job?

---

### Post by Dr. Nick on 2006-07-31
Ive just been reading on it aswell, a local news site decided to remake thier entire page in flash 8 *shakes fists*[-X

I have heard estimates that they will release in early 2007, who knows though some of the stuff you see online may not always be accurate.

Look at microsoft, Vista was origionally scheduled to come out when? lol
:^o

I think the 7 -> 8 is a large improvement and 7 cant really handle any of what 8 can unfortunately

A less then ideal solution would be to use wine and run the windows version of firefox. But that is a huge pain that I dont feel like doing at the moment, Im sure workarounds like this will be more popular in the near future as flash 8 usage increases

---

