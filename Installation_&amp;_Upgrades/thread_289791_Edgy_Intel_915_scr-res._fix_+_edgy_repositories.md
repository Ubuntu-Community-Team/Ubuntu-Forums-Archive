---
title: "Edgy: Intel 915 scr-res. fix + edgy repositories"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by carbonic on 2006-10-31
After a buggy udgrade from dapper to edgy that resulted in ubuntu going crazy at startup (even though I followed the official guide), I installed a new fresh installation of edgy and got two problems.

1. I got a Intel 945 chipset that can run with a wide screenresolution, and ubuntu don't wanna use that native so I'm used to use the two following commands to fix it:
"apt-get install 915resolution"
"# sudo 915resolution -l"

this doesn't work in edgy, and was wondering how I can fix it? This screenresolution is killing me.

2. I have noticed a lack of programs to get by using apt get etc.
I guess this is a lack of extra things in my repository and was wondering which ones I should add. Stuff like 3ddesktop would be nice.
Perhaps this is also why I can't find packages using apt-get I used to be able to find in dapper.

---

### Post by JayTee on 2006-10-31
I'm having the same problem here. I can't install 915resolution because it's not in the repositories for Edgy or so it would seem. I've tried several changes such as adding the correct modeline to my xorg.conf but it doesn't work. I've got 1440x900 in each of my Screen modes section but the highest that shows is 1280x1024. I've got the same monitor working fine in Dapper but it took me over 10 hours of reading, digging, trying this, trying that before I was successful. Time it took to get it set right in XP, 2 mins to download updated video driver and 3  minutes to install and less than 1 minute to set resolution. Time it took in Vista RC1, less than 1 minute total. Sheesh! I love Ubuntu but since I started using Dapper I've tried other distros and I think Ubuntu is much weaker than most in video and in audio hardware detection and configuration. Maybe this weekend I'll blow away the install, install Dapper and try the upgrade route but download 915resolution first in Dapper since it is in those repositories. Judging from the number of problems  I've seen here at least I'm not alone.

---

### Post by carbonic on 2006-11-02
I fixed it somehow. Automatix2 updated some list when I started it(not apt-get update) and now 915resolution is on the list. Weird distro.

---

