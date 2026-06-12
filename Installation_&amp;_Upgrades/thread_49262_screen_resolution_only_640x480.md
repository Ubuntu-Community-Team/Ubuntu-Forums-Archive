---
title: "screen resolution only 640x480"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by intrigue on 2005-07-15
i installed ubuntu last night, and the installation was a breeze. It looks really solid and functional, and i can't wait to get going using it. during the X installation it prompted me for the screen resolutions i would like to run, and I disabled everything but 1024 (this is the native resolution of my laptop lcd). upon logging into gnome the screen resolution was only 640x480 with a 4" black border around it. i went into the System>Preferences> Screen resolution and the only choice is 640x480. I thought it might not have detected and installed the right driver, so i did some searching and to my amazement found intel had a working linux driver for my card (intel 845GM) on their support website. (Dell was no help) It was in rpm format, so i did some searching on that and found out i've gotta use the alien -i package.rpm command. I ran this as root without the x server running, and it seemed to have installed it fine. I logged back into gnome and 640x480 was the only choice still.

Im running a Dell Inspiron 1100.

Is there some further configuration I need to be doing within gnome or grub? I looked for a hardware manager to install the drivers like most OS's have and couldn't find one.

As a possibly unrelated question, is there some way to increase the resolution outside of X?

What strikes me as odd, is that when i boot into the Ubuntu live cd and Knoppix the resolution is 1024, so i know there is a working driver out there. Is there some way i could find out which driver these are loading and manually load it into my installation?

Im sure its an easy newbie fix, but Ive looked in the forums and found nothing on installing this particular card, and don't know anything about configuring debian or ubuntu

thanks in advance for any help

---

### Post by badrinarayan on 2005-07-15
This should help: [http://ubuntuforums.org/showpost.php?p=199884&postcount=4](http://ubuntuforums.org/showpost.php?p=199884&postcount=4)

No further configuration is required. Just restart X. You might have to uninstall the alien created deb (via synaptic for example). Does that work?

Regards
Badri

---

### Post by gsmith on 2005-11-12
Have a look through this stuff:

[http://www.ubuntuforums.org/showthread.php?p=486490#post486490](http://www.ubuntuforums.org/showthread.php?p=486490#post486490)

---

