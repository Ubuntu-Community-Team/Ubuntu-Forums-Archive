---
title: "Should I reinstall ubuntu if yes how to reinstall?"
date: 2018-01-08
forum: Installation &amp; Upgrades
---

### Post by srikuntu on 2018-01-08
While installing ubuntu with dual boot using USB, while installing I skipped to download the required drivers. Due to that I am unable to use wifi and any other service. I have also messed up the terminal. I am looking to reinstall ubuntu 16.04 and start fresh. Help me with step by step with setting partition to whole reinstallation with USB. Thank you

---

### Post by ajgreeny on 2018-01-08
Without knowing your hardware it is impossible to tell you what to do but I doubt if a reinstallation is the easiest way to proceed.

If you can attach to an ethernet cable connection do so and run a system update with commands ```
sudo apt update
sudo apt upgrade
``` which may be all that is necessary to get you going on wifi.

You can also go to **Additional Drivers** from the menu or dash to see if any drivers are available.

Finally, install **inxi** from the repos and show us the output of command ```
inxi -F
``` which will show us a lot of info about your hardware.

---

### Post by srikuntu on 2018-01-09
I think even the path is not correct. Still not able to connect to wifi.

---

### Post by RobGoss on 2018-01-09
I think reinstalling the whole Ubuntu system might be harder and may cause other issues seeing you have a dual boot system

If you can use a hard wire connection you can update the system and install **Additional Drivers** as suggested

You might also want to provide some information about your machine so others can help trouble shoot this issue. Is this a older computer?

---

### Post by ajgreeny on 2018-01-09
I am not sure what you mean by "even the path is not correct"; do you mean the urls or sources that you have in your sources.list file, as I can see you appear to have some non-standard repos enabled, eg codeblocks and webupd8team ppas.
Try disabling them to see if it helps, though it may be that one of those has either installed a version of python3 that is causing the difficulties you have, or more likely in view of the image you show, needs a version of python3 that is not available.

---

### Post by joe129 on 2018-01-10
have you checked the existing hdd for any errors , does it boot from windows?

---

