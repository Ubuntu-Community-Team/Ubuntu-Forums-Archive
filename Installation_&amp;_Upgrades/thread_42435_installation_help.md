---
title: "installation help"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by lukus001 on 2005-06-17
I've just installed unbuntu today...

I'm trying to install things such as java and other programs, i've followed numerios topic here saying how to do it... but in the terminal all i get is "no such file or directory" even for:
sudo -s -H 
and then my password... which is suposed to stop me from having to re-type my password... why would i even need a file /directory? :s

help me please =)

---

### Post by trivialpackets on 2005-06-17
[QUOTE=lukus001]I've just installed unbuntu today...

I'm trying to install things such as java and other programs, i've followed numerios topic here saying how to do it... but in the terminal all i get is "no such file or directory" even for:
sudo -s -H 
and then my password... which is suposed to stop me from having to re-type my password... why would i even need a file /directory? :s

help me please =)[/QUOTE]
 [www.ubuntuguide.org](www.ubuntuguide.org)

Go to this site, it's a great site that gives more info than you'll likely need.  Make sure you activate repositories, and go to town.  The site gets your system up and going in a hurry.  Have fun.

---

### Post by trivialpackets on 2005-06-17
[QUOTE=lukus001]I've just installed unbuntu today...

I'm trying to install things such as java and other programs, i've followed numerios topic here saying how to do it... but in the terminal all i get is "no such file or directory" even for:
sudo -s -H 
and then my password... which is suposed to stop me from having to re-type my password... why would i even need a file /directory? :s

help me please =)[/QUOTE]
 Oh, and forget about the sudo -s -H.  It may work, but just as easy, but less secure to open the root terminal in your programs.

---

### Post by lukus001 on 2005-06-17
got the -s -h thingy working now... ive spent that last like 30 hours trying to install java...

can somone help me? i've got to the point where i've actually got java installed and i get a response from "java -version" but it doesn't work in firefox, how do i rig it with firefox?

and if i download a program, what sort of linux build do i download, all i usally see is name like PPC, i356 etc... and after i downloaded them and there on my desktop how do i install them? thanks=)

---

### Post by trivialpackets on 2005-06-17
[QUOTE=lukus001]got the -s -h thingy working now... ive spent that last like 30 hours trying to install java...

can somone help me? i've got to the point where i've actually got java installed and i get a response from "java -version" but it doesn't work in firefox, how do i rig it with firefox?

and if i download a program, what sort of linux build do i download, all i usally see is name like PPC, i356 etc... and after i downloaded them and there on my desktop how do i install them? thanks=)[/QUOTE]
 if you have a deb file... it's dpkg -i filename.deb in the directory that the file is located.  As to your first question, I still say, check out [www.ubuntuguide.org](www.ubuntuguide.org).  Check it out, lots of information there, and the majority of programs that you are going to be wanting, are available very easily by setting up the extra repositories as is shown on the above site, and using either apt or synaptic.  Your best luck with software will come from the repositories as per the above site again.  I'm not kidding... check it out!  :)

---

### Post by trivialpackets on 2005-06-17
[QUOTE=eric.proctor]if you have a deb file... it's dpkg -i filename.deb in the directory that the file is located.  As to your first question, I still say, check out [www.ubuntuguide.org](www.ubuntuguide.org).  Check it out, lots of information there, and the majority of programs that you are going to be wanting, are available very easily by setting up the extra repositories as is shown on the above site, and using either apt or synaptic.  Your best luck with software will come from the repositories as per the above site again.  I'm not kidding... check it out!  :)[/QUOTE]
 update 
sudo gedit /etc/apt/sources.list   (as per [www.ubuntuguide.org](www.ubuntuguide.org))

sudo apt-get update

sudo synaptic or open in repos.  

Alternatively, to search, 

apt-cache search filetosearchfor

to install via command
apt-get install filenamefoundthroughsearchabove

---

### Post by lukus001 on 2005-06-17
been through that.. the repositories from ubuntuguide.org 

but... i get errors whilst updating it specifically in the java area so i can't install it.   i've got java installed by an alternative place on the wiki.ubuntulinux.org/java (off my head.. might be a different ubuntu domain)... that was supose to work "out of the box" (first few didnt even work like ubuntuguide) and i guess it does but its not a plug in for firefox yet?

---

