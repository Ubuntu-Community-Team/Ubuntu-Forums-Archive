---
title: "Multimedia Works (basically) Out of the Box!"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brucewagner on 2010-04-20
Testing the "final freeze" release candidate of Ubuntu Lucid Lynx LTS 10.04  ....

SO FAR...  to my astonishment...  It seems to play all my media...  "out of the box"....   

By that I mean, by following the default links whenever prompted for "Search for Suitable Plugins?"  ....or....  "Search for Suitable Codecs?"   ....and just clicking Yes... Next... Ok... Yeah... Yes... Ok...

And it works!

Can your 9.10 do that....?    I think not.   :)

Give me some media to test!

YouTube - check
MP3s - check
MP4 movies - check
AVI movies - check
BBC News site videos - check
Adobe Flash Player test side - check
Commercial DVD in Totem Movie Player- check, it works
Commercial DVD in VLC - check, it works Much Better
Commercial DVD ripping using DVDRip - check 
Vimeo.com - check
Ustream.tv - check
Hulu.com - check
Brightcove.com customer properties - check 
NBC.com - "Sorry but we do not support that browser, please use one of these: Windows, Mac"
CBS.com - check
ABC.com - check

What else should I test?

---

### Post by arpanaut on 2010-04-20
G'on, Get outta here!

j/k

---

### Post by UpSignal on 2010-04-20
:o wasn't medibuntu needed for that? at least i added it to my repos

---

### Post by coffeecat on 2010-04-20
I'm curious about....

> **brucewagner said:**
> 
Commercial DVD in Totem Movie Player- check, it works
Commercial DVD in VLC - check, it works Much Better
Commercial DVD ripping using DVDRip - check

... because you'd need libdvdcss2 for encrypted DVDs, which comes from Medibuntu and the medibuntu package server is down atm - as attested by the 3738563¾ threads about Medibuntu liberally scattered about the forum. (Does no one use the forum search? :()

So - did libdvdcss2 come in the box? :?

---

### Post by splicerr on 2010-04-20
> **brucewagner said:**
> Testing the "final freeze" release candidate of Ubuntu Lucid Lynx LTS 10.04  ....

SO FAR...  to my astonishment...  It seems to play all my media...  "out of the box"....   

Commercial DVD in Totem Movie Player- check, it works
Commercial DVD in VLC - check, it works Much Better


Is this with a clean install? I think not. Last time I checked you had to manually run

/usr/share/doc/libdvdread4/install-css.sh

To get the required support for decrypting DVDs installed.

---

### Post by thiebaude on 2010-04-20
espn360.com and try and watch a sport event like soccer or such

---

### Post by brucewagner on 2010-04-20
Guess What!?  ...even .WMV files play fine!

When I look in Synaptic....  I search for w32codecs.....   And it is NOT there.

This is just plain vanilla Ubuntu 10.04  "out of the box"....

The only thing I installed was:

Plain Ubuntu 10.04
When prompted on YouTube to search for available plugins, I did.
When prompted on Movie Player to search for suitable codecs, I did.

The ONLY applications I installed:

-- Dropbox
-- VLC

However, all these played BEFORE installing VLC -- even commercial DVDs played before installing VLC.

The ONLY repositories I have installed are:

-- Canonical Lucid 
-- Dropbox

**Did the Ubuntu Developers / Canonical FIX all our multimedia issues with 10.04....????**

---

### Post by brucewagner on 2010-04-20
> **coffeecat said:**
> So - did libdvdcss2 come in the box? :?

libdvdcss2 seems to be included with Brasero...

So.... YES.... Since Brasero came preinstalled...  

So did libdvdcss2.

---

### Post by brucewagner on 2010-04-20
> **UpSignal said:**
> :o wasn't medibuntu needed for that? at least i added it to my repos

Nope.  I didn't add medibuntu

---

### Post by x-shaney-x on 2010-04-20
Hmm, first embedded (not flash) vid I came to in firefox and it said I need codecs and it installed them.
Haven't tried DVD but I very much doubt it would be playable out of the box on ubuntu.

---

### Post by coffeecat on 2010-04-20
> **brucewagner said:**
> libdvdcss2 seems to be included with Brasero...

So.... YES.... Since Brasero came preinstalled...  

So did libdvdcss2.

