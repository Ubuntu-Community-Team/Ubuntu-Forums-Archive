---
title: "my laptop will not boot from disc or flash"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by joel93442 on 2016-07-29
I have tried everything I could think of to install on a Acer laptop. I changed the boot order. Tried moving CD rom to the top of the boot list. Tried same thing with a flashdrive and nothing seems to work. It just boots into Windows 10. I have no idea what to try next. I'm desperate to get rid of windows 10 but am unable to do so.

---

### Post by yancek on 2016-07-29
If you are using Ubuntu then you would have it on a DVD rather than a CD, right?  The iso for Ubuntu for several versions has been to large to fit on a CD so the question is, what software did you use to burn the iso as an image to the DVD?  Did you do an md5 checksum on the downloaded iso file to verify that it was not corrupt?  When you put Ubuntu on the flash drive, what software did you use to do that?  Are you able to try the DVD and/or flash drive on another computer to see if either boots?

The official Ubuntu documentation on dual booting with windows 10 is at the site below so take a look at it.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Posting some hardware details or the manufacturer of the computer might give someone an idea.

---

### Post by joel93442 on 2016-07-29
Right, it's on a 4 gig DVD, burned with brasero and works fine on other computers.  Used checksum on the iso file. Very complicated. I don't even want to install with windows. Just a simple replacement.

---

### Post by grahammechanical on 2016-07-29
On my BIOS motherboard I have to do more than set the boot priority. I go into the Boot section of the BIOS and under Hard Disks I select which disk to load from. A USB memory stick with the Ubuntu ISO image on is seen as an external USB drive. The DVD drive gets treated in the same way.

Regards

---

### Post by ajgreeny on 2016-07-29
There may also be a one-time keypress to get a boot device list, usually one of the F# keys; on my machines it is either F8 or F11 but yours could be different so have a look in the motherboard manual, if you have one, or search online if not.

---

### Post by RobGoss on 2016-07-29
With Acer's you believe you have to **enable** the **Boot menu** to even see your devices listed. I'm currently working with a Acer now and I had to access the BIOS and enable the boot menu once that was done I was able to hit **F-12 **to choose my devices

I suggest taking a good look in your BIOS settings to see how this can be accomplish

---

