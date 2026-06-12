---
title: "Ubuntu 9.04 Beta Released"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wolfen69 on 2009-03-26
Steve Langasek has announced the beta release of Ubuntu 9.04, code name "Jaunty Jackalope": "The Ubuntu team is pleased to announce the beta release of Ubuntu 9.04 desktop and server editions. Ubuntu 9.04 desktop edition brings faster boot speeds and a new notification system to your everyday computing experience. Ubuntu 9.04 server edition makes it easy to experiment with cloud computing using Eucalyptus on your own servers, and sports an improved mail server integration stack based on Postfix and Dovecot. The Ubuntu 9.04 family of variants, Kubuntu, Xubuntu, Ubuntu Studio, and Mythbuntu, also reach beta status today." 

see [www.distrowatch.com](www.distrowatch.com) for download links.

Note: This release should not be used in production machines or when stability is of the utmost priority. Use at your own risk.

---

### Post by dragos240 on 2009-03-26
Yep since 8:30 US EST :)

---

### Post by richg on 2009-03-26
I just downloaded and burned a ISO for 9.04. Install ok but cannot view a commercial DVD movie out of the box. I was told that something was needed. I okd a search and the search came up zero. I suspect htis is not a bug but Ubuntu's way.

I left Ubuntu 8.04 some months ago as it would not play DVDs. I went to Mint 6 and it plays DVDs right out of the box. 

Hopefully Ubuntu will fix this with the final release. Everything else looks ok.

Rich

---

### Post by SunnyRabbiera on 2009-03-26
> **richg said:**
> I just downloaded and burned a ISO for 9.04. Install ok but cannot view a commercial DVD movie out of the box. I was told that something was needed. I okd a search and the search came up zero. I suspect htis is not a bug but Ubuntu's way.

I left Ubuntu 8.04 some months ago as it would not play DVDs. I went to Mint 6 and it plays DVDs right out of the box. 

Hopefully Ubuntu will fix this with the final release. Everything else looks ok.

Rich


Mint comes with libdvdcss, while Ubuntu doesnt because of legal BS.

---

### Post by Mehall on 2009-03-27
> **SunnyRabbiera said:**
> Mint comes with libdvdcss, while Ubuntu doesnt because of legal BS.

from terminal:

"sudo apt-get install ubuntu-restricted-extras"

sorted.

---

### Post by Chayak on 2009-03-27
> **richg said:**
> I just downloaded and burned a ISO for 9.04. Install ok but cannot view a commercial DVD movie out of the box. I was told that something was needed. I okd a search and the search came up zero. I suspect htis is not a bug but Ubuntu's way.

I left Ubuntu 8.04 some months ago as it would not play DVDs. I went to Mint 6 and it plays DVDs right out of the box. 

Hopefully Ubuntu will fix this with the final release. Everything else looks ok.

Rich

Ubuntu can't legally play DVDs out of the box.  Mint is on shaky legal ground by including it.

The fix is simple at the terminal
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SunnyRabbiera on 2009-03-27
> **wolfen69 said:**
> Steve Langasek has announced the beta release of Ubuntu 9.04, code name "Jaunty Jackalope": "The Ubuntu team is pleased to announce the beta release of Ubuntu 9.04 desktop and server editions. Ubuntu 9.04 desktop edition brings faster boot speeds and a new notification system to your everyday computing experience. Ubuntu 9.04 server edition makes it easy to experiment with cloud computing using Eucalyptus on your own servers, and sports an improved mail server integration stack based on Postfix and Dovecot. The Ubuntu 9.04 family of variants, Kubuntu, Xubuntu, Ubuntu Studio, and Mythbuntu, also reach beta status today." 

see [www.distrowatch.com](www.distrowatch.com) for download links.

Note: This release should not be used in production machines or when stability is of the utmost priority. Use at your own risk.

Thats why I use virtualbox :D

---

### Post by FuturePilot on 2009-03-27
> **Mehall said:**
> from terminal:

"sudo apt-get install ubuntu-restricted-extras"

sorted.

> **Chayak said:**
> Ubuntu can't legally play DVDs out of the box.  Mint is on shaky legal ground by including it.

The fix is simple at the terminal
```

sudo apt-get install ubuntu-restricted-extras
```

