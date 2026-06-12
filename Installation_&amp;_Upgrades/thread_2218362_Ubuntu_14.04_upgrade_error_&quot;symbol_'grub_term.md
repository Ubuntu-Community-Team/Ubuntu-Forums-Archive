---
title: "Ubuntu 14.04 upgrade error: &quot;symbol 'grub_term_highlight_color' not found&quot;"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2014-04-20
I'm in the process of upgrading my mom's computer from Ubuntu 13.10 to 14.04.  Like many others, I ran into the "symbol 'grub_term_highlight_color' not found" problem, documented in this bug report:  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)

I managed to get the system booting by booting an Ubuntu GNOME 13.10 live DVD, I had laying around, and running the Boot-Repair utility:  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I installed the Boor-Repair utility in the Ubuntu GNOME 13.10 live session.  After the utility completed, I was able to successfully boot the system.  As a sanity check, I shut the system down and attempted to boot it again.  This second boot attempt failed and the system displayed a message it couldn't find a valid OS to boot and instructed me to insert proper boot media.  I'll post the exact message I get, if it happens again.

Anyway, so I booted Ubuntu GNOME 13.10 a second time, re-installed and re-ran the Boot-Repair utility, and was able to successfully boot the system a second time.  I haven't shut it down yet.   I did run these commands, as mentioned in the bug report I mentioned above:
```

tom@computer:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for tom: 
dpkg-query: package 'grub-pc' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: grub-pc is not installed
tom@computer:~$ sudo dpkg-reconfigure grub-efi
tom@computer:~$ sudo debconf-show grub-pc
  grub-pc/chainload_from_menu.lst: true
  grub2/kfreebsd_cmdline:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_disks_changed:
  grub-pc/hidden_timeout: true
  grub-pc/install_devices_failed: false
  grub-pc/kopt_extracted: false
  grub2/device_map_regenerated:
  grub-pc/partition_description:
  grub-pc/install_devices_empty: false
  grub-pc/disk_description:
  grub-pc/mixed_legacy_and_grub2: true
  grub2/linux_cmdline:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/install_devices:
  grub-pc/timeout: 10
  grub-pc/install_devices_failed_upgrade: true
tom@computer:~$ sudo debconf-show grub-efi
tom@computer:~$

```

My question:  if the Boot-Repair utility was able to fix the grub2 issue such that I could boot the system successfully, any ideas as to why a shutdown and restart would result in an unsuccessful boot?

Thanks!

Peace...

---

### Post by tomdkat on 2014-04-25
> **tomdkat said:**
> I installed the Boor-Repair utility in the Ubuntu GNOME 13.10 live session.  After the utility completed, I was able to successfully boot the system.  As a sanity check, I shut the system down and attempted to boot it again.  This second boot attempt failed and the system displayed a message it couldn't find a valid OS to boot and instructed me to insert proper boot media.  I'll post the exact message I get, if it happens again.
Well, it's been happening each time I reboot the system.  :(   The message I get after a reboot is:
```

Reboot and select proper boot device or insert boot media in selected device and press a key

```

So, here's the current "procedure" I follow to get a successful boot:
[list=1]
[*]Boot from my Ubuntu GNOME 13.10 live DVD
[*]Install Boot-repair
[*]Run Boot-repair
[*]After it has repaired the system, I reboot
[*]I *can* successfully boot Ubuntu 14.04
[*]If I need to shutdown or reboot, when I reboot I receive the above "reboot and select proper..." message and I go back to step #1
[/list]

Fortunately, Ubuntu 14.04 runs fine, once it's booted, and I only have problems if I need to reboot the system.  I've tried re-installing Ubuntu 14.04 from a live DVD without success.  I've installed Ubuntu 14.04 with Secure Boot and UEFI enabled and with secure boot and UEFI disabled with the same results as above.  Based on what I've been reading about this general issue, it seems Ubuntu 14.04 *should* install ok with Secure Boot and UEFI either enabled or both disabled but I can't seem to get it to boot without use of the Boot-repair utility.

I just don't understand why I can reboot successfully after immediately running the Boot-repair utility and then not be able to boot Ubuntu 14.04 a second time.  I'm open to nuking the hard drive (deleting all partitions) and starting over.   This system does not have Windows installed at all, even though I do have the Windows 8 installation media if I need to have Windows installed to get Ubuntu to install and boot reliably and consistently.

Any thoughts or advice?

Thanks!

Peace...

---

### Post by oldfred on 2014-04-25
You could try some of the suggestions in this bug report.

 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

---

### Post by tomdkat on 2014-04-26
> **oldfred said:**
> You could try some of the suggestions in this bug report.

 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.Thanks for the reply.  I  have tried many of the suggestions in that bug report and none of them helped.  I also figured out the "dpkg-reconfigure grub-pc" command might not apply to those booting with UEFI enabled on their system.

In any event, I managed to get my Ubuntu 14.04 upgrade issues resolved.  What I did was this:
[list=1]
[*]Boot from my 14.04 live DVD and run GParted
[*]Delete ALL partitions on the hard drive (the data was already backed up)
[*]Re-booted the system and went into the UEFI settings. I turned off made sure Secure Boot was disabled and that "LegacyCSM" was set to "always".
[*]Re-booted the system and booted from the Ubuntu 14.04 live DVD
[*]Installed Ubuntu 14.04 as normal
[*]After re-boot, I received the "Reboot and select proper boot device..." message I mention above
[*]I re-boot from the 14.04 live DVD again
[*]I install and run Boot-Repair in the "live" session (making sure to change the repository from trusty tahr to saucy (I forget) :))
[*]This time, Boot-Repair was able to fix the grub issue
[*]I was able to consistently boot Ubuntu 14.04 on the system
[/list]

