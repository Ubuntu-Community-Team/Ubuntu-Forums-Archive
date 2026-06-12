---
title: "Install codecs (like mp3)"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by drutrax on 2007-12-03
Every time i try to install a codec or program i get a message.

"The list of applications is not availabe"

"Click on 'Reload' to load it. To reload the list you need a working internet connection."

how do i get it to work. I just want to get it to play movies and music but i always get in a loop with that message.

---

### Post by Pumalite on 2007-12-03
Do you have Internet?

---

### Post by erfahren on 2007-12-03
you didn't say but I assume your using Gutsy. When there's not an internet connection present when Gutsy is installed it will comment out (disable) the repositories in /etc/apt/sources.list
(that seems to be a new thing that is confusing many)

you need to go and enable the repositories

see:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

note: you can only use (have open) one package manager application at a time. So don't have Synaptic open when installing through the command line (terminal), or have Synaptic and Add/Remove open at the same time, etc.

---

