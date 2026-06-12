---
title: "Unknown monitor and No hardware drivers"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by Carlh13 on 2012-03-06
[SIZE=1]Hello, I'm new to Ubuntu (10.04LTS x64) after installing it a couple days ago. I followed the install into windows 7 (like an application) and then booted after completion.

I received an error but continued: (EE) [drm] failed to open device
                                                     (EE) No devices detected.

I found the screen resolution was 800x600 with an unknown monitor and when I checked for drivers it said there are no proprietary drives. I have looked around for answers but an afraid I might stuff up my computer. I want to keep Windows as my main OS but have Linux for university purposes.

Is there anything I can do to solve this?[/SIZE]

---

### Post by Mark Phelps on 2012-03-07
The message "no proprietary drivers" means that there are no AMD or NVIDIA restricted drivers available that will work with your installed version of Ubuntu and your video chipset.

The fact that you have a desktop indicates that graphics drivers HAVE already been installed.  It may be that there are no newer drivers available for your video chipset.

To confirm that, please open a terminal, enter "lspci", look for the line containing "VGA" and post that info back here.

---

### Post by Carlh13 on 2012-03-10
Thanks for the reply but it's not to worry now it somehow fixed itself. :)

---

