---
title: "No to LMB package integration into Jaunty"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eeried on 2009-02-27
Hello,

I've had a look at launchpad but I can't find what I'm looking for: a page where I can see if a package is registered for integration.

I tried to test LMB (Lundi Matin Business),a new software under the GNU AFFERO GENERAL PUBLIC LICENSE that's being developed in my area by a former computer shop owner who hasn't a pristine reputation.

If you can read French, have a look at:

 [LIST=1]
[*]LMB website: [http://www.lundimatin.fr/](http://www.lundimatin.fr/)
[*]LMB forum:[http://www.lundimatin.fr/site/forum/index.php](http://www.lundimatin.fr/site/forum/index.php)
[/LIST]

The piece of software is very useful as it seems to do a simpler job than OpenERP in a much simpler way and seems to be able do the job for shops and small-scale business. It's free as free beer too.

The problem is the software installs on a server like Apache or Wamp or Mamp and the developing team knows nothing about Linux/Unix. They would be unable to advise anyone wanting to buy Ubuntu-compatible hardware such as a small bar-code tag printer or a till plugged on the computer.

I can't install the software because I don't agree with the way it wants to install. According to Ubuntu users:

[LIST=1]
[*]it requires 777 on /var/wwww (not just on /var/www/lmb)

[*]the install file connects to LMB servers and retrieves your LMB version number, and what else??
[/LIST]

Now someone has made a package for LMB and the boss of LMB wants it to be integrated into Ubuntu Jaunty.

I don't think this is acceptable at all if you consider the software was first released only last July and is only in French and only applicable for French accountacy, for the moment at least.

I personally know a shop-owner who first accepted to fill in some forms for a training session with the LMB people but she wasn't given a copy of the presumed contract and they sent the application forms to the wrong organisation. The phone numbers written in the LMB flyers are wrong and the shop-owner had to send LMB a fax saying due to unexpected circumstances she had to cancell the training (she may have to give up buying computers for her shop, and so won't need any piece of software. LMB boss phoned back and demanded a full explanation and she wouldn't give any, saying it was none of his business. He said that she owned him a 90&#8364; fee (for sending a couple of forms to the wrong organisation, no doubt a justified fee).

Even if it doesn't matter much if the team of a piece of software are good or bad people if the software can be used freely, LMB isn't transparent about their software: on the website there is no mention of the current version number, nor of system requirement, no intruction how to install. On the forum users get very little help.

For those who read French this thread is rather revealing of the LMB boss's attitude: [http://www.lundimatin.fr/site/forum/viewtopic.php?f=5&t=330](http://www.lundimatin.fr/site/forum/viewtopic.php?f=5&t=330)

To install LMB I would need some help with the PHP code in the install file in order to disable any connection to the LMB*server and to be able to install the software off line entirely.

Cheers,

---

