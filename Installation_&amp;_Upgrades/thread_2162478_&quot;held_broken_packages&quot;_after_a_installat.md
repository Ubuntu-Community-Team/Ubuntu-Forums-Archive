---
title: "&quot;held broken packages&quot; after a installation (not upgrade), Lubuntu 13.04"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by CaRoXo on 2013-07-14
Hi community.
I tried to find this topic anywhere, in french, spanish or english, and nothing... So, here I go...

I just come to install from zero Lubuntu 13.04. Im usung lubuntu since some years, but as my last upgrade was giving some problems, I just erase, formated, and installed from zero. (as well I did with the Voyager 13.04, kubuntu flavour, in another partition)

First thing after doing apt-get update, and apt-get upgrade, was trying to install pulseaudio, but didnt allow me. Becouse of broken packages. The same with Fslint.

So, I thought maybe there was any problem with installation (someone unplugged the netbook while installing, but I thought was finished)...

I re-installed... and same problem
I re - re installed, looking to format properly again in ext4, and everything.

Same problem..

checksum with md5 its ok

Ah, another thing, I tryed to install Fslint in my Live-usb before installation, and was ok, it worked...

Now in my netbook, no... (eepc 1005 HA i think it is)

I copy paste the terminal:

$sudo apt-get install fslint

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 fslint : Depends: python-glade2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
 
____________________

I cant re-install this package, becouse of same problem but with another dependencies.


What could be the problem? and wich the solution.?

Im very begginer, so not able to understand very technical advanced answers..

Thanx beforehand...

Caroxo

---

### Post by Snowhog on 2013-07-14
Instead of using **sudo apt-get upgrade**, use **sudo apt-get dist-upgrade**. Then try installing fslint.

---

### Post by CaRoXo on 2013-07-14
Thanx Snowhog
I did it.
Had installed with this order some "headers' and image packages.
Trying to install fslint, have exactly the same answer.
trying with pulseaudio, I have

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 pulseaudio : Depends: libfftw3-single3 but it is not going to be installed
              Depends: libpulse0 (= 1:3.0-0ubuntu4b2) but 1:3.0-0ubuntu6 is to be installed
              Recommends: pulseaudio-module-x11 but it is not going to be installed
              Recommends: gstreamer0.10-pulseaudio but it is not going to be installed
              Recommends: rtkit but it is not going to be installed
              Recommends: pulseaudio-utils but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
_______________________________________

I have succesfully installed firefox and thunderbird (before this dist-upgrade)

So...

what else can I do? and why could happen this after a clean installation? and it seems that there is not soooo much people having the same.

thnx

---

### Post by CaRoXo on 2013-07-15
Ok, even if there is no answer giving solution, someone can explain me what are "held broken packages", how they stay in mode "held" and why could be them broken?...

Just trying to understand...

thanks.

---

### Post by CaRoXo on 2013-07-15
Ok, even if there is no answer giving solution, someone can explain me what are "held broken packages", how they stay in mode "held" and why could be them broken?...

Just trying to understand...

thanks.

PS: Broken packages seems related with python. Anyway, I could install pip, and some python stuff. But still not this I told before.

---

### Post by CaRoXo on 2013-07-15
Also, I read somewhere that for seeing the hold packages I should do:

aptitude search '~i~ahold'

But this command doesnt works in Lubuntu, wich one is instead?

Please, someone of the almost 200 that see the topic, please help me.

Thanks

---

### Post by Cheesehead on 2013-07-15
> **CaRoXo said:**
> 
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 pulseaudio : Depends: libfftw3-single3 but it is not going to be installed
              [COLOR="#FF0000"]Depends: libpulse0 (= 1:3.0-0ubuntu4b2) but 1:3.0-0ubuntu6 is to be installed[/COLOR]
              Recommends: pulseaudio-module-x11 but it is not going to be installed
              Recommends: gstreamer0.10-pulseaudio but it is not going to be installed
              Recommends: rtkit but it is not going to be installed
              Recommends: pulseaudio-utils but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


It's not a clean install. You seem to have added a PPA.
The PPA requires a specific version of libpulse0 (= 1:3.0-0ubuntu4b2) which is not current (1:3.0-0ubuntu6)

Disable all PPAs and try again.

---

### Post by CaRoXo on 2013-07-15
Hi Chesehead, thanx for answering.

Ok, I didn't add sources for "other software sources", but now that you tell me, I remember that the three times doing fresh installing, I check the options on the very begining of "installing third party software", and the last time I only uncheck the one of "upgrading while installing" but not this other one.

So now i unchecked the "multiverse" and "restricted" sources, in the "Ubuntu Software" part in synaptic (that was enabled by default, maybe becouse of this agreement in the usb installation). And it works, I was able to install Fslint and Pulseaudio, so this package of phyton-glade2.

Thanx, and if you can, tell me if without this 2 sources of restricted extras, I will not have problems with codecs and this in the future, or how i can replace it.

You can put like Solved or should I do, and how?


Thanks again.

---

### Post by CaRoXo on 2013-07-15
PS: and why packages are broken? and held? ... I dont understand this part. When they broke?

---

### Post by Frogs Hair on 2013-07-15
Packages can be held due to failure to connect with an archive/source . Broken packages are due to incompatibility/conflicts. To learn more about the package system and options use the following command. ```
man dpkg 
``` A ppa - personal package archive may conflict with other packages in the repository and have to be updated for new Ubuntu versions like other software. [http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/](http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/)

---

### Post by CaRoXo on 2013-07-15
Thnx for your time Frogs Hair!

I will study this now for better understanding. Even if limitated, Im motivated.

Last question about this issue is, if it would be usefull, and how to do it, to notificate people from the Lubuntu Team, that following their options for installation with the live-usb, had happen this problem.

Thanks for your time again. Hope one day I will be able to answer to others.

---

### Post by Frogs Hair on 2013-07-15
Lubuntu  Team:  [https://wiki.ubuntu.com/Lubuntu/Get%20Involved/WhoWeAre](https://wiki.ubuntu.com/Lubuntu/Get%20Involved/WhoWeAre)

---

