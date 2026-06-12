---
title: "Nvidia graphics driver install freezes!!"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by draconia11 on 2009-12-11
Ok, so I have been trying and trying to get my visual effects to work. i am running Ubuntu 9.10 on a lenovo T61p laptop. 64-bit.

I am trying to install an Nvidia driver so that I can activate the visual effects and there are two. One freezes a bout 1/4 of the way through, and the other seems like it will work, then freezes halfway and then does nothing. When I try to cancel out of it, it will not let me.
 
The 2 drivers are:
NVIDIA accelerated graphics driver (version 173)
and
NVIDIA accelerated graphics driver (version 185) (recommended)

I was using the same version of Ubuntu a while ago, and tried to get Windows 7 which then wanted me to pay for a new code, so i am now back to Ubuntu after fully deleting the partition. It worked fine before and the driver activated fine, but for some reason with the same install disk and computer it does not want to install this time!! very frustrating.

Edit: I tried installing EnvyNG as well and when i got to the prompt to install the driver it gave me this error which I do not understand:

result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 76, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required
[===================================50.0%

Please help!!

Thanks, SH

---

### Post by lemming465 on 2009-12-12
If 9.10 isn't supporting your video adequately, your basic choices are live with the less capable open source driver, reinstall with an older 9.04 release if that works OK, or live on the bleeding edge with a Lucid Lynx alpha quality release if that works OK.  You have my sympathy, but there may not be any immediate solution involving Ubuntu 9.10.  It's possible that some other distribution such as Fedora 12 would do better, if you need something very current, but supported, and don't have to have Ubuntu.

---

### Post by avtolle on 2009-12-12
IIRC, you need to run ```
sudo apt-get update
``` from the terminal before selecting to activate the driver. Jockey is looking for the most current packages, and (again, from memory), the release notes to 9.10 indicate that the repos need to be fully updated before proceeding. HTH.

---

### Post by draconia11 on 2009-12-13
I ran the above code in terminal and the same problem persists. Is that code what should update the repos? (sorry im still new to this stuff) It ran fine and completed, but the activation of the driver still freezes.

---

### Post by lemming465 on 2009-12-13
Another option is to skip the repositories and [download the Nvidia driver directly]("http://www.nvidia.com/Download/index.aspx?lang=en-us"); the current Ubuntu driver is 185.18.36 from late August; the current production nvidia driver is 190.42 from late October, and the current beta driver is 195.22 from late November.  That way is slightly more work, but can produce better results if you are seeing problems installing older drivers. If you decide to try one of the newer nvidia drivers, you need the kernel build infrastructure to compile the glue module between the open source kernel and the binary nvidia blob.  Something like:```

sudo -i
aptitude update
aptitude install build-essentials linux-headers
# download the driver
bash ./NVIDIA*run
# follow the prompts from the text-mode installer

```

---

