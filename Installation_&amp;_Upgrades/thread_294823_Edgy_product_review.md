---
title: "Edgy product review"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by ykanello on 2006-11-07
I have been using Ubuntu dapper a year now on three different systems, and since 2 weeks ago, I upgraded to Edgy.

Since I haven't seen an article like that, I would like to put my 2cents, on what I have seen so far, and I like, and things i didn't. 
The three systems. I am running ubuntu on an Intel P4 desktop system by NEC, a laptop by HP, and a custom system with AMD opteron 150. 
The first two have the desktop installation, and the amd has the server istallation. 
[LIST=1]
[*]Installation
I did one installation and two upgrades. The installation was finished in 30 mins on a laptop (amazing!) and there were no issues. 
The upgrades went somewhat ok, the desktop had no issues, but the server needed attention. The server failed to reboot. 
The new UUID in the grub conf file, really screwed things up. I use software raid, the system has 4 md groups, and the grub menu was completely useless. I had to fix all UUID's, since the dpkg-reconfigure script didn't check for md.
[*]Operation
Once in the new Ubuntu UI, all seemed new, nice, X looking much better. 
[LIST]
[*]Problem with fglrx
I am not the first one, nor the last, from what it seems like it, but there is great deal of confusion and things don't work out of the box for the 3d acceleration at least on ATI cards. The Intel i810 worked at once. 
[*]wifi
I have a problem with the wifi on the laptop that doesn't scroll all available networks anymore. I haven't fixed this issue yet, but its something, that out of the box, and with a little tuning is not fixed. 
I understand that nothing can be perfect, but... the software exists, just didn't quite worked :)
[/LIST]
These were my only problems with edgy. Everything else works fine and most important out of the box -- remember slack 1.0? hehehehe
so far so great :)
[*]Future
What I would really like to see in the future, is maybe a more 'advanced' option on configurations, and installations. A flag file can mention if we need novice or not installations, dpkg-configurations etc. 
Its great that you just do a dpkg-reconfigure apache2 to setup your web server, but in some cases i run into, I really needed to edit my conf files, and the dpkg-reconfigure would change them back to the defaults. I would prefer an 'advanced' option somewhere, so I can configure the software by myself.:-# 
[/LIST]
To recap I think the Ubuntu community did a fantastic job with Edgy, and I really hope to see U on every computer i put my eyes on :)

---

### Post by Freddy on 2006-11-07
If only Cedega would work, atleast with some games.   /// Freddan

ohhh need a better direct connect client to :-).

---

