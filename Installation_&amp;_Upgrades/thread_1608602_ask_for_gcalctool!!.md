---
title: "ask for gcalctool!!"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by zhengkarl on 2010-10-29
hi,everyone!

I upgrade to Ubuntu 10.10,and find the attached calculator gcalctool 5.32.0 is  very un  user friendly for use.

for example:I want to calculate how many is :0x1DFA7F in decimal or  the first 10 bit of 0x1DFA7F,

gcalctool 5.32.0 have no HEX,DEC,BIN,OCT convert button as prior version provide

I'd like to ask how can downgrade to the prior version of gcalctool.

---

### Post by kansasnoob on 2010-10-29
I'm using the Lucid version from here:

[http://packages.ubuntu.com/lucid/math/gcalctool](http://packages.ubuntu.com/lucid/math/gcalctool)

Notice that you must choose whether you're using the i386 or amd64 version of Ubuntu.

Then you must purge the Maverick version, I recommend just using Synaptic to do this. Simply type gcalctool into it's search and then mark for complete removal.

You'll notice that it wants to remove the 'ubuntu-desktop' meta-package. That's not a problem but you should remember to reinstall it before doing any distro upgrades in the future.

You can then install that .deb either with dpkg or USC (gdebi is no longer installed by default). After installing open synaptic again, search for gcalctool, click on it to highlight that line, then go to Package > Lock Version so it won't be updated to the Maverick version every time Update Manager runs.

---

