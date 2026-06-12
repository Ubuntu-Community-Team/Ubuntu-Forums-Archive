---
title: "Dapper-&gt;Edgy Upgrade Problems"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by bart_simpson on 2006-10-22
Hey everyone, recently about two weeks ago I decided to upgrade from Ubuntu Dapper Drake to the Beta Release of Ubuntu Edgy Eft. After some modifications everything was working fine, then my wireless internet stopped working (went through that whole ndiswrapper thing, still wasn't going) . I decided to wait until the Release Candidate shipped out so I could install that and see if that would solve the problem since this was a beta. I downloaded the Live CD but everytime I attempt to mount the package in Synaptic, it will automatically unmount it after I hit "Add CD". I have also tried putting the cd in, then going to a terminal and typing in:

sudo apt-cdrom add

(which unmounts the cd then asks if I want to add another cd and if I say yes then it will continue the process of unmounting then asking again)

then

sudo apt-get update
sudo apt-get upgrade

and after all that, it says 0 new packages have been installed/upgraded, so I was wondering if anyone had any ideas on how to fix this, thanks.

---

