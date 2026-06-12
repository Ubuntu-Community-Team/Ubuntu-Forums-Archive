---
title: "livecd as rescue CD"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2008-11-16
having fiddled with a remote machine  it now wont boot. 
Their wireless NIC is USB 
 Hardy Heron liveCD detects it at startup ( others dont) and we can configure it.

I want to use the liveCD  as a rescue CD - start it up , get them to manually configure the wireless  then start a reverse SSH tunnel ( ssh -R 24:localhost:22 myserver ) so i can connect to 'my' end of it 

but how do i mount /dev/sda2 . 
ihavnt got a user who has a password who can issue sudo commands

what i want to do is login 
mkdir /mnt/hd
mount /dev/sda /mnt/hd
cd /mnt/hd 

correct the stuff ive messed up and then log out 

so how do i do this from a liveCD ?

---

