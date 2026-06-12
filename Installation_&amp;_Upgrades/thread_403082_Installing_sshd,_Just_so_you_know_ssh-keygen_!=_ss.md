---
title: "Installing sshd, Just so you know: ssh-keygen != ssh-keygen2"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by brink on 2007-04-06
I'm posting this because I see a lot of sshd config problem posts but none of them discuss my particular issue, which I just figured out after several months of searching.

System is a 6.10 upgrade from 6.06. This may or may not be relevant.

One can apt-get install ssh and openssh-server, however the key generation always fails. Displaying the details in synaptic (or from the command line) tell you that "-f" is an illegal option.

I could not figure this out -- apparently (I assumed) my version of keygen was newer/older. 

Finally I did the following:
> 
root@box-jonw:/etc/ssh# locate ssh-keygen
/usr/bin/ssh-keygen
/usr/local/bin/ssh-keygen2
/usr/local/bin/ssh-keygen

root@box-jonw:/etc/ssh# ls -l /usr/bin/ssh-keygen 
-rwxr-xr-x 1 root root 105752 2006-10-05 05:44 /usr/bin/ssh-keygen
root@box-jonw:/etc/ssh# ls -l /usr/local/bin/ssh-keygen
lrwxrwxrwx 1 root root 11 2006-07-21 11:09 /usr/local/bin/ssh-keygen -> ssh-keygen2


Guess which one is executed when ou call just 'ssh-keygen'

So, if you have isues with 'cannot load key' or 'illegal option -f' when generating keys, check to make sure that you're running the one that is not a symbolic link to ssh-keygen2 -- it's not the same thing.

TIA

(as first posts go, I hope this is helpful (and coherent))

---

### Post by Sir_Brizz on 2008-07-04
I know this thread is over a year old, but I just dealt with EXACTLY the same problem on one of my servers. I had to change the symbolic link of /usr/local/bin/ssh-keygen from ssh-keygen2 (doesn't work) to /usr/bin/ssh-keygen (works). Otherwise reinstalling openssh-server in any manner would not regenerate the host keys like it should.

---