This won't work for DVD playback being that libdvdcss isn't even in the Ubuntu repos. This is what [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") is for.

---

### Post by pwnst*r on 2009-03-27
^^vlc

---

### Post by TBOL3 on 2009-03-27
back in the old days ~6.06 to 7.04 I had to install all the libraries manually (or apt), but now, I just download VLC, and put in a dvd, and when it tells me I need a codec, I can just click install, and it works.

---

### Post by wolfen69 on 2009-03-27
I'm using it now, (64bit version) and  i have to say i love it. flash finally works good. not great, but good. things in general seem quicker.

i may change to 64bit.

---

### Post by wolfen69 on 2009-03-27
> **richg said:**
> I just downloaded and burned a ISO for 9.04. Install ok but cannot view a commercial DVD movie out of the box. I was told that something was needed. I okd a search and the search came up zero. I suspect htis is not a bug but Ubuntu's way.

I left Ubuntu 8.04 some months ago as it would not play DVDs. I went to Mint 6 and it plays DVDs right out of the box. 

Hopefully Ubuntu will fix this with the final release. Everything else looks ok.

Rich

are you serious? 

wow. maybe i overestimated the general public. i tend to think computers are general knowledge. this is not the case.

---

### Post by lisati on 2009-03-27
> **wolfen69 said:**
> are you serious? 

wow. maybe i overestimated the general public. i tend to think computers is general knowledge. this is not the case.

I think there's still an ethos of mystery surrounding them, even though the technology has moved on from the days when the only computers around were monstrous room-filling beasts with a fraction of the capabilities of today's machines.

---

### Post by wolfen69 on 2009-03-27
> **lisati said:**
> I think there's still an ethos of mystery surrounding them

i guess that's good for the people that are elite.

---

### Post by lisati on 2009-03-27
> **wolfen69 said:**
> i guess that's good for the people that are elite.

I'm by no means the most knowledgable of computer users, but I've still managed to be accused of being a geek. This has even been by people with degrees who sometimes even seem to be unable to read the instructions. (I suspect "unwilling" to read the instructions might be the case sometimes)

---

### Post by itsStephen on 2009-03-27
I'm going to download it tomorrow and install it in vurtualbox

---

### Post by pwnst*r on 2009-03-27
> **wolfen69 said:**
> are you serious? 

wow. maybe i overestimated the general public. i tend to think computers are general knowledge. this is not the case.

???

---

### Post by pt123 on 2009-03-27
softpedia once again has a good coverage with the screenshots
[http://news.softpedia.com/news/Ubuntu-9-04-Beta-Screenshot-Tour-107809.shtml](http://news.softpedia.com/news/Ubuntu-9-04-Beta-Screenshot-Tour-107809.shtml)

I am surprised how beautiful the fonts look 
[http://news.softpedia.com/newsImage/Ubuntu-9-04-Beta-Screenshot-Tour-7.jpg/](http://news.softpedia.com/newsImage/Ubuntu-9-04-Beta-Screenshot-Tour-7.jpg/)

anyone else noticed that of have softpedia tweaked it

---

### Post by Paqman on 2009-03-27
> **wolfen69 said:**
> 
wow. maybe i overestimated the general public.

It's not a matter of "overestimating" anybody. Clearly this guy's just never been provided with specific piece of information. That's nothing to go making judgments about.

After all, there was a time when you and I didn't know that either.

---

### Post by swoll1980 on 2009-03-27
> **wolfen69 said:**
> are you serious? 

wow. maybe i overestimated the general public. i tend to think computers are general knowledge. this is not the case.

Are you serious? I'm the only person out of all my friends, and family that can do anything with a computer that isn't myspace, or yahoo messenger.

---

### Post by pbpersson on 2009-03-27
> **wolfen69 said:**
> are you serious? 

wow. maybe i overestimated the general public. i tend to think computers are general knowledge. this is not the case.

So....wait.....I think I am missing something here.

This person said they tried Ubuntu and it would not allow them to perform the tasks they need to perform (in this case play movies).  So they tried Mint and it worked fine.  They concluded that Ubuntu has a bug.

If I tried an OS and a bunch of stuff did not work I would also assume it was some sort of bug.

Why are people saying this means that this person does not understand computers?  I am not quite seeing the connection.  :confused:

---

### Post by LowSky on 2009-03-27
Been using the 9.04 alpha for over a month now, got he beta update yesterday, it still works great.

some issues thought

npviewer.bin (flash plugin) still fails almost constantly while using Firefox
exaile crashes always at some point, usually after playing 3-5 songs


nothing else is really an issue for me

---

### Post by Joushou on 2009-03-27
> **pbpersson said:**
> So....wait.....I think I am missing something here.

This person said they tried Ubuntu and it would not allow them to perform the tasks they need to perform (in this case play movies).  So they tried Mint and it worked fine.  They concluded that Ubuntu has a bug.

If I tried an OS and a bunch of stuff did not work I would also assume it was some sort of bug.

Why are people saying this means that this person does not understand computers?  I am not quite seeing the connection.  :confused:

The connection is quite simple. Not having the libraries isn't a bug. And since it told you it didn't have it, theres nothing wrong. All you have to do it get them.
The reason they're not there by default, is legalities, like someone said before.

---

### Post by jamarsa on 2009-03-28
> **pbpersson said:**
> So....wait.....I think I am missing something here.

This person said they tried Ubuntu and it would not allow them to perform the tasks they need to perform (in this case play movies).  So they tried Mint and it worked fine.  They concluded that Ubuntu has a bug.

If I tried an OS and a bunch of stuff did not work I would also assume it was some sort of bug.

Why are people saying this means that this person does not understand computers?  I am not quite seeing the connection.  :confused:

Well, If I tried to open an excel spreadsheet in a freshly installed windows, for example, and it wouldn't open, I would think it was because of certain 'legal issues' (not having certain commercial software), not because of bugs....

---

### Post by Nullack on 2009-03-28
It could be considered a bug, but its a wontfix bug because distributing other peoples intellectual property that is protected under patent law would cause legal strife.

Those distros that do, are doing so illegally. They get away with it because it appears they dont make money from their actions and the patent pool owners seem to have taken the view not to litigate when there is no money to be had and when the level of IP theft is relatively small.

---

### Post by Scotty Bones on 2009-03-28
> **Nullack said:**
> It could be considered a bug, but its a wontfix bug because distributing other peoples intellectual property that is protected under patent law would cause legal strife.

Those distros that do, are doing so illegally. They get away with it because it appears they dont make money from their actions and the patent pool owners seem to have taken the view not to litigate when there is no money to be had and when the level of IP theft is relatively small.

Not necessarily so. The IP laws are different from nation to nation.  It just so happens that in Clem's home country this is perfectly fine.

---

### Post by Vorian Grey on 2009-03-29
I've been playing with Jaunty since Alpha 4 and I can't get over how stable it is.

---

### Post by ikt on 2009-03-29
> **jamarsa said:**
> Well, If I tried to open an excel spreadsheet in a freshly installed windows, for example, and it wouldn't open, I would think it was because of certain 'legal issues' (not having certain commercial software), not because of bugs....

I've never heard of anyone calling up MS tech support because their spreadsheets didn't open when they didn't even have Excel installed in the first place...

..

I'm sure it happens all the time now I think about it..:(

The other thing is that windows xp doesn't play DVD's by default either, and it was MS's most popular OS.

> **pbpersson said:**
> If I tried an OS and a bunch of stuff did not work I would also assume it was some sort of bug.

You assume the OS has a bug instead of assuming you just don't have the knowledge to perform that action?

---

### Post by xiaoqi on 2009-03-30
Great news! downloading... will upgrade from my current 8.10 to this one.:popcorn:

---

### Post by andrewabc on 2009-03-30
> **xiaoqi said:**
> Great news! downloading... will upgrade from my current 8.10 to this one.:popcorn:

Make sure everything works on livecd before upgrading.

---

### Post by Therion on 2009-03-30
> **Vorian Grey said:**
> I've been playing with Jaunty since Alpha 4 and I can't get over how stable it is.
Ditto.  I'm getting downright bored with the 'Lope and it's just barely beta!

---

### Post by wolfen69 on 2009-03-30
> **Therion said:**
> Ditto.  I'm getting downright bored with the 'Lope and it's just barely beta!

that's a good thing in my book. if i want drama, i'll install fedora. :wink:

---

