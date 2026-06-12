---
title: "clonezilla - user configuration questions"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2011-12-29
Hello everyone, 

I never used clonezilla and don't know much about it, but I  really want to try it :p 

I would like to try to make an ubuntu image, which would be then deployed  to several computers. My questions is: does anyone know if clonezilla imaging removes  user specific configuration - or at least gives you a chance to change  it during the process (i.e, computer name, username, etc)? 

If not, after the image is deployed in all the client computers, is  there a "post installation" way to remove it so that each machine can be  given a unique computer name, username, etc?  

Many thanks in advance!  


linux.girl

---

### Post by howefield on 2011-12-29
I don't believe clonezilla will do what you want unless you start with an OEM installation to begin with.

---

### Post by linux.girl on 2011-12-29
Thanks!!! - do you have any suggestions then on how to make an ubuntu image which can then be deployed to several computers? 

Or cloning "ghost style" is the only way and the rest has to be done with post installation scripts?

Thanks a lot in advance, just beginning to delve in this "production imaging" world :popcorn:
Any imaging advice from sys admins will be highly appreciated!!!!

linux.girl

---

### Post by howefield on 2011-12-29
I would do an OEM install on one machine, setup as required, run sudo oem-config-prepare and then clone that to the other machines either individually or by multicast.

This would give you a machine that when the user logs on for the first time, they will be presented with a setup wizard with which can create their own user account ect.

Hopefully someone more experienced will offer something else. :-)

---

### Post by linux.girl on 2011-12-29
Thanks, that's an interesting suggestion - but for example, what would happen with the hostname, the user would also be asked to enter a new one?

I ask because the environment I use is a bit complicated to say the least, each computer has to authenticate with a windows domain using likewise-open - so unique hostnames here is of essence.

I wonder also if there are any experienced IT people here in the forum who had to deploy an ubuntu image...if they have any suggestions/tips that could be great!

Thanks again!

linux.girl

---

