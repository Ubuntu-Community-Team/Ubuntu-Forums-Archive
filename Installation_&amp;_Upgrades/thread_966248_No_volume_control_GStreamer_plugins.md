---
title: "No volume control GStreamer plugins"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Dale Gerdemann on 2008-11-01
I've just upgraded to Intrepid and as a result have lost my sound.I've spent hours googling and trying all sorts of things, but nothing helps. Can anyone help? Why should an upgrade cause this problem? Everything  else seemed to go okay, except for one warning during the upgrade that had something to do with CORBA.

---

### Post by Dale Gerdemann on 2008-11-01
I've tried tons of things recommended here and there. Here are a few test  results:


$ lspci|grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

$ cat /proc/asound
cat: /proc/asound: No such file or directory

$ dmesg
... ton of stuff ... What is important here?

$ pnpdump
bash: pnpdump: command not found

$ cat /etc/modprobe.d/sound
cat: /etc/modprobe.d/sound: No such file or directory


$ sudo apt-get install linux-backports-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic


$ cat /etc/modrprobe.d/alsa-base
cat: /etc/modrprobe.d/alsa-base: No such file or directory

$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory

Menu: System->Preferences->Default Sound Card
I can choose this from the menu. When I do, I get a "working" icon for
a couple seconds, but then nothing more happens.

I've installed all the gstreamer stuff and related things that were recommended here and there in various forums/blogs/etc.

---

### Post by Dale Gerdemann on 2008-11-01
Happy news! Problem solved! The relevant info was found [here]("http://help.ubuntu.com/community/SoundTroubleshooting").

I sure landed on a lot of pages with false leads before hitting this one.

---

### Post by tld on 2008-11-01
I have the same problem. My sound did not work after the last distribution release in Hardy.  I tried all the suggestions in the forums and the only thing that worked for me was installing StartUp-Manager and reverting to a previous distribution.  I had hopes that the upgrade to Intrepid would take care of the sound issues, but instead, it broke my sound again.  My solution (again) was to use StartUp-Manager and choosing the default operating system as "Ubuntu 8.10, kernel 2.6.24-19-generic"

---

