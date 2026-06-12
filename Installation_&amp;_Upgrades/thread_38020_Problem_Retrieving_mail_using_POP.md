---
title: "Problem Retrieving mail using POP"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by jones139 on 2005-05-29
I have recently upgraded my HP Compaq nx9005 from Slackware 10 to Ubuntu 5.04, mostly because I wanted a newer kernel to make the battery monitor etc. work correctly.  It all seems to work fine except for email....
  
When I try to check for messages on my ISP's mail server using POP (via thunderbird, but I get the same result with kmail), the mail client just waits with a 'connecting to xxx' message.  Eventually the message disappears, but there is no 'no new messages' displayed as would be expected if everything had worked.   It is a bit unpredicatable - connections to some ISPs mail servers seem better than others.  This at first appears to be a problem with the ISPs, but if I use my other computer, which is still running Slackware, mail works fine.  I am confident that it is not the settings within thunderbird because I use a shared home directory on both computers, so the thunderbird configuration (and executable for that matter) is the same on both systems.  At the moment I am running thunderbird remotely on my desktop machine and displaying it on the laptop as a workaround, but would like to make the laptop work too.

I am a bit out of ideas - I thought it might be a DNS problem, but I can ping and telnet into the mail servers ok.  I also thought it might be a firewall on the kubuntu system, but as far as I can tell iptables does not have any rules set, so I do not think it is that.  I suspect that this might not be a ubuntu problem because I have tried Fedora Core 3, and had the same problem - is it something to do with the 2.6.x kernel?   With fedora I had another problem which was that access to normal web sites worked but secure ones did not.  I have not noticed this with ubuntu.  

Any suggestions would be appreciated, because I have ran out of ideas and am starting to think I will have to go back to Slackware and build the new kernel and KDE from source myself - I thought changing to ubuntu was the easy way out for me!

Cheers


Graham.

---

