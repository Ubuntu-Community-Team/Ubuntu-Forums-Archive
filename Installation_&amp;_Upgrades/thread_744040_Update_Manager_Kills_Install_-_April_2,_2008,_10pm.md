---
title: "Update Manager Kills Install - April 2, 2008, 10pmEDT"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by AlanB66 on 2008-04-03
Last night, while sitting on the sofa and watching TV, I was diddling around on my Ubuntu laptop. The Update Manager icon lit up and, as usual, I clicked on it to check into updates.

A huge list of items were listed AND some could not be selected. A notice that only a partial update would be performed, if at all, if I wanted to continue. 

I tried the partial install/update and it failed almost immediately. So, I went and re-ran Update Manager and unselected a few items (Ubuntu System, for one) I felt ought to be done separately.

When all was said & done and all selectable items were supposedly successfully updated, I rebooted my laptop only to never get to the login prompt ever again.

This morning I restored a PartImage-created image of my sda1 partition. Thankfully, I took this image on the 31st of March - very recently.

After restoring and rebooting quite fine, I ran Update Manager manually and got, "Your system is up to date".  OK :confused:

Now, as I type this, I turn around to see the Update Manger icon is available in my Control Bar and I just clicked on it. I'm not being informed that I can only install partial updates, this time, and see "You can install **191 **updates."

Now, I'm off to the races, again, 'cause I know I have a good backup from which I can recover. But, is this typically the risk one takes with Update Manager??

Thanks!

---

### Post by ed-koala on 2008-04-03
I'm having a similar issue this morning.  I keep getting the "Partial Update" message, but clicking it only gets to Preparing then quits.  Nothing is installed and running Update Manager again gives the same result.

---

### Post by AlanB66 on 2008-04-03
Well, this morning I was opted to do a full set of 191 updates - no partial offering this time - and it has led to a system that won't reach the login screen.

So, don't do any update, if you don't have a good image backup!!!

---

### Post by AlanB66 on 2008-04-03
So, more information ...

I ran an update and removed any items reflecting 2.6.24-14.
Still, after update and attempted reboot, the system hangs just prior to offering me to log in. Little spinng circle is all I get.

I have turned on as much boot-up transcripting as I know how (removing "quiet" and "splash" from the boot command), but I don't know what it's getting hung up on once it's about to set the bootup-screen.

Is there a way to get full transcripting 'til it's absolutely ready for me to log in? Or, is there a log file I can read to see what's failing in the end?

Thanks!

---

### Post by Precipitous on 2008-04-03
I have had a similar experience, except that now when I try to boot the machine, it gets almost all the way through it then I get the message "The Greeter Application Appears To Be Crashing. Attempting To Use A Different One". If I click OK the boot process stops...

---

### Post by AlanB66 on 2008-04-03
I had updated my Sources to include Universe to get all (not partial) updates. I have since reverted to partial and am carrying out the update, again.

One thing I'm also doing is not starting my wireless card - as I think this is the culprit (modprobe ath_pci).

If I can get an update to behave w/o wireless, I'll tackle getting the wireless re-enabled after the fact.

I'll post more as I know it.

---

### Post by AlanB66 on 2008-04-03
After my partial install/update, I did these steps:

1. Open /etc/default/linux-restricted-modules-common:
     Put ath_hal and ath_pci in the double quotes of DISABLE_MODULES

2. Ensure I've Disabled, via Driver Manager, HAL and Wireless Driver.

These are per my post at:
[http://ubuntuforums.org/showpost.php?p=4588083&postcount=38](http://ubuntuforums.org/showpost.php?p=4588083&postcount=38)

I'll be carrying out the remainder of updates from enabling Universe as a source and then I'll see if I can get my wireless working, again.

---

### Post by AlanB66 on 2008-04-03
OK, I give up  'til Ubuntu 8.04 is released. Then, I'll start over completely if I cannot get a clean update.

After updating, my WiFi fails to work.

---

