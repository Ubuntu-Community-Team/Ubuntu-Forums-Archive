---
title: "Blank screen even in recovery mode"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by S6I6X on 2011-02-06
Hello,
i have the same blank screen after start up (due to my ati video card) as everyone else and i know i can fix it if i can get to the gui in safe mode. when i try to boot in safe mode i get the blank screen again.

i have read a ton of threads by now and searched all over the internet and every solution that has worked for other people either didnt work for me or i dont have the right options available to do it.

also i installed ubuntu 64 bit with the alternate installer.

thanks in advance.

---

### Post by mörgæs on 2011-02-07
If you know how to fix it, you can boot with a live CD and apply the changes.

---

### Post by efflandt on 2011-02-07
You didn't say which nvidia card/chip you have, or which Ubuntu version you are installing.

For legacy (old) ATI X1300 (desktop or mobile), I had to use **nomodeset** kernel boot parameter for Lucid (10.04) when Ubuntu switched from user space modules to kernel mode setting (kms) as a default.  Although, that does not seem to be required or a problem in Maverick (10.10), so maybe that was worked around automatically in Maverick.

I don't have any computer with newer ATI video, so not sure if they have issues with default drivers.

If you are trying to install Natty, that is just under "development", and there is a different forum for that lower on the list of forums.

---

### Post by S6I6X on 2011-02-07
I have tried it with Ubuntu 10.4 and 10.10. To use the live CD trick do I need to do a fresh install? I know how to get it to work with the live CD to but once I actually installed it and rebooted it did it again. I did try to install the video drivers only because I thought it would keep the changes but it failed. I am starting to think that might have negated the xforcevesa I initially used.

And thanks for the replies!

---

### Post by S6I6X on 2011-02-07
Oh, and I have an ATI Radeon HD 5770 video card. I am trying to do a 64 bit fresh install. I have the 32 bit 10.4 installed right now and I remember having all sorts of trouble getting it installed before but I think I ended up just installing like 9.10 or something (which never got the blank screen problem), installing the drivers and then upgrading.

---

### Post by mörgæs on 2011-02-08
The ATI cards should run without trouble using the open source drivers. Closed source can be a problem, but you might find some help here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by P4man on 2011-02-08
If your videocard needs nomodeset, see the link in my signature how to set it and solve the black screen problem.

---

### Post by S6I6X on 2011-02-08
Ok, so I tried installing 10.10 again this time I just used the live CD but I went strait to the install part and replaced the quiet splash with xforcevesa and I was able to complete the install normally (which I couldn't do without the xforcevesa). When it restarted after install it just showed this code:
[   5.211729] k10temp 0000:00:18.3: unreliable CPU thermal sensor;monitoring disabled

It just flashed a little cursor thingy for a while before the screen went completely black.

---

### Post by P4man on 2011-02-08
Have you tried nomodeset as per my link?

---

### Post by S6I6X on 2011-02-08
Ok, so I tried the exact way it was in your link and it worked! I tried it before but slightly different, partly due to other threads, and partly due to a vague remembrance of the last time I had the same problem. I didn't realise until I read your thread that the changes weren't permanent. I was able to get the already installed version to load and install the video drivers so now it runs like a champ! 

Once again thanks!

---

### Post by S6I6X on 2011-02-13
Sigh, I tried the nomodeset in your signature but I haven't had time to get around to making it permanent. Everything was working fine and I was even about to delete my old install bc I was so confident in my machine. Now it is doing the same exact thing as before... except the nomodeset doesn't work. Do you think I might have somehow messed up my bios? The only thing I can think of that changed was that I updated it. 

...so close! lol

---

### Post by P4man on 2011-02-14
You probably didnt make it permanent the right way. You might have edited grub.cfg, which works, until you do a (kernel) update. Then that file gets overwritten again. Please, read the link in my signature carefully.

---

### Post by S6I6X on 2011-02-14
No, what I am saying is that I never made it permanent at all. I hadn't gotten around to it. I was just doing it at start up every time temporarily but it just stopped working.

---

### Post by S6I6X on 2011-02-15
I got it to start in low graphics mode using "nomodeset single". I went in and changed the parameters to make "nomodeset" permanent. After that I don't know what to do. The image attached is what my screen looks like when it gets stuck.

---

### Post by S6I6X on 2011-02-15
I don't know why it put the picture upside down but hopefully this fixes it. 
*Edit No matter what I do it puts the picture upside down. I tried uploading the original right side up and upside down to no avail... sorry.

---

### Post by P4man on 2011-02-15
What motherboard is this?
Can you try disabling hpet in the bios, or boot with
```
hpet=disable
```
kernel option?

---

### Post by S6I6X on 2011-02-17
I tried just putting the code into the boot manager or whatever but it didn't do anything. I then changed it in my bios and it is starting every other time. I don't know why. I only tried the putting it in the boot manager once but in hind sight it might be bc it only works every other time. I know that sounds super weird but I tested it a bunch of times and its been the same so far. I am super baffled. Do you know of anything that would do that? I guess its better than it not working at all.

---

### Post by P4man on 2011-02-18
Can you post another screenshot now when it fails to boot? Make sure you remove "quiet" and "splash" boot options so we can see whats going on.

Then Id check for a bios update first and foremost. If you want to try working around it with kernel options, my signature has a link to a page giving a few you can experiment with. noapic and nolapic would be among the top of my list, but the acpi_osi ones are worth trying as well. And make sure you have nomodeset in there as well, as your videocard seems to need it.

---

