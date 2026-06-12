---
title: "Hardcore display issues"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by Vynesh on 2012-03-14
I'm sorry if this is the wrong place for this, but as I have yet to display Ubuntu for the first time so I'm going to have a thread under Installation as well as Hardware.
 
On day 3 of trying to figure this out now.
 
After selecting Ubuntu from my boot screen, my screen displays the option to either run Ubuntu, or Ubuntu recovery. Neither of these work. When I click one the screen goes black, and blue squares of various sizes start flashing randomly all over my screen. There are no sounds or error messages beforehand. I've tried booting from a LiveCD and that did the same thing. 
 
I can't tell if it's a hardware issue or a driver/something else problem.
 
Computer specs:
Compaq Presario
Windows XP Home
70g HDD
1.5g RAM
2.93GHz Intel Celeron
 
Please help me! I'm at my wits end with this. ](*,)
 
Thanks in advance.

---

### Post by Helen McCall on 2012-03-14
Hi Vynesh,

You need to find out the make and model number for your graphics adapter. Some graphics adapters need some parameters entered on the boot args line.

Post the details of your graphics adapter here, and someone should know the parameters to enter for it to work.

Helen x

---

### Post by Holdolin on 2012-03-14
Welcome to the forums Vynesh.  Glad to see you're interested in the goodness that is Ubuntu :)  I read both your threads on this issue, and as a freindly pointer, making multiple posts about the same subject is generally frowned upon.  That being said, lets see if we can get you some more direction in this issue.

In your other thread, you said that Wubi installed Ubnuntu in Windows.  If that has happened, you would not notice it on your boot up screen, it would appear as any other installed application on your Windows install, let's say your wordpad.  

Now, as far as your boot issue with the funk, like others have suggested, it sounds like either an unsupported video chip, or the system is not configured to use it. It sounds perhaps as if Unbuntu is trying to install in 3d mode and your vid card only supports 2d, or is not up to the task of rendering Ubuntu in 3d.  I actually ran into this problem testing 12.04 in a VM, had the VM set to 2d only dispaly and it totally hammered my video performance.  Also, what version of Ubuntu are you trying to install?

---

### Post by Vynesh on 2012-03-14
**Chipset type** Intel 845GV
**Type** Integrated
**Graphics Processor / Vendor** Intel Extreme Graphics Shared video memory (UMA)

---

### Post by Vynesh on 2012-03-14
> **Holdolin said:**
> Welcome to the forums Vynesh. Glad to see you're interested in the goodness that is Ubuntu :)
 
I'm really looking forward to using it!
 
> In your other thread, you said that Wubi installed Ubnuntu in Windows. If that has happened, you would not notice it on your boot up screen, it would appear as any other installed application on your Windows install, let's say your wordpad.
 
On the 3rd step on the website it says to reboot and select Ubuntu from the Windows Boot Manager. 
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
I tried doing this with the CD boot as well.
 
Is there an app within windows that will launch Ubuntu?
Maybe this is another issue :(
 
> Now, as far as your boot issue with the funk, like others have suggested, it sounds like either an unsupported video chip, or the system is not configured to use it. It sounds perhaps as if Unbuntu is trying to install in 3d mode and your vid card only supports 2d, or is not up to the task of rendering Ubuntu in 3d. I actually ran into this problem testing 12.04 in a VM, had the VM set to 2d only dispaly and it totally hammered my video performance. Also, what version of Ubuntu are you trying to install?
 
I'm trying to install 11.10

---

### Post by Holdolin on 2012-03-14
Admitedly, it's been a while since i've used that method to install Ubuntu, so i'll run through the process on my Windows box to refresh my memory and see what i might be able to find out.  I am thinking it has to do with your video card, but with an outdated memory on my part, at this point, i'd proably only be leading you on a wild goose chase, and I'd rather be helpful :)

---

### Post by Holdolin on 2012-03-14
> **Vynesh said:**
> I'm really looking forward to using it!
 

 
On the 3rd step on the website it says to reboot and select Ubuntu from the Windows Boot Manager. 
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
I tried doing this with the CD boot as well.


Are you trying to boot with the CD in the drive?

---

### Post by Vynesh on 2012-03-14
I tried it without the CD the first time, and the second time with the CD. Since then I have removed it. What would be the optimum way to install it? haha.

---

### Post by Holdolin on 2012-03-14
Given that you're running a laptop, I would reccomend just installing Ubuntu from an install disc.  Unless there's something you need to use that requires Windows, Ubuntu can do anything you like with it.  Now,  you may need to work with the video driver, since we know that the hardware works (you get a picture on Windows) that leads me to beleive it's a software/driver issue.  Sadly, I am not a good source of information on tweaking an install to add/modify a driver, but I'm more than sure there are a wealth of thsoe who do know how to do that.

---

### Post by Vynesh on 2012-03-14
It's actually a desktop :)
And I would just replace windows, if I was certain Ubuntu would display. Until I can get the trial version to display properly I don't think I have the confidence to replace Windows. I'm not exactly sure how or if you can install drivers without a working os? :(

---

