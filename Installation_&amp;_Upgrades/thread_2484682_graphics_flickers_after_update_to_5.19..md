---
title: "graphics flickers after update to 5.19."
date: 2023-03-06
forum: Installation &amp; Upgrades
---

### Post by slicken on 2023-03-06
I bought a Lenovo Yoga Slim 7i PRO running intel i5
I installed new Ubuntu 22.04 TLS some weeks ago and everything worked fine.
After the lastest update från 5.15 to 5.19 graphic started to flitch very hard. So hard its totally unusable.
I have now set /dev/default/grup , DEFAULT=3, this way it runs the programs 5.15 and everything works fine.

How do I fix 5.19 so it works fine and graphics not glitching?

---

### Post by ubfan1 on 2023-03-06
Does your machine have Nvidia hardware?  What driver are (were) you using?  Is that driver present when you check the modules loaded (lsmod |sort)?  Try sudo apt update then sudo apt full-upgrade and see if any Nvidia packages are held back (because of phasing).  Phasing holdbacks should clear up in a day or two.

---

### Post by MAFoElffen on 2023-03-06
I see it as having: NVIDIA® GeForce® RTX&#8482; 3050 4GB

---

### Post by slicken on 2023-03-06
> **ubfan1 said:**
> Does your machine have Nvidia hardware?  What driver are (were) you using?  Is that driver present when you check the modules loaded (lsmod |sort)?  Try sudo apt update then sudo apt full-upgrade and see if any Nvidia packages are held back (because of phasing).  Phasing holdbacks should clear up in a day or two.
no it has not nvidia. its not a gaming laptop, i think it has:  

