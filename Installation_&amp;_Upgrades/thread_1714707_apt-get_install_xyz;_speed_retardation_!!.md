---
title: "apt-get install xyz; speed retardation !!"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by Harsh Kumar Narula on 2011-03-25
Dear friends,

I have noticed several times that during the 'apt-get install xyz',specially if the size of xyz is big, downloading generally starts with a good speed but continuously or abruptly sometimes drops to the order of bites/second and takes a lot of time to speed up again; most of the times never gets the good downloading speed as it was in the starting.

So i stop the downloading in between by ctrl+C and again do "apt-get install xyz" and get an excellent downloading speed again.

I keep on doing this very frequently during the process.(size of xyz is large, point to be noted; say xyz = texlive-full ~ 500 MB or so).

I don't know if anyone else has experienced this. But I hope I am not alone.

may be we can make a shell script for the 'ctrl+C' and 'apt-get...' task during the downloading if speed is below predefined certain limit.

I have tried apt-fast and apt-proz as well. But apt-fast was not up to the mark and apt-proz produced corrupted downloading and hence errors.

I expect some good suggestion/solution/alternatives/views.

I hope I do make sense. Sorry for my poor English.

--------------
Harsh

---

