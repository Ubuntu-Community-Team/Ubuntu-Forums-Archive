---
title: "Upgrading from 12.10 Server to 14.04 Server"
date: 2014-10-12
forum: Installation &amp; Upgrades
---

### Post by James_Spinella on 2014-10-12
Hey all,

I have a bit of an odd issue... As some of you may know by now, I've been working with a CECHA PS3 (IBM PPC, 256MB RAM). I've thus far been able to figure things out after weeks and weeks of having at it.

Now I actually have Ubuntu installed on the thing. It's 12.10 Server, the only version that a) I could find a working link for PPC for and b) actually installs without error and boots.

So no, I can't "just" install 14.04 Server. I've been googling around, and I've learned that, since 12.10 is no longer supported, the links in /etc/apt/sources.list are 404, some of them anyway... So I've tried updating them to mirrors, but no luck with that. There has to be some way to get to 14.04 without reinstalling. I've read that it will likely be 12.10 -> 13.04 -> 14.04. In any event, no matter what I try, I get an error when trying the command for do-release-upgrade.

Perhaps someone can speak from experience, tell me *exactly* what I need to do? If not, I'm sure I'll figure it out on my own accord eventually... It just takes so much time researching and going through trial-and-error.

Many thanks to the brave soul who replies!

---

### Post by Doug S on 2014-10-12
> **James_Spinella said:**
>  I've been googling around, and I've learned that, since 12.04 is no longer supported, the links in /etc/apt/sources.list are 404, some of them anyway... 12.04 is a LTS (Long Term Support) version, and is still supported. do-release upgrade should work. Tell us some more about your issues.

---

### Post by MartyBuntu on 2014-10-12
What is your long term goal for this machine? Just to run Ubuntu Server?

---

### Post by James_Spinella on 2014-10-12
Sorry, I mean to say 12.10, not 12.04. If it was 12.04, I'm sure things would be easier (I can't seem to find 12.04 PPC Server anywhere... Desktop, yes; server, no.).

Long-term goal is just to act as a web server, possibly cryptocurrency mining (I realize it will probably be quite lousy at this point regardless of the CELL BE PPC Processor, but electricity is free, it's just sitting there, might as well try it).

Here's the error I get when I try do-release-upgrade:

[COLOR=#7C6563][FONT=Helvetica]*Traceback (most recent call last):*[/FONT][/COLOR]
[COLOR=#7C6563][FONT=Helvetica]*File “/usr/bin/do-release-upgrade”, line 145, in <module>*[/FONT][/COLOR]
[COLOR=#7C6563][FONT=Helvetica]*fetcher.run_options += [“–mode=%s” % options.mode,*[/FONT][/COLOR]
[COLOR=#7C6563][FONT=Helvetica]*AttributeError: type object ‘DistUpgradeFetcherCore’ has no attribute ‘run_options’*[/FONT][/COLOR]

Which is explored here:

 [http://www.prestonlee.com/2013/04/26/ubuntu-12-10-to-13-04-server-upgrade-error/](http://www.prestonlee.com/2013/04/26/ubuntu-12-10-to-13-04-server-upgrade-error/)

I tried the solution on prestonlee.com unsuccessfully.


I'm sure the problem has something to do with the sources now being 404 since 12.10 is no longer supported, so I think I'm on the right track... But like I said, editing the sources.list has proved unsuccessful thus far.

---

### Post by steeldriver on 2014-10-12
***I have edited your thread title - hoping you will get more relevant views***

---

### Post by James_Spinella on 2014-10-12
Thank you, much appreciated!

---

### Post by Bashing-om on 2014-10-12
James_Spinella; Hello'

Are you aware, or have you seen:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You are in for a long tough hard row when you choose to upgrade from 12.10 ==>
12.10 ->13.04 ->13.10 ->14.04

as 13.04 and 13.10 are also End-Of-Life . 

It is possible
[INDENT][INDENT]and might be done
[/INDENT][/INDENT]

---

### Post by James_Spinella on 2014-10-12
Thanks for the reply. I followed the instructions at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades), in fact that was the first thing I did, but that too was unsuccessful.

After adding those URLs to the /etc/apt/sources.list, I still get that error I mentioned above with the Traceback.

---

### Post by Bashing-om on 2014-10-12
James_Spinella; OK ;

The obvious question:
> 
After adding those URLs to the /etc/apt/sources.list, I still get that error I mentioned above with the Traceback.

what URL did you add ?

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by James_Spinella on 2014-10-12
All of the URLs listed, including the optional one (and their suffixes- replaced CODENAME with quantal).

## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-backports main restricted universe multiverse

And yes, I omitted the "#" ;)

---

### Post by James_Spinella on 2014-10-12
Should I remove the other URLs that were there by default?

---

### Post by Bashing-om on 2014-10-12
James_Spinella; Oh Boy ;

Does not "look" real promising.
Show us what is:
```

cat -n /etc/apt/sources.list

```
so we are all on the same page.

[INDENT][INDENT]on the road to resolution
[/INDENT][/INDENT]

---

### Post by James_Spinella on 2014-10-12
Sure thing, I'll post it as soon as I can tomorrow afternoon.

---

### Post by James_Spinella on 2014-10-13
[IMG]http://jatsby.com/img_0193.jpg[/IMG]

---

### Post by James_Spinella on 2014-10-13
There's the default. I reinstalled so it deleted the lines I manually put in, but it was just the above with those aforementioned lines added.

---

### Post by Bashing-om on 2014-10-13
James_Spinella; Hi !

Mind you, I do not recognize your URL configuration "ports" .. but but this I do know .
> 
There's the default. I reinstalled so it deleted the lines I manually put in, but it was just the above with those aforementioned lines added.

one does not "add" one "changes" -all- the lines in the file ,
the URL must point to "http://old-releases.ubuntu.com/ubuntu/  ; in one form or another -
and " CODENAME " is the code name of the release that you are upgrading to -next ( as in the 1st raring ) then when system is stable on raring -> suacy -> and when stable on saucy -> trusty .

A long process, and lots of bandwidth to go from 'quantal' - one step at a time - to 'trusty' .

That is the process
[INDENT][INDENT][INDENT]and it might be done
[/INDENT][/INDENT][/INDENT]

---

### Post by James_Spinella on 2014-10-13
I got it...

I went into /etc/apt/sources.list and manually edited each line (did not add any lines), replacing each instance of "quantal" with "trusty".

From there, I ran sudo apt-get update and sudo apt-get upgrade, and it proceeded to download a boatload of new packages.

It asked me a question, I said "yes", and it kept on keeping on... Eventually it finished with an error regarding being unable to install python.

To resolve this, I ran sudo apt-get -f install (for resolving dependencies).

At that point, I ran lsb_release -a to check the ubuntu version (since I'm on Server, not Desktop), and it's reporting it as 14.04.1 LTS.

Did a sudo reboot and ran lsb_release -a again to verify Ubuntu version.... All is well!

Thank you for your assistance. For anyone who visits this thread looking for a solution, such "complex" upgrades should be handled as mentioned above. It's nothing *too* complex!

---

### Post by Bashing-om on 2014-10-13
James_Spinella; Great !

Wheeehhww, got over that hurdle  - pleased ya up now and running 14.04 .

Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean 
and precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on
[INDENT][INDENT][INDENT]keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