libdvdcss2 is not a strict dependency of Brasero. In Synaptic it merely has a "suggests" status. So if you have libdvdcss2 it must have come in the tin, so to speak. Fascinating.

Just to be sure: do you have the file /usr/lib/lbdvdcss2.so.2.1.0?

---

### Post by splicerr on 2010-04-20
> **brucewagner said:**
> 
The ONLY repositories I have installed are:

-- Canonical Lucid 
-- Dropbox

Then your libdvdcss2 package must have come from the "Dropbox" repository. So it's not out off the box. Please stop spreading misinformation here.

---

### Post by brucewagner on 2010-04-20
> **thiebaude said:**
> espn360.com and try and watch a sport event like soccer or such

You can't even get to any videos on that site.  It has nothing to do with multimedia codecs and such...  Only that you don't have a valid PAID ACCOUNT for that web site.

---

### Post by x-shaney-x on 2010-04-20
Out of interest, how did you get the "final freeze" release candidate?

I thought RC wasn't out til 22nd?

---

### Post by mc4man on 2010-04-20
Due to an out of the blue showstopper on my laptop Im just finishing the updates on a fresh install, so will have to see.

Though am 100% sure there is no libdvdcss2 installed or available from ubuntu repo's.

You'd need to run the .sh, I'd be surpried if the codec finder would run it.

(though gstreamer has added some codecs over what was available in karmic

---

### Post by brucewagner on 2010-04-20
In Synaptic, I search for:   libdvdcss2

Nothing.

@splicerr  Why on Earth would it be in the Dropbox repository??   I highly doubt that.

How could I check?

Why don't you guys simply install 10.04 in a VirtualBox and tell me if I'm right or wrong...?

Do a Google search for:  Ubuntu ISO Testing   ....and you can Join and then download it.... for testing.

It's not the actual Release Candidate....  but it's very very close to it.  It's in Final Freeze..... which means only critical bugs can be fixed  (as I understand it.... I am new to all this.)

@coffeecat  See the attached image.

---

### Post by coffeecat on 2010-04-20
> **mc4man said:**
> You'd need to run the .sh, I'd be surpried if the codec finder would run it.

But /usr/share/doc/libdvdread4/install-css.sh simply installs libdvdcss2 from Medibuntu and the packages.medibuntu server is down at the moment. And the three medibuntu mirrors that everyone is posting links for are now redirecting download requests back to the main Medibuntu server.

Which still leaves unanswered the question as to how the OP got libdvdcss2. :?

---

### Post by coffeecat on 2010-04-20
> **brucewagner said:**
> @coffeecat  See the attached image.

I don't see the css library there. Are you sure those commercial DVDs are also **encrypted**? :)

---

### Post by mc4man on 2010-04-20
No go on a fresh, default "out of the box" install

---

### Post by qamelian on 2010-04-20
> **UpSignal said:**
> :o wasn't medibuntu needed for that? at least i added it to my repos

I haven't needed medibuntu to get all my multimedia stuff working for a while now. I think the last time I used their repo was when I was running Hardy.

---

### Post by franc00018 on 2010-04-20
libdvdcss2 in not installed by default and is not in the restricted packages

Here what I get with the restricted packages and other few stuff installed:

francois@francois-kubuntu:~$ ls /usr/lib | grep dvd
libdvdnavmini.so.4
libdvdnavmini.so.4.1.3
libdvdnav.so.4
libdvdnav.so.4.1.3
libdvdread.so.4
libdvdread.so.4.1.3

---

### Post by UpSignal on 2010-04-20
> **qamelian said:**
> I haven't needed medibuntu to get all my multimedia stuff working for a while now. I think the last time I used their repo was when I was running Hardy.

I'll remember that when i get my hands on lucid final version. thanks for the info, it's nice to know i can delete 1 repo :) loads faster

---

### Post by splicerr on 2010-04-20
> **brucewagner said:**
> In Synaptic, I search for:   libdvdcss2

Nothing.

@splicerr  Why on Earth would it be in the Dropbox repository??   I highly doubt that.

How could I check?

Why don't you guys simply install 10.04 in a VirtualBox and tell me if I'm right or wrong...?


Ehh, I have been running 10.04 since alpha, and I repeat there's no libdvdcss2 in the standard Ubuntu repositories. 

Do a:

```

dpkg -l libdvdcss2

ii  libdvdcss2                                    1.2.10-0.3medibuntu1 

```As you can see mine is coming from medibuntu repositories, which is also not out of the box.

