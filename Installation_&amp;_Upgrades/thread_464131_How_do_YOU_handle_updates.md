---
title: "How do YOU handle updates?"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by mvsjes2 on 2007-06-04
I've never bothered to apply automatic updates to my Linux distros before. Recently however, I decided to turn on automatic updates for security issues, thinking that they would be minor updates that had low risk of hosing my system.

Once I turned this on on my feisty system, the updates automatically upgraded my kernel. This of course hosed my nvidia drivers on the next reboot, which I did a couple of days later. I reinstalled nvidia, and things seemed to be going OK, but then when I started mythfrontend, it immediately seg faulted with no log entries anywhere, no indications of what was going wrong. I rebooted again and all I got was a black screen just before the kdm login screen. I booted to a rescue cd and checked all the logs I could see and found no problems. The xorg log was cut off in the middle of the nvidia initialization with no errors.

I finally threw in the towel and restored my whole root file system back to about a week before the trouble started and needless to say I've turned off automatic updates.

This leads me to conclude that automatic updates are useless for anyone with nvidiia drivers or other kernel dependent compiles.

I rather like the idea of automatic security or critical fixes being applied, and have used this on  my windoze systems for years and I can't remember a single glitch from doing this.

Is there any way of accomplishing a similar result with ubuntu?

Also, is there any way to find out what has been updated by whatever method (manual or automatic)? I've searched and can't find any way to get this information. If apt kept a log or something then at least I could query it and have a better idea of what's been happening with my upgrades next time something breaks.

---

### Post by MJN on 2007-06-04
I'm not at my machine right now but I recall there being a log at **/var/log/dpkg.log** if I remember correctly.
 
Mathew

---

### Post by Yoooder on 2007-06-04
> **mvsjes2 said:**
> 
This leads me to conclude that automatic updates are useless for anyone with nvidiia drivers or other kernel dependent compiles.

I have a small bash script that does an 
> apt-get update
followed by
> apt-get upgrade

which will fetch the list of updates and only update non system-critical.  I run it daily, to keep the majority of things up to date.

Then whenever I feel like it (usually weekly or bi-weekly) I will run an apt-get dist-upgrade to fetch kernel updates and anything else.  If there is a kernel update I recompile my nvidia-kernel as well as my ivtv module (for my TV tuner for MythTV).

This works well enough for my needs, and usually covers all my bases.  I just keep a list of kernel-dependant modules (like nvidia and ivtv) so that I can easily recompile them all whenever need be.

---

### Post by MJN on 2007-06-04
Yoooder,

It sounds like you may misunderstand the differences between the **upgrade** and **dist-upgrade** options. **apt-get upgrade** will still fetch, and install, kernel updates too. The only difference with **dist-upgrade** is the that the latter will also install any (new) dependent packages.

The net effect is that **upgrade** will only ever bring your currently-installed packages up to date but the overall package count won't increase. **dist-upgrade** on the other hand will, if necessary, install (or even remove!) additional/affected packages as required.

Theory aside, I only ever do a **apt-get update && apt-get upgrade** and always receive kernel updates and other 'system critical' updates. I've never done an **apt-get dist-upgrade** and having just tried it now there are no updates to be had. Needless to say, since the initial release of Dapper there have of course been numerous kernel and other system-critical updates released.

Mathew

---

### Post by mvsjes2 on 2007-06-05
Thanks a lot for the information! The dpkg log is exactly what I was looking for. I guess I missed it because I was looking for apt logs.

---

### Post by geoffree on 2007-06-05
You sound knowledgeable.  Perhaps you can help me with not one but two concerns.
I am running Dapper Drake 6.04 and want to reconfigure my kernel to eliminate unnecessary modules. Is there some site or book that would help me do this?  I have had former experience with Red Hat Linux but theres been a lag in time and in memory.

Along these lines, I discovered that some of these modules that SEEM unnecessary are NVidia drivers.  I am running an IBM ThinkCenter with a built-in Intel video card, not NVidia. Any idea why these files should be active?

