---
title: "How much additional disk space needed? --&gt; WIKI"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by glotz on 2006-06-01
Howdy! It's Dappertime! =P~

Tried to install dapper (on command line by changing breezys to dappers sources and inputting the apt command.) It failed however and told me that I need 295 megs additional disk space. I had some 150 megs available at the time. So I guess that ubuntu breezy > ubuntu dapper needs some 450 megs additional disk space. Is that correct? (I guess it depends on... *something*)

Would it be smart to mention this is the installation wiki? (should the note to close running programs too be added there?)

Thanksies.

ps. I guess it's time to ditch my windows 2000 installation. It's a tiny 6,5 gig disk and the windows partition takes more than half of it... And I don't use it for anything anymore anyways. I did a bad estimation back then partitioning my disk for the two OSes. Time to correct that mistake... :twisted:

---

### Post by Video Toaster on 2006-06-01
[QUOTE=glotz]Howdy! It's Dappertime! =P~

Tried to install dapper (on command line by changing breezys to dappers sources and inputting the apt command.) It failed however and told me that I need 295 megs additional disk space. I had some 150 megs available at the time. So I guess that ubuntu breezy > ubuntu dapper needs some 450 megs additional disk space. Is that correct? (I guess it depends on... *something*)

Would it be smart to mention this is the installation wiki? (should the note to close running programs too be added there?)

Thanksies.

ps. I guess it's time to ditch my windows 2000 installation. It's a tiny 6,5 gig disk and the windows partition takes more than half of it... And I don't use it for anything anymore anyways. I did a bad estimation back then partitioning my disk for the two OSes. Time to correct that mistake... :twisted:[/QUOTE]
Have you tried clearing out your old package cache and removing old kernels?  In a terminal window, type "sudo apt-get clean".  Also, in Synaptic, look for old linux-image packages (versions older than the one you're currently using) and purge them.  That freed up 1.25 GB on my machine... :D

EDIT:  Fixed a mistype...

---

### Post by johnc4510 on 2006-06-01
Good ideas VToaster, and here's a question. 
Is sudo apt-get clean the same as sudo apt-cache clean?

---

### Post by Video Toaster on 2006-06-01
[QUOTE=johnc4510]Good ideas VToaster, and here's a question. 
Is sudo apt-get clean the same as sudo apt-cache clean?[/QUOTE]
Oops... mangled the thoughts in my head and screwed up the command.  It is in fact "apt-get clean".  Sorry...

---

### Post by glotz on 2006-06-01
Hi Video Toaster! Thank you for your suggestions. Since I'm so starved for diskspace, I've set synaptic (actually apt then I guess) to not store the packages but to delete them. I only seem to have one linux-image installed. Nice catch johnc4510!

May your skies be blue...

---

### Post by umayado on 2008-01-25
Good afternoon, 

I am trying to upgrade from edgy to gutsy, but get noticed that there is not enough disk space, even after cleaning, the free 575Mb i have do not seem to be enough... 
could anyone tell me how much the upgrade normally requires?
and when wanting to add kubuntu, what the minimum size would be to preserve when i have to repartition...

thanks in advance

have a nice day

by the way I have preserved an extra linux partition on installment, anyway i can use those extra gigs? or do all packages always have to be installed on the root partition?

---

