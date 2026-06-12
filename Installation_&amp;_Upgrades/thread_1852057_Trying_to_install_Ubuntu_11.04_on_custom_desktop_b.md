---
title: "Trying to install Ubuntu 11.04 on custom desktop but keep getting an error"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by RadiationHazard on 2011-09-29
I just put together my first custom desktop and was wanting it to be a Linux box but for some reason it doesn't want to install. The disk will act like it's starting to boot and then will run into the same error every time. I remember years back when I used to have a Linux box I ran into a similar problem and it ended up being because I was burning the disk at to high of a speed but I've tried several different low burning speeds and nothing changes so I honestly don't really know what to do from this point. Any help would be great!

thanks

**[SIZE="3"]Computer Specs[/SIZE]**
Motherboard: [http://bit.ly/qxH77e](http://bit.ly/qxH77e)
CPU: [http://bit.ly/oPZIBm](http://bit.ly/oPZIBm)
GPU: [http://bit.ly/pdQJC8](http://bit.ly/pdQJC8)
SSD: [http://bit.ly/pIcBZM](http://bit.ly/pIcBZM)
RAM: [http://bit.ly/nXXiM1](http://bit.ly/nXXiM1)
WIFI: [http://bit.ly/rtATcD](http://bit.ly/rtATcD)
BLUERAY: [http://bit.ly/qWFfst](http://bit.ly/qWFfst)

Also, here is a video of my computer booting up and exactly what is happening.

**[SIZE="3"]Video[/SIZE]**
[http://www.youtube.com/watch?v=tK0rlrMyinA](http://www.youtube.com/watch?v=tK0rlrMyinA)

---

### Post by westie457 on 2011-09-29
Hi I am probably completely wrong at guessing what the problem is, it possibly could be a graphics driver issue. Have you tried tapping Shift or Esc while the CD is starting to bring up the Menu?
When in the Main Menu press F6 to adjust the Graphics start mode - I think it is called that. Take a look [here]("http://ubuntuforums.org/showthread.php?t=1743535") for more technical help than I could ever offer.

Good luck.

---

### Post by RadiationHazard on 2011-10-06
> **westie457 said:**
> Hi I am probably completely wrong at guessing what the problem is, it possibly could be a graphics driver issue. Have you tried tapping Shift or Esc while the CD is starting to bring up the Menu?
When in the Main Menu press F6 to adjust the Graphics start mode - I think it is called that. Take a look [here]("http://ubuntuforums.org/showthread.php?t=1743535") for more technical help than I could ever offer.

Good luck.

I just tried changing those settings because I'd forgotten about them and still no luck :/ any other ideas anyone?

---

### Post by MAFoElffen on 2011-10-06
> **RadiationHazard said:**
> I just put together my first custom desktop and was wanting it to be a Linux box but for some reason it doesn't want to install. The disk will act like it's starting to boot and then will run into the same error every time. I remember years back when I used to have a Linux box I ran into a similar problem and it ended up being because I was burning the disk at to high of a speed but I've tried several different low burning speeds and nothing changes so I honestly don't really know what to do from this point. Any help would be great!
Wow... Blew out between the Userinterface screen and Initial Menu in syslinux...  Didn't even get a chance to crash on an Ubuntu kernel image!  The errors in your video look like... well you focused down the screen on where in said it terminate and dumped... But above that it had just tried to load drm and nouveau right before it blew out.

No guarantees, but I built a custom Ubuntu LiveCD ISO for new users that had Nvida GPU's and were having difficulties.  The nvidia type kernel boot options are already hardcoded into it.  You might try downloading it and giving it a try:
[http://www.4shared.com/file/ga0F9_R1/ubuntu-11041-desktop-i386-cust.html](http://www.4shared.com/file/ga0F9_R1/ubuntu-11041-desktop-i386-cust.html)

Burn the ISO onto a CD at the lowest speed.  Hope it helps with this.

EDIT-- That is a 32bit ISO... See if it boots.  If it does, I'll throw together a 64bit version.

---

### Post by RadiationHazard on 2011-10-06
> **MAFoElffen said:**
> Wow... Blew out between the Userinterface screen and Initial Menu in syslinux...  Didn't even get a chance to crash on an Ubuntu kernel image!  The errors in your video look like... well you focused down the screen on where in said it terminate and dumped... But above that it had just tried to load drm and nouveau right before it blew out.

No guarantees, but I built a custom Ubuntu LiveCD ISO for new users that had Nvida GPU's and were having difficulties.  The nvidia type kernel boot options are already hardcoded into it.  You might try downloading it and giving it a try:
[http://www.4shared.com/file/ga0F9_R1/ubuntu-11041-desktop-i386-cust.html](http://www.4shared.com/file/ga0F9_R1/ubuntu-11041-desktop-i386-cust.html)

Burn the ISO onto a CD at the lowest speed.  Hope it helps with this.

EDIT-- That is a 32bit ISO... See if it boots.  If it does, I'll throw together a 64bit version.

thanks a lot! I'll give it a shot and report back.

---

### Post by RadiationHazard on 2011-10-06
> **MAFoElffen said:**
> Wow... Blew out between the Userinterface screen and Initial Menu in syslinux...  Didn't even get a chance to crash on an Ubuntu kernel image!  The errors in your video look like... well you focused down the screen on where in said it terminate and dumped... But above that it had just tried to load drm and nouveau right before it blew out.

No guarantees, but I built a custom Ubuntu LiveCD ISO for new users that had Nvida GPU's and were having difficulties.  The nvidia type kernel boot options are already hardcoded into it.  You might try downloading it and giving it a try:
[http://www.4shared.com/file/ga0F9_R1/ubuntu-11041-desktop-i386-cust.html](http://www.4shared.com/file/ga0F9_R1/ubuntu-11041-desktop-i386-cust.html)

Burn the ISO onto a CD at the lowest speed.  Hope it helps with this.

EDIT-- That is a 32bit ISO... See if it boots.  If it does, I'll throw together a 64bit version.

Okay, so we're making progress. now it sits on the blinking cursor screen for about 15-20 seconds and then acts like it's starting to boot showing the Ubuntu with the four dots under it and then after about 30 seconds on that screen I get the error in the image below?

[http://i138.photobucket.com/albums/q263/newkidrocks/IMG_20111006_220004.jpg](http://i138.photobucket.com/albums/q263/newkidrocks/IMG_20111006_220004.jpg)

---

### Post by MAFoElffen on 2011-10-07
> **RadiationHazard said:**
> Okay, so we're making progress. now it sits on the blinking cursor screen for about 15-20 seconds and then acts like it's starting to boot showing the Ubuntu with the four dots under it and then after about 30 seconds on that screen I get the error in the image below?

[http://i138.photobucket.com/albums/q263/newkidrocks/IMG_20111006_220004.jpg](http://i138.photobucket.com/albums/q263/newkidrocks/IMG_20111006_220004.jpg)
"unable to find a medium containing a live file system" is usually a Linux USB boot error... Are you trying to install via a USB?  Did you creat the LiveCD bootable USB from Win7 or Windows Vista? Thats a common error when creating a live-usb with Unetbootin from Windows (Vista/7)

---

### Post by MAFoElffen on 2011-10-07
> **MAFoElffen said:**
> "unable to find a medium containing a live file system" is usually a Linux USB boot error... Are you trying to install via a USB?  Did you creat the LiveCD bootable USB from Win7 or Windows Vista? Thats a common error when creating a live-usb with Unetbootin from Windows (Vista/7)
Sorry- previous post was too focused.  After hours...  Sonewhere I think the tidbits below tie this all together. 

Checked into this deeper--- Seems like there is some other common causes for this error message. 
On ISO itself:
- Bad download of ISO. (md5sum)
On CD:
- Burn at slowest speed...
- Dirty lens on CD/DVD drive. Bad read.
- Someone suggested it might be 2 cd/dvd drives on same channel... Was the  case on theirs.  They unplugged their second drive and was able to load their LiveCD and install.

There is somthing there... I went thru so many bug reports, such as:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774419)

One thing that worked around this for some was them just installing from an alternate-install CD... or if they were trying USB, to try CD and opposite/

One thought on your Blueray... I know it's new... If you borrowed a CD drive and plugged in to try(?)  If that ends up being the problem <> It's still on warrantee, right? That would be my concern if it was mine..

Another afterthought- Try to boot those LiveCD's from Another Box.

Enough ideas?.

---

### Post by RadiationHazard on 2011-10-07
The DVD that I burnt it on works on a friend's computer so I don't think its the disc. I'm burning the ISO at the lowest speed possible and because everything is brand new its all clean. Also I'm trying to boot from DVD not USB and I'm using imgburn to burn it on windows 7. I don't have any friends with a spare CD drive that I can borrow unfortunately.  I really hope I can figure out some way to get Linux up and running on my machine, its been to long since I last used it at like Ubuntu 7.10 I miss it. Thanks for all the helpful ideas that you've been offering 

> **MAFoElffen said:**
> Sorry- previous post was too focused.  After hours...  Sonewhere I think the tidbits below tie this all together. 

Checked into this deeper--- Seems like there is some other common causes for this error message. 
On ISO itself:
- Bad download of ISO. (md5sum)
On CD:
- Burn at slowest speed...
- Dirty lens on CD/DVD drive. Bad read.
- Someone suggested it might be 2 cd/dvd drives on same channel... Was the  case on theirs.  They unplugged their second drive and was able to load their LiveCD and install.

There is somthing there... I went thru so many bug reports, such as:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774419)

One thing that worked around this for some was them just installing from an alternate-install CD... or if they were trying USB, to try CD and opposite/

One thought on your Blueray... I know it's new... If you borrowed a CD drive and plugged in to try(?)  If that ends up being the problem <> It's still on warrantee, right? That would be my concern if it was mine..

Another afterthought- Try to boot those LiveCD's from Another Box.

Enough ideas?.

---

### Post by MAFoElffen on 2011-10-07
> **RadiationHazard said:**
> The DVD that I burnt it on works on a friend's computer so I don't think its the disc. I'm burning the ISO at the lowest speed possible and because everything is brand new its all clean. Also I'm trying to boot from DVD not USB and I'm using imgburn to burn it on windows 7. I don't have any friends with a spare CD drive that I can borrow unfortunately.  I really hope I can figure out some way to get Linux up and running on my machine, its been to long since I last used it at like Ubuntu 7.10 I miss it. Thanks for all the helpful ideas that you've been offering

You missed one of the tidbits in that post...  Try to install from the launchpad workaround for that error--> install from an Ubuntu Alternate Instillation CD ..

That was a workaround that is tied to an upstream bug in Novell:casper... Having to do with devices not getting or losing their "mount."  

If one of those where true, if you fail again with CD, you could try USB(?)

--- You got so close with that custom LiveCD ISO...  Just trying to help with other ideas and options...

---

### Post by RadiationHazard on 2011-10-07
> **MAFoElffen said:**
> You missed one of the tidbits in tha posrt...  Try to install from launchpad's workaround for that error--> install from an Ubuntu Alternate Instillation CD.

That was a workaround that was tied to an upstream bug in Novell: casper... Having to do with devices not getting or losing their "mount."  

If one of those where true, of you faili ahain on CD, you could try USB(?)

--- You got so close with that custom LiveCD ISO...  Just trying to help with other ideas and options...

Alright,  I will give it a shot after I get off work. We just added Unix to some of our machines which is got me wanting to play with Linux again. Hopefully that'll work. Thanks again for the suggestions!

---

### Post by MAFoElffen on 2011-10-07
> **RadiationHazard said:**
> Alright,  I will give it a shot after I get off work. We just added [COLOR=Teal]Unix[/COLOR] to some of our machines which is got me wanting to play with Linux again. Hopefully that'll work. Thanks again for the suggestions!
:p - Which flavor of Unix? (Look at my sig line below)

---

### Post by RadiationHazard on 2011-10-07
> **MAFoElffen said:**
> :p - Which flavor of Unix? (Look at my sig line below)

We have Solaris 10 running on them, not a big fan of it but it's not to bad. Also I tried the fix a [this]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875") link with no luck, I'm still getting the same error. :(
I'm going to try to install on USB sometime this weekend. If that doesn't work you're probably running out of ideas haha I really do appreciate the help though.

---

### Post by MAFoElffen on 2011-10-07
> **RadiationHazard said:**
> We have Solaris 10 running on them, not a big fan of it but it's not to bad. Also I tried the fix a [this]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875") link with no luck, I'm still getting the same error. :(
I'm going to try to install on USB sometime this weekend. If that doesn't work you're probably running out of ideas haha I really do appreciate the help though.
Will keep an eye out....

---

### Post by RadiationHazard on 2011-10-21
Alright, well I've tried installing from a usb and all it does is go to a blank screen and then it doesn't do anything else... :confused:

---

### Post by RadiationHazard on 2011-10-22
PS. I've also tried the newest release of Ubuntu with no luck.

---

### Post by RadiationHazard on 2011-10-23
Anybody have any other ideas on things that I can try or should I just give up on getting Ubuntu installed on my system for now?

---

