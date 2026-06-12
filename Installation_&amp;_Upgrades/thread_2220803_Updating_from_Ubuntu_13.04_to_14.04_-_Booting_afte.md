---
title: "Updating from Ubuntu 13.04 to 14.04 - Booting after first restart doesnt work"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by mueller-selfish on 2014-04-29
Hi everyone,

I just would like to say **thanks for providing an upgrade** that completly ****ed my OS.
I was really happy that there was a new LTS Version coming out. I closed all applications, started the upgrade process, restarted as wished by the update manager and to my surprise my machine cannot start anymore.
It hangs somewhere after grub when some daemon starts running and it switches from a terminal view into another view where then there is a blinking input sign on the left top of my corner.
I have run a 64bit ubuntu, my graphics card is an nvidea gtx 550 and I have no clue whats happening. =)

best regards
Lars

---

### Post by oldfred on 2014-04-29
A variety of work arounds in this bug report, and some work.
Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

You may be able to use Boot-Repair's advanced mode to totally uninstall grub and reinstall grub. Must have working Internet.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

And on upgrade the proprietary driver may cause issues. Often best to disable nVidia and then reinstall the newer nVidia drive with 14.04. You will need nomodeset on grub menu to boot to low quality graphics.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by doug12 on 2014-04-29
At boot press shift to get a GRUB menu, then press e and edit the boot parameters. Eg, I had this and could only get full graphics by editing out 'acpi=off noapic nolapic edd=on nodmraid nomodeset'. If this works then you need to make the changes permanent. GRUB stores command line parameters in /etc/default/grub. After editing this you need to run 'update-grub'.

My default GRUB command line parameters:

linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=75af250f-08d5-4f9b-a400-5d28020a6110 ro acpi=off noapic nolapic edd=on nodmraid nomodeset quiet splash $vt_handoff

---

