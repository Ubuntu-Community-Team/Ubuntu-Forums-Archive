---
title: "package system breaks easily!"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by {spitFire} on 2006-09-26
[FONT="Verdana"]
    Though I'm a newbie in Linux, I've been quite fortunate to get a chance to lay my hands on Debian - sid and cherish the distro for a long time. I've never had any problems during any package installation. Whenever there was a dependency apt-get would resolve it for me. I have never seen messages like 'conflicts...blah...blah...' or '...unresolved dependency ...blah...blah...'. The maximum I would encounter is package not found, which is usually bcos' of a missing repository source in the sources file. 

    However, my recent experience with Ubuntu has been so very frustrating! I still love it for the community and a lot of other goodies; nevertheless, i should mention that it breaks easily. 
  
    I salute the enlightened ones who wrote 'easyubuntu' or 'automatix'. However, I see that those tools are the starting point for problems. Once after using them, if I hit a 'apt-get -f install' or 'aptitude -f install', the pitiful state of my system becomes obvious. I've banged my head several times trying to figure out how to resolve the conflicts and most of the time, I give up!

    Is it because Debian has all the desktop systems (gnome, kde, etc...) in a single bundle that one doesn't see that many problems, or is it due to some buggy design in Ubuntu?
  
    I can't install amarok on my system (ubuntu dapper on dell e1505), and if I do I can't install totem-xine later :(
  
    And I was happy with xgl/compiz but even that broke and I can't install them now, cos' they are not there in the repository!!!
  
    Am I the only one facing such problems in Ubuntu? My intention is only to get to know what I'm overlooking, when it comes to Ubuntu. I simply can't digest aptitude spitting all over my screen when I try to politely install something.
[/FONT]

---

### Post by Jussi Kukkonen on 2006-09-26
You'll probably get more intelligent replys if you write one post per problem, but here's some general comments:

> Am I the only one facing such problems in Ubuntu?

Four machines running (first one from the Warty times), several dist-upgrades and hundreds of software installs done, and I've never had package management screwups. 

It could be just good luck, but I'm very careful about scripts that work 'around' the package management (like automatix) and about using third party repositories. I'm guessing many, many problems stem from added repositories  that inject wrong versions into the system...

---

### Post by {spitFire} on 2006-09-26
I'm seeing conflicts right after I installed proprietory drivers from "ati" for my video card. Well, is that normal???

---

