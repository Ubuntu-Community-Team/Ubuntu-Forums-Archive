---
title: "[SOLVED] ESC key not launching GRUB menu"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by masonfoley on 2008-06-30
Hardy Heron distro.

My system recently was upgraded to images .18 and .19, neither of which allow my networking interface to load and .19, the display manager doesn't load. It is forced into a "normal boot" (i.e. command line prompt).  Haven't had the patience or time to troubleshoot why it's broken but loading into the .16 version of the kernel is my last known working image and I was able to select that from the GRUB menu.

However now, for some inexplicable reason, pressing the ESC key does nothing during the GRUB countdown prompt.  The system simply performs it's countdown and chooses to boot the latest image.  I've attempted quite a few reboots and time and time again, the ESC key does not interrupt the GRUB countdown.

I'm 99.9% certain that the ESC key works as it functions within my BIOS setup.

Any troubleshooting tips for this?

---

### Post by lukjad on 2008-06-30
> **masonfoley said:**
> Hardy Heron distro.

My system recently was upgraded to images .18 and .19, neither of which allow my networking interface to load and .19, the display manager doesn't load. It is forced into a "normal boot" (i.e. command line prompt).  Haven't had the patience or time to troubleshoot why it's broken but loading into the .16 version of the kernel is my last known working image and I was able to select that from the GRUB menu.

However now, for some inexplicable reason, pressing the ESC key does nothing during the GRUB countdown prompt.  The system simply performs it's countdown and chooses to boot the latest image.  I've attempted quite a few reboots and time and time again, the ESC key does not interrupt the GRUB countdown.

I'm 99.9% certain that the ESC key works as it functions within my BIOS setup.

Any troubleshooting tips for this?

Well the only thing I can think of is:

Super Grub Disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

I have no experience working with  this but it might fix your problem.

TEENpup ([http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/TeenPup-31563.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/TeenPup-31563.shtml))

If you can't seem to access your files try TEENpup live CD. You can mount all your drives, copy them to another media type and then go and make a fresh install of Ubuntu. While in TEENpup you can surf the 'net to find any other help you need. There is even a version of GAIM so you can chat with your friends/tech-friends.

SLAX ([http://www.slax.org/get_slax.php](http://www.slax.org/get_slax.php))

Like Puppy Linux (TEENpup and others) this will run off of a CD. This will also run off of a USB key if you so desire. Useful and perhaps more to your liking.

***For the live CDs or USB keys make sure you set the BIOS to let the computer boot off them.

Hope this helps.

______________
EDIT
Is it possible that you just aren't hitting the Esc key too early or too late? Just a thought.

---

### Post by lukjad on 2008-06-30
Just another thought. You wouldn't happen to be running Vista on a dual boot? I heard there are problem along that line.

---

### Post by masonfoley on 2008-06-30
I attempted to use Super Grub Disk (I actually already had this tool...thanks for the hint to use it), however, the keyboard is totally inoperable within its menu.  

And before the question is asked, I've tried two different keyboards.  Both of which I know function in their entirety in another environment.

So, I'm either thinking there is something up with the version of GRUB I have or my USB ports aren't cooperating (the latter being highly unlikely).  

Or...for some unknown reason, my keyboard locale map got all hosed or switched up on me?

---

### Post by masonfoley on 2008-06-30
> **lukjad007 said:**
> Just another thought. You wouldn't happen to be running Vista on a dual boot? I heard there are problem along that line.

No, this is a straight up Kubuntu/Linux install, no other OS's on the box.

---

### Post by lukjad on 2008-06-30
> **masonfoley said:**
> No, this is a straight up Kubuntu/Linux install, no other OS's on the box.

Hmmmm... Have you tried the TEENpup or SLAX CDs? 

Also, what type of keyboards/keyboard layouts do you have? Are they really weird or rare?

Regardless, do the keyboard(s) work in the live CDs?

---

### Post by abn91c on 2008-06-30
if you are using an USB keyboard check your bios to enable USB in DOS setting  before you go reformmating/reinstalling.

---

### Post by masonfoley on 2008-06-30
> **lukjad007 said:**
> Hmmmm... Have you tried the TEENpup or SLAX CDs? 

Also, what type of keyboards/keyboard layouts do you have? Are they really weird or rare?

Regardless, do the keyboard(s) work in the live CDs?

The keyboard works anywhere and everywhere but GRUB (and the Super Grub boot CD).  The keyboard currently works within my current booted environment for example (.19 image that doesn't boot into the graphical environment).  Again, just not during the GRUB sequence.

Another reason why I believe the keyboard is fully functional is I use the keyboard to navigate MythTV.  The way I exit out of the application is to use a series of the ESC key presses (the number of which depends on where or how deep within the menu hierarchy I am.) 

And yet another reason why I feel there's nothing wrong with the keyboard, I'm able to launch into the BIOS configuration.  And I'm even able to use the ESC key there  (i.e. "Exit w/o saving changes?  y/n" which is the prompt I receive after hitting the ESC key from within BIOS). 

And I believe it's worth repeating, both keyboards (and their respective ESC key) work on my other systems.

My keyboard locale (at the time of installation was/is US-English or something like that.  And as far as I know, I've made no changes to this (besides, the more I think about it, I don't see how the keyboard locale has any bearing or control over the keyboard before actually booting the OS.  I could be wrong))

I have not tried the other CDs you recommend but will look into it when I have more time this evening.

---

### Post by masonfoley on 2008-06-30
> **abn91c said:**
> if you are using an USB keyboard check your bios to enable USB in DOS setting  before you go reformmating/reinstalling.

I'm not aware of this setting but I will look for it.  I'm wondering if it would make any difference if the keyboard works everywhere else in the system (i.e. entering BIOS, CTRL-ALT-DEL to reboot the system, etc.)

---

### Post by masonfoley on 2008-06-30
> **masonfoley said:**
> I'm not aware of this setting but I will look for it.  I'm wondering if it would make any difference if the keyboard works everywhere else in the system (i.e. entering BIOS, CTRL-ALT-DEL to reboot the system, etc.)

I'll be dadgummed.  There was a setting for "USB Keyboard Support" and I enabled it, saved the BIOS, rebooted and sure enough, was able to get into the GRUB menu and select the working image.

Many thanks abn91c.  Goes to show anything is worth a try.  (Although a bit confusing since the keyboard was functional in other aspects - i.e. getting into and navigating the BIOS, CTRL-ALT-DEL, etc.)

---

### Post by abn91c on 2008-06-30
you are welcome masonfoley, it is just that it sometimes takes a bit longer in kubuntu to find all the hardware and that is why you could not get into grub before:D

---

### Post by lukjad on 2008-07-01
Remember to mark this thread as solved. (PS Don't forget to thank abn91c for the tip.) Glad this was resolved.

---

### Post by masonfoley on 2008-07-01
> **lukjad007 said:**
> Remember to mark this thread as solved. (PS Don't forget to thank abn91c for the tip.) Glad this was resolved.

I've done both....or so I thought

Editing the subject to include the string "[SOLVED]" does not propagate into the forum listing of topics.  Is there another way to do this?

It was my assumption all along that the forum software parses for "thank yous" and related the "thanks" to the username referred to in the post to where the thanks occurred.

If this is not how this is done, can you point me to some documentation that explains how to do both?

Thanks

EDIT:  I figured out how to mark as solved.  Still would appreciate how to properly thank someone.

---

### Post by gluer_2 on 2008-07-06
thanks. worked for me too!

---

