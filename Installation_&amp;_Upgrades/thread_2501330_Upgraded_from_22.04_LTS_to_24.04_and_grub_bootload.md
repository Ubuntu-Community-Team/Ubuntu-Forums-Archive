---
title: "Upgraded from 22.04 LTS to 24.04 and grub bootloader disappeared"
date: 2024-10-02
forum: Installation &amp; Upgrades
---

### Post by operator-error on 2024-10-02
I upgraded from Kubuntu 22.04 LTS to Kubuntu 24.04 LTS and the grub screen no longer loads when I start my machine. I have Windows 10 on a separate drive that I boot occasionally (to play games) so this is more than a little annoying. To be clear, I ran the upgrade program and didn't do a fresh install. Any ideas on how to get my grub screen back???

---

### Post by oldfred on 2024-10-02
UEFI installs?
Then can you boot Windows directly from UEFI?

Did Windows updates turn on fast startup? That sets hibernation flag & causes issues.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If you run this does it see Windows?
sudo update-grub

---

### Post by operator-error on 2024-10-02
When I run sudo update-grub, I get the following:

[FONT=monospace][COLOR=#000000]Sourcing file `/etc/default/grub' [/COLOR]
Generating grub configuration file ... 
Found linux image: /boot/vmlinuz-6.8.0-45-generic 
Found initrd image: /boot/initrd.img-6.8.0-45-generic 
Found linux image: /boot/vmlinuz-5.15.0-122-generic 
Found initrd image: /boot/initrd.img-5.15.0-122-generic 
Found memtest86+x64 image: /boot/memtest86+x64.bin 
Warning: os-prober will be executed to detect other bootable partitions. 
Its output will be used to detect bootable binaries on them and create new boot entries. 
Found Windows 10 on /dev/sdb1 
Adding boot menu entry for UEFI Firmware Settings ... 
done

I still didn't get the grub menu when I restarted my system. Please note that I haven't booted Windows in months, so Windows couldn't have done something to affect my system. I can boot Windows through the BIOS, but it's a tad annoying. Fast Start is still disabled in my BIOS. In fact, nothing in my BIOS settings has changed. The only thing that changed was my grub screen disappearing after I ran the upgrade program and it restarting my system after it finished. [/FONT]:(


> **oldfred said:**
> UEFI installs?
Then can you boot Windows directly from UEFI?

Did Windows updates turn on fast startup? That sets hibernation flag & causes issues.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If you run this does it see Windows?
sudo update-grub

---

### Post by yancek on 2024-10-02
There might have been changes made in the /etc/default/grub file so that would be worth checking.  I'm still using 22.04 so don't know but look at the top of that file for entries like GRUB_TIMEOUT_STYLE=hidden.  If you have this line, the menu won't show. If you replace hidden with menu, it will.  If you have the line I posted here and comment it out (put a # symbol at the beginning of the line), the menu should show.  If you're not sure what to do, just post the file contents.  If you make any change and it fails, post back with exact information on what you did and exact results.

---

### Post by operator-error on 2024-10-02
You nailed it!!! GRUB_TIMEOUT_STYLE=hidden was the culprit. I made the change as you suggested, re-ran sudo update-grub, restarted and, viola, the grub menu returned. Thanks a bunch.

> **yancek said:**
> There might have been changes made in the /etc/default/grub file so that would be worth checking.  I'm still using 22.04 so don't know but look at the top of that file for entries like GRUB_TIMEOUT_STYLE=hidden.  If you have this line, the menu won't show. If you replace hidden with menu, it will.  If you have the line I posted here and comment it out (put a # symbol at the beginning of the line), the menu should show.  If you're not sure what to do, just post the file contents.  If you make any change and it fails, post back with exact information on what you did and exact results.

---

