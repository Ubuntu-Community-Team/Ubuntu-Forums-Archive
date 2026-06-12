---
title: "Debconf error in Edgy upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by kkuzia on 2006-10-27
In trying to upgade from Dapper to Edgy using apt-get, I am running into an error I cannot seem to get past and have not the slightest idea what the heck it means (still fairly new to the who Ubuntu game).

The upgrade will be rolling along and then I get the following:
> X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Fontconfig error: Cannot load default config file
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Extracting templates from packages: 100%
DESTROY created new reference to dead object ' Qt::Frame', <> line 1326 during global destruction.
Preconfiguring packages ...
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN52> line 7.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN52> line 7.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN57> line 4.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN57> line 9.


At the same time, I get a window that pops open outside of the terminal that is for Debconf which says:
"Incorrect nice value

Please enter an integer between -20 and 19."
Bottom of the window has a Help button (which does nothing) a Next and Cancel.

Well, banging away on Next solves nothing and trying cancel just eventually causes a hang after a while.

Thoughts?

---

### Post by chippy99 on 2006-10-27
I believe the preferred method of upgrading is 
gksu “update-manager -c -d”
It updates all the required repositories automatically.

Do you get same problems with this ?

---

### Post by Paul Dufresne on 2006-10-27
Nice value is an indication of the priority of the process.
10 is the default value.
I would guess a package tried to run debconf with an unrecognizable value.
Have you tried to give a value in the window?

---

### Post by Paradoxdruid on 2006-10-28
I'm getting the same error on multiple copies of kubuntu Dapper being (well, trying to be) upgraded.

I have used The dialog box doesn't allow you to enter a nice value--  it's only choices are "Next" or "Cancel".  Next does nothing, and cancel stops the package installation script, so dpkg errors and things fail.


This has happened on 2 pure Kubuntu and one Ubuntu machine so far, with no successful upgrades.  I am not impressed.

---

### Post by Paul Dufresne on 2006-10-29
This looks like:
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68267](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68267)

The comment there would suggest that if you do in a terminal window:
$sudo dpkg-reconfigure debconf
then choose 'dialog' in the first screen,
keep 'high' for level, or whatever is there,

then you should be able to then upgrade.

---

### Post by kkuzia on 2006-10-30
> **Paul Dufresne said:**
> Nice value is an indication of the priority of the process.
10 is the default value.
I would guess a package tried to run debconf with an unrecognizable value.
Have you tried to give a value in the window?

I did try to enter a value in the window, to no avail.  Fortunately, I tried running a few times later and (for reasons I cannot fully explain) it loaded up dandy.  I am now onto a new problem:
[http://www.ubuntuforums.org/showthread.php?t=288716](http://www.ubuntuforums.org/showthread.php?t=288716)

lol

Thank you everyone for your help.  It is greatly appreciated. :KS

---

### Post by fraenhawk on 2006-10-30
> **Paul Dufresne said:**
> This looks like:
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68267](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68267)

The comment there would suggest that if you do in a terminal window:
$sudo dpkg-reconfigure debconf
then choose 'dialog' in the first screen,
keep 'high' for level, or whatever is there,

then you should be able to then upgrade.

Thanks, that worked to get me past my debconf nice errors.

---

### Post by Paul Dufresne on 2006-10-30
Ah, finally... I was able to give a usefull advice! :D

---

### Post by eilker1917 on 2006-11-04
> **Paul Dufresne said:**
> This looks like:
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68267](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68267)

The comment there would suggest that if you do in a terminal window:
$sudo dpkg-reconfigure debconf
then choose 'dialog' in the first screen,
keep 'high' for level, or whatever is there,

then you should be able to then upgrade.

this doesnt work for me :( kubuntu here...

---

### Post by ruya on 2006-11-22
Worked for me going from kubuntu Dapper to Edgy.:)

---

### Post by Miquelets on 2007-03-06
Do
   sudo dpkg-reconfigure debconf  then choose 'dialog' in the first screen, keep 'high' for level,

Then
  sudo apt-get upgrade

This got me out of a mess when upgrading Feisty

---

