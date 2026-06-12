---
title: "preseed and default profile"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by smadon on 2008-01-31
Hi,

I am doing an automatic installation of Ubuntu 7.10 with PXE and preseed option.

It working fine, but I would like to change the parameter for the default user.
I check the configuration with gconf-editor, and I think all the parameter are save in .profile or in /etc/skel 
But I don't know how to add it during the installation process in the preseed file. :confused: ? 


Then another question I would like to run a script (add the workstation on the AD) 
I think it need to be here : d-i preseed/late_command string
but not sure how I can do it? Can I do a wget d-i preseed/late_command string [http://myserver/myfile.sh](http://myserver/myfile.sh) usr/local\ | ./usr/local/myfile.sh ?


Thanks for your reply. :)

---

### Post by smadon on 2008-01-31
Oh, and I forget I use apt-proxy to speed up the network installation :-)

---

