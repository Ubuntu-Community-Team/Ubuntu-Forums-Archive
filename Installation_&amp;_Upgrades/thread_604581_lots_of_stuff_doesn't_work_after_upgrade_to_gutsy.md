---
title: "lots of stuff doesn't work after upgrade to gutsy"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by skrribble on 2007-11-06
I just upgraded to Gutsy from Feisty.  First of all, my dual screens running on an ATI Mobile X600 using the radeon driver, doesn't work anymore.  This would be fine, and I would just do it using the fglrx driver and the built in support for dual monitors in Gutsy, but I can't open either of those from System > Administration.  In fact most of the items in System > Administration won't open.  For instance, I can't actually open the Update Manager, but if it comes up in the Upper Right hand corner i can right click it and say Install the Upgrades, but I still can't actually open the Update Manager.  

Second of all, it seems that my sound card isn't recognized anymore.  when I click on the Volume Control in the Panel, I get the Error message:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

As I can see, all of the Gstreamer plugins are there, just like they were before the upgrade.  

One last thing that is not quite as important, but just as strange.  My Exaile music player won't open either.  I've tried uninstalling and reinstalling a couple of times to no avail.  I don't know what to do here, and some help would be much appreciated.

Again, all of these things worked in Feisty before the upgrade. 
Thanks

---

### Post by skrribble on 2007-11-06
Please, if anyone has any ideas they would be helpful... anything!

---

### Post by skrribble on 2007-11-07
nothing?  no one has any ideas?

---

### Post by bulldog on 2007-11-07
Ideas enough but you have nothing at them.

I don't like to upgrade,most of the times it ended up in a mess.
Did it twice and had to do a clean install to get things running again.

So,as you can guess,I only upgrade with a fresh install,leaving the previous one intact in case of trouble.
In this way I have always a good working ubuntu.

---

### Post by Pumalite on 2007-11-07
Prefer clean install too. I actually think that people that have a working OS that they like; they should keep it until there is no support. I have Gutsy in clean install, but I still have my Feisty.

---

### Post by hferinga on 2007-11-08
For your sound stuff, add the user in the audio group (/etc/group). That fixed it for me.

---

### Post by Pumalite on 2007-11-08
Here are some links:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=503342](http://ubuntuforums.org/showthread.php?t=503342)

---

