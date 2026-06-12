---
title: "ubuntu 7.10 install woes"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by pantlegz on 2008-01-28
I've been attempting to install ubuntu 7.10 64 bit for about 2 days on and off with no luck at all. To get started, it took 8 mirrors to get a decent iso downloaded, 15 CD's for one with no errors( 5 at 1x which atakes about 15 min just to burn), both in Nero and the Check disk for errors(I think) in the live CD menu. Finally, I think I'm making some progress, having used up a ton of bandwidth on the fourm, looking up issues and how to resolve them. then at about 82% through the install, it hangs up on 'checking mirror' not sure what it's doing, being my first linux install, I let it "think" about 45 min later I come check up on it and it's froze. While I normally don't have an issue just trying again, I'm at wits end. Is this just a try again situation or is there something I did wrong?  I setup a 32gb ext3 partition as / and a 10gb swap. current hardware setup -- EPoX NF4 Ultra Mother board AMD 6000+ @ 3.2Ghz 2GB DDR2 800 RAM. 320gb WD and 500GB maxtor(I think). If there's anything else you need, I'll do my best, like I said this is my first linus attempt, and thus far it's been a lot of... fun?  Thanks in adavance for the help :)

---

### Post by Partyboi2 on 2008-01-28
> here's a quick fix to this issue, disable your network devices and it will time out within 30secounds and proceed with the install. Just enable your network after that and everything should be fine.
(quoted from ubuntuforums.org)After you have installed ubuntu you will need to go to System>Admin>Software Sources and on the first tab tick all of them except source code then click on the updates tab and tick the first 2 boxes. This is needed because  the installer timed out at scanning the mirrors.


Edit: Alot of people have just left there pc scanning the mirrors and went off for a few + hours and returned to the install finished.

---

