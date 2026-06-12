---
title: "[SOLVED] Can't login... Authentication failed"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by mr_john_simone@yahoo.com on 2008-03-28
Well I messed it up good today.   I'm new to linux, and I thought it would be a good learning experience to activate  compiz and try out some of the beryl type window effects. 

On restart, my box came up with the xfe login (not the gnome login that usually comes up).  A popup message window came up in front of the login textbox that prompted "Authentication Failed"  Clicking OK does not clear the box, so I can't get rid of the popup to get to the login prompt.  Clicking restart in the lower left doesn't work either because the message box has sole focus.  I can cntl-alt-F8 to a console and startx as root but not as myself.  

Any ideas on what I can do now to fix this?  Command-line instructions will need to be detailed because I just started using Ubuntu.  I hate the thought of re-installing because it took me a while to get all the peripherals working on my laptop.  Getting them to work again will be painful.

For now I am stuck typing this from a live-cd session.

Thanks,

John.

---

### Post by mr_john_simone@yahoo.com on 2008-03-29
I did some searching and have solved the problem.

For anyone else who might have this problem, here is what I did:

Booted from a live CD and launched a terminal session.

then became root by 

sudo su   .....................followed by password
gedit  ...................... to launch a text editor as root
file - open - /media........  /etc/pam.d/gdm

found the line:  @include common-pamkeyring  and commented it out
##@include common-pamkeyring

saved and restarted.

John Simone

---

