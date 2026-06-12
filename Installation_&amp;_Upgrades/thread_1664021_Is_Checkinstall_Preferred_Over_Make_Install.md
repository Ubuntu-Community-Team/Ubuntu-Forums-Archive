---
title: "Is Checkinstall Preferred Over Make Install??"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by hayhursm on 2011-01-10
I installed Aircrack-NG from the source using the "sudo checkinstall" command.  It worked but just for a test I decided to remove the package using "sudo dpkg --purge aircrack-ng".  The process seemed to have removed all the files until I did a "sudo find / -iname 'air*' and found traces of Aircrack-NG on my system.  I removed those traces and then installed Aircrack-NG again using the traditional "sudo make install" command and then removed it using "sudo make uninstall".  I then did a "sudo find / -iname 'air*' and couldn't seem to find any traces of Aircrack-NG on my system.   Should I use "sudo make install" rather than "sudo checkinstall" if later I want to remove an app completely?   I also want to add, that after I used "sudo checkinstall" and then ran "sudo apt-get upgrade" it tried to remove the newly installed aircrack-ng and downgrade it to the one found in the repositories.  Not sure why "sudo apt-get upgrade" thought it was better to downgrade??  Any help will be greatly appreciated!  BTW I'm using Ubuntu 10.04

---

### Post by endotherm on 2011-01-10
this should answer your question:
[http://www.asic-linux.com.mx/~izto/checkinstall/]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/")

it sounds like this is really for packages where there isn't a 'uninstall' label in the makefile. I would take a distributers make uninstall before i would try to craft my own, as checkinstall appears to.

checkinstall registers the package with dpkg, which is why you are getting "upgrades" for it. most likely dpkg can't tell your version, so it applies the greatest it knows.

---

### Post by hayhursm on 2011-01-11
> **endotherm said:**
> this should answer your question:
[http://www.asic-linux.com.mx/~izto/checkinstall/]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/")

it sounds like this is really for packages where there isn't a 'uninstall' label in the makefile. I would take a distributers make uninstall before i would try to craft my own, as checkinstall appears to.

checkinstall registers the package with dpkg, which is why you are getting "upgrades" for it. most likely dpkg can't tell your version, so it applies the greatest it knows.


I really appreciate your help!!!  Thank you!!

---

### Post by hayhursm on 2011-01-12
> **endotherm said:**
> this should answer your question:
[http://www.asic-linux.com.mx/~izto/checkinstall/]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/")

it sounds like this is really for packages where there isn't a 'uninstall' label in the makefile. I would take a distributers make uninstall before i would try to craft my own, as checkinstall appears to.

checkinstall registers the package with dpkg, which is why you are getting "upgrades" for it. most likely dpkg can't tell your version, so it applies the greatest it knows.

I also wanted to ask, what do you do when you come across a source that doesn't have the "make uninstall" feature?  Just today I was compiling the go7007 driver from source to install an old Plextor capture device and I was not able to perform a "sudo make uninstall"

---

