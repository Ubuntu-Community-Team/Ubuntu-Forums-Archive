---
title: "User rights problem? (.dmrc and synaptic)"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Ceased2Be on 2008-02-15
Hi there, 

First of all, I'm fairly new to the whole Linux-thing... last week I installed Ubuntu 7.10 on my new T61 for work and all's been running fairly well. 
Except just this morning I got a message while logging in stating I didn't have '644'  rights on the $home/.dmrc file? Don't know the message exactly but that was the gist of it.
And trying to start up synaptic to get a package I got the following message:

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

I'm beginning to suspect there's something wrong in the user-rights for my primary user but I don't know how to fix it (except for just a complete reinstall of the system) which seems a bit too much :)

Thanks for the help

mark

---

### Post by hyperair on 2008-02-15
Sounds to me like you screwed up your root account. The Home directory for root is supposed to be /root. Not /home/root. O_o

To fix it, go to System->Administration->Users and Groups. Click on the user "root, and  click on Properties. On the "Advanced" tab, change Home Directory to /root.

---

### Post by Ceased2Be on 2008-02-15
Thanks! Changing the root home solved my synaptic problem. 
Still have the .dmrc error though... but I think I can figure that one out myself now...

Mark

---

### Post by hyperair on 2008-02-15
Glad to hear it worked. Could you post the fix you have in mind for .dmrc when you're done? Perhaps it can help somebody searching for a fix for this error in the future.

Either way I tihnk changing the permission of .dmrc to 0644 will work. ```
chmod 0644 ~/.dmrc
``` or you can do it in Nautilus.

---

