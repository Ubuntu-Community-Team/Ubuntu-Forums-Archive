---
title: "How can I launch CCC from command line?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sonnet on 2009-10-25
I have installed Karmic RC with all the updates.
Then I have installed the ati proprietary driver.
Now I need to configure my 2 monitor through Catalyst control center.
But when I launch from Others->Ati Catalyst Control center (administrative),
I get error message:"Failed to execute child process amdxdg-su: no such file or directory".
How can I solve this problem or alternatively launch the CCC from command line?

---

### Post by Rinzwind on 2009-10-25
if you installed it through synaptic go into synaptic again, search for the package you installed and check properties -> installed files.

Any executable should be in one of these directories:
/bin/
/sbin/
/usr/bin/

---

### Post by sonnet on 2009-10-25
> **Rinzwind said:**
> if you installed it through synaptic go into synaptic again, search for the package you installed and check properties -> installed files.

Any executable should be in one of these directories:
/bin/
/sbin/
/usr/bin/

I have installed the driver (with the CCC) through the Administration->Hardware drivers wizard.
Thanks to your suggestion I found in /usr/bin the executable amdcccle.

---

### Post by Rinzwind on 2009-10-25
For as far as I can see I should be

amdxdg-su 


But I have a nVidia so i can not test it for you :D

do a 

locate amdxdg-su

maybe you get a file not found because it is in another directory (that is not included in PATH).

---

### Post by c_martini on 2009-10-26
I have a similar problem as well with an ATI Mobility Radeon HD 3470 (laptop: Asus M51se). The laptop as lcd and second monitor as dfp1. Both are mirrored and are sharing the same resolution in error. Both need to be at their native resolutions (lcd at 1440x900 and dfp1 at 1650x1080) and have the desktop extend from the first to the second. I have read that the Catalyst Control Center app can manage this as the monitor settings within KDE are buggy and do not work in this scenario.  Really what I need to know is how to launch the Catalyst Control Center. I cannot find this anywhere in any of the application menus. Is there a terminal command to launch this? I am assuming this catalyst control center was installed during the restricted driver installation prompt after I installed the system yesterday (Kubuntu Karmic 9.10 rc).

Would the control center have been installed or not and how to confirm this?

How would I launch it?

---

