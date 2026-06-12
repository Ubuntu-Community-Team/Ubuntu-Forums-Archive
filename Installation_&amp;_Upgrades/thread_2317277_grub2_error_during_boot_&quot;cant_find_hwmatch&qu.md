---
title: "grub2 error during boot &quot;cant find hwmatch&quot; after upgrading from grub1"
date: 2016-03-15
forum: Installation &amp; Upgrades
---

### Post by painterengr on 2016-03-15
I have been running Ubuntu 14.04 LTS for some time and have not changed the grub program not the config since the installation. Periodic updates are done and new kernels have been installed by "software updater". I have assumed (incorrectly) that these new kernels were moving the head of the line and getting booted. I can't remember if I have ever invoked the grub menu but I suspect never.

I have 100 mb /boot partition. Today during a new kernel update by "software updater" a popup arose indicating the partition was getting full. So I looked at the list of kernels and decided to delete some of the old ones. It was at this point I discovered I was actually running on a very old kernel and not any of the many newer ones installed. After some research I discovered I was running grub1. I then read [https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading) and followed it to now use grub2.

I was able to boot OK afterward and the most recent kernel was booting. So I decided to test getting the grub2 menu to come up and see the look and list of kernels, etc.

this worked fine only when I commented out GRUB_HIDDEN_TIMEOUT="0" in /etc/default/grub. When booting I could access the grub menu as expected.

However, when I ran update-grub it complained about having both GRUB_HIDDEN_TIMEOUT="0" and GRUB_TIMEOUT="10" EVEN THOUGH GRUB_HIDDEN_TIMEOUT was commented out!

So I again researched the Ubuntu grub info and it recommended to edit the /etc/default/grub file and comment out both HIDDEN assignments and add the STYLE item as follows:
#GRUB_HIDDEN_TIMEOUT="0"
#GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT_STYLE="countdown"
GRUB_TIMEOUT="2"

update-grub now did not complain. Now when I reboot during the time one would see the grub boot screen all I get is a quick error to the effect of "cant find hwmatch" and the default kernel is silently loaded. No grub menu ever appears.

I see the /boot/grub/grub.cfg script has several points where it is invoking this "hwmatch" command. But clearly it is not finding it.

I can see a binary file /boot/grub/i386-pc:
-rw-r--r-- 1 root root 47288 Mar 14 23:27 hwmatch.mod

uname -r reports
3.19.0-56-generic

The cpu is Intel® Core™ i5-3320M CPU @ 2.60GHz × 4 
and the kernel is 64 bit.

So, how do I get grub to work? Why is it not loading this hwmatch.mod command?

thanks
oldunixguy

---

### Post by kc1di on 2016-03-15
Hi The error during update-grub can be ingnored go back and uncomment the Grub_hidden_timeout="0" line.  boot menu should reappear. 
of course you'll have to do ```
sudo update-grub
``` again. 

If your running Nvidia graphics card with Nvidia driver you'll have to do what [this page]("http://askubuntu.com/questions/362722/how-to-fix-plymouth-splash-screen-in-all-ubuntu-releases") says in order to get the plymouth splash screen back.

I just remove the "quiet splash"  in the ```
GRUB_CMDLINE_LINUX="quiet splash"
``` line
so it looks like this ```
GRUB_CMDLINE_LINUX=""
``` and it will boot with the boot output not as pretty but much more informative if something goes wrong.
good luck  ;)

---

### Post by painterengr on 2016-03-16
> **kc1di said:**
> Hi The error during update-grub can be ingnored go back and uncomment the Grub_hidden_timeout="0" line.  boot menu should reappear. 
of course you'll have to do ```
sudo update-grub
``` again. 

If your running Nvidia graphics card with Nvidia driver you'll have to do what [this page]("http://askubuntu.com/questions/362722/how-to-fix-plymouth-splash-screen-in-all-ubuntu-releases") says in order to get the plymouth splash screen back.

I just remove the "quiet splash"  in the ```
GRUB_CMDLINE_LINUX="quiet splash"
``` line
so it looks like this ```
GRUB_CMDLINE_LINUX=""
``` and it will boot with the boot output not as pretty but much more informative if something goes wrong.
good luck  ;)

I removed the comment or the line in /etc/default/grub and ran update-grub.

This did NOT change the results. I STILL get the error coming from the grub script upon boot that reports "couldnt find command hwmatch" and grub never paints the grub menu but instead starts the default kernel.

this is NOT about the grub config but rather that grub is not loading the internal module hwmatch.mod and thus that command fails during the execution of the grub.cfg script. This is an indication there is something wrong with the internals of grub and not the default settings.

This is serious and it is not responding to any "editing" of the grub input files.

thanks
oldunixguy

---

