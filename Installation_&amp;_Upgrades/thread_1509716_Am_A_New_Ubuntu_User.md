---
title: "Am A New Ubuntu User"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by bwedjong on 2010-06-14
i just started using Ubuntu, but after installation i realized that i cld not open media files and i cld not also install my USB wireless Internet modem on it. all .exe files failed to install. please help me with ideas.

---

### Post by peccish on 2010-06-14
If you search for the make and model of your wireless modem you should find some information for it on the forums.


To set up a new installation of ubuntu so it will read your media files, I recommend following these instructions [http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.04-lucid-lynx).

And just give up trying to run exe files for now that's windows.

---

### Post by bwedjong on 2010-06-14
tanx 4 th assistance. now i download media softwares and application for Ubuntu but i cant install them. i have just downloaded VLC for ubunti from softpedia but i cant install it. pls help will be so much appreciated.

---

### Post by steveneddy on 2010-06-14
:|

OK - look at the links in my sig.

Click on the first link:

[Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Lucid"):Lucid

There you will find all of the answers you are looking for.

For instance - to play multimedia files look here:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Restricted_Extras](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Restricted_Extras)

The command is simply - in terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

and to install VLC you merely - in terminal again:

```
sudo apt-get install vlc vlc-plugin-pulse
```

Just open up a terminal by going to

Applications --> Accessories --> Terminal

and copy and paste the commands I just gave you into the terminal.

Easy peasy.

Good luck - we're all counting on you.

---

### Post by howefield on 2010-06-14
> **bwedjong said:**
> tanx 4 th assistance. now i download media softwares and application for Ubuntu but i cant install them. i have just downloaded VLC for ubunti from softpedia but i cant install it. pls help will be so much appreciated.

You'll find VLC in the Ubuntu repositories already, so you don't have to download it from elsewhere.

Go to the Applications > Ubuntu Software Centre menu, and from the window that pops up scroll down and click on Sound & Video, then in the search field type VLC.

Highlight VLC and press the install button.

It should be pretty rare that you need to get software from outside the official repository.

Have a read at this page

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by howefield on 2010-06-14
> **steveneddy said:**
> :|

Yes, precisely.

Hmmm.

---

### Post by amauk on 2010-06-14
In general, you do not download and install software from the the web
Ubuntu (and many other linux distributions) have central software stores that you should use

Click on Applications > Ubuntu Software Centre
and install what you want from there

---

### Post by steveneddy on 2010-06-14
> **howefield said:**
> Yes, precisely.

Hmmm.

there are detailed instructions up there for performing the tasks you need to do.

I posted the emoticon prematurely - sorry.

Simply follow the instruction I gave you and you will be as good as gold.

And read the Ubuntu Guide link there for Lucid - there is LOTS of great information there for you to read.

---

### Post by howefield on 2010-06-14
> **steveneddy said:**
> there are detailed instructions up there for performing the tasks you need to do.

Simply follow the instruction I gave you and you will be as good as gold.

And read the Ubuntu Guide link there for Lucid - there is LOTS of great information there for you to read.

No need to tell me that.

You seem to be in a bit of a tizz.... have a cup of tea.

---

### Post by steveneddy on 2010-06-14
> **howefield said:**
> No need to tell me that.

You seem to be in a bit of a tizz.... have a cup of tea.

**I wasn't telling you** - I was merely letting the OP know there was more info up there in case he bypassed it.

Either solution should work for the OP - your with the Software Center and mine the old fashioned way with the terminal.

---

### Post by minhajmsm on 2010-06-14
I usually download " .deb " files.. so it can be installed like any other software like in windows.... 2days ago Ive downloaded VLC n installed it the same way.... and more... for " .exe " the windows file format, use "wine" Ive Photoshop CS3, Acrobat reader, & Delta force - Black hawk down .... and many more installed and they function almost the same as in windows.... & you can try - "CrossOver games" or "CrossOver Software" also..


Quote :
""Most of them have problems which Ive faced but no one's ever faced problems which Ive faced"" so don't get fed up when you aint getting the expected answer.... Feel Free --- Feel UBUNTU.... 

"{Another Age Must be The Judge}-Charles Babbage"

