---
title: "[SOLVED] Gutsy: Updates where aborted and may left my system unstable"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by antiOST on 2008-07-13
Hi 

Just hit the "install updates" icon and choose to install latest updates.

First it told me that I had to a partial updates because of some incosistencies. Well I'm a little new to ubuntu so I thought, fine, it's gonna skip the parts that not alright, but no!, half way though the updates where aborted and it told me that my system might be left unstable.

The package that caused the problem was firefox and I guess thats because I installed firefox 3 using this [guide]("https://help.ubuntu.com/community/FirefoxNewVersion") since synaptic. don't include this version.

Should I be worried? 
How do I get the updates installed correctly and still have my firefox3?

When trying to reinstall updates it gives me an error that says I should sudo apt-get install -f which leds me to this error (that confirms my suspicion of firefox):

dpkg: error processing /var/cache/apt/archivesfirefox_2.0.0.15+1nobinonly-0ubuntu0.7.10_i386.deb (--unpack):
 trying to overwrite `/usr/bin/firefox', which is the diverted version of `/usr/bin/firefox'
Please restart any running Firefoxes, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.15+1nobinonly0ubuntu0.7.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be appriciated.
Kim

---

### Post by CJ_Hudson on 2008-07-13
All I know is that from a previous reply on this forum on a similar topic I got:

"sudo apt-get -f install" 

(missing out the speech marks) , not what you had.
Hope that's some assistance!

---

### Post by antiOST on 2008-07-13
Thanks,

I already tried the command you suggested as stated in my first post 
Edit: didn't see that your suggestion were a bit different, but same outcome though...


I properly could uninstall firefox3 and run the command and install updates, but then I would have to reinstall firefox 3 again afterwards :-(


-Kim

---

### Post by antiOST on 2008-07-16
I solved my problem, I'm not entirely sure what I'm doing but it works.

Removing firefox 3.0 temporarily (not removing my custom installation of FF3 by pointing to ubuntu install of FF)

sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox

Then I run 

sudo apt-get -f install

after that I point back to FF3

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox


-Kim

---