Some things I noticed during the above.  
[list]
[*]Even though I disabled Secure Boot and made sure "LegacyCSM" was set to "Always", I noticed the system would flagged the hard drive or the optical drive with "UEFI".  I presume this means it would try to boot either device in UEFI mode.
[*]After a reboot or two, after disabling Secure Boot and making sure "LegachCSM" was set to "Always", I noticed the system wouldn't show the hard drive or the optical drive as valid boot devices.
[*]Once I was able to get the hard drive and optical drive recognized as bootable devices and WITHOUT a "UEFI" indicator, I was able to get the system booting reliably, as it was before the Ubuntu 14.04 upgrade.
[/list]

This has been a painful learning experience, but a learning experience, nonetheless.  I plan on building a new system for myself later this year, so I anticipate another learning experience in getting Ubuntu running on that system as well.  :)

Peace...

---

### Post by oldfred on 2014-04-26
If in always CSM you should have converted to BIOS only boot.

Ubuntu will boot from a gpt partitioned drive with UEFI if you have an efi partition or with BIOS if you have a bios_grub partition for grub to install correctly in BIOS boot mode. I often suggest both an efi & bios_grub so you can later change boot mode if desire. 

Windows only boots from gpt drives with UEFI.
Both Windows & Ubuntu will only boot from MBR(msdos) partitioned drives with BIOS.

---

### Post by yetanotherrandomname on 2014-04-26
Wait, what?  The solution is to loose everything and reinstall?!  That's not a solution, that's damage control.  Sure, things are backed up, but recovering from an utter system crash seems like a pretty weak reason this is "SOLVED."

I have this issue, too, and aded to the [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977) string.

I tried dpkg-reconfigure grub-pc and other pretty blind attempts to fix what I really don't understand, and have been expectedly unsuccessful.

---

### Post by oldfred on 2014-04-27
Most do not have to totally reinstall.

And it looks like tomdkat converted from a UEFI install to a BIOS/CSM type install. 
If Windows is pre-installed you could not reinstall Windows in BIOS mode as it is only configured and licensed for UEFI. 

 Product key now in UEFI
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

You do have to run the repairs from inside your install not the live installer. 
Or you have to chroot into your install which Boot-Repair can help you with or boot into your install with Supergrub.
Boot-Repair also can help run a full purge & reinstall of grub2 which may also work.

---

### Post by pa-card on 2014-04-29
[COLOR=#000000]Same here with Xubuntu and Windows 7. Other machines without W7 have had no such an issue. After reading a lot of stuff, I came to this very simple solution following these instructions to re-install grub from a live usb:[/COLOR]

[https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)

[COLOR=#000000]All the partitions are visible, including W7[/COLOR]

---

### Post by Mountaintree on 2014-06-08
I also encountered this grub error "symbol 'grub_term_highlight_color' not found" after upgrading Xubuntu from 13.10 to 14.04 on a dual partition Windows 8.1/Xubuntu. I've upgraded Xubuntu in the past with no issues, but when upgrading last night from 13.10 to 14.04, I found myself stuck at the grub rescue prompt. Given that I haven't encountered this issue before, I decided to try the Boot Repair utility as is detailed here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I needed to go with the "2nd option" noted on that help page, because I had no way to create a Boot Repair CD. 

**Here's what I did exactly:**

[LIST]
[*]On my laptop I went here: [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) where I downloaded the Live Xubuntu ISO. If you have a writeable disc drive, I'm sure you can create a LiveCD with this ISO file (presumably you could create a Boot Repair CD, too), but my laptop has no optical drive.
[*]So, I then created a bootable LiveUSB of Xubuntu 14.04. The instructions I followed to create the LiveUSB can be found here: [http://blog.tinned-software.net/create-bootable-usb-stick-from-iso-in-mac-os-x/](http://blog.tinned-software.net/create-bootable-usb-stick-from-iso-in-mac-os-x/) (keeping in mind my laptop's Mac OS required the "sudo" command to write to the formatted USB, as detailed in the comments of that post).
[*]With the finished LiveUSB of Xubuntu in hand, I rebooted the grub error computer, changing the boot menu to recognize the LiveUSB, which loaded the Xubuntu Live.
[*]I chose "Try Xubuntu" when the LiveUSB asked me to try or install. This loaded a Xubuntu session showing all my partitions as desktop icons.
[*]I opened a terminal and ran the following as detailed in the above-linked Boot Repair help page:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)
```
[*]I followed the instructions in the Boot Repair utility, which were fairly self-explanatory. Boot Repair recognized my partitions and ran its process, but finished with an "error" Ubuntu Pastebin address. I copied that down, but it seemed that the error was linked to extra drives on the machine that have no OS. Regardless of the error, Boot Repair still gave the option to reboot, so I did.
[/LIST]

I obviously made sure my boot menu pointed to the correct drive, and voila! Grub recognized all my partitions again as it was supposed to. I loaded up Xubuntu, and it looks like 14.04 runs just as it should now that the Boot Repair has done its work. Additionally, I can load Windows 8.1 just fine. 

Hopefully my notes are of some usefulness. I'm grateful for Boot Repair and for all the dedicated troubleshooters out there! :)

---

### Post by peter-totleben on 2014-10-28
The basic reason for this bug is that Ubuntu 14.04 and 14.10 ship with a buggy version of Grub (2.02beta2). In order to get things working, you need to downgrade your grub to the version that is in 13.10, and then re-install everything, possibly running boot-repair again.

For more information and complete instructions . . . 

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977/comments/250](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977/comments/250)

---

