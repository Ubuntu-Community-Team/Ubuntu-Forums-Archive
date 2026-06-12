---
title: "problem with the first thing to do after installation"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by guru.palani on 2008-11-09
hi..
this is my first post. i was using ubuntu 7.04 for about a year now and have just installed intrepid. this is the first ever ubuntu installation i myself have done without my friends' help. i just have used the live cd to install intrepid in my harddrive. after restarting i connected to the net to see what other procedures i had to complete.i checked out this webpage

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

and have tried to do them. when i typed 

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

it gave an error like this..

--2008-11-10 03:06:32--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... failed: Connection refused.

the network connection is working fine and i am actually sending this post from the same laptop where i have just installed intrepid. 
can someone help me to find out what is wrong..?

thanks.
pal..!

---

### Post by guru.palani on 2008-11-09
And i just manually edited the medibuntu.list file. when i installed medibuntu-keyring, it tried to connect and says 

E: Couldn't find package medibuntu-keyring

i know somewhere i am making a mistake. i dont know what is that.
-pal.

---

### Post by bulldog on 2008-11-09
Take a look at this site,you can find here how to add the repositorie for medibuntu,and a whole lot more information.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by guru.palani on 2008-11-14
Hi all..
I now has got problems with installing vlc. When I did sudo apt-get install vlc, it said

""""
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.9.4-1ubuntu3) but it is not going to be installed
       Depends: libass1 but it is not installable
E: Broken packages
""""


Does this mean that the iitm repository that I use has a lower version or an incompatible one with intrepid? Or does it mean to some other problem?

-pal..!

---

