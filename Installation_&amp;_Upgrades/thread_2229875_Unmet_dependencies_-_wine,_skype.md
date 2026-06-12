---
title: "Unmet dependencies - wine, skype"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by omegacrown on 2014-06-15
Hello,

I'm having a lot of trouble installing wine and skype. I have searched a lot of forums and tried everything I could, all to no avail. Any suggestions?
Ubuntu 13.10

----------------------------------------------------------------------------------------------------
$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
----------------------------------------------------------------------------------------------------
$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

---

### Post by mörgæs on 2014-06-16
I don't think it's worth the effort to troubleshoot 13.10, as it has only a month of support left. You need to install 14.04 soon, why not today?

---

### Post by LastDino on 2014-06-16
13.10 is going to run out of its life in few days, so I would +1 to what morgaes said.

Go for 14.04 LTS version if you like to keep it around for long.

---

### Post by omegacrown on 2014-06-19
Thanks for the responses. I upgraded to 14.04 LTS and was able to install skype and wine successfully.

---

