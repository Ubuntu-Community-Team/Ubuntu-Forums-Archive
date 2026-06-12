---
title: "Unfixed Bug in Update Manager for 8.10"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by forkandles on 2008-11-26
When I use Update Manager in Ubuntu 8.10 it tells me that 
"The package information was last updated 22 days ago."  
The number quoted has risen from 6 to 22 as the days have gone by.

This appears to be Bug Number 284541 in 8.10 which does not appear to have been fixed yet.

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/284541](https://bugs.launchpad.net/ubuntu/+s...er/+bug/284541)

Does anybody have a workaround or do I just wait for the bug to be fixed?

---

### Post by lemming465 on 2008-11-28
Run *sudo apt-get update; sudo apt-get upgrade* from a terminal as a possible workaround.  You may or may not have to disable the bogus repository (with a prefix '#') in /etc/apt/sources.list first.  I think you could probably do that using the GUI System -> Administration -> Software Sources tool if you hate text editors.

---

### Post by forkandles on 2008-11-28
lemming465,
Thanks for that. By the way I love text editors, or at least one in particular, vim.

You are one of a rare breed on the Ubuntu forums who has actually replied to one of my posts. 

I do appreciate that there are vast numbers of posts and most people generally just look at the recent ones. The search function is fine and a lot of useful information can be gleaned from the forums.
This is an instance, in my opinion, where Ubuntu appears to be a victim of its own success.

Yes, I had tried the update and upgrade method you suggested.

When the last lot of 16 software updates (including a kernel update) announced themselves I went to Synaptic and installed them from there. Synaptic worked perfectly.

For your information, there is also another bug (number 273979)
in 8.10.
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/273979](https://bugs.launchpad.net/ubuntu-cdimage/+bug/273979)

Thanks once again for your help.

---

### Post by lemming465 on 2008-11-28
I'm glad you are making headway with your problem. I've got several bug reports open against intrepid, myself.  It was working generally well enough for me that I upgraded both my home desktop and my experimental laptop by the beta or the release candidate.  But it hasn't been completely smooth on video drivers and wireless.

My favorite editor is probably emacs, but I'll happy use vi or even nano. Or gedit. Or whatever.

I noticed that recent forum postings tend to have lots of people jumping on them.  So I started doing advanced searchs for postings which had been around for a few hours without any responses, and trying to help out with them.

---

### Post by forkandles on 2008-11-29
Whilst on the subject of bugs, I have noticed that occasionally since doing the last 16 updates, my mouse pointer and keyboard freeze when I attempt to enter my username from boot up.
I can only imagine it is something to do with the kernel update (2.7.27-9) or similar.
I have never used emacs but of the rest I find vim by far the easiest to handle.

You are probably familiar with vim but I will put a link here anyway to help others. I will do a separate post about vim shortly.

[http://www.stat.tamu.edu/~dahl/teaching/604/calendar/2007-08-28/vim-tutorial/html/index.html](http://www.stat.tamu.edu/~dahl/teaching/604/calendar/2007-08-28/vim-tutorial/html/index.html)

That is a good idea of yours to look for postings under advanced search.

---

### Post by forkandles on 2008-11-29
I know it is not good form to answer your own posts but who cares.

For the benefit of others who are suffering from problems with Update Manager in 8.10, this may help.

The particular bugs are numbers 284541 and 273979.
The links are in the above posts. If one or both of the launchpad links do not work, just google the bug number.

Pending the release of suitable bug fixes I would recommend avoiding using Update Manager. 
When you receive a Software Update Notification just go to Synaptic Package Manager and click on Installed-Upgradeable to download and install the updated packages.

---

