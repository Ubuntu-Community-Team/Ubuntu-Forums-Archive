---
title: "Minor post-upgrade problems"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by rob.fender on 2005-10-23
Hi - 

Last week I successfully upgraded from Hoary to Breezy, with a few glitches but essentially ok.

However, I still have some minor problems which I've not been able to sort. Any assistance would be gratefully received - I am sure they are quickly and easily remedied by the gurus ...

1. Firstly, when booting, I get this 

FATAL: error inserting hci_usb [plus lots more text]

- I have no idea what, if anything, this is affecting ... perhaps I should just edit the modules file ? am i losing some important feature which i'm unaware of ? (the USB port works fine still with external drive, stick and camera..)

2. Whenever I update / download + install with synaptic or on the command line with apt-get, I get the following (this from synaptic - essentially the same from command line too):

E: postfix: subprocess post-installation script returned error exit status 1
E: mailx: dependency problems - leaving unconfigured
E: mutt: dependency problems - leaving unconfigured
E: lsb-core: dependency problems - leaving unconfigured
E: lsb-graphics: dependency problems - leaving unconfigured
E: lsb-cxx: dependency problems - leaving unconfigured
E: lsb: dependency problems - leaving unconfigured

thanks in advance for any help!

---------------
UPDATE - in case anyone cared! - I seem to have solved problem 2 by doing 

sudo dpkg -r postfix
sudo apt-get install postfix

which seems to have removed then reloaded all the above-mentioned error-generating packages... 
[not sure if this was unnecessary brute force but it worked.]
----------------

Rob.

---

### Post by Edd on 2005-10-28
Thanks for the information about how to solve the postfix issue. I had the same problem after upgrading, and this helped me nicely :)

---

