---
title: "install nomad 2c mp3 player?"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by not_yet on 2005-06-27
hello,

I have an older mp3 player, a nomad 2c

when connected with usb the nomad screen shows a connection to the computer

what I don't know is how to set up the driver for Ubuntu?

this site [http://nomadii.sourceforge.net/main.php3?action=download](http://nomadii.sourceforge.net/main.php3?action=download)

has drivers, but how can they be set up?

thanks

---

### Post by angryfirelord on 2006-11-26
I too, have an old Nomadiic player laying around and found a way to get it up and running in Ubuntu.

First, we need to get a little tool called alien. Do a sudo apt-get install alien. What this will do is allow us to convert package formats.

Grab the rpm package and do a sudo alien (name of rpm package). This will convert it into a deb package.

Install the generated deb package with dpkg -i (name of deb package)

Now, nomadiic can only be used by command prompt. However, when you try to run nomadii at the prompt, it complains about a dependency error. When I tried it, I got 2 complaints. The first one con be found at Synaptic but the second one was rpm only. Just do an alien of the second one and install that.

To use nomadii, you have to issue it commands at the terminal. Let's say I have a song called "track 1.mp3". To transfer it, I would type nomadii -i -s "track 1.mp3" (with the quotes). The -i means internal storage and the -s sends it. Doing a man nomadii should answer any questions.

I realize that this post is old, but I can't stand seeing questions without responses. :)

---

