---
title: "Can't install 22.04 on Asus Z790-V MB with 12th gen i9"
date: 2023-10-30
forum: Installation &amp; Upgrades
---

### Post by scottwwright on 2023-10-30
I am trying to install the server version of 22.04.3 on new system that consists of an Asus Z790-V motherboard and a 12th gen i9 processor. 

I select install in the GRUB installer and it gets about a second and a half in and just hangs. It gets through recognizing the drives and loads the ASUS WMI generic driver and stops.

For testing I tried Debian 12.2 it installs and runs fine. I also tried 20.04 which installs and runs fine. However if I upgrade from 20.04 to 22.04.6, the system will not boot. 

While I am a proficient Ubuntu user, I haven't had much experience testing this kind of installation issue. What should I be doing to troubleshoot this?

Thanks!

---

### Post by MAFoElffen on 2023-10-31
I have 2 systems here that are recent i9. One is 10th Gen i9, the other is 13th Gen i9. The 13th Gen is a Z790 chipset. Both were installed originally as 22.04 server. Both did fine...

Could you post your installer log to paste.ubuntu.com or a pastebin at termbin.com?

---

### Post by scottwwright on 2023-11-02
I just wanted to respond that I figured this out. It was display related. I used the instructions here: [https://dgpu-docs.intel.com/driver/installation.html](https://dgpu-docs.intel.com/driver/installation.html) to fix the issue.

---

### Post by garfnon on 2024-04-02
> **scottwwright said:**
> I just wanted to respond that I figured this out. It was display related. I used the instructions here: [https://dgpu-docs.intel.com/driver/installation.html](https://dgpu-docs.intel.com/driver/installation.html) to fix the issue.


I'm running into the same issue with the same hardware when trying to install 22.04 from USB. Could you elaborate on what you did from that documentation?

---

### Post by MAFoElffen on 2024-04-05
> **scottwwright said:**
> I just wanted to respond that I figured this out. It was display related. I used the instructions here: [https://dgpu-docs.intel.com/driver/installation.html](https://dgpu-docs.intel.com/driver/installation.html) to fix the issue.
@scottwwright --

Ditto on the last question asking you to elaborate.

I (personally) have been working with two Intel Graphics Support Engineer Teams on those exact instructions and drivers. So I know those have big holes there with that. So--> "Informed people" want to know what went right for you with that?

This would help me, and them in our work with their drivers, and those instructions for them...

Because it is my experience with this hardware combination, that the standard Intel in-kernel i915 driver works. Also that the Intel OOT graphics driver introduces some challenges and problems that we are actively working on.

---

### Post by sander-l123 on 2024-07-02
Hi,

I've a question. I'm considering buying this mainboard with an intel Core i9&#8722;14900K 3200 1700 CPU, and planning to install the newest Ubuntu 24.04 LTS. I'm wandering if this issue is resolved on the newest Ununtu. Or will I run into trouble and is it advised to buy another mainboard?

Thanks!

---

### Post by oldfred on 2024-07-02
Since different CPU and Ubuntu version would be better to create your own thread.
But there is this:
[https://www.phoronix.com/review/intel-14600k-14900k-linux](https://www.phoronix.com/review/intel-14600k-14900k-linux)
But different motherboards brands or versions may have different issues, but should work.
Issues often are the chips used for Wi-Fi or Internet. And if separate video card you have to be sure to have correct driver installed during install.
Best just to test with live installer.

---