I hope I am not writing to an inappropriate locale.  If not, and you can provide a little help, it would be appreciated. I dont have friends now who are into Linux, as in past days, which is how I learned the basics, using man pages for the quick reminders and to fill in the empty spaces.

Geoffrey

---

### Post by tgalati4 on 2007-06-05
Ubuntu is trying to appeal to a wide audience, so the kernel selected has a lot of module hooks compiled in.  The actual modules are not loaded unless you do a sudo modprobe loadyourfavoritemodule.  The hardware detection algorithm (HAL) will detect your hardware during boot and select modules that get loaded.  lsmod will show what modules are loaded in your operating system.  

You could recompile your kernel to remove those hooks, but then you might break other packages that are expecting those hooks to be there.  I can't tell you in advance what is safe to remove.  Perhaps others can.

---

### Post by mvsjes2 on 2007-06-05
> **geoffree said:**
> Along these lines, I discovered that some of these modules that SEEM unnecessary are NVidia drivers.  I am running an IBM ThinkCenter with a built-in Intel video card, not NVidia. Any idea why these files should be active?


I too have been picking up Linux recently after a long lapse. I played around with Debian and Red Hat years ago, then much later started using kubuntu. A lot has changed. While frustrating at times, overall it's a real joy to use.

If you have an Intel graphics chipset, then the nvidia chipset wouldn't be necessary and I don't think would even load. Go to /etc/X11/xorg.conf and see what you have for the "driver" entry there.

I'd take a stab and say that you may have an nvidia bridge chipset (not the graphics card), which is why you may see nvidia references in your modules. If I do an "lspci" on my system I see nvidia mcp55 all over the place, for ram memory, isa bridge, smbus, usb etc. I also have an nvidia graphics card, a geforce 7300, so I use the drivers supplied by nvidia for this particular card.

---

### Post by web1b on 2007-06-06
I don't understand the basics of how this works.

Exactly how can you set an Ubuntu workstation to automatically install critical security updates unattended on a schedule?  I would like to keep several workstations updated without having to log into each workstation myself and not worry that some major version upgrade will be installed.
If it is batch file script, how do you set it up and where do you save the file?  I guess there is no option in the GUI to do this?

---

### Post by MJN on 2007-06-07
Automatic updates are generally considered *A Bad Thing* (TM) given that if something can go wrong it will. Updates can go wrong, particularly when requiring user input/intervention and so it is something you really want to be sat in front of at the time, or at least be confident with the consequences of a particular update or be able to safely automate any input/intervention beforehand.
 
A halfway house you might be interested in is **cron-apt** - there have been numerous articles/discussions on the package so search away and see what you think. No doubt that are other such packages so in the absence of any specific recommendations try Googling for them.
 
Mathew

---

### Post by mvsjes2 on 2007-06-07
I come from a mainframe world, and when installing fixes here the author of the fix could put a "hold" on it, signifying that the fix needed some kind of intervention or could cause other problems. This way, regular, non-disruptive udpates could be installed unimpeded, and  those that required, for instance, a reboot to install, would be held until the user manually released them. I think that's all that is missing from this process.

---

### Post by web1b on 2007-06-07
Is there a way to centrally manage and monitor updates on many Ubuntu workstations other than logging into each individual workstation one by one to review and launch updates?

We are considering moving large numbers of XP workstations to virtual machines running as guests in Ubuntu.  We can manage updates of the XP machines with Windows Software Update Services and other methods, but if we would have to log in to each Ubuntu host and approve updates on each workstation one at a time, it will be way too labor intensive to be viable.

Are there any solutions to efficiently handle updates on more Ubuntu workstations than is practical to log into one by one?
We also do not want the end users to deal with Ubuntu at all.  The plan is to find a way for the virtual machines to automatically launch in full screen mode with the users being locked out of the Ubuntu desktop.

---

