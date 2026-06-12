---
title: "Boxes greyed out in Add/Remove Application"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by imcompa on 2007-10-20
Several of the main packages I want won't install via the Add/Remove application manager. 

For example: RAR, WINE... I couldn't find anything about this.

edit:I just installed them through the package manager. I guess maybe it's because I am running 64-bit proc? I dunno :(

---

### Post by brucewagner on 2008-01-07
Imcompa,

Did you ever get an answer to this question?

I'd love to know the answer too....

:confused:

---

### Post by zvacet on 2008-01-07
Did you chek in add/remove that is set to **all available apps **? Version is important(32 or 64 bit) not the procesor.

---

### Post by brucewagner on 2008-01-08
yes

If I hadn't had it set to All Open Source apps, it would not show up on the list at all. 

Wine shows up, but the checkbox is greyed out, so I cannot check it.

You say version is important. Why?  I have AMD64 platform. It was my understanding that I can run BOTH 32bit and 64bit apps. No?

Anyway, there is only one version of Wine - which shows up on Add / Remove....

Why would the checkbox be greyed out?

---

### Post by tigerplug on 2008-01-10
I'd usually try
> 
sudo apt-get remove --purge applicationnamehere

But then again Im a Windows administrator ... not Ubuntu/Unix.
Worth a try?

---

### Post by zvacet on 2008-01-10
> You say version is important. Why?

Because some apps don´t run so smooth in 64 bit version,and you will feel speed difference only if you have more then 4GB of ram.In system>administration>software sources chek all under Ubuntu software and under updates tab.Reload.You can install Wine with synaptic or [read](http://wiki.winehq.org/WineOn64bit) this.For Rar

```
sudo apt-get install rar unrar p7zip p7zip-full
```

---

### Post by brucewagner on 2008-01-10
> **zvacet said:**
> Because some apps don´t run so smooth in 64 bit version,and you will feel speed difference only if you have more then 4GB of ram.In system>administration>software sources chek all under Ubuntu software and under updates tab.Reload.You can install Wine with synaptic or [read](http://wiki.winehq.org/WineOn64bit) this.For Rar...

Wow.

So under System>Administration>Software Sources> Updates tab, you want everything checked --- including "Pre-release Updates (gutsy-proposed)"?

And, since I have only 4GB of ram, and you say "some apps don't run so smooth in 64 but version", it sounds like maybe I should switch to the 32-bit version of Ubuntu...?

About installing Wine, is there any advantage to installing it with Synaptic versus installing it with Applications>Add/Remove...?

What repositories do I need to make sure are listed for everything I need?   Are there any I should definitely NOT have listed?

---

### Post by zvacet on 2008-01-10
> About installing Wine, is there any advantage to installing it with Synaptic versus installing it with Applications>Add/Remove...?

No,it should be the same.If you want you can add wine repo to your source list (if you decide to swich to 32 bit because I don´t know is it any for 64)
[Here](http://www.winehq.org/site/download-deb).

---

### Post by brucewagner on 2008-01-10
Why add Wine's repo to my source list?

Is there some advantage to doing that?

(By the way, yes, that page seems to imply that their repo covers both 32 and 64 bit versions.)

EDIT:   I may have answered my own question.  When I just now added the Wine repo....  within 1 minute, I was notified, by Update Manager, of new updates available to Wine.   So, apparently, their repo is more up-to-date.   

So, apparently, the advantage would be:  faster updates to Wine.

---

### Post by daInvincibleGama on 2008-01-18
The same happens to me. I'm running the AMD64 variant of Gutsy. RAR and Wine don't install from the Add/Remove Programs manager. It installs from the Synaptic Package manager, but the way that works best is through the command line.

I can get them installed, but it's annoying not to know the reason. I'm trying to figure it out, but if someone can help it would be appreciated.

---

