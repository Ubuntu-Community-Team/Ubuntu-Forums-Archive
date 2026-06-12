---
title: "xterm display problem"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by spiritflare on 2007-03-14
Heya

I'm trying to display the Xterm from my redhat server onto my Ubuntu desktop.. it works to my PC running Exceed, but not to the Ubuntu. On the redhat server, i have:

setenv DISPLAY x.x.x.x:0.0
export DISPLAY
xhost +
xterm &

This display perfectly to my Windows IP running Exceed. When I change the IP to my Ubuntu desktop, I get this message:

"Warning: Tried to connect to session manager, Authentication Rejected,
reason : None of the authentication protocols specified are supported
and host-based authentication failed"

I typed "xhost +" on my Ubuntu, and I also tried to put the hostname of the Redhat server in my .rhosts file - neither helps.

Not sure what I am missing... any advice would be appreciated

tx

~k

---

