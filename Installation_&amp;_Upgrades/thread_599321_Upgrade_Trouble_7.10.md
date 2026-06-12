---
title: "Upgrade Trouble 7.10"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Saxomophone on 2007-11-01
I used update manager to upgrade from Feisty to Gutsy, and something didn't go well in the process, because now when I reboot the screen flickers a little bit, and then goes black and I can't see anything. Once in a while I actually get to see something that says ubuntu is running in limited graphics mode, and if I try to set the driver for my 8800 GTS, the screen again goes black. Other times it boots, and the entire screen is distorted and I can half make out the limited graphics message. If I boot in recovery mode, the text on boot flickers a little bit, but eventually I get a command line.


I'm not sure how to fix this

---

### Post by Pumalite on 2007-11-01
For your card do this:

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Let's see if it works.
__________________

---

### Post by Saxomophone on 2007-11-01
I get an error. "could not resolve us.archive.ubuntu.com" it told me to try updating apt-get, which i did, and then it said to try using --fix-missing, but I wasn't sure what to do about that.

---

### Post by Pumalite on 2007-11-01
Try
sudo apt-get update
sudo apt-get upgrade

---

### Post by Saxomophone on 2007-11-01
update tells me there are files it can't access so it has either ignored them or used older ones

upgrade doesn't install anything new.

---

### Post by Pumalite on 2007-11-01
Take a look at your /etc/apt/sources.list. You might need to install repos and comment out others.

---

### Post by Saxomophone on 2007-11-01
Okay, I'm a novice when it comes to using the command line, so how can I do that from recovery mode?

---

### Post by Pumalite on 2007-11-01
First backup:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back
gksudo gedit /etc/apt/sources.list (to edit)
Post your sources.list (copy and paste) and let's have a look at them.

---

### Post by Saxomophone on 2007-11-01
Okay, will do, but is there a way to access this web page from recovery mode? i'm using the windows partition to go on the forum at the moment

---

### Post by Saxomophone on 2007-11-01
Okay, I think this is more than just a graphics problem. When i try to boot, the mouse pointer is a black X, and the background is black. After I choose whatever option in the low graphics mode dialog box, the screen goes black, and nothing happens. Is there a way to re-apply the update?

---

### Post by Pumalite on 2007-11-01
Your best bet is to save /home and data and do a clean install.
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

