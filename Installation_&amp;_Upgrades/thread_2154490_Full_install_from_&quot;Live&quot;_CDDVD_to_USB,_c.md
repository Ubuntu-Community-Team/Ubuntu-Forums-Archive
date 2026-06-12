---
title: "Full install from &quot;Live&quot; CD/DVD to USB, could it be that easy?"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by TNFrank on 2013-06-14
I did a search on the forum about making a "Live" USB thumb drive for Ubuntu that would be persistent so any upgrades or changes would actually stick just like in a "real" hard drive.  
 I saw that many simply used a "Live" CD or DVD of the Op System that they wanted and did the full install to a USB thumb drive and with that the USB thumb drive would act just like a normal install on a hard drive.  Could it be that easy?
    I have a 32GB Kingston USB drive that I'd like to use to make up with a distro like Ubuntu or maybe Peppermint so I could take it with me and basically have an Op System that I could plug into any computer and be on my own familiar desktop no matter where I was at.
 As long as the Op System is under say, 6o0MB that'd be small enough to fit onto a CD which I could make a "Live" CD by using Startup Disk Creator then once it boots I can do a full install to my sdg where my USB would be at, kind of like installing it on a little SSHD(solid state hard drive) then it'd take updates and changes just like a normal hard drive would.
 Do I have this right, could it really be that easy? If so what distro would ya'll recommend that would be close to the 12.04 that I'm using now only small enough to stick onto a CD? Thanks in advance for any help and thanks for putting up with all my noobie questions, I know I've had a bunch of em' and ya'll have be really great at helping "the new guy" learn to really Love Linux. ;)

P.S.S.
I just noticed that Peppermint Four is out and it's only 588MB, more then small enough to fit onto a CD. I think that'd be the one I'll go with. 

P.S. 
Just noticed Lubuntu, so what do ya'll think, it's  687MB so it shoud fit onto a CD and it's Ubuntu based, would that be a winner In ya'll opinion?

---

### Post by TNFrank on 2013-06-14
Well, even at 588MB neither UNetbootin or Startup Disk Creator would see the CD as a means of installing Peppermint Four. I tried to go from one USB to the other for a full install but that was also a no go. :confused:

---

### Post by ahallubuntu on 2013-06-14
~

---

### Post by ubfan1 on 2013-06-14
It's really that easy, but there are some performance optimizations which make the stick a lot nicer to use -- see  [http://www.systemateka.com/usbboot.html](http://www.systemateka.com/usbboot.html)  The usb to usb should work, but there is a known problem with the initial boot of the target, the grub.cfg devices are frequently mixed up, because when the grub.cfg was written, there was an additional usb on the system (the install media) (bug384633).  Manually fix the grub commands and at the first successful boot, immediately run sudo update-grub to fix things.  I have to admit, most of my experience is setting up 4G sticks, with an occasional 8G.  Only had problems with an 8G USB3, corrupted filesystem, could have been a machine problem, since a tar copy of the OS from a successful 4G also had corruption.  The copy did work on an older machine however, so don't know if it was the stick or machine or both.

---

### Post by TNFrank on 2013-06-15
The question was about making a USB thumb act like an actual hard drive in the computer so that the OS will keep all the updates, additions and everything just like my laptop does now so that if I modify something on the USB, say I add ClamTK to the OS, it'll still be there the next time I boot to it. 
Someone here was saying that you can use the Live CD/DVD to do a full install but instead of installing to the hard drive you install to a USB which in turn will act just like a hard drive and keep the info and mods you add. ;)

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by oldfred on 2013-06-15
I have a full install in an 8GB partition on my 16GB flash drive. With some extra settings to reduce writes it works reasonable well. Not speedy but once an app is loaded into RAM there is no speed difference.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by snowpine on 2013-06-15
A drive is a drive; Ubuntu doesn't care whether it is physically internal to the machine, or sticking out of a USB port.

---

### Post by TNFrank on 2013-06-15
I've just been using a copy of 12.04 that I installed onto the 8GB USB thumb drive with  2GB set aside for file saving and it IS persistent. I'd doing pretty much what I wanted it to do which is act and feel just like my install on my hard drive.  I think this is going to work out ok.

---

