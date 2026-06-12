---
title: "Remote Install"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Shin_Gouki2501 on 2007-06-18
Hello there!
I want to install ubuntu remotly(onto my sis PC), although i know this is not a supported method i found this: 
[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)
AS i read through i think this is just "partly" what i need.

The good thing is i don't need to do the install "complete" remotly.
My ideal scenario would look like :
I call my sister and she uses a "linux" boot cd , to boot up.
The boot CD setups:
*starts a SSH SERVER

and  I can resume the install then via shell on my side of the network.

Would that be possible?
Can it be done with the alternate install CD?( if not how then?)
Can i modify the alternate install CD todo so(or even the Live cd?!)?
Im really open to any suggestions :)
wbr Shin Gouki

---

### Post by Shin_Gouki2501 on 2007-06-21
Did i post in wrong forums?
is my Problemdescription inapropriate or confusing?

---

### Post by Shin_Gouki2501 on 2007-06-28
Hello i want to ask again if somebody is arround how has some suggestions regarding the "remote" install?
wbr Shin Gouki

---

### Post by louieb on 2007-06-28
Probably could be done, but I'm clueless as to how.  The link to the Debian how to looks complicated as a Rub Goldberg machine. Might try the Gentoo forum, those Gentoo folks are a lot geekier that the Ubuntu crowd.    I guess you could have a nice long talk with your sister as you walk her through a Ubuntu install. BTW: the psychocats site has a good tutorial on the Live CD installer. And the dual boot link has a walk through of the alternate install. (Links in signature). 
     
One problem trying to install Ubuntu via  ssh-server is that by default the distro only comes out of the box with the ssh-client. Your sister would have to install the ssh-server package.

---

### Post by Shin_Gouki2501 on 2007-07-04
Thx for ur reply!
Your sister would have to install the ssh-server package <-
I see would it be possible to customize the ubuntu alternate CD?

---

### Post by scxtt on 2007-07-04
what kinda of network setup does she have? - at the very least you'd need to be sure eth0 comes up when you boot the LiveCD and that you can access SSH/VNC {i.e. port forwarding} ... or that you can walk her through it ...

i see no reason why should couldn't install openssh-server and/or x11vnc (or use gnome's "remote desktop" (the icky vino)) to install off the LiveCD ...

---

### Post by Shin_Gouki2501 on 2007-07-04
thx again for reply! :O
1. she is only via wireless 
2. the Pc is running XP which is full of virus and other nice things..

So if i understand u right she would use the "Live/desktop isntall CD " , put it in and then i could connect to that PC?

Before i wanted to use the alternate install CD because i thought it is a bit more stable ?!

Can ur method also be done with alternate CD?

---

### Post by scxtt on 2007-07-04
if you're looking for the EASIEST method, save for really obscure hardware, i'd think the LiveCD will work better for you - esp. if you need to talk to her on the phone in order to coach her through getting internet to work -- which is really the dealbreaker in this case ... you need to find out what chipset her wireless uses and if it's supported "out of the box" - easiest way for that is for her to pop in a LiveCD and see if it works ...

once that's working, you'll have 3 things to do:

1. install openssh-server {if for nothing else, cause CLI rules!}
2. get a GUI session going {via "vino" (if ubuntu disk) or x11vnc (if kubuntu, xubuntu, etc.)
3. click on "Install" on the desktop and set up user(s), partitions, etc. ...

ports involved (if she's behind a router): 22 {ssh}, 5900 {vnc}

---

### Post by Shin_Gouki2501 on 2007-07-05
I think ur right concerning the wireless!
For the remote connection: on a local setup i did a try with winXP and xubuntu and a free NX server and it worked pretty nice. i hope i can get it to work with her same way ;)
I check it out at the weekend thx so far!

wbr Shin Gouki

---

