---
title: "Upgrade from Kubuntu 10.04 to 10.11: Keyboard and mouse lock at boot"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by johnerskine2010 on 2010-11-03
Running Landmarq Intel Atom DC330 Desktop

I have just attempted to upgrade my desktop machine from Kubuntu 10.04 to Kubuntu 10.10.

I used KpackageKit to do the upgrade which proceeded smoothly until the install packages phase, which seemed to complete and then repeat. I don't know the detail of what happened as I was out of the room.

The repeat almost completed, but then I got a set of error messages, which basically told me that KpackageKit was unable to install the upgraded packages. I closed KpackageKit, and closed the machine and tried a reboot. This time, I got as far as the splash screen, but although the cursor flashes, I can't type anything in the password box. In addition, the mouse pointer won't move. Using a different wireless mouse works, but I still can't type in a password. 

However, the command ctrl+alt+sysrq+RSEIUB works, so the machine is accepting some keyboard input.

I also know from using a live disc that my home directory is intact. 

Ideally, I would like to revert to my 10.04 installation, and re-try an upgrade to 10.11 afterwards. 

What should I do first?

---

### Post by silvervein on 2010-11-17
I too have this same message. When I boot keyboard works in GRUB but after I select Kubuntu and it boots, I can't do anything at the login screen.

---

### Post by dr_leviathan on 2010-11-17
This happened to me shortly after a fresh Kubuntu 10.10 install on a MacBook Pro laptop.  I was able to fix it. I think it was caused by the pommed package or config which I had just installed to fix the default behavior of the "function" keys.

I was able to use the installation CD to get access to the installation drive and disabled the pommed init script in runlevel2.

> sudo mv /media/disk/etc/rc2.d/S20pommed /media/disk/etc/rc2/K20pommed
I'm not 100% sure this was the fix because at the same time I also removed a file that I had added in /etc/modprobe.d that was also supposed to fix the function key problem.  I had been following two different set of instructions on the net.

---

### Post by dr_leviathan on 2010-11-17
I re-enabled pommed and had a working keyboard, however KDE would lockup on initialization after I had logged in.  Disabling pommed again (via the CTRL + ALT + F4 terminal) and then rebooting solved that problem.  Perhaps I'll have to live with the crappy FN modifier key behavior until Kubuntu 11.

I should mention... I was also struggling with some nvidia driver issues at the same time when I first encountered this problem.  I ended up removing the nvidia-173 package contents at the same time as the pommed stuff and completely reinstalling all the regular nvidia packages.  I eventually got the nvidia driver working -- I had to run the "sudo nvidia-xconfig" command in the end.

---

