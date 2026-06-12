---
title: "kernel upgrade killed all drivers - please help"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by spalmer8 on 2010-04-28
Upgraded 

from Ubuntu 8.04.2, kernel 2.6.24-24-lpia 
to     Ubuntu 8.04.2, kernel 2.6.24-27-lpia

Drivers Lost / Missing: Wireless via USB, Printer, Webcam, Sound, etc...

No indication whatsoever there would be problems with the upgrade except for the changes in /boot/grub/menu.lst which I merged by hand to avoid problems.

Please advise:
A) What to do next? 
B) Where in the Ubuntu bugs do I open this bug? 

Thanks much!

---

### Post by snowpine on 2010-04-28
Hi, curious if you tried my suggestion in your other thread?

[http://ubuntuforums.org/showthread.php?t=1463342&highlight=lpia](http://ubuntuforums.org/showthread.php?t=1463342&highlight=lpia)

---

### Post by spalmer8 on 2010-04-28
I just now saw your message - thank you so much for the response.  I did boot back into Ubuntu 8.04.2, kernel 2.6.24-24-lpia but only some of the drivers were there not all.  I do not have the package you mentioned.  Questions:
1) Booted into which kernel should I install the package you mentioned?  
2) Where do I file the bug?
3) What would you suggest I do - should I try and migrate to the latest and greatest 10.4 off of 8.04.2?  If so, what do you think the migration, upgrade path should be? (I am one of the ununtu netbook remix folks.)  

Thanks so much for any and all advice!

---

### Post by snowpine on 2010-04-28
If you want to keep 8.04, I recommend opening your Synaptic Package Manager, and selecting to install the 'dkms' package and UNINSTALL the package linux-2.6.24-27-lpia. Apply these changes (dkms will pull in some other packages as dependencies, that's ok). When complete, try reinstalling linux-2.6.24-27-lpia, hopefully this time it will rebuild the modules you need. :)

I do recommend moving on from 8.04 at some point, as it is somewhat outdated (8.04 = April 2008). Ubuntu no longer supports the lpia architecture, so the only migration is to back up your data and do a fresh reinstall of the regular i386 release. If you tell me more about your hardware I can give better advice--I'm guessing this is a netbook that you purchased with Ubuntu pre-installed?

I have a Dell Mini 9 that came with the special Ubuntu 8.04 pre-installed, and I had no problem moving on to a newer release; the only minor difficulty was Broadcom wireless, which is easy to fix if you know how.

---

### Post by spalmer8 on 2010-04-28
Thanks so much snowpine!!  I will try what you suggest.  I hope I can get back my USB drivers so I can use a bootable USB stick to load ubuntu back on!  I have the rebranded MSI WIND AKA Sylvania Meso G Netbook. Model LC89.  I have loved everything about this little netbook so far.  I understand maintaining the lpia achitecture was a pain - I just wish there had been some sort of a migration strategy.  

There are a bunch of non tech people who bought these netbooks with ubuntu remix loaded and they are probably pretty frustrated and this probably sent them back to Microsoft and Windows.  :-(  If only the whole was on some flavor of linux or unix or mac.   Ahhh to dream.

Thank you again snowpine!

---

### Post by snowpine on 2010-04-28
Always glad to help. :) Another thing you can check, next time you boot, go into BIOS and check that USB, wifi, webcam, etc. are all enabled there. Sometimes it's the simple things...

Also I checked the Ubuntu wiki for you, and it says support for the Sylvania Meso G is pretty good (except maybe wifi): [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Sylvania%20MESO%20G](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Sylvania%20MESO%20G)

Good luck!

---

### Post by spalmer8 on 2010-04-28
Hi Snowpine,

Hopefully this will be my last question...  Again, thank you thank you!  

So I am removed linux-2.6.24-27-lpia and its image via Synaptic while in the linux-2.6.24-27-lpia kernel. (fyi - still shows up in grub/menu.lst)  

I am back in linux-2.6.24-24-lpia kernel and installed dkms - but I am not sure how and when I should use it.  

I just ran the update manager and linux-image-2.6.24-27-lpia is selected for install but I am unable to select the linux-image-lpia.  

Would you rather I use the dkms command to install these?  Is it just as simple as: 

dkms -install linux-2.6.24-27-lpia linux-image-lpia

or should I be tweaking the whole conf file?

Thanks Much Again!

---

### Post by snowpine on 2010-04-28
If dkms is installed, it just does its thing automatically... no action necessary on your part. I hope it solves your problem, but no guarantees. :)

---

### Post by cfastner on 2010-05-04
spalmer8:

I also have a Sylvania Meso G (a yellow one, looks like a bumble bee!) and I Love it!  I have installed the latest version of Ubuntu (Lucid Lynx) and I have no issues.  You should try THAT!  I installed the desktop version and not the lpia or the netbook remix and I think it looks/works just fine.

Also, the only drawback that I saw with this netbook was the lack of a Right Shift key on the keyboard so I remapped a key for Right Shift.

---

### Post by Channah1973 on 2010-05-23
cfastner:

I think I'd like to follow your example, but I can't seem to find a howto, and I don't really want to reformat if I can avoid it.  I never seem to find all the files and things that I would have wanted to save.  Can you tell me where to look, or give some advice?
Thanks

---

