---
title: "From Dapper to Edgy gone DAFFY"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-02-12
I have Dapper 6.06LTS. Desktop version. Installed from Canoncal CD.

I thought I could upgrade to Edgy. I did: 

gksu "update-manager -c"

which ran, got my password, the terminal string ended with Future Warning

the Synaptic Update Manager ran, then the UPGRADE Manager. It closed the repos for Dapper, updated some files, etc and lastly asked me if I wanted to "Upgrade?" I clicked on the upgrade button.

Now the Manager is downloading and removing and installing 1049 files. I didn't realize this would be an upgrade by individual file, seemingly uncached until all the files were ready to install (a typical Synaptic Update Manager scenario). I have Dial-up ISP. I'm running 56K. The Distribution Manager says it is: "Fetching and Installing the Upgrades" and it will continue to do so for: "About 1 days 17 hours 33 minutes" Then it intends to Clean Up and Restart the System. But sometimes the Manager varies, saying: "About x days xx hours and xx minutes" varies from moment to moment, running as high as 3 day and about as low as 1 day 13 hours 11 minutes -- you get it, as the 'net and servers serve it up.

I cannot leave the phone on the modem for that length of time. Can I stop this SAFELY? Has the Distribution Upgrade Manager installed files which are dependent on others? OR has it safely cached these pending finishing the entire "download"? Would I be better off stopping the download ASAP or waiting as long as possible?

I really did read the Forum and [http://wiki.ubuntu.com/EdgyReleaseNotes](http://wiki.ubuntu.com/EdgyReleaseNotes). Nothing seemed to indicate the magnitude of the problem I've got.

Any thoughts much appreciated. Except 'PULL THE PLUG'

---

### Post by PapaWiskas on 2007-02-12
Well I am on a cable modem, and ran into the same issue.

I am not saying you and I are at the same point, but I do know it was in the middle of downloading some files.  Then, the cable service went out, lost my connection about a half hour later it came back up.

I am not sure what happened exactly, but it was like it partially upgraded some stuff and not other stuff, like it was in between two places.  Bad part was, I could not do anything as SUDO....it kept asking me for my password, I would type it in and it was incorrect.

At that point I didnt know what to do, also most of my windows that i would open were in garbled and not real letters....

Luckily I saved my important files, all my email in thunderbird (just copied the .mozilla-thunderbird)

Did a clean install of Uberyl and waalaa was up and running.

It was just weird, because I upgraded from Breezy to Dapper with no issues, and probably could have this time as well, but the cable service went out.

Ah well I am much happier now anyway.

Not that any of this ranting helps you, just trying to caution you.

---

