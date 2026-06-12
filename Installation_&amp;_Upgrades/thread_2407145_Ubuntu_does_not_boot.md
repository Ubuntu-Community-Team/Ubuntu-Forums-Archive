---
title: "Ubuntu does not boot"
date: 2018-11-30
forum: Installation &amp; Upgrades
---

### Post by sudomakemeasandwich2 on 2018-11-30
This is my first time using ubuntu and linux, so i am a complete beginner at this stuff. I have been getting a lot of errors while trying to install ubuntu on a new laptop, with a completely clean hard-drive aside from FreeDOS it came with. The laptop is an HP OMEN 15-ce0xx. It has an i5-7300HQ and a GTX 1050. It has UEFI. The secure boot option is disabled by default and grayed out. Trying to set a password, then trying to change secure boot after a reboot doesn't work; it's still grayed out. I have tried it with legacy support on and off. I have switched USBs, I have switched port but nothing worked. I have also googled extensively and nothing solved it. I'm probably missing a lot of other things I should tell in order to find the root cause of this issue, but as I said; I'm a complete beginner and i know nothing about this stuff :/ The problem starts when i try to install ubuntu. I have tried it by booting ubuntu on the USB and I have also tried it by installing it on the computer. The md5 checksum also checks out. The ubuntu logo with 5 white dots below it appears and it gets stuck at the last one. I have tried seeing whats going on by pressing escape but since I cannot copy it (at least I don't know how to do it) and I don't have access to internet on that computer, i cannot post it here. So i am going to write it byt hand. (There might be a lot of typos, sorry)
> 
[0.042141] ACPI Error: [_SP_.PCIO.RPO5.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[0.042153] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20170831/psobject-252)
[0.042158] ACPI Error: Method parse/execution failed \_SB.PCIO.RPO4.PXSX, AE_NOT_FOUND (20170831/psparse-550)
[0.042669] ACPI Error: [_SP_.PCIO.RPO5.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170831/dswload2-191)
[0.042677] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20170831/psobject-252)
[0.042681] ACPI Error: Method parse/execution failed \_SB.PCIO.RPO8.PXSX, AE_NOT_FOUND (20170831/psparse-550)
[7.427120] Couldn't get size: 0x800000000000000e
[7.427135] MODSIGN: Couldn't get UEFI db list
[7.429923] Couldn't get size: 0x800000000000000e
[7.942275] ACPI Error:  [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psobject-252)
[7.942287] ACPI Error: Method parse/execution failed \_SB.PCIO.SATO.PRT2._GTF, AE_NOT_FOUND (20170831/psparse-550)
stdin: Invalid argument
stdin: Invalid argument
[12.892268] usb 1-2: device descriptor read/64, error -110
stdin: Invalid argument
stdin: Invalid argument
[14.173895] sd 4:0:0:0: [sdb] No Caching mode page found
[14.173895] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[43.576782] NMI watchdog: Watchdog detected hard LOCKUP on cpu 1
[53.212036] xhci_hcd 0000:00:14.0: xHCI host controller not responding, assume dead
[53.212061] xhci_hcd 0000:00:14.0: HC died; cleaning up
[80.032001] watchdog: BUG: soft lockup - CPU#3 stuck for 22s! [kworker/3:1:46] (repeating)


---

### Post by TheFu on 2018-11-30
[https://askubuntu.com/questions/1057659/freeze-installing-ubuntu-18-04-on-omen-by-hp](https://askubuntu.com/questions/1057659/freeze-installing-ubuntu-18-04-on-omen-by-hp)
says to boot with acpi off.

---

### Post by sudomakemeasandwich2 on 2018-11-30
huh? I didn't see that when I was searching. Thank you! I'm going to try that and report the results
EDIT: It worked!

---

### Post by TheFu on 2018-11-30
> **sudomakemeasandwich2 said:**
> huh? I didn't see that when I was searching. Thank you! I'm going to try that and report the results
EDIT: It worked!

My google-fu is strong.  "HP OMEN 15-ce0xx ubuntu" was the search term I used.  It looked like you'd done the homework to me. Happy that it worked.  Other search tools don't seem to work as well, at least for me.  I don't login to google BTW.  And there are times when I can't find answers too - sometimes the brain just doesn't work in the right way. ;)  We all have days like that.

BTW, if solved, please use the "Thread tools" button near the top to mark it [solved].  That helps the askers and answerers in this community.

---

### Post by sudomakemeasandwich2 on 2018-11-30
Thanks! I didn't know such a button existed and was searching for it. However, that option makes the touchpad irresponsive and from what ive read, it isn't something that i would want. ([https://askubuntu.com/questions/858370/is-it-dangerous-to-turn-acpi-off](https://askubuntu.com/questions/858370/is-it-dangerous-to-turn-acpi-off)). The answer you linked also recommends updating the drivers. I've tried that and that doesn't do anything. nomodeset works with one problem, the resolution is bad. I need another solution :/

---

### Post by oldfred on 2018-11-30
If you have nVidia, you normally need to use nomodeset to boot in low resolution  or to terminal and install the nVidia driver from Ubuntu repository.
You may want to add ppa to get newer drivers, although repository should be new enough. But if you want to change drivers you must totally purge everything nVidia related first or else you get conflicts.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
       # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
With 18.04, the only way I can get to this now is with Software Updater & Settings.
ubuntu-drivers devices 
            [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
   
# to uninstall ppa, if not desired later
sudo add-apt-repository --remove ppa:graphics-drivers/ppa 

    
 # should show newest versions available from ppa in addition to defaults
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by sudomakemeasandwich2 on 2018-12-14
Sorry for the long wait. It was because first I couldn't get a persistent usb to work, then I waited for my win10 key to come, then I installed ubuntu and tried to troubleshoot it a little on my own. It seems that the drivers are not the issue, and it seems like its an OMEN related issue. The bug is this one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1786906](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1786906). I haven't found any solution to this yet nor could I find any solution to this on the internet. EDIT: also, win10 didnt appear on grub for some strange reason? Both windows and ubuntu were booting uefi and they were installed in the same disk. Also might be an OMEN issue.

---

