---
title: "Upgrade from a minimal install to a newer minimal install????"
date: 2019-10-21
forum: Installation &amp; Upgrades
---

### Post by soufianta on 2019-10-21
Hello,

Stupid question maybe but can I upgrade my Ubuntu machine (minimal ISO image) to a newer Ubuntu version but also minimal? For example from minimal ISO 18.04 to 19.04-10 or even future 20.04.

Because I'm afraid to be forced to make a "clean" install from a newer minimal ISO or am I  totally wrong?

Thanks.

---

### Post by Dennis N on 2019-10-21
If you upgrade using software updater without doing a new install, that would only upgrade packages already installed, plus any new additional packages required for the newer version.

---

### Post by soufianta on 2019-10-21
From the terminal too and what do you mean with "packages" required for the new intall?

If I made a minimal install from a minimal ISO, it's not the purpose to upgrade to a "bloated" version. I'd like to keep my minimal install but be able to upgrade :).

I think that you mean "any core packages required for the newer version" is that correct?

Because "required" can means all the other packages included in the classic versions (bloating) and that's what I wanted to avoid !! :).

---

### Post by Dennis N on 2019-10-21
> **soufianta said:**
> I think that you mean "any core packages required for the newer version" is that correct?
Yes. You aren't going to end up with the regular Ubuntu install.

---

### Post by soufianta on 2019-10-21
But only if I upgrade from the "software updater" or even from the "terminal" too??

I'll test it on a VM and come back if it's not so ;).

---

### Post by sudodus on 2019-10-21
Yes, I think that is what Dennis N means, and I agree that it should work like that.

But my general experience with upgrading between versions is not very good. So I would recommend:

Alternative - keep only the 'home' partition:

- I have good experience of making a fresh installation of the system, but keeping the home partition. This way the personal data stored there survive. It is even better to store personal data elsewhere, for example in a 'data' partition. Last but not least, the personal tweaks stored in [hidden] directories and files in the home directory survive.

- You have to re-install the program packages, that you want. There is some work to do it, but it is also a good way to get rid of program packages, that you installed for some reason but no longer need. So particularly when you want a minimal system it is a good idea. Install packages if/when you need them.

[hr][/hr]
- **Backup** your current system (at the very least everything that you cannot afford to lose) before you start on this adventure whichever path you prefer: {upgrade} or {install fresh system but keep 'home' partition}.

---

### Post by soufianta on 2019-10-21
It's very frustrating to do all these things for an "upgrade". A backup is for sure required (to avoid other problems in other cases) but it's IMO too much stressiness for a normal "upgrade" :(. An upgrade is always a risky thing but shouldn't be soo risky as it is now.

---

### Post by uRock on 2019-10-21
> **soufianta said:**
> It's very frustrating to do all these things for an "upgrade". A backup is for sure required (to avoid other problems in other cases) but it's IMO too much stressiness for a normal "upgrade" :(. An upgrade is always a risky thing but shouldn't be soo risky as it is now.

My install wasn't minimal, but I recently upgraded from 18.04 to 19.04 and then to 19.10 when it was still alpha with no issues. The machine is used more for entertainment and isn't the one I use for production, so I wasn't worried about it breaking. Backups are always a good thing. I haven't had many upgrades break on me. The only bad breakage I had was when upgrading from 8.10 to 9.04 on a very old laptop. As the versions imply, that was a very long time ago.

I do tend to back everything up and do a clean install of the latest on my production machine. Not out of fear of breakage. I just like to have a clean install to remove any junk I may have installed to either see what it looked like or to aid in helping someone else.

---

### Post by Holger_Gehrke on 2019-10-21
Actually if the versions you quote are what you currently have, then I would wait for 20.04. Reason: you can update from one LTS to the next, so 18.04 -> 20.04 in one update is possible, put to go from LTS to the current non-LTS you'd have to do multiple upgrades 18.04->18.10(which is already EOL, I believe)->19.04->19.10 and eventually ->20.04.

As far as updates are concerned: my current personal machine (bought January 2017) went from XUbuntu 16.10->17.04->17.10->18.04 (at which point I decided to stay with the LTS) without any problems I noticed. Just anecdotal evidence for sure, but it backs up uRock's statement. As long as you don't have a configuration full of personal modifications and you don't have lots of non-standard repositories set up (do remember to deactivate those and any PPAs before an upgrade ...) and have updated/upgraded the old version completely at the time of a release upgrade, it should just work. Yes some unused remains might potentially stay on the system, but you'll have the system mostly set up your way after the release upgrade.

Holger

---

### Post by rsteinmetz70112 on 2019-10-21
A do-release-upgrade will only upgrade those packages you have installed but will also add new packages based on changes in the standard install. Over time this can add packages which are not included in a fresh install. As far as I know there is no clean way to avoid this.

---

### Post by soufianta on 2019-10-22
@[[COLOR=#000000]rsteinmetz70112[/COLOR]]("https://ubuntuforums.org/member.php?u=252572")[COLOR=#000000] : That was an answer on my question ! New packages like "amazon" or something weird and that's what I'm trying to avoid ! If I made a fresh/minimal install, I'd like to keep it so after an upgrade but seems to be impossible to keep it like you want except if you make a clean/minimal install again :(...[/COLOR]

---

### Post by rsteinmetz70112 on 2019-10-22
> **soufianta said:**
> @[[COLOR=#000000]rsteinmetz70112[/COLOR]]("https://ubuntuforums.org/member.php?u=252572")[COLOR=#000000] : That was an answer on my question ! New packages like "amazon" or something weird and that's what I'm trying to avoid ! If I made a fresh/minimal install, I'd like to keep it so after an upgrade but seems to be impossible to keep it like you want except if you make a clean/minimal install again :(...[/COLOR]

I don't think an upgrade will install a lot of extra stuff but will add new packages where the default has been changed. I've never done one on a minimal install so I don't really know but on the upgrades I done of desktop system and servers you usually get the new default as well as the one you had.

---

