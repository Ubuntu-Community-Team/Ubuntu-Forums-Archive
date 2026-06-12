---
title: "upgrade to18-04-5 lost comment section on youtube videos"
date: 2020-09-30
forum: Installation &amp; Upgrades
---

### Post by jaxom98 on 2020-09-30
I updated 18.04 to 18.04.5 and fixed 2 issues with missing or broken video drivers.  Now when I watch a youtube clip the video is in the middle of the screen and there is no comment section, and the list of next video clips is under the playing video.
   Before the major update youtube played on the left 2/3s of the screen with the comments section underneath, and the list of next video clips was on the right 1/3 of the screen.

Issues fixed are 1 that prevented any updates. I found a fix via google (manually run "dpkg-configure-a" )and it worked, and updated to 18.04.5. Beore it would not.
The 2nd issue was a MPEG-4 decoder not installed, this was installed and now problem videos work properly. 

How do I get the comments section back on youtube?
What questions do I need to ask?
What terms do I need?
Is the MPEG-4 the problem or a red herrring?

---

### Post by CelticWarrior on 2020-09-30
The situation with Youtube very (extremely) likely has nothing to do with the updates or lack thereof. What probably happened is you clicked the "cinema mode" button, the one at the left of the full screen button. But even so the comments would be below the video.

This doesn't mean that you don't have other issues but the MPEG4 one is a red herring. For better results is recommended to install additional codecs with 'sudo apt install ubuntu-restricted-extras'. And periodically either use the Updates tool or run 'sudo apt update && sudo apt full-upgrade" to make sure your system is fully updated. If you find any error message when running it you may post it here as surely it'll give an indication about any problem.

---

### Post by slickymaster on 2020-09-30
*Thread moved to **Installation & Upgrades**.*

---

### Post by jaxom98 on 2020-10-02
Hello, Celtic Warrior. Please excuse the delay in reply.
I found the cinema button on the youtube video, but it does not go back to original configuration.

I had already run "sudo apt update && sudo apt full-upgrade" to get to 18.04.5 from 18.04
 I tried to  run sudo apt install ubuntu-restricted-extras and got error message "E:  dpkg was interupted, you must manually run "sudo dpkg --configure-a" to correct the problem.  When I tried this I got  "error: unknon option  --configure-a

---

### Post by CelticWarrior on 2020-10-02
Yes, if it suggested running ```
sudo dpkg --configure -a
``` (please note the spaces) it means there's a problem. Try running the command again, correctly, and then follow with ```
sudo apt update && sudo apt full-upgrade
```

Then you can try again to install the restricted extras.

---

### Post by jaxom98 on 2020-10-03
I ran the sudo dpkg --configure -a  succesfully. I then ran the sudo apt "update && sudo apt full-upgrade".  The process hung at : "Package Configuration" , "configuring ttf-mscorefonts installer".  At this point you have to click (ok) buttton on the eula. The ok button is broken , and everything waits for ok reguardless of how many times you click on it.  When you close the terminal you are warned this will kill the process.

I then tried to run sudo apt install ubuntu-restricted-extrasand got 
  E:could not get lock/var/lib/dpkg/lock-frontend - open (11: Resource temorarily unavalible)
E: Unable to aquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

---

### Post by coffeecat on 2020-10-03
> **jaxom98 said:**
>  At this point you have to click (ok) buttton on the eula. The ok button is broken 

No, it isn't. Just press the TAB key to highlight the OK button, and then enter to confirm OK. This is a terminal process - you can't click on the button with your mouse.

> **jaxom98 said:**
> 
I then tried to run sudo apt install ubuntu-restricted-extrasand got 
  E:could not get lock/var/lib/dpkg/lock-frontend - open (11: Resource temorarily unavalible)
E: Unable to aquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

Did you have another package manager open when you got this error message?

---

### Post by jaxom98 on 2020-10-04
No I did not have a 2nd package manager open.

I ran sudo apt --configure -a 
then sudo apt update && sudo apt full-upgrade
then sudo apt autoremove          this process did not finish.
The last line is    libdvd-pkg:'apt-get check' failed, you may have broken packages. Aborting...

---

### Post by jaxom98 on 2020-10-11
11 Oct:  This thread is now closed unsolved
An OS reinstall was used to bypass the broken packages problem and original change in the youtube format.
Thank you to Celtic Warrior and Coffecat for your time.

---

