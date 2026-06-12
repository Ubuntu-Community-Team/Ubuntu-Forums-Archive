---
title: "Regarding Upgrading Ubuntu"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by craig10x on 2013-12-04
[COLOR=#000000]I have been using the upgrade option on the live session iso installer for upgrading to the next version of ubuntu and it has worked really well...however, i am considering doing it using the Update Manager when 14.04 is final released next April....[/COLOR]

[COLOR=#000000]Two questions:[/COLOR]

[COLOR=#000000]1) How soon after a final release does it usually pop up on Update Manager?[/COLOR]

[COLOR=#000000]2) I do have my software sources set to notify me when a new version is available but i was just wondering, in case it doesn't come up automatically in the update manager, what is the terminal command you use to prompt it to come up in update manager? (i am talking about upgrading to each new final release not into the next development version)...[/COLOR]

[COLOR=#000000]Hope someone can let me know...i want to make a note of it for when i do my next upgrade [/COLOR]:wink:
[COLOR=#000000]Thanks...[/COLOR]

---

### Post by oldos2er on 2013-12-04
```
do-release-upgrade
```

---

### Post by craig10x on 2013-12-04
Thank you, Ann...:D
Does that terminal command make it come up on the update manager itself?  Or do you have to run the actual upgrade directly in the terminal?

---

### Post by craig10x on 2013-12-05
Anyone know? (or is there a different command to use?)...

---

### Post by sudodus on 2013-12-05
Go ahead and try the command :-)

It doesn't bite ... but as always when upgrading between versions, many things can go wrong, so you'd better ***backup everything important*** before you try.

---

### Post by craig10x on 2013-12-05
LOL...i know...actually i won't be doing it again until 14.04 arrives (final version) as i already upgraded to 13.10 when it went final (but using the iso installer's upgrade option)....
I have all my important data backed up on a flash drive, so no worries there ;)

I was just wondering how you get it to come up in software updater in case it doesn't come up automatically as it should...I have heard some pretty good experiences using the option from the software updater so thought i might be adventurous and and try it THAT way the next time around...

---

### Post by oldos2er on 2013-12-05
> **craig10x said:**
> Thank you, Ann...:D
Does that terminal command make it come up on the update manager itself?  Or do you have to run the actual upgrade directly in the terminal?

Are you using Unity? I don't know if that command would make the Update manager appear. 

But whether it runs graphically or in terminal, it's the same process.

---

### Post by craig10x on 2013-12-05
Yes, Ann...using the main edition of Ubuntu with Unity...so it would be the same whether graphically or terminal, then?
Also, i was wondering...when using the iso installer upgrade method...no questions were asked during the process....using the the updater or terminal, does it ask any questions along the way? (like if you want something replaced or not)...i was able to walk off and come back when it was finished, so i was wondering if it would be the same with the other method...

---

### Post by oldos2er on 2013-12-05
I've run do-release-upgrade in terminal, and yes, it does ask questions. If you've changed any config files in /etc, it asks whether you want to keep the current version or install newer default versions; I tell it to overwrite the old ones with new default versions, just to be safe. I always make backup copies of system files before changing them (learned to do that the hard way), so it's not a problem for me.

I think it asked something else, but I don't recall what.

I see do-release-upgrade has a sandbox option, but I know nothing about that. Might be something to look into.

---

### Post by craig10x on 2013-12-05
Thanks Ann...appreciate the input :D

Interesting...yet when done with the iso installer's upgrade method...no questions are asked...i guess it must be set that way to just automatically do what you would normally likely say "yes" to anyway (lol)...
Also, with the installer you get the slide show, choose your time zone and log in password just as if you were doing a totally clean install...although watching what was going on underneath, i saw a lot of different things going on and at the end, it restored all my programs, data and most of my settings...

I might try it with the terminal command next time...or perhaps maybe i should just stick with doing it with the iso installer since it's worked very well for me...

---

