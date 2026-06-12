---
title: "ltsp client display mirrored"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by pjeitler on 2010-07-24
Hello,

long time user - first time poster...
Today I tried installing an LTSP server (10.04). I got it up and running ok (2 NIC) but I can't get past the mirroring issue. I found 1 post by googling, but it didn't tell me much.
Here is my issue:

I installed ltsp from the alternate CD. User 1 is the user created during installation. Once I logged in on my thin client, everything was mirrored. I disabled twin view on my server and saved the xorg.conf file. then I ran teh ltsp-update-image and the display was normal. I reenabled twin view on the server and it still worked on the client. Then I added two additional users on the server but logging in with their credentials on the server still cause a mirrored display. I read that removing compiz may help, but it didn't in my case.
I have messed with lts.conf files, but I don't think i should have to since it works with one user account.

Do you guys have any ideas what is causing this to be different for different users? I am at a loss. Your help is appreciated.

---

