---
title: "Ubuntu Load Question"
date: 2019-04-11
forum: Installation &amp; Upgrades
---

### Post by aceofcarnesie on 2019-04-11
Newbie here. I am loading  Ubuntu 18.04 on an old lap top. It is a Thinkpad EDGE 15 .   I have downloaded the install file from the Ubuntu website and transferred it to a  USB flash Memory Stick. The laptop has no software on it except the BIOS Setup program. I reset it to also read the USB port on startup, so as to load the ubuntu from the USB Flash Memory Stick .

I then power up the laptop and it appear that nothing is loading . How do I know if this is working and if it is working correctly? The laptop is running after I power it up.

Thank you in advance for the help.

---

### Post by TheFu on 2019-04-11
You cannot just copy the ISO file over.  It needs to be placed there using one of about 20 different tools. 
If you google "ubuntu create install flash" ... a how-to guide will be found.  [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)  There are versions for OSX and Windows as well.

Or if you are not new to unix, you can use any of the bit-for-bit copy tools.
 
Also, older laptops with old GPUs will probably struggle with Gnome3, which is the default GUI for Ubuntu 18.04.  Best to use Mate, XFCE, LXDE/LXQt variants instead.  Of course, "old" means something different to everyone.  If "old" is 2013 or newer, ignore me.  If "old" is 2010 and older, definitely choose a different DE/variant.  From 2010 to 2013 ... it might work well or not. Depends.

Gnome3 and KDE and a few other of the really pretty GUIs need fast CPUs and fast GPUs.  I'm not expert enough to make suggestions for settings to reduce the requirements in those, to make them feel good on older hardware. I always use a minimal GUI.

---

### Post by aceofcarnesie on 2019-04-11
Thank you for the response . I followed the link and shows how to create an install disk on existing Ubuntu machine. I do not have one. I have a mac and windows machine .
I would prefer to do it on my mac are there tools for that ?

Is an install disk available anywhere?

Ace

---

### Post by Autodave on 2019-04-11
You can use Windows to create it.  *Unetbootin *will work.  [URL="https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwjMy9Lm_cjhAhWRuVkKHWUMAVwQFjAAegQIBxAC&url=https%3A%2F%2Funetbootin.github.io%2F&usg=AOvVaw2vVaBihYKA2QK7JBoIy25U"]https://unetbootin.github.io/
[/URL]

---

### Post by oldos2er on 2019-04-11
[https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows](https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows)

---

### Post by TheFu on 2019-04-11
> **aceofcarnesie said:**
> Thank you for the response . I followed the link and shows how to create an install disk on existing Ubuntu machine. I do not have one. I have a mac and windows machine .
I would prefer to do it on my mac are there tools for that ?


As said above ... 
> There are versions for OSX and Windows as well.
Click the link **and** read it?  On the first page are links to guides for OSX and Windows. Linux is an OS of details, but we have to pay attention.
Also, there are hundreds of guides on youtube for how to do this. 

> **aceofcarnesie said:**
> 
Is an install disk available anywhere?

The ISO file is an install disk. 
Making a bootable disc or flash drive is a basic skill. There are many reasons for this. Hopefully, you won't need it, but you probably will.  It takes 3 minutes, once you know and work through it once.

Or you can locate a LUG, take a flash drive to a meeting with a lapto, and ask them for help.
Or you can pay someone on ebay to make one and mail it.

---

### Post by aceofcarnesie on 2019-04-11
Again thank you for the response . The disk drive on my windows machine will burn or write a new cd . Do you have any other suggestions? My mac does not have a cd drive at all.

---

### Post by TheFu on 2019-04-11
> **aceofcarnesie said:**
> Again thank you for the response . The disk drive on my windows machine will burn or write a new cd . Do you have any other suggestions? My mac does not have a cd drive at all.

Follow the instructions in the links above to create a bootable flash drive.  That's how 99% of the world boots these days and does installs. I haven't burned a CD/DVD in about a decade.  Again, youtube and the links above have step-by-step instructions to accomplish this task. If that isn't sufficient, I'm at a loss. Sorry.

Or you might be able to find someone on ebay to make one and ship it to you for $10-$50.

---

### Post by aceofcarnesie on 2019-04-11
Yes, I can make a bootable flash drive . I thought you were referring to "burning" a cd. I  will follow those instruction . Thank you again,

---

### Post by oldos2er on 2019-04-12
The terminology is still "burning" to USB even though no real burning is involved. I agree it can be confusing.

---

### Post by slickymaster on 2019-04-18
Thread moved to **Installation & Upgrades** for a better fit.

Some more info on these two closed threads, as they address the same issue: [https://ubuntuforums.org/showthread.php?t=2416805](https://ubuntuforums.org/showthread.php?t=2416805) and [https://ubuntuforums.org/showthread.php?t=2416575](https://ubuntuforums.org/showthread.php?t=2416575)

---

