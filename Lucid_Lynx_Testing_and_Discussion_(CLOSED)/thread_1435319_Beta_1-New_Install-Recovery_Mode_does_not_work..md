---
title: "Beta 1-New Install-Recovery Mode does not work."
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-21
It boots to the point where the login screen would appear on a non-recovery boot and then just sits there with a blinking cursor.  (Shades of 1980!) 

Anyone else confirm?

What Synaptic packages are the Recovery Mode, so I can reinstall them for now?

---

### Post by ratcheer on 2010-03-21
I am getting the same thing, just a black screen with a single underscore characher on the top line, near the left. I cannot boot to normal or recovery mode. I installed from Mar 21 LiveCD.

Tim

---

### Post by mereih on 2010-03-21
Same here. Clean install doesn't boot.

---

### Post by grandtoubab on 2010-03-21
+1
same here :o

---

### Post by andrek on 2010-03-21
Seems serious but it works here. I'm using 2.6.32-16-generic x86-64 kernel with FGLRX driver ( 2:8.721-0ubuntu**3** ). I used to experience the same behaviour with 2:8.721-0ubuntu**2**, though.

---

### Post by cariboo on 2010-03-21
> **emarkay said:**
> It boots to the point where the login screen would appear on a non-recovery boot and then just sits there with a blinking cursor.  (Shades of 1980!) 

Anyone else confirm?

What Synaptic packages are the Recovery Mode, so I can reinstall them for now?

Recovery mode isn't a package, it is an option in grub. Hold down the shift key to get to the grub menu and select Recovery Mode, it will take you a menu where you can choose some repair options.

---

### Post by emarkay on 2010-03-21
Bug filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543673](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543673)

---

### Post by emarkay on 2010-03-21
> **cariboo907 said:**
> Recovery mode isn't a package, it is an option in grub. Hold down the shift key to get to the grub menu and select Recovery Mode, it will take you a menu where you can choose some repair options.

OK, literally, on boot, I get the options in GRUB2 ; a list of the Kernel number and OS name and then below that, the same with "(Recovery Mode)", then Memory Test below that. Selecting "Recovery Mode" usually goes to a DOS-like screen (limited graphics) that provides options for recovery. In this case I do not get the "options list".

So if the Recovery Mode itself is corrupted, it requires a GRUB 2 reinstall, or an update to that "package" (GRUB2)?

---

### Post by wilee-nilee on 2010-03-21
I am using the beta from a install on release. I updated/upgraded everything, which had grub do a update and everything is working here including the recovery.

If you hit esc and then c at boot you will get a command prompt login the run sudo update then upgrade the update portion is what recovery is doing anyway. Recovery probably does more then just this; but it is where I start if I can't get a boot, and I check to see if a desktop has been installed.

---

### Post by cariboo on 2010-03-21
> **emarkay said:**
> OK, literally, on boot, I get the options in GRUB2 ; a list of the Kernel number and OS name and then below that, the same with "(Recovery Mode)", then Memory Test below that. Selecting "Recovery Mode" usually goes to a DOS-like screen (limited graphics) that provides options for recovery. In this case I do not get the "options list".

So if the Recovery Mode itself is corrupted, it requires a GRUB 2 reinstall, or an update to that "package" (GRUB2)?

Recovery mode takes you to a menu where you should have the option to:

[list]
[*] Resume
[*] Clean
[*] dpkg
[*] grub
[*] netroot
[*] root
[/list]

From the menu you can choose different options to repair your broken installation, choosing dpkg will install missing dependencies, grub will update grub, netroot will drop you to a root prompt with networking and root will drop you to a root prompt. I think what you are looking for is an analog to Windows System Restore, there isn't one. Selecting dpkg should solve your problems.

---

### Post by ratcheer on 2010-03-21
We understand that. When we boot to recovery mode, that menu never comes up. As I said, I end up with a black screen with a single underscore character near the top left of the screen.

Tim

---

### Post by emarkay on 2010-03-21
> **cariboo907 said:**
> Recovery mode takes you to a menu where you should have the option to:

[LIST]
[*] Resume [Boot]
[*] Clean (Free Space)
[*] dpkg ("Fix Broken Packages")
[*] grub (Rebuild Grub)
[*] netroot
[*] root
[/LIST]
I think what you are looking for is an analog to Windows System Restore, there isn't one. 

Jeez, man - I have been using Ubuntu since 2006...
I know what  it is and what I am saying...  It's BROKEN.  (Early indication is it may be an ATI graphic issue.)
Aw, nevermind.  :)

---

### Post by mc4man on 2010-03-21
See the same thing - had a filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/543580") earlier today on grub.

Here the recovery menu shows up on an install that's nvidia-current/no plymouth, doesn't on an install that's nouveau/plymouth

---

### Post by bcbc on 2010-03-21
I had same problem - fixed it by removing plymouth.

---

### Post by emarkay on 2010-03-21
> **bcbc said:**
> I had same problem - fixed it by removing plymouth.

[SIZE=3]OH NO!![/SIZE]
I thought all that Plymouth was corrected!  And I just reinstalled Beta 1 and ***did not*** remove Plymouth!

"Say it ain't so, Joe..."

---

### Post by ratcheer on 2010-03-21
Well, since I am on one of the Ubuntu testing teams, I am not really supposed to remove plymouth or make other changes. I have to do a fresh install every week and go through the prescribed tests.

Tim

---

