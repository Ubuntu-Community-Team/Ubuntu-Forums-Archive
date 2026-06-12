---
title: "Thanks to chromium-daily, now in Lucid"
date: 2009-11-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-11-15
Just want to thank the chromium browser team for making the chromium daily ppa available so early in the Lucid testing cycle, also a heads up for chromium users/testers :P
```

sudo add-apt-repository ppa:chromium-daily

```

---

### Post by Gina on 2009-11-15
Ah, great :) :)  I'll set up my rsync script to grab the daily updates tomorrow :)

I'll be testing as soon as I've got my boot problem sorted out.

---

### Post by VMC on 2009-11-15
Great news. The version I'm currently running is "4.0.237.0". I can finally get to one of my financials with my latest update. They have progressed nicely.

Good tip thanks!

edit: I just updated, its "249"

---

### Post by Regenweald on 2009-11-16
Although, the 'get more extensions' link refers me to the google search page. Which I think is hilarious :P. Should I give the developers an infraction ? :P

---

### Post by baizon on 2009-11-16
I can't get my Chromium through the Peacekeeper test. It hangs up on the Social networking # 2/6 test. 
I've tried that solution but it doesn't work.
[http://code.google.com/p/chromium/issues/detail?id=13184]("http://code.google.com/p/chromium/issues/detail?id=13184")

---

### Post by gnomeuser on 2009-11-16
I wonder when we will be able to start branching off Chromium for some more stable releases (more akin to Chrome), I could imagine getting tired of daily git snapshots at some point.... oh who am I kidding, bring it on!

---

### Post by castrojo on 2009-11-16
When upstream has a "beta" and "release" branch available (when they release) we'll be able to have that.

---

### Post by emigrant on 2009-11-16
i still wait for chromium untill it is able to support WYSIWYG.

---

### Post by Merk42 on 2009-11-16
> **emigrant said:**
> i still wait for chromium untill it is able to support WYSIWYG.

I'm not sure what you mean.
That term usually deals with graphical editors of some sort.

---

### Post by emigrant on 2009-11-16
i mean, using chromium, not supports WYSIWYG for text editors. for example in this forum. :(
i.e. you can't see what formattings you do in the text editor, until you hit the submit button.
i hope i used the term correctly???

---

### Post by joey-elijah on 2009-11-16
It works okay for me?

---

### Post by MacUntu on 2009-11-16
I'm paranoid. Has there been some kind of code review to make sure there are no bits of spying in Chromium?

---

### Post by maheshasolkar on 2009-11-16
4.0.248.0 build also has bookmark sync (Via Google Docs). You can enable this feature by passing '--enable-sync' to the command line. Google account required.

---

### Post by Starks on 2009-11-16
WYSIWYG has nothing to do with Chromium. All you have to do is spoof your useragent to Firefox or something and it will work. Blame the forum software for not supporting Chrome or Chromium useragents.

---

### Post by Tompalaz on 2009-11-16
I might have missed something essential but:
```
tomas@Mac:~$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  chromium-browser: Depends: chromium-codecs-ffmpeg but it is not installable or
                             chromium-codecs-ffmpeg-nonfree but it is not installable
E: Broken packages
tomas@Mac:~$ 

```
> Package chromium-codecs-ffmpeg-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package chromium-codecs-ffmpeg-nonfree has no installation candidate


---

### Post by joey-elijah on 2009-11-16
> **MacUntu said:**
> I'm paranoid. Has there been some kind of code review to make sure there are no bits of spying in Chromium?

The whole "spying" in Google Chrome is vastly exaggerated and hyped beyond all sanity. If you're that scared of cookies or history items don't use the web!

---

### Post by emigrant on 2009-11-16
@Starks,
You mean its wrong with the forum Sw? I thnk i even cant copy paste an image in gmail composing on chromium. That means gmail themselvs hav nt added chromium useragent?

---

### Post by Starks on 2009-11-16
Perhaps. There's a similar issue with Firefox 3.6/3.7 using the Namaroka/Minefield useragent. Maybe Chromium's is too new.

Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/532.5 (KHTML, like Gecko) Chrome/4.0.249.0 Safari/532.5

Also, in order to properly pull the ffmpeg codecs, you need to use the karmic repo for chromium-daily with the lucid one or just use the karmic one for now.

---

### Post by Regenweald on 2009-11-16
> **Tompalaz said:**
> I might have missed something essential but:
```
tomas@Mac:~$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  chromium-browser: Depends: chromium-codecs-ffmpeg but it is not installable or
                             chromium-codecs-ffmpeg-nonfree but it is not installable
E: Broken packages
tomas@Mac:~$ 

```

Have you added the ppa ? the ffmpeg package is also there. Try aptitude.

---

### Post by VMC on 2009-11-16
> **maheshasolkar said:**
> 4.0.248.0 build also has bookmark sync (Via Google Docs). You can enable this feature by passing '--enable-sync' to the command line. Google account required.

I noticed that "Sync my bookmarks" was grayed out. Now I know why. thanks for that tip.

BTW - We are now at "4.0.250.0 (Ubuntu build 32056)", with recent updates.

---

### Post by ktp on 2009-11-18
> **emigrant said:**
> @Starks,
You mean its wrong with the forum Sw? I thnk i even cant copy paste an image in gmail composing on chromium. That means gmail themselvs hav nt added chromium useragent?

maybe you are hitting this issue:

[http://crbug.com/27966](http://crbug.com/27966)

Seems like clearing cache seems to fix the issue for me.

---

### Post by SalvoMaltese on 2009-11-20
> **Tompalaz said:**
> I might have missed something essential but:
```
tomas@Mac:~$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  chromium-browser: Depends: chromium-codecs-ffmpeg but it is not installable or
                             chromium-codecs-ffmpeg-nonfree but it is not installable
E: Broken packages
tomas@Mac:~$ 

```

Me too, same situation, kubuntu lucid.

---

### Post by MacUntu on 2009-11-20
Change your sources from lucid to karmic.

---

### Post by SalvoMaltese on 2009-11-21
> **MacUntu said:**
> Change your sources from lucid to karmic.

Now it works, but still no java.

Frash install of lucid, chromium no java, after that tried FF 3.7, no java, FF 3.5 java ok.

Anyone experienced/solved that?

---

### Post by renkinjutsu on 2009-11-21
> **baizon said:**
> I can't get my Chromium through the Peacekeeper test. It hangs up on the Social networking # 2/6 test. 
I've tried that solution but it doesn't work.
[http://code.google.com/p/chromium/issues/detail?id=13184]("http://code.google.com/p/chromium/issues/detail?id=13184")

Are you using 64bit? i'm having that problem too, when it didn't exist in 32bit

oh, and Java just plain doesn't function in both chromium and Firefox =], applets load, and close immediately

---

### Post by ubulette on 2009-12-30
> **gnomeuser said:**
> I wonder when we will be able to start branching off Chromium for some more stable releases (more akin to Chrome), I could imagine getting tired of daily git snapshots at some point.... oh who am I kidding, bring it on!

We now have both the [Beta Channel]("https://launchpad.net/~chromium-daily/+archive/beta") and the [Dev Channel]("https://launchpad.net/~chromium-daily/+archive/dev") in PPAs. They are perfectly aligned with the official builds so updates should pop up the same day, providing there's no build error and enough builder resources.

The daily PPA is still there.

As of today, daily: 4.0.286.0, dev: 4.0.266.0, beta: 4.0.249.30
(266 branched off Dec 6; 249 Nov 15)

---

### Post by Jordanwb on 2009-12-31
I added the chromium PPA, "apt-get install chromium" and I got a game. :confused:

*Edit* I forgot to "apt-get update" so when I ran "aptitude search chromium" it didn't get listed. *facepalm*

---

### Post by Regenweald on 2009-12-31
> **Jordanwb said:**
> I added the chromium PPA, "apt-get install chromium" and I got a game. :confused:

*Edit* I forgot to "apt-get update" so when I ran "aptitude search chromium" it didn't get listed. *facepalm*

remember that the package name is chromium-browser :)

---

### Post by jppr on 2010-01-26
chromium-browser in repos soon... [https://launchpad.net/ubuntu/lucid/+source/chromium-browser/4.0.305.0~svn20100123r36929-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/chromium-browser/4.0.305.0~svn20100123r36929-0ubuntu1)

---

### Post by jppr on 2010-01-28
Chromium now repos, just install it and works fine

---

### Post by SKLP on 2010-02-06
> **jppr said:**
> Chromium now repos, just install it and works fine
Seems to be based on daily and not beta channel ( like the beta ppa mentioed above), which seems a bit odd as beta should be more stable

---

