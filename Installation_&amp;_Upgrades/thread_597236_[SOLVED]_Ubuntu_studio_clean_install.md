---
title: "[SOLVED] Ubuntu studio clean install"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by serfcx on 2007-10-30
Hi, just a quick question.
Am planning to do a clean install of Ubuntu Gutsy and as I want this box to be mainly for audio/video work would it be best to install Ubuntu Studio from the DVD iso or use the standard Ubuntu Gutsy install and then just add the "studio" variants from the repos ?

Thanks

---

### Post by por100pre1 on 2007-10-31
Either way will install the packages from the same repositories. You can use the method you prefer. IMHO, to install using the Gutsy Live CD is more convenient. Install Regular Gutsy and then:

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

---

### Post by serfcx on 2007-11-01
> **por100pre1 said:**
> Either way will install the packages from the same repositories. You can use the method you prefer. IMHO, to install using the Gutsy Live CD is more convenient. Install Regular Gutsy and then:

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

OK, but what about the rt kernel, does one of these programs install that ?

---

### Post by Drunky on 2007-11-01
The Ubuntu Help has a wiki for [UbuntuStudio/UpgradingFromGusty]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29").

Open a terminal and paste:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

This will include real time kernel.

---

### Post by Chappy7777 on 2007-11-01
Question Serfcx,

Since you obviously are up on the programs to use for the best voice and/or best audio, do you mind telling me which programs you prefer for this stuff? I have installed Real Player, XMMS, Amarok, Streamtuner, and a few others. It's okay now because I have the room on my HDD, but it seems likely that I am doubling up on some programs I don't need. 

What I would like to find is a way to play streaming audio is real player files, ie: ra, rm. When I click on a Real Player link at most sites, I end up with an error saying "source .cgi" isn't happy. I don't want to keep windows on here just for the few sites where I get these results. Sites like MLB, Glenn Beck, and others.

I know this is the wrong place to ask this question, but you seemed like the guy to ask, so don't hit me too hard.

---

### Post by blakesle on 2007-11-01
> **por100pre1 said:**
> Either way will install the packages from the same repositories. You can use the method you prefer. IMHO, to install using the Gutsy Live CD is more convenient. Install Regular Gutsy and then:

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

This was wonderful!!! I had installed Gutsy some time back and did not want to do a clean install. I now have Studio installed and it is absolutely great.

Thanks a million.

---

### Post by serfcx on 2007-11-02
> Question Serfcx,

Since you obviously are up on the programs to use for the best voice and/or best audio

High chappy7777,

I am not sure that I am the right guy to ask as I am just setting up the box as an "experiment" for my wife to use to help with her guitar work and songwriting - purely amateur.

Especially I dont listen to streaming audio that much and have used both xmms, amarok and lately exaile with about equal success in the past.

I ended up doing an install of Studio from the dvd via the text installer and everything went fine and now also have compiz running. Nice interfaces - I am so far a happy bunny !

---

