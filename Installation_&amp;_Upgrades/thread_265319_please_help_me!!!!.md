---
title: "please help me!!!!"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by hvaughn on 2006-09-25
i've posted for help in the desktop forum, but no luck. so maybe someone here can help me here. i've installed ubuntu on a dell desktop. version 6.06. when i boot the pc, i get a "f1 to reboot f2 to setup" message. if i reboot and hit f12 on the dell screen, i can load ubuntu by select option 6 "boot to utility partition". if i try to run from the primary drive, i get a boot error. i've tried to redo grub by running the sudo commands and this doesn't work either. is it possible that i need to do something with the bios? my system lists a primary sata drive that is unavailable (doesn't exist) and a primary IDE drive, which is a brand new drive I plugged in as the master drive. i'm beating my head against the wall here](*,) 
what am i doing wrong??????????? a friend of mine said that i need to create the boot record, but can't remember how he did it. it's my understanding that the install loads grub (boot) in the mbr. any help in this matter will be GREATLY appreciated.....

thanks!

---

### Post by confused57 on 2006-09-25
> **hvaughn said:**
> i've posted for help in the desktop forum, but no luck. so maybe someone here can help me here. i've installed ubuntu on a dell desktop. version 6.06. when i boot the pc, i get a "f1 to reboot f2 to setup" message. if i reboot and hit f12 on the dell screen, i can load ubuntu by select option 6 "boot to utility partition". if i try to run from the primary drive, i get a boot error. i've tried to redo grub by running the sudo commands and this doesn't work either. is it possible that i need to do something with the bios? my system lists a primary sata drive that is unavailable (doesn't exist) and a primary IDE drive, which is a brand new drive I plugged in as the master drive. i'm beating my head against the wall here](*,) 
what am i doing wrong??????????? a friend of mine said that i need to create the boot record, but can't remember how he did it. it's my understanding that the install loads grub (boot) in the mbr. any help in this matter will be GREATLY appreciated.....

thanks!

If I understand correctly, you only have the one new IDE hard drive installed on your Dell?  On my Dell Dimension 4550, I couldn't get it to boot with only one hard drive connected as the master drive(hd0) until I went into bios and disabled the slave drive(hd1) controller(changed from auto to disable)...
  If this doesn't work, give us a little more information about your setup...if you have 2 hard drives, dualbooting with Windows(separate hard drives or both on same hd),etc

---

### Post by hvaughn on 2006-09-26
can you please explain (in detail, not familiar with bios) as to how you did that?????

thanks

---

### Post by confused57 on 2006-09-27
> **hvaughn said:**
> can you please explain (in detail, not familiar with bios) as to how you did that?????

thanks
At the Dell logo screen during bootup, there should be a key to press to enter bios setup(mine is F2, or I can press F12 to enter boot menu).

On my Dell Dimension 4550, I have to press "down arrow" to highlight "Primary Drive 1", press enter...highlight "Drive Type" & change from "auto" to "off"(might be "disabled", can't remember which)...the menu at the bottom of the screen tells how to make changes.
Press "Esc" to exit...you should have the option to save with changes.

Primary Drive 0 is your master drive on the primary IDE controller, which is automatically set to "auto" on my Dell...however, Primary Drive 1(slave drive) default was "off", since I bought it with only one hard drive(added a 2nd hd later).

The above instructions are if you only have one hard drive,i.e. the Primary Drive 1 must be set to "off"...if you have 2 hard drives, it must be set to "auto".  If the changes don't work, you can always go back into the bios setup and change it back.

Primary Drive 0 =  Master hard drive
Primary Drive 1 =  Slave hard drive

With only one hard drive connected to Primary Drive 0, my system would not boot with the Primary Drive 1 set to "auto" in bios...I think I got an error message similar to yours.

---

