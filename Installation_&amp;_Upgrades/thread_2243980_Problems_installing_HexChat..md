---
title: "Problems installing HexChat."
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by Zhitzu on 2014-09-12
I'm trying to install HexChat!

I'm using these in the terminal:

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/hexchat-stable

sudo apt-get update

sudo apt-get install hexchat
```

The first two goes fine, but when I use that last commend; sudo apt-get install hexchat, I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 hexchat : Depends: hexchat-common (= 2.10.1-0ubuntu1~trusty1) but 2.10.1-0ubuntu1~utopic1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Tried using "sudo aptitude install hexchat" instead of the apt-get, but all I get is this output: "aptitude: command not found".
Also tried a "dpkg --get-selections | grep hold" for a list of held packages.... no result at all, so guess there isn't any..

Finally I check with a "dpkg --get-selections", and on the list I found a "hexchat-common" installed.... But I don't know what to do with this, the HexChat program still doesn't appear in the Utiny Dash...!

Come on people, almost 30 views, and no one can help me????
I've searched everywhere, I really need help!!

---

### Post by ibjsb4 on 2014-09-12
Looks like it installed the wrong hexchat-common.  You are running 14.04?
> hexchat : Depends: hexchat-common (= 2.10.1-0ubuntu1~trusty1) but 2.10.1-0ubuntu1~utopic1 is to be installed
Check in /etc/apt/sources.list.d to make sure you have the right download.

Also Xchat is free and in the software center.  I don't know why the Hexchat site says different.

---

