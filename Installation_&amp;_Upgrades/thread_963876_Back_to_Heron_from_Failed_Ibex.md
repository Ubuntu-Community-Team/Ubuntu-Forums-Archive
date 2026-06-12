---
title: "Back to Heron from Failed Ibex?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by dfreedman on 2008-10-30
My upgrade to Ibex failed miserably--seemed fine through reboot up through log-in, then goes to a blank (not black) splash screen.  What's the best way to get back to Heron, preserving as many of my settings as possible?  Also, is there some sort of service I can sign up for where someone will come over to my house and jab me in the eye with a pencil whenever I think about upgrading any perfectly fine-working open-source software within a month of its roll-out?

---

### Post by jerrylamos on 2008-10-30
Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

---

### Post by dfreedman on 2008-10-30
Worked perfectly, thanks much.  I'll hold off on compiz via Synaptic.

---

### Post by DrthTater on 2008-11-01
Ok, I'm new to Linux. I installed Ubuntu 8.04 last week and everything was fine. Decided to upgrade to 8.10 and now my graphics maxx out at 800x600. 

Can you explain how to either roll back to 8.04 or how to boot to rescue mode?

---

### Post by DrthTater on 2008-11-01
OK, Hate to double post, but...

I figured out how to get into resue mode. I tried removing compiz following the steps mentioned. I am STILL unable to go to a higher resolution.

I am using a T42 laptop. 1.5 G ram. Not sure what graphics card.
model  #  2374-eh4

---

### Post by DrthTater on 2008-11-01
Bump?

---

### Post by dfreedman on 2008-11-02
Hello DT,

Being a newbie myself, I'm not only clueless about your problem, I'm pretty clueless about how things work in the forum, too.  But I'm wondering if you'd be more likely to get help with a new post, since it may be that this one isn't attracting any attention any more.

Good luck,
Dave

---

