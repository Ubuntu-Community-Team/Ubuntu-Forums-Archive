---
title: "Need Help Installing Radeon HD 6450 w/Wine"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by w201 on 2012-08-07
Hi- I'm trying to install drivers for a new graphics card, Radeon HD 6450. 

I'm using wine for the install. Problem is that it's asking if I want to install under Windows XP, or Vista. Those are the only two options. 

Any help would be great, thanks!

---

### Post by QIII on 2012-08-07
Do you mean that you do not have the driver installed at all on your machine?

---

### Post by w201 on 2012-08-07
IDK- I guess there are drivers installed because I can talk to you. But ubuntu isn't recognizing my graphics card, and I can't get ubuntu 3D to work. That led me to believe that perhaps I need to install the drivers that came on the CD with the graphics card

---

### Post by QIII on 2012-08-07
The Windows driver that came with your card cannot be installed in Linux.  What you are using right now, if you have not installed the ATI proprietary Linux driver, is the open source Radeon driver.

What do you mean when you say the driver "is not recognized"?

---

### Post by w201 on 2012-08-07
In System Settings > Details.... Graphics is Unknown

I haven't installed ANY drivers.

---

### Post by QIII on 2012-08-07
OK.  Sorry to ask so many questions, but I hate to just rattle off a bunch of instructions without knowing where people are starting off.

You do not *have *to install any driver.  The open source Radeon driver, which is used by default, is very good.  For most people, it will do just fine.  (I don't remember that I had any problems with Unity 3D, but maybe I did.)

If you want to have the proprietary ATI driver, it can be installed by two methods from the Ubuntu repo.  It is version 12.4, which is not the latest, but is not far behind.

You can install the latest from the AMD/ATI website, but I would not recommend that route at this point unless you are familiar with what you are doing.

Please see the ATI driver wiki in my signature.

The "Additional Drivers" method can be found in the table of contents under "Using the Ubuntu repositories (recommended)".  Although it is not stated, I would recommend running 

```
sudo aticonfig --initial
```after using that method before rebooting.

*That method does not always work*. And don't install the "Post release updates" version.  That has caused enough problems with enough users that I simply recommend against it for now.

I generally recommend the section "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"

In that section, you can skip step 8 if you don't want to mess with hardware acceleration.  When I get a chance I'm going to move step 8 to its own section.

Please read the wiki first and let me know if you have questions.

If you have problems, of course, let me know so I can work at getting you sorted back out.

---

### Post by w201 on 2012-08-07
Okay- before I go any further, I did exactly what you told me not to do, I installed the Post release updates version.... I tried that before I saw your last reply. That installation failed.

So before I move on with your other instructions, is there anything I need to do with the failed attempt, or with the /var/log/jockey.log files?

---

### Post by QIII on 2012-08-07
```
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
```

should get you back in order.

---

### Post by w201 on 2012-08-07
Okay, thanks for the fix. That's done. I'll give your wiki a read and try this again.

I did check on the AMD/ATI website and found the following drivers:
[**AMD Catalyst™ 12.6 Proprietary Linux x86 Display Driver**]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-6-x86.x86_64.run")

is it a straightforward install, reboot and you're done, or is it more involved? Either way, I'm reading your wiki.

---

### Post by QIII on 2012-08-07
Someone other than I included instructions for that in the wiki.  It is not perfectly straight forward if you use the process of creating a .deb file.  But if you are interested in the latest driver, that section details how you should do it.  I would do it that way in general.

Just below that I added a section on using the downloaded .run file directly, but I recommend against that because it is "foreign" to Ubuntu's normal installation process and it leaves you dependent on the amdconfig utility to uninstall it later.  I only included that to try to help people with hybrid Intel/ATI graphics on notebooks.

For the time being, if you only have ATI graphics, use the "Alternate command line method..."

(Oh.  It's not "my" wiki.  It's the community's.  A whole lot of people keep it up.)

---

### Post by w201 on 2012-08-07
I tried the alternate command line method, minus the hardware acceleration. 

everything went smoothly...just a few things I'm still noticing....launcher bar doesn't work on ubuntu 3D... I know that's probably a different topic, and you've been helpful enough, but anything I can check to make sure the installation was done right? Or would installing hardware acceleration help the matter?

Also, in system settings under graphics now it reads "VESA:CAICOS" whatever that means.

***EDIT***

Got unity to work, just realized I didn't have it enabled on compiz. So everything seems to be working fine. This video card actually sucks, says 2GB on the box, but I highly doubt it judging by its performance. Paid 35 for it, so I guess you get what you pay for.

I really appreciate you helping me out with all this man. Have a good one.

---

