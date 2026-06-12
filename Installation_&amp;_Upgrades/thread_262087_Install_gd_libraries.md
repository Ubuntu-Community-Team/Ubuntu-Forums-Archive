---
title: "Install gd libraries"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by Firestar on 2006-09-21
Hi Everyone,

I've tried searching for this the last two days, but it seems the search feature is broken, since I get a vbulletin database error when trying to search, so please forgive me if this is a duplicate of another thread.

I'm trying to get these installed, but I'm having some problems.

Firstly, what I'm running:
Ubuntu 6.06 AMD64 server edition with the latest kernel, I think (how do I check? kernelversion doesn't work).
I have an Opteron 265 with 4 GB ram (of which only 2.8 GB's is picked up, another problem I need to try and fix) and 4 SATA2 HDD's.

I am a complete linux noob, and google is my best friend, so please be gentle.

I'm running vbulletin forums over at [http://forums.prophecy.co.za]("http://forums.prophecy.co.za") and the GD/ImageMagick image libraries doesn't seem to work. I need to install them to get a hack working, as well as the human verification image thingy.

I've tried the following:
apt-get install php5-gd
apt-get install libgd-dev

I've also tried the above with the aptitude command, which I only read about last night trying to find a problem for this.

The problem with GD seems to be that php isn't compiled with GD. You can see my phpinfo over [here]("http://forums.prophecy.co.za/version.php"). There is no GD library section, and because of the REALLY stupid name of this library it's very difficult to search for the right thing on google/forums/wherever.

Can anyone tell me how to compile PHP5 to include support for GD version 2? I'm not scared to read, so if you've got a link for me where I can try this, I'm more than willing to do so.

I think I'll post more threads about my RAM problem and ImageMagick. There's also a few other problems that I need help with.

Thanks for the help.
Firestar

---

### Post by coffeepunk on 2006-09-23
I had a simillar problem. I couldn't use imagecreatetruecolor. Scanned php.net and found out that it has to be enabled via gb. Looked around and tried the following.

sudo apt-get install php5-gd

After installing the package I restarted the apache

sudo /etc/init.d/apache reload

This worked for me and when running phpinfo(); I get the gd information and things seems to be in order. But I still can't see what's built/compiled with the php installation though.

---