---

### Post by steveneddy on 2010-06-15
> **minhajmsm said:**
> I usually download " .deb " files.. so it can be installed like any other software like in windows.... 2days ago Ive downloaded VLC n installed it the same way.... and more... for " .exe " the windows file format, use "wine" Ive Photoshop CS3, Acrobat reader, & Delta force - Black hawk down .... and many more installed and they function almost the same as in windows.... & you can try - "CrossOver games" or "CrossOver Software" also..




IMHO this is poor advice for current version available in the repos. Maybe you should read the links in my sig, too. If a user is installing everything with a .deb file then the soft will not update with the automatic updates. This is the reason for installing through the repos.

I would not use .exe in wine unless you can't find an alternative for the software you need in Linux.

Ask here on the forums and we will tell you what applications substitute for commonly used Windows applications.

---

### Post by howefield on 2010-06-15
> **minhajmsm said:**
> .. for " .exe " the windows file format, use "wine" Ive Photoshop CS3, Acrobat reader, & Delta force - Black hawk down .... 

Acrobat Reader is available in the partner repository, maybe you have a reason for using the Windows version, maybe you are unaware.

Using Wine is usually best as a last resort, and for supported applications can be very good, but why use Linux in the first place to run a shed load of windows applications, most times you will find an alternative that works well.

[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
[http://www.osalt.com/](http://www.osalt.com/)

---

### Post by minhajmsm on 2010-06-16
> **steveneddy said:**
> IMHO this is poor advice for current version available in the repos. Maybe you should read the links in my sig, too. If a user is installing everything with a .deb file then the soft will not update with the automatic updates. This is the reason for installing through the repos.

I would not use .exe in wine unless you can't find an alternative for the software you need in Linux.

Ask here on the forums and we will tell you what applications substitute for commonly used Windows applications.


yes steveneddy .... your a prof in these and im just an beginner and i do appreciate your reply and I will read your Sig, Thanks a lot .... and how should i take this IMHO...????>>>  [http://www.acronymfinder.com/Slang/IMHO.html](http://www.acronymfinder.com/Slang/IMHO.html) ....lol ... :KS

---

### Post by minhajmsm on 2010-06-16
> **howefield said:**
> Acrobat Reader is available in the partner repository, maybe you have a reason for using the Windows version, maybe you are unaware.

Using Wine is usually best as a last resort, and for supported applications can be very good, but why use Linux in the first place to run a shed load of windows applications, most times you will find an alternative that works well.

[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
[http://www.osalt.com/](http://www.osalt.com/)

Thanks for the info howefield,,,, Ive just new the linuxappfinder but wasn't aware of other 2 sites... and i use wine for my sis needs photoshop...nothin else..](*,)..  & acro n games Ive just tried.... 

Neways ... thanks a lot for your info.... My dad always says ---->> BETTER LISTEN TO EXPERTS N LEARN..>>> keep on rocking well follow on....:guitar:

---

### Post by steveneddy on 2010-06-17
> **minhajmsm said:**
> yes steveneddy .... your a prof in these and im just an beginner and i do appreciate your reply and I will read your Sig, Thanks a lot .... and how should i take this IMHO...????>>>  [http://www.acronymfinder.com/Slang/IMHO.html](http://www.acronymfinder.com/Slang/IMHO.html) ....lol ... :KS

ROFLMAO



AFAIK **IMHO** means **I**n **M**y **H**onest **O**pinion

or

**I**n **M**y **H**umble **O**pinion

It a phrase that has been around the internet since as far back as I can remember. I started using these phrases in the late 80's and early 90's while corresponding with colleagues.

I'm sorry if you don't understand commonly used terms used for communication on the internet. But AFCPS that these little terms keep one from typing so much.

So, AWGTHTGTATA - so please DND because DILLIC?

Now LMA and LLAP

---

### Post by minhajmsm on 2010-06-19
bk 2 schl .. na na.... 1st I betr lrn englsh...thn shrtning .. thn progrmn abbrvtins..... 1/2wy I'll b dead .... bt ..... 

thnx 4d info..... TC ... don't reply 2 this pls ... na na...

---