### Post by emarkay on 2010-03-21
> **ratcheer said:**
> Well, since I am on one of the Ubuntu testing teams, I am not really supposed to remove plymouth or make other changes. I have to do a fresh install every week and go through the prescribed tests.
Tim

I had to - see some posts from a week or so ago - but that's all Alpha now... :)

---

### Post by garok89 on 2010-03-22
> **cariboo907 said:**
> Recovery mode isn't a package, it is an option in grub. Hold down the shift key to get to the grub menu and select Recovery Mode, it will take you a menu where you can choose some repair options.

actually, it is.....friendly-recovery is the package for it

---

### Post by ratcheer on 2010-03-22
After all the hair pulling I did yesterday, today I got a very good installation. I used the Mar 22 alternate image. On the first normal reboot after installation, there was no disk clicking / grinding at all and the desktop was up very quickly. Everything was exactly as it should be.

Then, for my Xorg Proprietary Driver testing work, I installed the nvidia-current (195.36.15) driver and rebooted, again. This time, the normal boot did a fair amount of disk clicking / grinding, but after only about 40 seconds of it, the desktop came up. After that, I have successfully rebooted to recovery mode several times (to eliminate the wear and tear on the disk drive). Then, I choose "drop to a root prompt" and then "service start gdm" and the desktop comes up, almost immediately.

All in all, a good day. :)

Tim

---

### Post by grandtoubab on 2010-03-22
I confirm, when uninstalling
libdrm-nouveau1
plymouth
plymouth-X11

Back to standard recovery screen :popcorn:

---

### Post by emarkay on 2010-03-22
So yes, another Plymouth issue.
(Keeping it installed for now.)
Doesn't look like they are taking the bug too seriously...  They are still "Unassigned".
Will keep up on this.

---

### Post by mc4man on 2010-03-22
> So yes, another Plymouth issue.
(Keeping it installed for now.)
Doesn't look like they are taking the bug too seriously... They are still "Unassigned".
While it does appear plymouth is involved, at least here it's only the combo of plymouth, nouveau and friendly-recovery, so i'd think it will be addressed.

(remove any 1 of the 3 and recovery mode won't hang

---

### Post by cariboo on 2010-03-22
See [here]("http://ubuntuforums.org/showpost.php?p=9011531&postcount=1") for a better explanation of the problem.

---

### Post by mc4man on 2010-03-22
Actually now have recovery mode with the 'recovery menu' working with all installs
nvidia-current/plymouth
nouveau/plymouth

---

### Post by emarkay on 2010-03-22
> **mc4man said:**
> Actually now have recovery mode with the 'recovery menu' working with all installs
nvidia-current/plymouth
nouveau/plymouth


Recent update, rebooted to Karmic, or what ;)

---

### Post by emarkay on 2010-03-22
> **cariboo907 said:**
> See [here]("http://ubuntuforums.org/showpost.php?p=9011531&postcount=1") for a better explanation of the problem.

[I]"What about the recovery mode...in karmic there used to be a recovery menu...this menu seems to be what is broken now."

[/I]Huh?  Seems to just be another post with a related problem, not "behind the scenes" info or a resolution...

---

### Post by mc4man on 2010-03-22
> Recent update, rebooted to Karmic, or what
Posted what I did in the last comment in LP. 
The reason why is somewhat unknown  to me, (though logical), but it has withstood multiple reboots now with all packages installed.

---

### Post by emarkay on 2010-03-22
Yea, it's working now - must have been the last update - and then a bit later another update of GRUB2 came and still, so far, so good.
Marking this "Solved"!

Thanks all!

---

### Post by ratcheer on 2010-03-23
> **ratcheer said:**
> After all the hair pulling I did yesterday, today I got a very good installation. I used the Mar 22 alternate image. On the first normal reboot after installation, there was no disk clicking / grinding at all and the desktop was up very quickly. Everything was exactly as it should be.

Then, for my Xorg Proprietary Driver testing work, I installed the nvidia-current (195.36.15) driver and rebooted, again. This time, the normal boot did a fair amount of disk clicking / grinding, but after only about 40 seconds of it, the desktop came up. After that, I have successfully rebooted to recovery mode several times (to eliminate the wear and tear on the disk drive). Then, I choose "drop to a root prompt" and then "service start gdm" and the desktop comes up, almost immediately.

All in all, a good day. :)

Tim

And, of course, after this morning's updates, it is back to not booting in normal or recovery mode. Normal mode starts the disk into its continual clicking /grinding. Recover mode starts disk clicking / grinding, then stops for a while and gives me a text desktop login prompt. After I enter the username and password, it resumes the continual disk clicking / grinding, again.

At least Karmic still boots ok.

***What is all this disk drive resetting about, anyway?***

Tim

---

### Post by ratcheer on 2010-03-23
> **ratcheer said:**
> And, of course, after this morning's updates, it is back to not booting in normal or recovery mode. Normal mode starts the disk into its continual clicking /grinding. Recover mode starts disk clicking / grinding, then stops for a while and gives me a text desktop login prompt. After I enter the username and password, it resumes the continual disk clicking / grinding, again.

At least Karmic still boots ok.

***What is all this disk drive resetting about, anyway?***

Tim

And now, after running update again and picking up kernel 2.6.32-17, everything is working flawlessly. No disk drive clicking, at all. Normal boot is very fast and recovery mode works, as expected.

Boy, this is a roller coaster ride!

Tim

---

