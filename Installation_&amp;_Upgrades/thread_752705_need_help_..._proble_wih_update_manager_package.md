---
title: "need help ... proble wih update manager package"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by james_bandido on 2008-04-11
need help please, i got this on my system, and i cant even run update manager or even synaptic package manager ... 

[B]
[B]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]
[/B]

---

### Post by Pumalite on 2008-04-11
Post the output of:
sudo dpkg --configure -a

---

### Post by james_bandido on 2008-04-11
here is the output 

[b]
james@bandido-laptop:~$ sudo dpkg --configure -a
[sudo] password for james:
james@bandido-laptop:~$ 
[/b]

nothing came out .... :(

---

### Post by warp99 on 2008-04-11
> **james_bandido said:**
> need help please, i got this on my system, and i cant even run update manager or even synaptic package manager ... 

[B]
[B]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]
[/B]

Your error is about this packages list::

[http://ppa.launchpad.net/awn-testing/ubuntu/dists/gutsy/main/binary-i386/](http://ppa.launchpad.net/awn-testing/ubuntu/dists/gutsy/main/binary-i386/)

You can remove the file '/var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages' and then 'sudo apt-get update' and the file will be recreated with the correct package information. If you still get the same error then the package information at the repository is bad and needs to be corrected.

---

### Post by james_bandido on 2008-04-12
**Pumalite** & **warp99**,  thank you veru much ... 

i removed all existence of the ppa.launchpad.net files in the var/lib/apt/lists folder ... 

afterwards, i performed a system update through the System-Administration menu, and it worked just fine now ... 

thank you very much, you've been both of great help ... 

cheers !!!

---

### Post by levelnext on 2008-04-12
I am getting the same error, i guess the AWN package is corrupted or something, cause I understand that if i take the AWN out of my selected repositories then it will work, but i still want the AWN to update regularly.

error:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


So i guess i will wait for the file to be corrected.


Or shouldnt i?

EDIT:   OK i erased the AWN list file and then did the sudo apt-get update =   the file is back where it should be and now i can update succesfully!!!

THANKYOU VERY MUCH

---

### Post by warp99 on 2008-04-12
> **levelnext said:**
> I am getting the same error, i guess the AWN package is corrupted or something, cause I understand that if i take the AWN out of my selected repositories then it will work, but i still want the AWN to update regularly.

error:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


So i guess i will wait for the file to be corrected.


Or shouldnt i?

EDIT:   OK i erased the AWN list file and then did the sudo apt-get update =   the file is back where it should be and now i can update succesfully!!!

THANKYOU VERY MUCH

That happens every once in a while. I Just read another post complaining about the the same repository. Best thing in the future if any repos give you an error like that is to just comment out the line your /etc/apt/sources.list, then check them later by uncommenting them and running apt-get update. It does the same thing as deleting the file from the /var/lib/apt/lists/. 

In Linux there's like 20 different ways to come up with the same result. :lolflag:

---

### Post by Pumalite on 2008-04-12
[QUOTE=levelnext;4701633]I am getting the same error, i guess the AWN package is corrupted or something, cause I understand that if i take the AWN out of my selected repositories then it will work, but i still want the AWN to update regularly.

error:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


So i guess i will wait for the file to be corrected.


Or shouldnt i?

EDIT:   OK i erased the AWN list file and then did the sudo apt-get update =   the file is back where it should be and now i can update succesfully!!!

THANKYOU VERY MUCH[/QUOTE
. Good luck.

---

