---
title: "can't install g++-4.1 and libstdc++6-4.1 packages"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by noob12345 on 2007-04-29
g++-4.1 is dependent on libstdc++6-4.1, 
while libstdc++6-4.1 is dependent on g++-4.1
all other versions also work that way

HOW IS IT POSSIBLE TO INSTALL EITHER!!!

I'm trying to install the build-essential package, so i can install linux-wlan-ng, so i can use my netgear ma111 usb adapter

I'm trying to install it ti my other computer which is still using dapper drake

---

### Post by davidgarcin on 2007-04-29
Thankfully, you don't need to compile packages yourself anymore.  To install linux-wlan-ng, all you need to do is go System -> Administration -> Synaptic Package Manager.  Hit the search button in the toolbar and type in linux-wlan-ng.  It should show up in a list.  Click the box beside it, and select "Mark for Installation".  Then hit the Apply button in the toolbar.

That's how you generally install new programs in Ubuntu.

---

### Post by noob12345 on 2007-04-30
do i need to be connected to the internet to do that?

---

### Post by davidgarcin on 2007-04-30
yeah, it downloads the packages, so you'll need to use a wired connection until you get that all setup.

---

### Post by noob12345 on 2007-05-01
i did what u said, and it told me that linux-wlan-ng was already installed, but it is useless without the modules
How do i get the modules? it said i might have to build it myself

i also followed the instructions on AbsoluteValue Systems to activate the driver, but i got a message that said "operation not permitted: wlanctl-ng" or something like that on the second step
I'm sorry if this should be in the networking or absolute beginner section
plz help

---

### Post by noob12345 on 2007-05-01
nevermind what i just posted,

---

### Post by ferahl on 2007-05-07
edit - nvm

---

### Post by davidgarcin on 2007-05-07
do you guys have it worked out now?  maybe I wasn't very clear.  but if you're installing new software/drivers/whatever, first check the repositories using the package manager (or apt-get or aptitude if you prefer, Synaptic is easier though).  If they are not there and you find you HAVE to compile it from source code, you will need the build-essential package, which itself can be installed from Synaptic.  (you can also install the individual compilers like g++ in Synaptic  if you don't want the whole thing, but you need to be familiar with what the program requires)

Generally, compiling from source is a last-ditch option.  There are other better options, like installing from a .deb or converting an .rpm to a .deb and then installing.  Here's a great site which walks you through just about every option:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

