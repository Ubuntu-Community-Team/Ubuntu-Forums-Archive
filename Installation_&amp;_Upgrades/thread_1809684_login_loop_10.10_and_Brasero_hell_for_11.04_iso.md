---
title: "login loop 10.10 and Brasero hell for 11.04 iso"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by Clive McCarthy on 2011-07-21
It's my own damned fault. I figured it was time to update the OS (9.04) on my music server which was working just fine. It's a VERY old Sempron based board with VIA Unichrome integrated graphics. I took my "standard" 10.10 CD and installed it and added all the 300MB of updates. 

I then got the login loop problem (get the login screen -- enter password -- screen flashes -- back to login) that others have experienced with apparently no 'clean' resolution. I hit <Ctrl><Alt> F1 and the screen is garbage -- so no console.

So I figure it _might_ be time to try 11.04 -- I go to another machine to burn a DVD iso image. Damn, Brasero doesn't work. I get the infinite checksum calculation saga.

I have just traded one problem for another. ](*,)

So I'm looking for a clean solution to the 10.10 login loop problem or some kind of assurance that 11.04 _doesn't_ have this problem? There was this bug reported: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/311051]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/311051")
Is there any way of knowing that this regression from 9.04 to 10.10 has been fixed in 11.04?

If I have to burn an 11.04 disk I'll flip back to Windows and get it done there. Brasero is inadequate.

The plot thickens: I re-installed 9.04 and things were back to normal. I installed 10.04 alongside and things were still good when I ran 10.04. I then updated 10.04 and the "login-loop" returns. Something is bad in the update.

---

