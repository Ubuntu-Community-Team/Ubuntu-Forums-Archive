---
title: "Why Has Installation Been Made So Difficult?"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by cosmarchy on 2012-08-25
What is it with installaion on 'abmornal' systems been made so complicated?
 
By abnormal, I mean it doesn't have a cdrom (probabily not all that uncommon nowadays?).
 
I've created a usb key which boots and runs through the menus fine until it gets to the point where I get an error:
 
```
There was a problem reading from the cd-rom. please make sure it is in the drive.......
 
failed to copy file from cd-rom
```
 
So, I do a bit of looking around and find an article here [http://ubuntuforums.org/showthread.php?t=1550317](http://ubuntuforums.org/showthread.php?t=1550317).  After trying these commands ```
mkdir /mnt/usb /mnt/iso
mount –t vfat /dev/<usb drive partition device file> /mnt/usb
``` I am unhelpfully informed ```
mount: mounting /dev/sda on /mnt/usb failed: device or resource busy
```
 
So I am now left with a problem.  The solution to which, go only knows.
 
What I cannot understand is why I get the error with the cdrom in the first place.  Yes, I am aware I don't actually have one but the fact I made the usb key from an ISO file detailed here [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) you would have thought there would be some mention of this error or a get around or something.
 
It doesn't inspire people to use and learn linux, in fact it is encouraging a lot of people to go straight back to Windows.

---

### Post by MG&amp;TL on 2012-08-25
I only get this problem with a server installation-are you trying a server or a desktop?

Feel free to "go back to Windows"-use whatever is currently working for you.

---

### Post by cosmarchy on 2012-08-25
> **MG&TL said:**
> I only get this problem with a server installation-are you trying a server or a desktop?
 
Feel free to "go back to Windows"-use whatever is currently working for you.
 
I am trying to install a server.
 
It's a shame really.  As a company we are looking to do a 1000+ pc install of ubuntu because we were led to believe this is a better option and therefore willing to try this and see what whether it actually was better.  
 
We are in the process of looking for paid support  but I'm not so sure we need to continue with this - we have to be able to do some things ourselves but if we cannot even install the product then we are off to a non starter ):P

---

### Post by MG&amp;TL on 2012-08-25
> **cosmarchy said:**
> I am trying to install a server.
 
It's a shame really.  As a company we are looking to do a 1000+ pc install of ubuntu because we were led to believe this is a better option and therefore willing to try this and see what whether it actually was better.  
 
We are in the process of looking for paid support  but I'm not so sure we need to continue with this - we have to be able to do some things ourselves but if we cannot even install the product then we are off to a non starter ):P

Wow, that's a lot of PCs. If you're looking at that sort of scale, paid support might be a good idea regardless of whether you're having trouble or not. *In my opinion* Ubuntu is a better option as it's more flexible, scalable, and works better as a server. (Also, how much does 1,000 Windows licenses cost?) Bear in mind with that sort of network, you'll probably need at least one dedicated system administrator.

It is certainly possible (done it myself at some point), but I confess I can't remember how I did it, or why it's not been fixed yet. Have you seen this thread: [http://ubuntuforums.org/showthread.php?t=1750464](http://ubuntuforums.org/showthread.php?t=1750464) ?

---

### Post by darkod on 2012-08-25
You are actually VERY helpfully informed that /dev/sda can't be mounted. In the instructions that yourself quoted it says <drive partition> not just <drive>.

/dev/sda is the usb stick (drive), under the assumption it's really /dev/sda and not /dev/sdb or other.

/dev/sda1 would be the first partition on it, if you have only one partition on the stick it would be the only one.

So, you need to mount /dev/sda1 (or /dev/sdb1, etc) and NOT /dev/sda.

It works very well, I have installed server OS like that on a machine with no cd-rom.

---

### Post by Lars Noodén on 2012-08-25
If the problem is with the server image, it might be worth raising a bug report before trying a different image.  CD/DVD drives are becoming increasingly rare.  I would not be surprised if they disappear completely from default hardware configurations during the next 4 years.  

Right now you could try another image.  The Alternate install disc has the option to install a 'Command Line' system.  That gives a bare bones system suitable for a server.  If you want you could even add the server kernel.

---

### Post by cosmarchy on 2012-08-25
Yep this is a big undertaking :eek: which is why are trying to walk before running!!  
 
We would have been looking for a administrator with linux experience (as most of our people have experiece with windows) in conjunction with the support.  
 
Yep, the cost of windows licenses will be high but compare that cost to having a business that has functioning computers :p
 
Thanks for the link.  I had seen it (and others like it which give the same details)....and i've tried everything; 'cdrom-detect/try-usb=true', mounting iso as cd, the lot.
 
The biggest problem is when I try to mount the usb key I get this error:
```
mount: mounting /dev/sda on /mnt/usb failed: device or resource busy
```

---

### Post by darkod on 2012-08-25
> **cosmarchy said:**
> 
 
The biggest problem is when I try to mount the usb key I get this error:
```
mount: mounting /dev/sda on /mnt/usb failed: device or resource busy
```

Look at post #5. It seems you are only reading email notifications. Visit the forum since by email you are missing posts (replies).

---

### Post by SeijiSensei on 2012-08-25
Once you get over the hump, I recommend installing the client machines [over the network]("https://help.ubuntu.com/community/Installation#Server_and_network_installations").  You can create a Clonezilla image of your standard machine, mount the ISO image on a server, and install from there.

---

### Post by cosmarchy on 2012-08-25
> **SeijiSensei said:**
> Once you get over the hump, I recommend installing the client machines [over the network]("https://help.ubuntu.com/community/Installation#Server_and_network_installations"). You can create a Clonezilla image of your standard machine, mount the ISO image on a server, and install from there.
 
When booting from usb image there is no option to boot from network or pxe server etc so this is out of the question.
 
> **darkod said:**
> Look at post #5. It seems you are only reading email notifications. Visit the forum since by email you are missing posts (replies).
 
Even when I try SDA1 instead of SDA, I still get the same error!!

---

### Post by darkod on 2012-08-25
> **cosmarchy said:**
> 
Even when I try SDA1 instead of SDA, I still get the same error!!

Are you sure that the usb is /dev/sda1 then?

And are you sure it's not already mounted anywhere? You can't try to mount already mounted partition.

I have used that exact process to install ubuntu server from usb and it works without problems. You are either doing something wrong or there is some other problem.

---

### Post by lbcadden3 on 2012-08-25
Do the systems have the ability to pxe boot?

With that many systems I hope so and if so you should start testing now.

[https://help.ubuntu.com/community/Installation/LocalNet#Advanced:_Hands-Off.2C_Preseeded_Network_Server_Install](https://help.ubuntu.com/community/Installation/LocalNet#Advanced:_Hands-Off.2C_Preseeded_Network_Server_Install)

---

