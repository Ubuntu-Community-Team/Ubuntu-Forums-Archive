---
title: "Help! Installing Canon Pixma iP1300 with CUPS on ubuntu 12.04.1"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Frawsty on 2013-01-25
):P

Hi, 

i just **migrated** from windows :D and im trying to  setup **Canon Pixma ip1300 **color **printer **on Ubuntu *64 BIT***  V12.04.1** LTS. Since Canon **officially** dosent support **Linux **for ip1300 model. I thought of looking for some tricks..to get it work on 'U'? and i Found this

[http://ubuntuforums.org/showthread.php?p=3450617](http://ubuntuforums.org/showthread.php?p=3450617) (seems to work) 

but i'm getting **error** at **3rd Step**

> cnijfilter-common-2.60-1.i386.rpm is for architecture i386 ; the package cannot be built on this system^^Maybe it has something to with 32 n 64 bit , i dont really understnd :P so Would any1 help me  out?  :sad:

---

### Post by pdc on 2013-01-25
You say you are running 64bit Ubuntu

you are attempting to install

> i386

.....that is a 32bit package, so there may be issues;

if you look here

[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

Michael Gruz seems to do a sterling job of being chief shepherd and collecting Canon drivers under one roof

the commands would be

> [COLOR="Red"]sudo add-apt-repository ppa:michael-gruz/canon-trunk[/COLOR]

then 

> [COLOR="Red"]sudo apt-get update[/COLOR]

then 

> [COLOR="Red"]sudo apt-get install cnijfilter-ip13000series[/COLOR]

..... and see if such a package is in his PPA:

Your printer could be politely described as elderly: and Canon didn't supply much linux support then: 2006 .......some of us were using Red Hat 9 about then ...........

Canon supply drivers for more recent printers

---

### Post by Ezetreal on 2013-03-13
Thank you PDC !

Your solution worked for me on Linux Mint 14.

For the next soul with a Canon PIXMA ip1300, follow pdc's post and install the cnijfilter-ip2200series. The ip1300 is not available. The 2200 series works well with it.

Again thank you pdc and Michael Gruz !



PS: Frawsty, if you are reading this, please mark this as solved...

---

