---
title: "Thunderbird will not fly!"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by TheFlamingBush on 2009-11-25
Ok i had a fresh install only last week, and tbh Koala was chewing eucalyptus leaves all day long....its been wonderful so far!

last night i decided to sort out my mail client, so i dumped evolution in favour of thunderbird, which i use on the XP partition to my lappy. I then went through the prescribed procedures for shared profile usage between the thunderbirds, and voila perfect!....had all my mail accounts in Koala in no time, i was so happy i could have hugged a tree! (and maybe had a eucalyptus tea!)

Then this morning i booted it up, and doh!....couldn't get into koala at all.....no desktop!!!...o.O..........and it appeared several other rather peculiar events were happening, so i decided to do a full re-install, as one is want to do with new versions of distro's

At first i thought it might have been the new kernal, as everything seemed fine until i started using that. Anyway....reinstalled, and reconfigured, and got my environment back up and running in a few hours. Then dumped evolution and re-installed the bird!

Now the problem seem to be that i cannot open thunderbird after having opened it the first time, everytime i try it says that i already have a current version of thunderbird running, and that i need to close it before opening any operations. except i dont....ive looked at the processes and there is nothing. So i uninstalled it completely....TWICE!....re-booted fresh without it on, then re-installed it again, SAME problem!.........when i go to open it up it says a current version is already running and i will need to close it before opening up any further thunderbird files...ive tried entering thunderbird profiles through the terminal, but no luck.....what can i do please......HELP!!! o.O....my leaves are running out and im getting vertigo up this binkin tree!

---

### Post by TheFlamingBush on 2009-11-25
ok you will be pleased to hear that i have solved this problem myself. 

It had to do with the mount points for the windows partitions, i need to remount the nfts partition and the fat partition that i have used for my windows XP. so everytime i use thunderbird, before i can access the mail i need to remount the partitions, so that the shared profile can be used.....i guess i could copy the file and slip it into /home somewhere, but that would be cheating, so much more interesting to be able to find a way to not have to double everything up and just share files between distro's :P...which brings me onto another slightly sticky question, 

WHY do i need to remount my windows partitions every single time i reboot Koala???....is there a way to make the mounts a permanent fixture?

---

