---
title: "Screen lock while Upgrading 20 LTS to 22 LTS"
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by rekurzionkwesi on 2022-09-07
Logged in. Initiated upgrade from Software Updater. Began successfully. Locked screen so roommates won't mess with the computer while the upgrade is in progress. 

Now I can't log back into the system to check the status of the upgrade. The log in screen is clearly visible but with a message right beneath the password field reading: "Authentication Error". This message blinks every second and I cannot click inside the free text field where you enter the password. If I do manage to TAB into the password field the cursor immediately disappears on the 'tick' of the flicker. It feels like the TAB button is being held down but after replacing the keyboard this is not the case.

is this what happens when you lock the screen during a version upgrade? did i ruin my chance of being able to finish a clean upgrade? is there a way to log back into the profile and continue the upgrade? 

any help here would be hot.

---

### Post by guiverc on 2022-09-07
The *[ubuntu-release-upgrader]("https://launchpad.net/ubuntu/+source/ubuntu-release-upgrader") *process **intentionally** prevents the screen lock function (*on inactivity*) during the upgrade purposes as it can result in a locked out session. I understand why you did it, but the *lock* function is disabled for a reason.

FYI: The 20 & 22 systems are intended for server use only; so I assume you're talking about 20.04 & 22.04 which are available for desktop & server use. Ubuntu has used the *year* format (eg. Ubuntu Core 20) to highlight the *specialist* snap only server products since 2016.

I'd switch to terminal & look at what is running there & forget about your GUI session (using `top`, `htop` etc).  Did it complete? or it waiting for a user prompt which I suspect you'll be unable to provide.

Personally I'd treat your desktop session as *dead* and not try and recover it; in QA (*Quality Assurance*) testing of the GUI upgrade is tested to ensure *screen locking* doesn't auto-occur as that is a problem! (*not recovery as you now need*).

  If the upgrade completed (*or appears to have from the `htop` enquiries earlier*); I'd likely reboot & test it after upgrade, or if you think the system didn't complete (*not login with GUI by text terminal only* *post-reboot*) attempt to have the *release-upgrade* process complete.... Once I was happy it had finished upgrading successfully (`sudo apt update` to update software lists & all looked good, then `sudo apt full-upgrade` which completed without any issues), I'd then reboot & try a normal GUI login.

If I saw issues during the `apt upgrade`, `apt full-upgrade` etc. I'd stay at [text] terminal & fix whatever I saw that looked wrong.

Others may have different, or *more useful* advice for you.

---

### Post by rekurzionkwesi on 2022-09-08
thank you. 

yes, I am referring to the desktop versions. I am prepared for a fresh install, luckily a thorough backup was performed so there is no issue of data loss. i will run with your suggestions and post results for those unfortunate souls who have followed in my footsteps.

---

### Post by grahammechanical on 2022-09-08
You may find that you cannot power off the OS and that you need to shut down/power down the machine. When you reboot pull up the Grub boot menu. On machines with a single OS we press Esc as the OEM splash screens appear. It is shift when we have a BIOS motherboard and not UEFI. At the Grub menu select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode.

At the Recovery menu select network to establish an internet connection. Then select Root shell prompt. Now you can enter all the command you want. Afterward type "exit" to get back to the recovery menu and the select Resume. See if you get to a working desktop. The system may be using a low resolution video driver. A reboot will load the desktop with the usual video driver.

Regards

---

### Post by rekurzionkwesi on 2022-09-08
OK. switched to a term and was able to run ***top*** (***htop*** wasn't installed unfortunately) and jammy was still running. tried running ***reboot*** and was denied due to the upgrade still being in progress. NOTE: i left the computer alone for at least 10 hours so there may indeed have been a prompt waiting for a human touch as i can't picture why the upgrade would take that long when a fresh install takes me under 30 minutes). 

so i ran ***sudo reboot --f*** which restarted the system. booted up fine until login screen where it promptly failed with "Oops. Something went wrong" suggesting the upgrade was not completed in a meaningful way.

at this point i decided to just fresh install from USB which did recognize there was an existing 22.04 install that i replaced. 

the true moral of the story is backup your stuffs. at least that's what i'm going with.

---

### Post by rekurzionkwesi on 2022-09-08
> **grahammechanical said:**
> You may find that you cannot power off the OS and that you need to shut down/power down the machine. When you reboot pull up the Grub boot menu. On machines with a single OS we press Esc as the OEM splash screens appear. It is shift when we have a BIOS motherboard and not UEFI. At the Grub menu select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode.

At the Recovery menu select network to establish an internet connection. Then select Root shell prompt. Now you can enter all the command you want. Afterward type "exit" to get back to the recovery menu and the select Resume. See if you get to a working desktop. The system may be using a low resolution video driver. A reboot will load the desktop with the usual video driver.

Regards

apologies, didn't see this post until i posted my reply. was on a bit of a time crunch to get the system functional and wasn't able to try all of your suggestions.

---

