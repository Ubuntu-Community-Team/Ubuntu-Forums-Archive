---
title: "Can't start ubuntu after update"
date: 2021-08-04
forum: Installation &amp; Upgrades
---

### Post by himanshu.tecstub on 2021-08-04
Hello,

Ubuntu 20.04.2.0 LTS installed on my laptop and working fine till yesterday.
Today i just run apt get update and apt get upgrade than after ubuntu not start at boot time. (just showing laptop company logo)

I try to format with new Ubuntu 20.04.2 which is working fine. but when i run below two commands same problem fetch (install ubuntu with minimal installation and without install any extra software).

Please suggest what should i do?

---

### Post by mippi on 2021-08-05
I have exactly the same problem. It comes from new kernel and GPU driver....

---

### Post by MAFoElffen on 2021-08-05
To the Original Poster )The "OP") 
You said 
> I try to format with new Ubuntu 20.04.2 which is working fine. but when i  run below two commands same problem fetch (install ubuntu with minimal  installation and without install any extra software).
Could you please try to explain that in more detail... If a problem in English, I will try to translate on my side. I want your words. What you see and what is does,... Because what you had as title describes after an update. But what you described was more like from an installation.

To the second poster, do you have another thread open on your problem? If so, I will help you there.

---

### Post by himanshu.tecstub on 2021-08-11
In my laptop Ubuntu 20.04.2.0 working fine.
But when i run `apt-get update` & `apt-get upgrade` & `reboot` than can't start Ubuntu (freeze on laptop company logo)


Because of that problem.I install fresh Ubuntu 20.04.2.0 (with minimal installation option)  on same laptop which is working fine after installation process complete.
than after when i run `apt-get update` & `apt-get upgrade` & `reboot` same problem occurs.

So there is some problem with any update program.

---

### Post by MAFoElffen on 2021-08-11
1. What is the brand and model of your laptop?
2. When you boot the LiveCD media and use try, does it run stable"
3. While in the LiveCD Environment, please go to Activity, type "term" asmd open a terminal session... Please post the result of the following, withoin [noparse]```
 Output_here 
```[/noparse] tags...
```
sudo lshw -C video
egrep -m 1 "Model" /proc/cpuinfo
```

---

### Post by himanshu.tecstub on 2021-08-14
1. HP EliteBook
2. Download latest version from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) and create bootable USB in ubuntu and install that via boot manager
3. 
> sudo lshw -C video  *-display                 
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:d4000000-d43fffff memory:c0000000-cfffffff ioport:4000(size=64) memory:c0000-dffff
No result for "egrep -m 1 "Model" /proc/cpuinfo"

---

### Post by MAFoElffen on 2021-08-14
It has a 3rd Gen Intel iCore i5 CPU/APU. Your graphics are using the in kernel Intel Graphics driver i915 and the mesa drivers. By not answering which version of the two choices on the download page you posted, you are either running versions 20.04.2.0 or 21.04. (It would help to narrow that down to one of those.) There was 3 diifrent models of the HP Elitebook. It would be good to narrow that down also.

When you boot on the LiveCD and select "Try"... Does it run okay?

Please explain what you mean by this" Please Describe...
> but when i run below two commands same problem fetch (install ubuntu  with minimal installation and without install any extra software).
... Do you mean in the installer, you only choose those options... And after the install finishes, after the reboot, then it only goes to the boot splash with the Ubuntu Logo... and never gets to the graphical log on screen? Either confirm that, or tell me the differences of...

---

### Post by himanshu.tecstub on 2021-08-17
I choose [COLOR=#000000]20.04.2.0 on download page.[/COLOR]
[COLOR=#000000]Also select install ubuntu option for new installation. (not "[/COLOR][COLOR=#000000]Try[/COLOR][COLOR=#000000]")[/COLOR]

[COLOR=#000000]After finish installation (can't connect wifi for ignore update during installation) connect wifi and update command run.[/COLOR]
[COLOR=#000000]After reboot laptop can't load [/COLOR]ubuntu OS (just shown HP logo)[COLOR=#000000]

Also try this 2 times on same day but same problem (with [/COLOR]"Normal Installation" & "Minimal Installation" option[COLOR=#000000])[/COLOR]

---

### Post by janeku2 on 2021-08-17
I think I finda solution based on some other experience:
 
[LIST]
[*]apply fix for 5.11 kernel: 
[/LIST]
 
[LIST=1]
[*]Boot in first available kernel that is working (for me it is 5.8.0.59) 
[*]Add repository: add-apt-repository ppa:kelebek333/nvidia-legacy 
[*]Apply fix: apt install xorg-modulepath-fix 
[*]try to update and upgrade 
[*]reboot 
[/LIST]
If still do not solved please change from Nvidia to nouveau drivers (also in older working kernel version). Try to reboot with 5.11 kernel.

 For me this was working combination.

 Please do not forget to use sudo command before applying above  commands. 
Note: Definetely there is some bug with lib32gcc1 and libgc6xx and their  incompatibility with this and later kernel updates. We have to wait for  this fix for nvidia drivers.

EDIT: I do not know if it is legal or allowed to link to external sites, but this is a link from launchpad dot net where this problem is described and solved. I contacted author and tell him about libs problem so I expect asap to get back answer from him.
[URL="https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy"]https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy
[/URL]

---

### Post by tea for one on 2021-08-17
> **himanshu.tecstub said:**
> Hello,

Ubuntu 20.04.2.0 LTS installed on my laptop and working fine till yesterday.
Today i just run apt get update and apt get upgrade than after ubuntu not start at boot time. (just showing laptop company logo)

I try to format with new Ubuntu 20.04.2 which is working fine. but when i run below two commands same problem fetch (install ubuntu with minimal installation and without install any extra software).

Please suggest what should i do?

When you run the second command, do you see something like this where another kernel is being installed:-

```
edited@edited:~$ [COLOR="#0000FF"]sudo apt upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
 [COLOR="#0000FF"] linux-headers-5.11.0-27-generic linux-hwe-5.11-headers-5.11.0-27
  linux-image-5.11.0-27-generic linux-modules-5.11.0-27-generic
  linux-modules-extra-5.11.0-27-generic[/COLOR]
The following packages will be upgraded:
  linux-firmware linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04
  linux-image-generic-hwe-20.04
4 to upgrade, 5 to newly install, 0 to remove and 0 not to upgrade.
Need to get 190 MB of archives.
After this operation, 428 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

---

### Post by MAFoElffen on 2021-08-17
He still has not answered any kind of questions about what kind of Laptop he has. The model and model number... It wasn't until his post #8 that he mentioned that is stops at the "HP Logo"... Which, by the results of what he posted as results in Post#6, being Intel Graphics from a Gen 3 iCore, we can assume that it is some kind of older HP Laptop.

But: Freezing at the Laptop BIOS Screen(???) before it even gets to Grub2(???)... And being caused by an update, where it was running fine before that... Something very weird is going on there. We definitely need more info on what is going on. That would mean there might be some kind of boot loader problem there.

EDIT: I'm thinking it might be a Firmware problem with his BIOS. And that, since he hasn't told us what the Laptop is, that "he" needs to check the HP Support site to see if there is a BIOS firmware update available for it. I don't see us being able to steer him in the right direction for that without further information from him. I think that his is first step and what he needs to try first, before trying anything else. That would set the baseline and rule that out.

EDIT2: Ignore the post from " janeku2 "... He didn't read through the thread, and posted a solution for NVidia Graphics, which the OP is using Intel Graphics. His intent was good trying to help, but... That solution would break this person's machine further. Just saying... a simple well-intentioned mistake.

---

