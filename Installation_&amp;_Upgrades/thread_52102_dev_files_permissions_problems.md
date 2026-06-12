---
title: "/dev files permissions problems"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by wgscott on 2005-07-26
I seem to run into different manifestations of the same problem on a daily basis.

For some reason when logged in as a user other than the original admin user, /dev files cause failures that can be corrected by changing file permissions.

For example, today I tried to use the unix program "screen" and got an error about /dev/pts/0

Changing the permissions like this solved the problem:

 sudo chmod 666 /dev/pts/0
 
Similarly for /dev/pts/1

I've also had this same sort of problem with the nvidia dev files, again, resetting the permissions as superuser fixed it.

Upon reboot the problem returns (as the permissions seem to get reset).


Is anyone else having problems such as these?

I created all the new users with 

sudo adduser <username> 

FWIW.
  ](*,)

---

### Post by Xian on 2005-07-26
Make sure the user(s) is in the audio, video and cdrom group.

---

