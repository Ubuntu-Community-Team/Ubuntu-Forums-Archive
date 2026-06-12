---
title: "help me build LTSP client"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by benner on 2007-02-14
i followed this set of instructions
[http://ubuntuforums.org/showthread.php?t=195956](http://ubuntuforums.org/showthread.php?t=195956)

and got as far as the build client command, the thing downloads, updates and installs a million and one things for about half and hour, gets to 99% and in the final 5 seconds gives me this error:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-5ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-5ubuntu1_i386.deb)  Error reading from server. Remote end closed connection [IP: 91.189.89.182 80]

i have edubuntu installed, downloaded edubuntu-server, and all the server stuff (ltsp-server-standalone) and i can't get this thing going.  i have a classroom full of students waiting for me to get their computer lab set up with thin clients and am trying to teach myself as quickly as i can.  it is really frustrating.  please help.  i have read every posting i could find about installing and setting up ltsp but nothing has gotten me too far.  

i am running edgy.  i have 2 network cards.  i have a switch with one client ready.  when it boots from LAN it does get an ip address assigned but then it hangs.  i guess it is waiting for an OS to come from someplace and i assume that i need the client kernel built inside the server to be passed along.  it really is a lot i am trying to learn very quickly.  i would appreciate any guidance.

---

### Post by Serpicozaure on 2007-02-16
Hi benner,

I don't know that much about LTSP but i'm working on it right now, i have  one thin client and my server , after different attempts my client seems running or at least boot , i can log-in and can see the same desktop than in my server on my client screen, then i can try to help you 

can u explain more precisely what you did ?

i used this [http://developer.novell.com/wiki/index.php/Edgy/HOWTO:_Install_MueKow_on_Ubuntu](http://developer.novell.com/wiki/index.php/Edgy/HOWTO:_Install_MueKow_on_Ubuntu)
to build and set my configuration + some advices from [www.LTSP.org](www.LTSP.org)

in the first link they said " If this process ends prematurely because all the packages cannot be downloaded delete the entire LTSP directory and restart. (Ensure debootstrap >= 0.3.3.0ubuntu7). "

tell me more if you want

Read you soon

Serpico

---

