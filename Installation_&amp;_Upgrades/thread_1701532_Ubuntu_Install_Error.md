---
title: "Ubuntu Install Error"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by wcipolli on 2011-03-06
I just purchased a lenovo u160 laptop. It comes with Intel HD graphics on the processor. It doesn't come with an optical drive so I have to install using a USB port. I created the USB install using the directions on the Ubuntu website.

I tried to install both 10.10 32-Bit, and 10.04 and both had the same behavior. When I restarted and booted from the USB the Ubuntu options screen came up prompting me to choose how to start it, install to disk or run off drive. I choose install to disk, because I want to partition and run off of that. It appears to run some things and then the screen turns black and there's no recovering from there.

I'm not sure what to do from here. I've been searching online, I saw the most frequent answer is setting nomodeset. I don't see that option anywhere and I'm not sure what else to do. 

Any help is greatly appreciated thank you very very much!

---

### Post by YesWeCan on 2011-03-06
It is usually recommended to try Ubuntu without installing as a trial run.
Ubuntu sometimes gets stuck during the first boot because of graphics card support issues. The nomodeset boot option generally fixes this. This isn't necessarily the issue.

Go back to the usb menu and you should see a function key boot options menu. Select nomodeset and then try to boot off the usb. If that works you know the install will work...with the same option.

Try this first and report back.

---

### Post by wcipolli on 2011-03-10
Hi, sorry for the delay. I booted up again and got to the USB screen and had the following options:

Run from usb
install on hard disk
Test memory
boot from first hard disk
advanced options
help

I chose run from usb this time. You hear the start up music but no visual.

I didn't see where I could set nomodeset, is there a particular function button to use? advanced options leads to a screen with back or boot as its only options.

---

### Post by Dutch70 on 2011-03-10
The directions are just a little ways down the page.
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

_

---

### Post by wcipolli on 2011-03-11
My boot option is different. It doesn't show the options along the bottom here is my boot menu.

Here's a photo of my screen:
[https://docs.google.com/leaf?id=0B3QVnLcW9eSjYWNjZjUwNGEtZWIyZC00ZjBiLWIwNGItMzQ2NWY4MDhiYWU5&sort=name&layout=list&num=50](https://docs.google.com/leaf?id=0B3QVnLcW9eSjYWNjZjUwNGEtZWIyZC00ZjBiLWIwNGItMzQ2NWY4MDhiYWU5&sort=name&layout=list&num=50)

Sorry for the quality. First line says try without installing.

That tutorial doesn't apply to this and I cant figure it out.

What should I do from here?

---

### Post by Dutch70 on 2011-03-11
Your link doesn't work. The way to attach a picture is with the paper clip in the toolbar when you post. 

Did you read the link I gave you, or just skim read it?

---

### Post by wcipolli on 2011-03-11
I read it, it just doesn't apply to the screen I'm reading. F6 doesn't do anything.
Hopefully the attachment worked!

---

### Post by Hedgehog1 on 2011-03-11
***Isn't this the menu of the Alternate Installer without the LiveCD?***

wcipolli,

The iso with the 'try' option is here:

[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

We call it a LiveCD (or a LiveUSB if you install it that way).

Please use the LiveCD image, and then you can 'TRY' Ubuntu off the CD/USB, and we can also use the 'TRY' mode to inspect your PC before the install.

***The Hedge***

:KS

p.s. It will look like this if you have the right one:

[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/trial_01_medium.jpg[/IMG]

[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/trial_02_medium.jpg[/IMG]

---

### Post by wcipolli on 2011-03-11
This is where I downloaded originally, I also followed the USB making instructions. I'll try again, but I think I'll fall in the same spot.

---

### Post by wcipolli on 2011-03-11
Yes, when I initiate the download of 10.10 it creates a download of the same file. Is there a special iso I should download or just the generic 10.10?

---

### Post by Dutch70 on 2011-03-12
> **wcipolli said:**
> Yes, when I initiate the download of 10.10 it creates a download of the same file. Is there a special iso I should download or just the generic 10.10?

Several things can go wrong when getting the download & putting it on a cd/usb. Did you check the md5sum? 
[[COLOR="Blue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
Or you may just want to try another download.

Also I don't think you listed your pc specs, but there could be an incompatibility issue, in which case you may want to try Xubuntu. 
[[COLOR="Blue"]http://www.xubuntu.org/getubuntu[/COLOR]]("http://www.xubuntu.org/getubuntu")

Kind regards

---

### Post by wcipolli on 2011-03-12
Lenovo u160 - Intel i7 Processor, 500GB HD, 4GB DDR3 Memory, Intel Graphics Media Accelerator

Does XUbuntu have the same features? I will try that later tonight or tomorrow if I don't hear any other solutions.

Thanks!

---

### Post by wcipolli on 2011-03-12
By the way MD5SUM is a ok.

---

### Post by wcipolli on 2011-03-13
We made some progress, it shows the same start up except now xubuntu is the header. I hit run from usb stick a white screen flashes with a blinking underscore like a terminal and then it black screens again. Any idea of what I could do? Maybe I'll try to call lenovo and see what they have to say. Is there any information I can give that can help in the diagnosis of this issue?

Thanks!

---

### Post by wcipolli on 2011-03-13
I just tried xubuntu as well that doesn't bring up a  boot menu, just one line on a command prompt something like syslinux and copyright info.

What do you think about this? I have no idea how I could install that other thing without being able to boot it.

[http://lenrek.wordpress.com/2010/09/09/ubuntu-lucid-lynx-10-04-and-lenovo-ideapad-u460/](http://lenrek.wordpress.com/2010/09/09/ubuntu-lucid-lynx-10-04-and-lenovo-ideapad-u460/)

I also tried to do the discrete graphics. Hitting F2 on boot up did no help.

---

### Post by Dutch70 on 2011-03-13
This seems to be a bug, have you checked launchpad? check the following links for info & pay particular attention to the 2nd to the last post by greybeard in the 1st link.
good luck

[[COLOR="Blue"]http://ubuntuforums.org/archive/index.php/t-1393413.html[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-1393413.html")
[[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/608907[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/608907")
[[COLOR="Blue"]https://bugs.launchpad.net/gentoo/+bug/554569[/COLOR]]("https://bugs.launchpad.net/gentoo/+bug/554569")

---

### Post by wcipolli on 2011-03-14
I just tried ubuntu natty 11.04, works like a champ off of the USB. I think I'll take the chances of bugs for a usable version that I needed asap.

Thanks for all the help!

---

### Post by Dutch70 on 2011-03-14
Well, glad to you hear you've chosen a development release. That gives you the opportunity to help prevent others from running into the same problem with 11.04 that you did with 10.10. As long as you take the time to report the bugs.

Just a heads up... On my system, one day it works beautifully. The next day Ubuntu One opens & crashes repeatedly on its own, Nautilus won't open at all. Some things open & won't close, and it's just basically unusable that day, and there is no one to help you with it, as it is a development release.

That being said, we're almost done with the Alpha releases.
Beta 1 comes out March 31st.
Beta 2 comes out April 14th
Ubuntu 11.04 scheduled for release on April 28th. They'll have to get really close to that date... or it will be Ubuntu 11.05 :wink:

---

