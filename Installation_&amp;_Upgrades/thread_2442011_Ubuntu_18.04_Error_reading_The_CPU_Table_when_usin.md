---
title: "Ubuntu 18.04 Error reading The CPU Table when using apt or apt-get."
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by reidmuchow on 2020-04-28
Hello everyone,

I am new to Ubuntu and I recently installed Ubuntu 18.04 on a Hostinger VPS account.  I can't remember exactly what I was doing that caused this but I was able to use apt commands like(apt-get, sudo apt-get and apt) but now I cannot use them at all and there are 2 errors that they throw:

1)E: Error Reading the Cpu Table 
2) -hash: apt-get: command not found

So the backstory is that last week I initially set up a VPS with Hostinger and I ran into the same issue.  It stated throwing the same errors as I listed above when using the same commands after I had installed everything and was able to execute apt commands.  Like I said up above, I can't remember what I was doing (I'm a server newb) but I was making some changes and then all of the sudden I could not use any apt commands to make installations.  I was frustrated so I canceled the VPS server concluding that I was not fit to set up a server yet.  After thinking about it I wanted another go and I thought starting fresh with a new IP and VPS that the apt commands would no longer be an issue but straight out of the box I tired to run apt update and apt-get update but it threw out the exact errors.  I'm not sure why this would happen again?  

Judging from other forum posts on here and sources on google I checked out, I think it may have to do with the file structure of the folders in my server or I need to reinstall some specific packages?  I just don't know where to locate them in the server.  All the solutions say that I need to use sudo apt-get update or apt get but those are not working since it's not letting me use those commands as a root user in my VPS ssh terminal.   I definitely need help with this and I've tried for several days to find a solution and it's the 2nd VPS server in 2 weeks that I have tried to get to work.  Can anyone offer me some solutions or suggestions?  Here is some screen shots below of the errors thrown while trying to run apt commands.
[ATTACH=CONFIG]285652[/ATTACH][ATTACH=CONFIG]285654[/ATTACH][ATTACH=CONFIG]285653[/ATTACH]

---

