---
title: "Unable to get past Grub on live usb on Dell Inspiron 7710 AIO All in One"
date: 2023-07-24
forum: Installation &amp; Upgrades
---

### Post by galosaimi on 2023-07-24
[COLOR=#454545][FONT=Arial]The computer bought newly is Dell Inspiron 7710 All in One PC

[/FONT][/COLOR]
[COLOR=#454545][FONT=Arial]1- Comes with pre-installed Windows-11 only
2. Flashed Ubuntu 20.04 on USB using Rufus (GPT)
3. I follow this video to change ONLY BIOS settings (youtube video on a different computer At minute 2:28 of youtube video titled “A clean install of linux mint 21 (Dell UEFI BIOS with Secure Boot and MOK)”).
4. Rebooted
5. Grub loads
6. On choosing Ubuntu option in Grub, the screen goes blank

[/FONT][/COLOR]
[COLOR=#454545][FONT=Arial]So, I cannot proceed to install Ubuntu.

[/FONT][/COLOR]
[COLOR=#454545][FONT=Arial]As, I am beginner in linux and its commands and editors, if it possible to provide me with deatiled steps or video that I can follow.

Thanks[/FONT][/COLOR]

---

### Post by tea for one on 2023-07-24
New hardware often requires a recent kernel.
Why not try Ubuntu 22.04?

---

### Post by galosaimi on 2023-07-24
Since I have to work with ROS neotic and ROS neotic will not offically support Ubuntu 22.04.

---

### Post by ubfan1 on 2023-07-24
The easy solution is to get an older machine, not a 13th Gen Intel cpu!  Alternatively, install an Ubuntu release that works (22.04, or even 23.04), then install the older software needed by ROS Noetic.  Treat it like a cross development platform, keep the old stuff in your own directory, with it early in your path to pick it up.

---

### Post by galosaimi on 2023-07-24
It is not clear to me "install[COLOR=#000000] the older software needed by ROS Noetic. Treat it like a cross development platform, keep the old stuff in your own directory, with it early in your path to pick it up.[/COLOR]"

---

### Post by guiverc on 2023-07-24
> **galosaimi said:**
> [COLOR=#454545][FONT=Arial]
2. Flashed Ubuntu 20.04 on USB using Rufus (GPT)
3. I follow this video to change ONLY BIOS settings (youtube video on a different computer At minute 2:28 of youtube video titled “A clean install of linux mint 21 (Dell UEFI BIOS with Secure Boot and MOK)”).
4. Rebooted
5. Grub loads
6. On choosing Ubuntu option in Grub, the screen goes blank
[/FONT][/COLOR]

You weren't specific as to what Ubuntu 20.04 LTS ISO you were using.

Ubuntu 20.04 LTS including up to 20.04.5 LTS media may no longer boot due to *revoked *keys, which is what led to the creation of Ubuntu 20.04.6 LTS media.

Refer to a [20.04.6 announcement]("https://fridge.ubuntu.com/2023/03/23/ubuntu-20-04-6-lts-released/") and you'll read 

> Unlike previous point releases, 20.04.6 is a refresh of the amd64  installer media after recent key revocations, re-enabling their usage on  Secure Boot enabled systems.

where the *revoked* key will prevent boot, but how a machine achieves this can be unique (*ie. message, no message or machine just stops are all compliant with expected results*)

Rufus allows you to *reformat* an ISO which can prevent booting on specific hardware and version of the rufus app itself matters (*thus I'd recommend just a simple clone; dd-mode I think its called in Rufus, but sorry I don't use that app* *as that tends to remains consistent*)

---

### Post by ubfan1 on 2023-07-24
Your 13th Gen Intel processor needs a 6.0 kernel or later.  Right now, only Ubuntu 23.04 has such a kernel (6.2), but at some point in the future, the hardware enablement packages (hwe) will allow the later point releases of 20.04 and 22.04 to install the 6.2 kernel.  Some special kernels for 22.04 (and I assume 20.04 too)  but not the generic, already have the hwe 6.2 kernels.  You could move your SSD to another older machine and try to install Ubuntu 20.04 then update the kernel with an Ubuntu 6.2 kernel or a mainline kernel 6.0+.  Or, you could go with the latest supported Ubuntu 23.03 with the 6.2 kernel, knowing it has only 9 months support, so an upgrade would be needed much sooner than an Long Term Support (LTS release like 20.04 and 22.04).  Getting a 20.04 system running on your hardware seems like more effort than just setting up the latest release (23.04) designed for your hardware, and then getting any tools required for your project (ROS).

 With a running 23.04 system, you can now select the tools needed for your project. See [https://www.ros.org/reps/rep-0003.html#noetic-ninjemys-may-2020-may-2025](https://www.ros.org/reps/rep-0003.html#noetic-ninjemys-may-2020-may-2025)   Those older tools are (probably) available in the 20.04 archives, so you should be able to download the package, and install it wherever you want (NOT in a system area).  e.g.  /home/<username>/ROS/bin  for the executables   .../ROS/lib for the libraries, etc.  Have a setup script for ROS to add the ~/ROS/bin early to your PATH environment, so typing c++ will find the ROS/bin version before the system one.  Multiple projects may have different setup scripts, but if you only do ROS, you may just put the PATH changes into your .profile.  

Generally, it is far better to have the projects separated from your system -- that way, no system update can "break" something in your project.

---

### Post by galosaimi on 2023-07-24
Many thanks to the provided advices.

Acutally, I installed Ubuntu 22.04 and the installation went smoothly with no any issues. Then, I installed ROS neotic on Ubuntu 22.04 by building ROS env via Mambaforge package mangaer. I tried to run many examples and show correct result. I hope no issues when I am working with other packages in ROS.

---

### Post by MAFoElffen on 2023-07-25
If it does have issues, there is another path that would open up more to you.

13 gen iCore and 22.04 runs KVM Hosting very well. I have an iCore 9-10900K... I use 22.04 with the HWE Hardware Enablement Stack.  

You could always run a 20.04 VM on that, with 'ROS Noetic' installed on the supported target Ubuntu version. That way the hardware in the VM  is more generic.

---

### Post by galosaimi on 2023-07-25
Ok, thanks !

---

