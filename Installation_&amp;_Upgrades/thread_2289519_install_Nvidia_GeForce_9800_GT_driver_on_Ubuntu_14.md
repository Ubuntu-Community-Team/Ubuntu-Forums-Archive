---
title: "install Nvidia GeForce 9800 GT driver on Ubuntu 14.04 64bit Unity"
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by morbo2 on 2015-08-04
a driver is downloaded from Nvidia official website through the recommended driver search on the website.  

The file name is called "NVIDIA-Linux-x86_64-340.76.run"

Now, I am really new to Linux and I don't have much experience of computer operation system in general.  I don't want to screw my Ubuntu 14.04 up by installing the wrong file or by incorrect procedure.  I've installed 14.04 more than 3 times this week....

It's showing I'm using the open source driver  x.org X server in the "additional driver section" of "software and upgrade section".  I haven't install any driver for my video card prior to downloading the 341.76 version of Nvidia driver.

Can someone guide me thruogh the installation process using Synaptic??
Please explain the complete procedure of doing it with easy understanding terms due to my lack of computer related knowledge.
Thank you so much for your patience... :)

---

### Post by Vladlenin5000 on 2015-08-04
Do NOT do what you're about to do.
Just select the recommended proprietary driver in in Additional driver, apply, let it download and install automatically for your convenience. Reboot. Done.

---

### Post by oldfred on 2015-08-05
While the 340.xx is the last update for your nVidia card you can use the newest version in the Ubuntu repository.
This screen shot was from my older install with 9600GT.

---

### Post by morbo2 on 2015-08-05
There are a few similar drivers in the additional driver section of software and update.

one of them is 
Nvidia binary driver - version 331.38 from nvidia-331-updates (Proprietary)
the other one is 
Nvidia binary driver - version 331.38 from nvidia-331 (Proprietary, tested)

What are the difference of these two?  
it seems like the only difference is the "updates" part
what's the updates mean here?
Should I just go with the one it's being tested?

---

### Post by morbo2 on 2015-08-05
I have 331.38 from nvidia-331 (tested) and 331.38 from nvidia-331-updates
which one should I go for?
is the one with the word "updates" the newest one but hasn't been tested by ubuntu?
Is that what it means??

thanks

---

### Post by grahammechanical on 2015-08-05
You seem to be in a simliar situation to me where our video cards are now considered obsolete by Nvidia and are no longer supported by the newest Nvidia drivers. Newer versions of Ubuntu come with newer versions of proprietary video drivers and if those drivers do not support our video card the installer uses the open source video driver. For Nvidia cards that is called Nouveau.

I have Nvidia GT220 and Additional Drivers offers me Nvidia legacy driver 304.125 and 340.76 both "tested" and "updates." Neither of which are listed "legacy." But I am taking no chances. I am using legacy driver 304.125 and it works well with Ubuntu 15.10 and the new Linux kernel 4.0 series.

Best to play safe. Install the "tested" version. And become familiar with Recovery mode before experimenting further. Advanced Options for Ubuntu>recovery mode>Resume. You may need Recovery mode to get to a usable desktop. Or, stick with Nouveau. I only stopped using Nouveau because I was getting GPU lockup (freezing) when selecting large blocks of text in Libreoffice documents. And I needed to select large blocks of text.

Regards.

---

### Post by oldfred on 2015-08-05
The 340.xx driver is now a legacy driver. They announced a year or more ago before 340.xx version was even released it would be the last version for many not so old cards.
But any driver released after the card that is in repository should work, but you want the newest up to the last version that is released for your card or the legacy driver.

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Only if you have an brand new just released video card like all the Maxwell family would you need a nVidia driver that is newer than the versions available in the Ubuntu repository. But there are several ppa or private archives where users compile the newest drivers and make them easily available, just as easy as Ubuntu's archives.

---

### Post by SeijiSensei on 2015-08-05
I still see nvidia-304 in the repositories for 14.04, which is the driver I used successfully with a 9500GT card.  
```

sudo apt-get update
sudo apt-get install nvidia-304

```

---

### Post by morbo2 on 2015-08-05
What's a legacy driver? 
I don't really play any games so I guess I don't need a video card with the most efficient driver
As long as I will be able to browse the web and process some text documents for python
I'll just stick with the tested driver for now and learn a bit about safe mode before I proceed any further then.
Thank you all, you have been a great help in this situation as it's a bit frighten without much support and knowledge of Linux
Thank you so much~!!

---

### Post by morbo2 on 2015-08-05
Would you happen to know if I need to remove the driver I am currently using at the moment?

The Nouveau open source driver is currently being selected as my driver right now.

I haven't install anything other than Nouveau

Any precaution should be taken before I install the tested 340.76 nVidia driver?

---

### Post by oldfred on 2015-08-05
If you install any nVidia driver, you must totally purge it before installing another nVidia driver.
And do not install from nVidia .run file. Only from Ubuntu repository or from a ppa.

Legacy driver means it has stopped updates. If they find a major security issue they will release fixes to that version. Big part of that is that newer driver is for newer cards and have many newer features. New driver may then not really work on older card.
       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by morbo2 on 2015-08-06
I see, thanks a lotI've learned a lot
I'm installing the driver from software and update
it's really a long and slow process.....
But I really needed to do it.....
My screen is showing black patch from the context menu drop down section or the google book mark selection menu
can't really browse the web like this....
nonetheless, thank you for your help!!
I really appreciate this :)

---

