---
title: "lens remove shopping, no sending personal data"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by b00n on 2014-01-13
I am installing 13.10 and trying to remove all shopping features.  More generally I would like to write a script I can run on every install to

 * disable/remove shopping features
 * stop sending data
 * disable external access

I do not understand the whole schema of things involved, so I'm a little lost about how to proceed.

As a start, I understand I can go to [FONT=courier new]System Settings > Security and Privacy > Search > include online search results > Off[/FONT].

I'd like to script that, so I do not have to type it every time after an install, instead I want to write a script I can copy to any fresh install, run it, and it just happens.

(Basically, I want to write one script with a bunch of setups stuff like this, this would be just one entry in the script.)

More generally, there's a bunch of things I want to disable, but I'm not even clear how to find them all.  For example, l did the above then went to install [FONT=courier new]dconf Editor[/FONT] from [FONT=courier new]Ubuntu Software Center[/FONT] and got many listings for payware.  I don't hate shopping, but I'd like to never see payware listings here and I do not understand how to turn them off.  (In general I don't even want to see random web-wide freeware here.  I'd like to see stuff in a standard Linux repo.)

Also, using dconf editor I see [FONT=courier new]com > canonical > unity > webapps > "preauthroized-domains ['amazon.ca', 'amazon.cn', 'amazon.com', 'amazon.co.uk', ...]"[/FONT] a list that goes on quite a way.  I don't know why I am authorizing them, but I am sure I do not want to preauthorize sending or receiving data from them.  (In general, even "receiving" is a problem, aside from privacy issues, because I may be on a slow link or a pay-per-byte link.)  I want to know about Ubuntu updates, but I certainly do not want to waste pennies on stuff I was not going to use anyway.

And while I can click on [FONT=courier new]com > canonical > unity >  webapps > integration-allowed[/FONT] to turn it off (I think), I do not understand either (a) how to purge anything that already got hoovered up, nor (b) how to make a script so that every time I do a clean install I just run the script to turn it off.

Also, in the launcher there's an icon for Amazon.  I searched for what it might be -- and what I could [FONT=courier new]sudo apt-get remove[/FONT] so I can script it away -- but I do not find it.  Any hints?

---

### Post by tgalati4 on 2014-01-13
[http://www.linuxmint.com/](http://www.linuxmint.com/)

---

### Post by craig10x on 2014-01-14
In the privacy settings, you can simply turn off all online searches by hitting the off button...that is the easiest way to do it...then all you will get in the dash search is apps, files, and other stuff that is on your computer...it only takes about 5 seconds to do it, so why go to all those lengths?

---