[COLOR=#555555][FONT=Lato]integrated Intel® Iris® Xe Graphics[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-03-06
Can you show us this please:
```
inxi -Gz
```

---

### Post by MAFoElffen on 2023-03-06
Please post the output of
```

sudo lshw -C video

```
...wrapped within code tags.

@1fallen -- LOL (Great Minds Think Alike)

---

### Post by slicken on 2023-03-06
```

slk@slk-pc:~$ sudo lshw -C video
[sudo] password for slk: 
  *-display                 
       description: VGA compatible controller
       product: Alder Lake-P Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=2880x1800 resolution=2880,1800 visual=truecolor xres=2880 yres=1800
       resources: iomemory:600-5ff iomemory:400-3ff irq:177 memory:601c000000-601cffffff memory:4000000000-400fffffff ioport:3000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff

```

---

### Post by MAFoElffen on 2023-03-06
In /etc/default/grub, Line with "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", change to 
```

GRUB_CMDLINE_LINUX_DEFAULT="-- quiet splash intel_iommu=off i915.enable_psr=0 intel_idle.max_cstate=2"

```
Then do
```

sudo update-grub

```
Note that this should take care of your screen flickering, but will make it hard to recover from a Sleep condition. At 'intel_idle.max_cstate=4' there should be no problems with recovering from Sleep state, so you may want to try that setting if you use 'Sleep'...

---

### Post by guiverc on 2023-03-06
You do realize an option is to remain on the 5.15 kernel (ie. GA kernel stack) which is *supported* for the life of Ubuntu 22.04 LTS.  Certain media (eg. Ubuntu 22.04 LTS Server & *flavors *of Ubuntu 22.04 where 22.04 or 22.04.1 media was used) default to using the GA kernel stack.

**I'm only offering this as an option** - see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for more details.

(*Note: you can have both GA (5.15) & HWE kernel stack (now 5.19, next move is to 6.1)** co-exist on the same install, you'll receive upgrades to both so slight more bandwidth will be used on updates & two sets of kernels will exist on your disk so more disk space used esp. in /boot, but both are minimal*)

---

### Post by slicken on 2023-03-06
i tried both thoes but they dont work. only thing that works so far is, if I use the 5.15. program

---

### Post by #&amp;thj^% on 2023-03-06
Yep kernel 5.19 got off to a rough start, and remains so for some hardware specs and users.

---

### Post by guiverc on 2023-03-06
If you want remain on the 5.15 kernel stack, you can.

Refer to the [link I provided earlier]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") & search for "*To downgrade from HWE/OEM to GA kernel:*" which gives instructions on the process of install the GA kernel stack. 

You'll hopefully note it tells you to test it out prior to removing the unwanted stack. There is no need to actually ever remove the other stack, as I mentioned both stacks can co-exist unless you're using certain closed-source kernel modules (nvidia drivers for example) that prevent multiple stacks from co-existing. The extra disk space & bandwidth used by the extra packages you have installed/upgraded is minimal.

With many people on this thread, I suggest you be very clear as to what you'd like help with, if you are needing help with something specific (*either quote or reference someone, or their text, as whilst many can help you, they need to know what you're wanting in order to provide the help you want*)

---

### Post by MAFoElffen on 2023-03-07
> **slicken said:**
> I bought a Lenovo Yoga Slim 7i PRO running intel i5
I installed new Ubuntu 22.04 TLS some weeks ago and everything worked fine.
After the lastest update från 5.15 to 5.19 graphic started to flitch very hard. So hard its totally unusable.
I have now set /dev/default/grup , DEFAULT=3, this way it runs the programs 5.15 and everything works fine.

[COLOR=#ff0000]How do I fix 5.19 so it works fine and graphics not glitching?[/COLOR]
I am confused... I think. Is this not what was asked?

---

### Post by slicken on 2023-03-07
I gave these kernels installed.
```

slk@slk-pc:~$ apt list --installed | grep linux-image


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


linux-image-5.15.0-43-generic/jammy-updates,jammy-security,now 5.15.0-43.46 amd64 [installed,automatic]
linux-image-5.19.0-35-generic/jammy-updates,jammy-security,now 5.19.0-35.36~22.04.1 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,jammy-security,now 5.19.0.35.36~22.04.10 amd64 [installed,automatic]

```

If press enter on boot and choose the 5.15.0 than all works fine.
How do I remove everything 5.19 and make the 5.15 work as the "main one" ?

---

### Post by #&amp;thj^% on 2023-03-07
```
sudo apt remove --auto remove linux-image-5.19.0-35-generic
###and 
sudo apt remove --autoremove linux-image-generic-hwe-22.04
```

---

### Post by slicken on 2023-03-07
yes, but the DEFAULT=3 thing, does not work.
it boots 5.19 that way abyway. 
I can only press excape at startup and choose the third option.. this way it works.

Why doent DEFAULT_GRUB=3    boot me right into 5.15?

option 1 = 5.19
option 2 = 5.19 recovery more
option 3 = 5.15 <- this works how do I make it default?
option 4 = 5.15 recovery more

---

### Post by #&amp;thj^% on 2023-03-07
I'm not sure how it could boot to a removed kernel, but I'll take your word for it.
the working kernel is now booted, if not please do so before doing this:
Add two lines to /etc/default/grub
to edit use:
```
sudo nano /etc/default/grub
```
```
GRUB_SAVEDEFAULT=true
GRUB_DEFAULT=saved

```
save and exit.
Do the sudo update-grub, and reboot,

---

### Post by slicken on 2023-03-07
> **1fallen said:**
> ```
sudo apt remove --auto remove linux-image-5.19.0-35-generic
###and 
sudo apt remove --autoremove linux-image-generic-hwe-22.04
```

thanks.. i removed em and now it boots me to 5.15  witch is working fine.

Now i want to pin this kernel so i dont get automatic updates to newer one?

Anyone knows how to do it?

---

### Post by slicken on 2023-03-07
[SOLVED] thanks all [/SOLVED]

---

### Post by #&amp;thj^% on 2023-03-07
> **slicken said:**
> 
Now i want to pin this kernel so i dont get automatic updates to newer one?

Anyone knows how to do it?

Just remember you set this:
```
sudo apt-mark hold linux-image-5.15.0-43-generic linux-headers-linux-image-5.15.0-43-generic
```

---

