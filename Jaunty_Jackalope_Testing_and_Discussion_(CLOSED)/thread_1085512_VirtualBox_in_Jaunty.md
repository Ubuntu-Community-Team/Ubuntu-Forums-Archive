---
title: "VirtualBox in Jaunty"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Gina on 2009-03-03
Quick question... (not sure if it belongs here or in the Virtualisation section).  Been looking at VirtualBox as an option for running the Cumulus USB weather station Windows software in Ubuntu.  The latest version of Ubuntu they quote for VB is Intrepid but I was wondering if anyone has tried it in Jaunty.  I would like to run it on my test system but being new to VB I thought I'd ask here first in case I'd be wasting my time.  Thanks in advance :)

---

### Post by forumache on 2009-03-03
yes, i'm using it in jaunty. no problems, works as designed.

---

### Post by rogerdean on 2009-03-03
same here, no bother at all

---

### Post by nyarnon on 2009-03-03
Usually to be on the safe side you wait until a few weeks in the stable release. As Virtualbox and other virtualisation strongly depends on stability of the kernel it's not a good thing do do anything else than trail and error on a alpha. Expect your images to break any time.

---

### Post by Gina on 2009-03-03
Thank you for your replies, everyone :) :)  And yes, I realise things may break with development software.  Running it on my test machine means I can continue running the software on my main machine while I set up everything (and sort out why it won't work first time, if necessary :lol:).  Then swap the USB cable over and run from the test m/c whilst setting up on my main one :)

---

### Post by linux6994 on 2009-03-03
Works just fine Jaunty.

---

### Post by Gina on 2009-03-04
I installed the Intrepid 64 bit version in Jaunty on my AMD64 with no trouble at all.  The Instruction Manual is very clear and I just followed the steps - it went like a dream :) :)  I must complement the author(s) of VirtualBox for an excellent product! :)  Installing Windows XP within it also went perfectly.  I then installed the Cumulus weather station software and after enabling USB it read my weather data with no problem.  I'm very pleased.  Now I can set it up on my main machine and run it in the background while using Ubuntu.

---

### Post by nyarnon on 2009-03-04
> **Gina said:**
> Now I can set it up on my main machine and run it in the background while using Ubuntu.

Just remember what I tolled you about alpha-versions, it can break anytime.

---

### Post by Gina on 2009-03-04
Yes, thank you :)  Main machine runs Intrepid - I don't risk alphas or even betas on that.  Too much to restore if a disaster happens.

---

### Post by nanog on 2009-03-04
Vbox images are portable so backup and restoration is trivial. I also heartily recommend using nlite to create a slipstreamed image that removes the unecessary junk you don't need in a virtual machine. Tutorials available at lifehacker. (you will be amazed at how lightening quick xp can be.)

---

### Post by Regnulify on 2009-03-04
I wanted to add: I have Jaunty running in VirtualBox. Adding the VBoxAdditions causes the X Server to fail on the config every time I boot. I reinstalled and left the additions off and no problem.

I just wanted to throw that out there.

---

### Post by Kareeser on 2009-03-13
> **Regnulify said:**
> I wanted to add: I have Jaunty running in VirtualBox. Adding the VBoxAdditions causes the X Server to fail on the config every time I boot. I reinstalled and left the additions off and no problem.

I just wanted to throw that out there.
Same. The version of Guest Additions bundled with Virtualbox 2.1.4 only supports up to Intrepid (at least, so says the website)...

According to the install script, the drivers couldn't match up with the updated x.org version, and abored without installing drivers at all.

---