---

### Post by brucewagner on 2010-04-20
@mc4man   That is NOT what I got.  I got that it found some codec... and I allowed it be installed.   I think it might have been a gstreamer...something or other...

As for the WMV files...

This from Hacktolive (creator of SuperOS and SuperDebs), in an email to me just now: 

"It seems the ffmpeg group reversed-engineered the format and created an open-source decoder that works in with many .wmv files:  [http://ffmpeg.org/general.html#SEC3](http://ffmpeg.org/general.html#SEC3)   good thing to know!"

---

### Post by brucewagner on 2010-04-20
Just checked as follows...

> bruce@bruce-desktop:~$ dpkg -l libdvdcss2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  libdvdcss2     <none>         (no description available)
bruce@bruce-desktop:~$ 
bruce@bruce-desktop:~$ 

---

### Post by splicerr on 2010-04-20
Can you start totem from a terminal and play a DVD. If the DVD is encrypted you should see something like this in your output.

```

libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to retrieve all CSS keys
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001a0
...

```

EDIT: 

And this is what I get if I rename livdvdcss:

```

libdvdread: Encrypted DVD support unavailable.

```And no video.

---

### Post by mc4man on 2010-04-20
> As for the WMV files...
ffmpeg did wma3(pro quite some time ago, more recently wmas (voice

The gstreamer version in lucid has added wma3(pro, amr, and wmas support to the plugin(s)

The whole libdvdcss2 deal - you got it somewhere, just not from ubuntu

---

### Post by qamelian on 2010-04-20
> **UpSignal said:**
> I'll remember that when i get my hands on lucid final version. thanks for the info, it's nice to know i can delete 1 repo :) loads faster

Yeah, the gstreamer codecs have come a long way, and the only part that isn't immediately obvious is the piece to get DVDs working. A quick search of the docs on Ubuntu.com for 'RestrictedFormats' will help a user sort that quickly though.

---

### Post by flipper9 on 2010-04-20
I bet the DVD you are playing isn't actually encrypted.  Since publishers have to pay royalties to encrypt their DVDs, not all actually use CSS encryption.  It's useless anyways.

---

### Post by seenthelite on 2010-04-20
I currently have 4 installs of 10.04, 2 kubuntu and 2 ubuntu, in 3 of these I have installed all the normal multimedia stuff, restricted extras, sudo /usr/share/doc/libdvdread4/install-css.sh, libdvdcss2, w32 or w64 codecs etc; and the repositories. These 3 play all the media OK. The other install I have not as yet installed the multimedia stuff and it does not play DVDs or You Tube or anything requiring flash, yes I get the search for suitable plugins popup but the search is not successful, "no packages with the suitable plugins found."  I'm curious to know why your system is different.

---

### Post by brucewagner on 2010-04-21
Ok, peeps.   It is possible that this DVD I was using to test is not encrypted.  It is a sampler DVD with various scenes from HereTV... so it's given away, not sold.  Maybe that's why.

Can you believe I don't think we OWN a commercial DVD... I'll try to find one somewhere.

Meanwhile....

> **seenthelite said:**
> ... I have not as yet installed the multimedia stuff and it does not play DVDs or You Tube or anything requiring flash, yes I get the search for suitable plugins popup but the search is not successful, "no packages with the suitable plugins found."  I'm curious to know why your system is different.

I got the same thing, "no suitable plugins found" or some such...

BUT... I clicked the resulting link that said, "Click here to search manually..."    THAT took me to the dialogs that allowed me to add a new "Ubuntu Partners" repository or something... and the Adobe web site where it asked me to select my verion of Ubuntu... THEN, youtube etc worked fine.

HOWEVER, strangely, no other repositories show up in my Software Sources (see attached images).

As an aside:  Do you think there going to be any differences in installing that "*Multimedia and Video Comprehensive How To*" guide.... for Lucid...?

---

### Post by seenthelite on 2010-04-21
I think the answer is [here]("http://en.wikipedia.org/wiki/Ubuntu-restricted-extras") and most people also use the Medibuntu repository and install 64 bit Flash if needed.

---

### Post by bshosey on 2010-04-21
ubuntu 7.10 was the last ubuntu version I had to use medibuntu repos

Now I don't remember what version I had to use totem-xine to get DVD to work right.

---

