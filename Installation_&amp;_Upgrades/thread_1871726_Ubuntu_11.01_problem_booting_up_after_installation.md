---
title: "Ubuntu 11.01 problem booting up after installation"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by prazooo on 2011-10-29
Hi,

I have been using Ubuntu 10.10 and thought to migrate to the latest 11.10. 

So i installed the 11.10 image from Ubuntu download page and burned it to a cd and tried to installed it. First it didn't work. Both Ubuntu live and direct install froze upon select. So i pressed F6 and selected "acpi=off" option and then it worked. The installation finished successfully. (I have a dual boot system with windows 7. I selected the option to remove existing Ubuntu 10.10 version and reinstall)

When it asked me to restart the system to complete the installation i restarted. But from then when i select Ubuntu from grub main menu, i did not boot up. 

Then i selected the recovery mode and the system started up. I made some Google searches and some previous threads and tried all solutions given by the community. But i still cant get to start it the normal way. Only through recovery mode. 

If anyone have any suggestions/ideas/advice to overcome this issue, please reply.

Thanx

---

### Post by raja.genupula on 2011-10-29
Hi are you getting error while you're booting Ubuntu ? please provide us more information about your issue.

Thanks.

---

### Post by RcK17 on 2011-10-29
Hi,

I'm having this exact issue on an old Asus M2400N laptop ([specs]("http://gdgt.com/asus/m2400n/specs/"), mine has 768 MB of RAM). The setup wouldn't start at first, but pressing F6 and choosing "acpi=off" helped - the installation completed successfully.

Now, choosing Ubuntu in the grub menu only gives a blinking cursor in the top left corner for a few moments and then the laptop restarts. However, for me the same happens for the recovery mode - I get to see two lines of text ("Loading Linux 3.0.0-12-generic ..." and "Loading initial ramdisk ..."), then a screen with lots of text appears for a second and the laptop restarts.

Any help is welcome :) Thanks in advance!

---

### Post by drs305 on 2011-10-29
> **prazooo said:**
> Hi,

I have been using Ubuntu 10.10 and thought to migrate to the latest 11.10. 

So i installed the 11.10 image from Ubuntu download page and burned it to a cd and tried to installed it. First it didn't work. Both Ubuntu live and direct install froze upon select. So i pressed F6 and selected "acpi=off" option and then it worked. The installation finished successfully. (I have a dual boot system with windows 7. I selected the option to remove existing Ubuntu 10.10 version and reinstall)

When it asked me to restart the system to complete the installation i restarted. But from then when i select Ubuntu from grub main menu, i did not boot up. 

Then i selected the recovery mode and the system started up. I made some Google searches and some previous threads and tried all solutions given by the community. But i still cant get to start it the normal way. Only through recovery mode. 

If anyone have any suggestions/ideas/advice to overcome this issue, please reply.

Thanx

Have you tried adding the same kernel option to the Grub default menuentry as you did to boot the LiveCD?

You can see if that is the issue by editing the Grub entry during boot. When the menu displays, press 'e'. Cursor to the 'linux' line and add "acpi=off" at the end (no quotes). Press CTRL-x to boot and see if that works.

If it does, after booting, open /etc/default/grub as root (gksu gedit /etc/default/grub) and add the same to the GRUB_CMDLINE_LINUX_DEFAULT= line. Save the file, then run "sudo update-grub".

Here is a page that lists other *acpi* options that may be less restrictive than acpi=off (if that works):
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")


@ RcK17,

Welcome to the Ubuntu forums. 

If the above doesn't work for you, either monitor this thread to see if something else is recommended for the OP. If the OP finds a solution and it doesn't work for you, please open your own thread.

---

### Post by prazooo on 2011-11-20
> **drs305 said:**
> Have you tried adding the same kernel option to the Grub default menuentry as you did to boot the LiveCD?

You can see if that is the issue by editing the Grub entry during boot. When the menu displays, press 'e'. Cursor to the 'linux' line and add "acpi=off" at the end (no quotes). Press CTRL-x to boot and see if that works.

If it does, after booting, open /etc/default/grub as root (gksu gedit /etc/default/grub) and add the same to the GRUB_CMDLINE_LINUX_DEFAULT= line. Save the file, then run "sudo update-grub".

Here is a page that lists other *acpi* options that may be less restrictive than acpi=off (if that works):
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

.

HI,

Thanks for the reply. I tried adding the same "acpi=off" option while booting as you said (by pressing e) and it booted up. But then i added the entry to the grub file and tried to start in the normal way but the same problem persists. I checked if the value i edited is not saved, but it was saved and for some reason its not picking up while booting. 

Do you have any other solution for this.

Thanks in advance
PraZ

---

### Post by drs305 on 2011-11-20
> **prazooo said:**
> I checked if the value i edited is not saved, but it was saved and for some reason its not picking up while booting. 

Do you have any other solution for this.

How did you check to see if 'acpi=off' is still in the menu? Did you check at the Grub menu during boot by pressing 'e'? The reason I ask is that this is the only sure way you know the kernel option is in the menu. 

Sometimes there is more than one Grub menu on the computer, and the incorrect Grub menu gets updated.

If that is how you checked, confirm 'acpi=off' is in the menu and press CTRL-x to boot. If it boots, I'm not sure what the problem is. 

If it doesn't boot, then there is something other than 'acpi=off' required. If it boots to a black screen you might try 'nomodeset' as an option. Otherwise, I'd try determining the difference between how the recovery mode and the normal mode boots, but I'm not sure what it is.

If you are still having problems please describe in detail how the system doesn't boot - what you see (and what you don't) as it boots, especially what you see last.

---

### Post by darkod on 2011-11-20
I'm not sure if you are aware, but the value being present in the edited /etc/default/grub does not mean it's in the grub.cfg file and used at boot.

Did you run
sudo update-grub

after the editing? That way it will generate new grub.cfg file with the value included and will be used during boot.

---

