---
title: "Multipath install on 14.04LTS?"
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by Asquirrel on 2015-03-02
I feel like an idiot. According to [https://help.ubuntu.com/lts/serverguide/multipath-setting-up-dm-multipath.html](https://help.ubuntu.com/lts/serverguide/multipath-setting-up-dm-multipath.html) I should put "install disk-detect/multipath/enable=true" at the installer prompt. I'm using the minimal install ISO and I can't find the prompt it's talking about; even in expert mode.

Strictly speaking, I can install ubuntu. It's just that I see the four paths to my device as 4 disks instead of one (hence the need for multipathing...). This means when I install the files show up on all four drives, but the boot record is only on one of the 4 paths, so if that path dies...I can't boot. Please, someone, tell me how to install with multipathing support!

---

### Post by Kirboosy on 2015-03-02
When the Installer boot menu pops up tap the "TAB" key and append that line to the end of the boot argument. That should then enable multipath.

Hope that helps!
~Caboose

---

### Post by Asquirrel on 2015-03-02
I tried that. tab didn't work, but F6 did (source: [https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line](https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line)). I placed "install disk-detect/multipath/enable=true" in the same location as the red box in the image. No joy, I still see each path individually instead of a unified device. :(

---

### Post by Kirboosy on 2015-03-02
What kind of hardware are you using on this system? Perhaps its not liking the hardware for some reason.

---

### Post by Asquirrel on 2015-03-02
...derp. Hardware no, driver yes. The hardware is a Cisco UCS chassis (B200 M3 blades), the HBA, as it were, is a virtual HBA. RHEL works just fine because RHEL wants to play nice with enterprise hardware. Ubuntu probably doesn't have the same driver. *does more googling*

edit: I am thankful. Sometimes you need a voice outside your own brain to jostle your thoughts in a new direction.

---

### Post by Kirboosy on 2015-03-03
Looks like the server is "Ubuntu Certified" So one would think the drivers and everything would play nicely together.

[Cisco UCS B2000 M3]("http://www.ubuntu.com/certification/hardware/201311-14337/")

Perhaps a BIOS update will fix part of the issue. I had a issue with a home server where I had to update my BIOS to a newer version to get my RAID working. You can see on the Ubuntu page the version their machine was running when they certified it. Cisco Systems: B200M3.2.2.2.0.042820141643 (Legacy)

~Caboose

---

