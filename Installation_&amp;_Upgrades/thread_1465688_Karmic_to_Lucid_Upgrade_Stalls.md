---
title: "Karmic to Lucid Upgrade Stalls"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by plasmoidal on 2010-04-29
Specifically, after downloading the necessary packages, they get unpacked up through package "tzdata", at which point the following appears:

Processing triggers for man-db...
Processing triggers for doc-base...
Processing 2 changed doc-base file(s)...
Registering documents with scrollkeeper...

At which point the upgrade stalls (just blinking cursor at the console, not frozen), and I'm unable to stop it (even with ctrl-alt-C).  Has anyone encountered a similar problem, and/or know a way to safely stop the upgrade (it doesn't look like it's actually installed any of the unpacked packages yet)?

Thank you.

---

### Post by plasmoidal on 2010-04-29
Probably on a related note, the desktop is broken as well--I can't open any new nautilus windows and if I open up a new console, it is entirely unresponsive (I try to type, but nothing appears).  Other applications seem unaffected (e.g., Gedit works just fine).

---

### Post by Maliron on 2010-04-29
Not to tag-along off of your post, but I have a similar problem.

During my upgrade the unpacking and everything went fine. It was during the "Installing Packages" portion, when it got to the linux-headers, the entire system froze. No mouse, no caps-lock, nothing. I left it there for about half an hour and nothing progressed. I had no choice but to shut the system down....

Obviously I don't have a working system now, and have no idea how to go about fixing.

Anyone have any starting points, or are we both destined to fresh installs?

***EDIT***
I should note, that I cannot even boot into the recovery console. I am booted to a liveUSB of 10.04 right now.

---

### Post by Maliron on 2010-04-29
From my liveUSB I've chroot'ed over to my install and I am trying the following.

```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing

```

/crossing_my_fingers

---

### Post by plasmoidal on 2010-04-29
I just did the same thing and got karmic back up and running, minus some config files.  I very much hope things are going well on your end--there are few things scarier than a broken OS!

Thanks.

---

### Post by Maliron on 2010-04-29
Glad to hear the good news! Mine is a bit more sorted. It seems the upgrade got a lot further than I thought. The above steps got me a semi booting system again. I get the Lucid boot splash, but it hangs and says:

"An error occurred while mounting /proc/bus/usb"

It gives me the option to S Skip or M Manual recovery. Hopefully I can figure out what's causing that to not mount and maybe be in luck here. When I get a chance though I think this system is destined for an entire rebuild, they never seem to run right after something like this.

---

### Post by joham34 on 2010-04-30
> **Maliron said:**
> Glad to hear the good news! Mine is a bit more sorted. It seems the upgrade got a lot further than I thought. The above steps got me a semi booting system again. I get the Lucid boot splash, but it hangs and says:

"An error occurred while mounting /proc/bus/usb"

It gives me the option to S Skip or M Manual recovery. Hopefully I can figure out what's causing that to not mount and maybe be in luck here. When I get a chance though I think this system is destined for an entire rebuild, they never seem to run right after something like this.


Have exactly the same problem . In /etc/fstab , the last line says :
 none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
presumably the correction should be done there but I am too newbie to change fstab. 
Help please !

---

### Post by Dubbayoo on 2010-04-30
Same here. For my system that last line was added for VirtualBox. I commented it out and everything is fine now.

---

### Post by fred0310 on 2010-04-30
Same problem while booting... :
"An error occurred while mounting /proc/bus/usb" 
S skip to continue or M to manual

What to do to resolve this ?

Thanks

---

### Post by kenbaldwin on 2010-05-01
Same problem while booting...
"An error occurred while mounting /proc/bus/usb"
Doesn't seem to have any effect I can detect. USB mouse and external drive work fine.
Fix anyone? Thanks

---

### Post by kenbaldwin on 2010-05-01
It was a problem with a previous install of VirtualBox. This worked for me
[http://ubuntuforums.org/showthread.php?p=9209373](http://ubuntuforums.org/showthread.php?p=9209373)

Ken

---

### Post by Amydale on 2010-05-01
it works for me too
Thks !
:P

---

### Post by Maliron on 2010-05-03
Yah, I remember having to add that "hack" for VirtualBox a while ago. It's good to know that it is no longer needed, because I ended up commenting the line out of my fstab as well.

The lappy boots now, and even though it says there are no packages that need updating, I don't know how much I can trust that the install of 10.04 went correctly, with the crash and all. The laptop seems to be running fine, but I think just to be safe I am going to do a fresh install of Lucid on there. It's a pain, but this thing has survived 2 or 3 drive crashes and has lasted several Ubuntu upgrades, so I think it's time for a fresh start anyways. :sad:

---

### Post by joham34 on 2010-05-05
As I saw from other forums, one just have to comment ( put a # in the beginning of,) list line , the one that says ¨ none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 ¨ in /etc/fstab and the problem is solved (at least for me)

---

### Post by maxideci on 2010-05-26
Hi All, 

My up-gradation to Lucid is stuck at 'Configuring mysql-server 5.1'

11 mins to go.

attached is the screen shot.

Thanks and waiting for expert comments.

Cheers!!

---

### Post by maxideci on 2010-05-26
> **maxideci said:**
> Hi All, 

My up-gradation to Lucid is stuck at 'Configuring mysql-server 5.1'

11 mins to go.

attached is the screen shot.

Thanks and waiting for expert comments.

Cheers!!

Hi all, 

I worked it out, just stopped mysql daemon. Its moving ahead now.
:)

Cheers!!

---

