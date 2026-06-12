---
title: "Thunderbird mail doesn't import after upgrade"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by mertle on 2009-11-24
OS: Kubuntu 9.10 Karmic
Client: Thunderbird 2.0.0.23 (20090817)

So I've recently did a fresh install of Karmic from Gutsy, all went amazingly well (yay!), but I can't seem to import my old Thunderbird mail into the new installation. I'm able to see all my folders in the left pane, but when I click on one to view its contents, Thunderbird just hangs (with a busy cursor) and no messages load. It's been a while since I've had a problem that I had to ask the forums about.. I know they're there, dammit, just can't seem to access them.

I've read just about every thread on here (plus other forums) tagged with Thunderbird and importing/exporting mail, but no luck. This is what I've tried so far:

[INDENT]1. Saving my whole ~/.mozilla-thunderbird folder and copying it into the new installation's /home folder.

2. Creating a new profile and replacing the 'Mail' folder with my old one.

3. Deleting all the indexing files (.msf files) and reloading Thunderbird in hopes it'll reload the emails.

4. Renaming each mailbox file (inbox1, inbox2, etc.), moving them over one by one, sacrificing a lamb, and praying to the Gods that be...[/INDENT]

Nothing has worked. Just a constant 'busy' cursor, and no email. I can't even download current email- it just... does nothing when I press the button. Have I missed something obvious? I consider myself fairly (k)Ubuntu knowledgeable, as I've been using it as my sole OS since Edgy came out, but this is really frustrating me. Any help would be greatly appreciated. :)

- mertle

P.S.
Firefox was no problem whatsoever- even most of my extensions transfered when I moved my profile over.

---

### Post by mertle on 2009-11-25
Well, I seemed to have fixed my problem, but I'm not quite sure what did it.

Due to something I screwed up, I just ended up reinstalling Kubuntu. Instead of immediately moving the Thunderbird folder to /home, I ran the program first- didn't make a profile, didn't add any accounts, just gave it an initial run. THEN I overwrote the .mozilla-thunderbird folder in /home, restarted it, and all was right as rain.

Who knows if that did the trick, or just a fresh re-install worked out any glitches.

---

### Post by presence1960 on 2009-11-25
As a rule I always start the thunderbird application & close it prior to making any changes either to profile folder or using command from terminal ```
thunderbird -profilemanager
```

When I tried in the past without starting the application then closing it my changes never worked.

---