### Post by Wim Sturkenboom on 2007-06-07
On the original question:
I'm running Dapper on a system with NVidia card. Even after kernel updates, I have never had to install the drivers again. I was pleasantly surprised with that after the first kernel update (specially printed the instructions so I would have them at hand in case I had to).

---

### Post by mvsjes2 on 2007-06-07
Are you using the :"nvidia" driver or the "nv" driver?

---

### Post by Wim Sturkenboom on 2007-06-08
If you're addressing me, I use the nvidia driver.

---

### Post by mvsjes2 on 2007-06-09
Wim,

Sorry, I was addressing you.

That's interesting since I always seem to have to recompile the driver when the kernel changes. I wonder if I'm doing something wrong.

---

### Post by MJN on 2007-06-09
It depends on which driver you're using and where/how you got it. If it's the 'nvidia-glx*' driver(s) from the Restricted repository then as long as you've got the restricted modules installed (i.e. linux-686 package, for example, which in turn depends on linux-image-686 and linux-restricted-modules-modules-686) then it will all be handled automatically requiring no additional work when the kernel is updated.

Run **dmesg |grep -i nvidia** and **aptitude search nvidia** (or **dpkg -l |grep nvidia**) to confirm which 'nvidia' driver you're using, and where it was from.

Mathew

---

### Post by Wim Sturkenboom on 2007-06-09
```
wim@internet-desktop:~$ **dmesg |grep -i nvidia**
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x0 00f7c00
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x3bef3040
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x3bef30c0
[17179569.184000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x3bef8140
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x3bef7e80
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @  0x00000000
[17179592.320000] nvidia: module license 'NVIDIA' taints kernel.
[17179592.324000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oc t 16 21:56:04 PDT 2006
wim@internet-desktop:~$ **aptitude search nvidia**
i   nvidia-glx                                                - NVIDIA binary XFree86 4.x/X.Org driver
p   nvidia-glx-dev                                            - NVIDIA binary XFree86 4.x/X.Org driver development files
p   nvidia-glx-legacy                                         - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
p   nvidia-glx-legacy-dev                                     - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files
v   nvidia-kernel-1.0.7174                                    -
v   nvidia-kernel-1.0.8762                                    -
v   nvidia-kernel-1.0.8776                                    -
i   nvidia-kernel-common                                      - NVIDIA binary kernel module common files
p   nvidia-settings                                           - Tool of configuring the NVIDIA graphics driver
p   nvidia-xconfig                                            - The NVIDIA X Configuration Tool
wim@internet-desktop:~$

```

I only remember that I followed method 1 for Dapper for the installation, no other details.

---

### Post by mvsjes2 on 2007-06-09
Rght, that makes sense now. I always use the latest driver from the nvidia web site, not the ones in the repos.

Thanks very much for the useful information!

---

### Post by johndoesacc on 2007-06-13
> **web1b said:**
> Is there a way to centrally manage and monitor updates on many Ubuntu workstations other than logging into each individual workstation one by one to review and launch updates?

Certainly. Behold, the beauty of linux. :D

I've used [omnitty]("http://omnitty.sf.net"). Unfortunately i had to compile it, though. I don't remember the process, but it seems that its only dependency (librote) is in the repos, so it shouldn't be too bad. I might make a tutorial on easy ubuntu setup of it sometime somewhere. :)

Omnitty works by making you able to log in to several clients and overview them all in one terminal. From this terminal you can activate which of the clients you want to send commands to. Then you can send one command, e.g. "apt-get update && apt-get upgrade" to all of them by only typing the command once. It shows the last couple of lines on all the clients in the overview, so you can easily see if one of the clients gave a different output, most likely an error. Then you can choose to only work on that single terminal to manually check what's wrong. It's brilliant. You can do anything, not just updates.

And BTW, it's all done via SSH. It's encrypted and you can do all the usual password-less login magic and all.

Otherwise, you could probably set the clients to install automatically no-questions-asked via a cron-job and maybe through an apt-mirror to control which updates go through.

---

