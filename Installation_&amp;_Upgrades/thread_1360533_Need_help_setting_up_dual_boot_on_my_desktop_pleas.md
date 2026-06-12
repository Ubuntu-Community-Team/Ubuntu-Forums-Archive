---
title: "Need help setting up dual boot on my desktop please"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by n1x1n on 2009-12-21
I currently have Windows XP SP2 installed on my desktop on a 1TB hdd, and I would like to setup a dual boot with Ubuntu 9.10.
Can someone please walk me through the steps I need to take in order to do so?
I've already downloaded Ubuntu 9.10 and burnt it onto a disc using InfraRecorder.

If you have msn, mine is "eurodancingmonk@hotmail.com", I have a seperate laptop I can use if you would like to walk me through step by step.
If not then instructions here are just fine.

Thank you sooooo much in advance :)

---

### Post by plusnplus on 2009-12-21
Hi n1x1n,
take alook the link. hope that can help you install the ubuntu

[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)

[http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)

---

### Post by Bucky Ball on 2009-12-21
BACK UP ANY DATA YOU DON'T WANT TO LOSE!! Precautionary only, data loss is unlikely if you make a plan and know what you are doing. Installation for a dual-boot is pretty straightforward.

Stick CD in and install! When you get to partitioning use 'manual partitioning' and just leave your Windows partition alone (and any others you want untouched). 

9.10 can be pretty buggy for now as it has been out only two months in a few days time (check the number of 9.10 issues on the forums) and may not be the greatest place to start with Ubuntu. To start with I would advise something a little more stable (8.04 LTS (Long Term Support) or 9.04). Once you get the hang of things, upgrade to a newer version. I only use LTS releases personally and 8.04 LTS is the current Enterprise release and recommended for business, is currently rock solid.

Manual partitioning, make sure you add these partitions at least, and they are defaulted in there for your selection in the 'Manual Partitioning' section so pretty simple:

```
/
/home
/swap
```But you could add more:

```
/vids
/music
/recipes
```The '/' partition = root partition. You also get to define the size of them with 'manual partitioning' and will pick up your Windows install and add it to the menu list you get at boot.

If all this is a bit beyond you, the links in Post #2 could be the go or a combination of both. Good luck. It's pretty straightforward and you learn as you go so enjoy the curve. :)

* NEW USER TIP: Research your issue a bit more next time. There is heaps of info out there about this:

[http://www.google.com/cse?q=windows+ubuntu+dual-boot&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8]("http://www.google.com/cse?q=windows+ubuntu+dual-boot&sa=Search&cx=partner-pub-2070091971271392%3Aougxymc6y19&ie=UTF-8")

---

### Post by n1x1n on 2009-12-21
ok I did all the steps but I need help because when I see the menu to select OS, when I select the first linux option (not the other one that says "recovery mode" or something like that), it doesn't launch ubuntu...

instead I get to a black screen asking for my username and password, and when I enter that it's asking me to enter a command... it's not taking me to Ubuntu... :(


EDIT:  It says "Ubuntu 9.10 username tty1

username login: _


this is weird... what did I do wrong? Help please!! :)

---

### Post by elite_angel on 2009-12-21
@n1x1n

Welcome to ubuntu!

---

### Post by Bucky Ball on 2009-12-21
For now, login to that screen and then type in:

```
startx
```Does that take you to a desktop??

Is the Windows boot working from the new menu? You haven't done anything wrong so far as we can see at this point. Just a tweak required.

ps: I did mention that 9.10 may not be the best place to start! But this looks fixable and there are a lot of 9.10 users about who tweak with it A LOT. I am not one of them. :)

---

### Post by n1x1n on 2009-12-21
> **Bucky Ball said:**
> For now, login to that screen and then type in:

```
startx
```Does that take you to a desktop??

Is the Windows boot working from the new menu? You haven't done anything wrong so far as we can see at this point. Just a tweak required.

Thank you for your reply!

Windows boot works perfectly, but I tried what you told me to do, on that screen I put in my username and password and then I put in:

```
startx
```

and it said:

```
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
username@username:~$ _
```

what should I do now?

---

### Post by Bucky Ball on 2009-12-21
More research or try another release. Perhaps 'install xserver ubuntu' might be somewhere to start.

It seems not to have installed the xserver which is odd. You did install the right ISO? 64bit for ANY 64bit machine and 32bit for older ones? You didn't install the server version by mistake (that doesn't load a desktop by default from memory but works from the CLI exactly as you're describing)? I have to go out for awhile but will have a look around later. For now ...

You haven't done anything wrong by the looks. This is a 9.10 issue probably. If you want to be really certain, install 8.04. If that works, try 9.04. Generally six months after release is getting safe if you don't want to be forever fiddling and tweaking which is why a stabler version is a good place to learn the ropes. Then you can dive in with the 'bleeding edge' release and help the community by tweaking and using if that grabs ya.

Also, boot from the CD again and run 'Check CD for defects' from the options if you haven't already. A torrent download of the desired ISO is the fastest and most reliable way if you're into that.

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Also, after logging in to the CLI screen, make sure you have your ethernet cable plugged in and type this in:
```

sudo apt-get install ubuntu-desktop
```What happens?

My pleasure and welcome to Ubuntu and the forums. You might like to have a look at my NEVER TRIED LINUX link in my signature once you are rolling. Stick with it. I think you might like. ;)

---

### Post by n1x1n on 2009-12-22
If 9.10 isn't stable, then why would they offer it for download at ubuntu.com?? Doesn't make sense at all... lol

Thank you so much for trying to help me, but for me first impressions are everything and by the looks of this, hmm not so good, therefore I'm going to have to stick with Windows.

Take care :)

---

### Post by darkod on 2009-12-22
> **n1x1n said:**
> If 9.10 isn't stable, then why would they offer it for download at ubuntu.com?? Doesn't make sense at all... lol

Thank you so much for trying to help me, but for me first impressions are everything and by the looks of this, hmm not so good, therefore I'm going to have to stick with Windows.

Take care :)

It is stable, in most cases. As with any technology, on some occasions there can be problems.
First of all, it might be a dumb question, but are you sure you downloaded the desktop version? The server version does not install GUI desktop by default. Also I think the alternate install cd doesn't install desktop GUI by default too.
Another possibility is that somehow the install went wrong. Or it's a video driver issue so it isn't loading the desktop for you.
You can try slecting the recovery mode entry in the menu, and then "root with networking" in the next menu. Once it loads the command prompt for you, you can try the command:
sudo apt-get install ubuntu-desktop

as suggested.
See if that will help.

---

### Post by Bucky Ball on 2009-12-22
> **darkod said:**
> 
First of all, it might be a dumb question, but are you sure you downloaded the desktop version? The server version does not install GUI desktop by default. Also I think the alternate install cd doesn't install desktop GUI by default too.

I said that to start. OP gone back to Windows. Perhaps OP could mark the thread 'solved' from thread tools to save others some time. :)

---

