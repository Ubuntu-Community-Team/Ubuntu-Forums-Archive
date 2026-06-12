---
title: "Booting problems, caused by grub config changing maybe.. Please help"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by linaafryn12 on 2019-03-06
Hello, i am new user to ubuntu bcs i want to migrate from windows, i like to set up my pc by looking tutorials and articles. i'm not a pro user, but i understand how to use terminal, installing programs, 
and until yesterday, I installed many program for my daily using, but that time, maybe i accidentally changed the grub config. So i tried to look tutorials and solved the first problem, but I'm too obsessed haha, and then i changed the grub config again, and after i tried to reboot...
[B]1. system bootorder not found. initializing default
creating boot entry "Boot000A"with label "ubuntu" for file "EFI\ubuntu\shimx64.efi' [/B]and then...
**2. error: can't find command 'hmwatch'.**
**system bootorder not found. initializing default**
**3. error: no su**[B]ch device: F515-593E
error: out of memory
press any key to continue...

failed to boot both default and failback entries.

4. and the last one, the biggest nightmare i've ever had, maybe....
sooooo many abstract characters came out, oh my goodness that was so scary:"

[/B]and then it went to grub2, and there were like 3 or 4 choices, like ubuntu, advanced setting for ubuntu, system setting (BIOS), etc i forgot.
i can't figure it out what really happens to my laptop, and until now i haven't found any helpful articles or yt video tutorials that work for me.
idk how to fix it, and rarely people around me using linux. **and i haven't backup my data huhu, **but i think it won't be deleted, hope so. i can't reinstall ubuntu for now, since i haven't backup my data.
**I hope that you guys can help me, big love from Indonesia!! <3 <3 thank you so much  (sorry for my bad english, not a native hehe)**

---

### Post by kc1di on 2019-03-06
I Think at this point a fresh install may be the best bet.  You can boot to the Live session and copy any important files to a usb stick or external drive Then reinstall Ubuntu.

---

### Post by yancek on 2019-03-06
> **3. error: no su****ch device: F515-593E**

The error above and the others appear to show a problem with the EFI partition.  Do you have or did you have an EFI install?  Did you or do you have windows still installed?  If so, which version of windows?  Was it an EFI install?  Boot the Ubuntu install media and open a terminal and run this command to see if it shows an EFI partition.  If so, create a mount point for it then mount the partition and check to see if you have an ubuntu directory there with Grub boot files.  Do you have an option in the BIOS on boot to select different boot options?  If so, what are they and what happens when you select them?

---

### Post by oldfred on 2019-03-06
While kc1di suggestion of re-install is probably the quickest and easiest solution, if you want to see if it can be repaired:

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

My install to a pre-partitioned drive with validated ISO to an SSD takes less than 10 minutes.

---

### Post by linaafryn12 on 2019-03-07
how to install boot-repair offline? i can't connect to any wifi bcs there's no wifi adapter, it said when i running ubuntulive cd..

---

### Post by linaafryn12 on 2019-03-07
> **yancek said:**
> The error above and the others appear to show a problem with the EFI partition.  Do you have or did you have an EFI install?  Did you or do you have windows still installed?  If so, which version of windows?  Was it an EFI install?  Boot the Ubuntu install media and open a terminal and run this command to see if it shows an EFI partition.  If so, create a mount point for it then mount the partition and check to see if you have an ubuntu directory there with Grub boot files.  Do you have an option in the BIOS on boot to select different boot options?  If so, what are they and what happens when you select them?

i'm sorry, i don't have an idea what is EFI.. i'm newbie user. I've deleted my windows, there's only ubuntu 18.10 left.
I can't open any option in the BIOS except system/BIOS setting, when i choose ubuntu or advanced system (there're 4 version of ubuntu maybe, recovery mode if i'm not wrong) of ubuntu, it couldn't open, it said you must load the kernel first, thank you.

---

### Post by linaafryn12 on 2019-03-07
> **oldfred said:**
> While kc1di suggestion of re-install is probably the quickest and easiest solution, if you want to see if it can be repaired:

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

My install to a pre-partitioned drive with validated ISO to an SSD takes less than 10 minutes.

[COLOR=#000000]how to install boot-repair offline? i can't connect to any wifi bcs there's no wifi adapter, it said when i running [/COLOR][ubuntu]("https://ubuntuforums.org/#")[COLOR=#000000]live cd..[/COLOR]

---

### Post by yancek on 2019-03-07
Since you can't get online, can you boot the Ubuntu install DVD/USB and from a terminal run the commands below consecutively and post the output?

> sudo parted -l
sudo efibootmgr

---

### Post by oldfred on 2019-03-07
Does live installer boot and get you on-line?
If so you just install Boot-Repair into Ubuntu live installer per instructions in link.

---

