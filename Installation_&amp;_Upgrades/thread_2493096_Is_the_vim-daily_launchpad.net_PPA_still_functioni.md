---
title: "Is the vim-daily launchpad.net PPA still functioning?"
date: 2023-12-03
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2023-12-03
It says on vim PPA manager [Jonathon F's launchpad page]("https://launchpad.net/%7Ejonathonf") that:[INDENT] [I]
"This account belonged to a deceased user and has been archived."[/I]
 [/INDENT]

(In fact, Jonathon F. [died in January of 2023]("https://forum.endeavouros.com/t/jonathon-passed-away/35814").)

 But on the [vim-daily PPA page]("https://launchpad.net/%7Ejonathonf/+archive/ubuntu/vim-daily"), it can be seen that vim has been updated as of ***01 December 2023*** for Ubuntu versions 22.04.1, 20.04.1 and 18.04.1:

 [I]vim    2:9.0.0749+really.v9.0.2143-0york0~ubuntu22.04.1    Jonathon F (2023-12-01)
[/I]
 So, it appears that ***someone*** is still updating the vim-daily PPA.

 However, I have had vim-daily in my /etc/apt/sources.list.d/ for some  time, but my vim has been stuck for a few weeks now at version *9.0.1837*,  and has not upgraded to *9.0.2143*.

 I've checked to make sure I have the source entry correct, but  updated vims are not being installed. 

If vim is being updated on the  PPA, shouldn't the updates be getting installed on my machine when I
*sudo apt update && sudo apt upgrade*?

 Anyone know what's going on with this?   Thanks

---

### Post by deadflowr on 2023-12-03
Seems like a question for launchpad itself and how they deal with something like this.
You can post a question here: [https://answers.launchpad.net/launchpad](https://answers.launchpad.net/launchpad)
Maybe someone there can take a look at it do something about it.

Could be that he setup auto-building that is still running.
>  it appears that someone is still updating the vim-daily PPA.

However, I have had vim-daily in my /etc/apt/sources.list.d/ for some time, but my vim has been stuck for a few weeks now at version 9.0.1837, and has not upgraded to 9.0.2143.

I've checked to make sure I have the source entry correct, but updated vims are not being installed.

All builds since July 2022 have seemed to have failed to build.
Which I would expect from something set to auto-build and no one was periodically checking to see if they were successfully building or not.

---

