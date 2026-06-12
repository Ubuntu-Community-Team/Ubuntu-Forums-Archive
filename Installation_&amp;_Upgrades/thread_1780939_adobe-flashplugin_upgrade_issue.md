---
title: "adobe-flashplugin upgrade issue"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by amberleafguy on 2011-06-12
Hi there,

The problem is quite simple

I recently updated to 11.04, during the installation process there was a fetch issue with adobe-flashplugin output was 

W: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.181.22-0natty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.181.22-0natty1_i386.deb)
  Hash Sum mismatch

So, I thought I would delete flashplugin prior to upgrading hoping to update after installation. 

The installation worked and I upgraded to 11.04 abeit 3d acceleration (boo!!!), tried to install adobe flashplugin same issue. 

Now, 2 things I need help with 

1. Is there a way of fixing this issue

2. what is a Hash Sum mismatch ( is that something to do with the cryptographic signature) 

I have done the following

1. changed repository servers to see if that would give me a fix that way.

2. physically downloaded the offending .deb file and used gdebi to try install it that way. 

3. tried flash website to get a version from there, without success. 

4. Kicked the machine numerous times. (the last one was a joke) 

I have been quite happy with the majority of solves on here, lets see if this could be fixed

thanks

---

### Post by oohbuntoo on 2011-06-12
This is just a guess as I am fairly new to the Linux game.  When I upgraded to Natty it automatically switched me from 32-bit to 64-bit.  I didn't get the error you did during installation.  It sounds like you are currently running 64-bit since you are getting an i386 error.  I had a HELL of a time trying to get flash to work in any browser.  I succeeded, but, every time I upgraded Chromium I had to repeat steps to get flash to work again.  I eventually reinstalled Meerkat.  Hope this helps. :popcorn:

---

### Post by garvinrick4 on 2011-06-12
Hope this helps you below:
[http://ubuntuforums.org/showthread.php?t=1464217](http://ubuntuforums.org/showthread.php?t=1464217)

---

### Post by desktorp on 2011-06-12
When I search for stuff about the hash sum mismatch, I find some crazy stuff.  If you're unable to download the file* at all*, try restarting your modem.  If you can confirm that you are now using 64-bit Ubuntu, I would suggest deleting the flash plugin and getting the native 64-bit plugin, from [http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

Hope you figure it out. Worse comes to worst - do a fresh install because upgrades are yucky.

edit: looks like garvin may have found it!  woooo

---

### Post by amberleafguy on 2011-06-13
Hi again, 

My machine is quite old, I am 100% sure that it is _not_ 64bit it is only 32 bit. 

Deleting the repository would be an idea, however as you know flash is important when it comes to running certain web apps. I wish everything could be in HTML 5 however I digress.  

Personally I would love not to use flash at all however my hand has been forced due to the types of applications I use which require flash to run.

Clean install would be another good idea maybe that will resolve all the current issues, however I feel the issue would be a bit harsh considering that I dont use dual boot. 

Is there any way of sorting this out?

---

