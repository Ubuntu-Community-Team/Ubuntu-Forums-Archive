---
title: "Installing Google Earth on 12.04 Doesn't work for me."
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by suomalainen on 2012-11-18
Ubunteros,

I'm running 12.04LTS. I want to install Google Earth but it appears to be an incomplete install.

When I launch Google earth I get the "globe" but no land masses appear. Only yellow border lines outlining countries is the only thing I see.

I downloaded the package from the Google earth web site and the file name is:

google-earth-stable_current_i386.2.deb

Thanks for your help.!

---

### Post by suomalainen on 2012-11-18
Finally!

Found these and now it works!


[http://linuxforums.org.uk/index.php?topic=10397.0](http://linuxforums.org.uk/index.php?topic=10397.0)

To install Google Earth (stable) in Ubuntu 12.04, or Peppermint Three from this PPA:
[http://www.ubuntuupdates.org/ppa/google_earth](http://www.ubuntuupdates.org/ppa/google_earth)
(use the commands below, NOT the commands listed at the above link, or you'll end up with 2 duplicate sources which will cause you issues in the future)

Open a terminal, and run these 4 commands in sequence:
Quote

    wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -

    sudo sh -c 'echo "deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main" > /etc/apt/sources.list.d/google-earth.list'

    sudo apt-get update

    sudo apt-get install google-earth-stable

---

### Post by TedinOz on 2012-12-02
> **suomalainen said:**
> Finally!

Found these and now it works!


[http://linuxforums.org.uk/index.php?topic=10397.0](http://linuxforums.org.uk/index.php?topic=10397.0)

To install Google Earth (stable) in Ubuntu 12.04, or Peppermint Three from this PPA:
[http://www.ubuntuupdates.org/ppa/google_earth](http://www.ubuntuupdates.org/ppa/google_earth)
(use the commands below, NOT the commands listed at the above link, or you'll end up with 2 duplicate sources which will cause you issues in the future)

Open a terminal, and run these 4 commands in sequence:
Quote

    wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -

    sudo sh -c 'echo "deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main" > /etc/apt/sources.list.d/google-earth.list'

    sudo apt-get update

    sudo apt-get install google-earth-stable

 
Excellent! Finally it works! Thank you!

---

### Post by SuperFreak on 2012-12-09
Thanks...worked for me also

---

### Post by rburkartjo on 2012-12-18
ted tks for the info didnt work for me though

---

### Post by rewyllys on 2012-12-18
Suomalainen, many thanks!:popcorn:

Your four command-line instructions worked like a charm for me in Linux Mint 13, which is based on Ubuntu 12.04.

---

### Post by ZACHSP8 on 2012-12-19
Thank you, works fine on Kubuntu.

---

### Post by lillyvip on 2013-03-26
Thanks [COLOR=#000000] [/COLOR]**[COLOR=#000000]suomalainen, [/COLOR]**[COLOR=#000000]definitely works! [/COLOR]

---

### Post by suomalainen on 2013-03-26
Thank you fellow Ubunteros for the kinds words! Much appreciated!

---

### Post by smauleon on 2013-04-03
Worked for me too, in three 12.04 machines. It's Google Earth 7 that doesn't show the maps, and these instructions install version 6.

Thanks a lot!

---

### Post by tbk515 on 2013-07-06
I have a bug with commands from Suomalainen, more specifically the problem is with the fonts in Google Earth! Here is the s-shot:
[http://img534.imageshack.us/img534/2881/1eh.png](http://img534.imageshack.us/img534/2881/1eh.png)
I using Xubuntu 12.04 without installed M$ Fonts. Pls, Help!

---

### Post by allCuExpMa on 2013-09-23
Thanks suomalainen, finally it works....

---

### Post by sjanzeir on 2014-01-25
> **suomalainen said:**
> Finally!

Found these and now it works!


[http://linuxforums.org.uk/index.php?topic=10397.0](http://linuxforums.org.uk/index.php?topic=10397.0)

To install Google Earth (stable) in Ubuntu 12.04, or Peppermint Three from this PPA:
[http://www.ubuntuupdates.org/ppa/google_earth](http://www.ubuntuupdates.org/ppa/google_earth)
(use the commands below, NOT the commands listed at the above link, or you'll end up with 2 duplicate sources which will cause you issues in the future)

Open a terminal, and run these 4 commands in sequence:
Quote

    wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -

    sudo sh -c 'echo "deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main" > /etc/apt/sources.list.d/google-earth.list'

    sudo apt-get update

    sudo apt-get install google-earth-stable

Thanks! This worked perfectly for me on a 64-bit 12.04LTS system I just installed, but I still had to upgrade to Google Earth 7 to get rid of the "invalid HTTP request" error that now seems to be an issue with pre-GE7 packages. Problem is, now Panoramio pictures won't work with GE7! :(

---

