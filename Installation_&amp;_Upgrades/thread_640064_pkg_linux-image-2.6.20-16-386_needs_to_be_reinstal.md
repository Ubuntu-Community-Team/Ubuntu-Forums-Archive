---
title: "pkg linux-image-2.6.20-16-386 needs to be reinstalled.."
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by teripittman on 2007-12-13
I am getting this in synaptic pkg manager, update manager, apt-get and aptitude. In the gui based managers, I get the error and it immediately closes the program. The other two programs give me the error but can't move past it. I tried the fix listed on the forums (sudo dpkg -r linux-image-2.6.20-16-386) and it fails. It says there are dependencies that prevent removal. But when I try to see about removing the dependencies, it goes back into files that seem to jepordize the kernal that is sort of working (like removing linux-386--I know that's not exactly the file mentioned but it seemed to be part of the base install.)

At any rate, I am trying to come up with a solution. I have burned the live CD of Gutsy and I could do a fresh install if I have to.  The downside of that is that I am not sure if I am looking at the linux partition when I check the partitions for installing. It is on the /media directory, which makes me think it is talking about the CD, although the size is correct. It shows 20gb which is my linux partition size but does not show my windows partition at all.  I'd love to come up with a solution for this. Any ideas of a possible fix?

---

### Post by teripittman on 2007-12-13
This is too strange.  I ran the update again (and trust me, I've done this several times over the last few weeks). It told me to run sudo apt-get install -f. That seems to have fixed the update manager and I am now running a partial update, as suggested, to see if that will resolve the issue. If it does, I'll mark this one as closed.

---

