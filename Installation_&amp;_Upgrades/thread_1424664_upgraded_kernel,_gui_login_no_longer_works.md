---
title: "upgraded kernel, gui login no longer works"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by djmokoia on 2010-03-08
Morning,

I recently installed Unbuntu 9.10 from a cd (downloaded iso) on to a desktop machine with a 2.4Ghz celeron processor and 2Gb of ram.

Everything was working as it should have been following the install. The kernel version installed was 2.6.31-14 generic

Yesterday the update manager was run and all 244 or so recommended updates were downloaded and installed. I restarted the machine after the installation was done and everything worked ok.

This morning I was woken up at 6:30 am by my father (the user of the machine) to be told he couldn't login. I tried to login at the gui login screen with his details and it failed. 
Specifically after entering the password the login prompt goes away but then the screen goes to the Ubuntu splash screen but this is mangled, then it drops back to the login screen again.
I changed to failsafe GNOME and logged in successfully.

I did a reboot to check the options presented by GRUB (I did not update GRUB during the update process) and it was presenting the correct kernel versions. 

I tried booting 2.6.31-14 but I had the same issues. I changed to failsafe GNOME and still had the same problems.

I can boot using 2.6.31-20 recovery mode, login and startx to get into GNOME.
When in recovery mode I ran update GRUB and also dpkg and nothing needed updating.

Personally, I could cope with using the system as it is but I need to leave it in a state where my dad can use it without problems. He does not live in the same country as I do, so I need to get this fixed asap. The internet speed here is limited so downloading can be a slow painful and problematic process.

I have searched the forums but couldn't find any other issues like this. I found issues related to graphics drivers and not being able to login but that does not appear to be the issue here.

If more information is required please let me know

---

### Post by congdang on 2010-03-08
I have same problem, but just fixed success.
1. Restart Ubuntu
2. When system load menu 1...2.., press Esc key
3. Replace 2.6.31-14 with 2.6.31-20 and Boot continus (press b)

Note: to edit line press e key

hope it can help you! If have any problems, plz contact me: !YH: ngoccong244

---

### Post by djmokoia on 2010-03-08
Hi,

thanks for your suggestion but it didn't help. I guess I probably didn't explain very well in my first post. It was early, I was very tired!

The GRUB screen gives me the following options (GRUB version 1.97~beta4):

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Professional (on /dev/sda1)

If I try to boot eithr the 1st or 3rd option I get as far as the login screen (GUI) put the login details in, it goes to the splash screen, then a black screen, then back to a messed up splash screen then back to the login screen. This happens if I select GNOME or failsafe GNOME. 

However, the first time I tried failsafe GNOME this morning for the 2.6.31-20 kernel I was able to login but not once since.

I can boot using the (recovery mode) options, login at the command line then use startx to launch the window manager so the installation appears to be ok, just something to do with the login via the gui.

if I chose edit for the first option I am presented with:

recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 763169e7-7988-4ef8-9524-b22b84e34\
7d1
linux /boot/vmlinuz-2.6.31.20-generic root=UUID=763169e7-7988-4ef8-9\
524-b22b84e347d1 ro  quiet splash
initrd /boot/initrd.img-2.6.31-20-generic

so it is looking at the correct kernel version

the only difference between that and the (recovery mode) option for the same kernel version is the 

quiet splash 

options are replaced by 

single

to boot into single usermode

so how can I figure out what is going wrong with the splash login process?

---

### Post by JayLFC on 2010-03-08
Do you have a nVidia or ATi graphics card? Maybe the new kernel does not have built in support. If so, restore your xorg.config to a previously working generic one and then update the nVidia/ATi drivers?

Just a suggestion, good luck!

---

### Post by djmokoia on 2010-03-08
if that were the case then why can I boot using the recovery mode and startx from there? surely I would get similar issues?

Also, I am experiencing the same issues with the older version of the kernel and the new version of the kernel so I'm not sure it is kernel specific but perhaps to do with another module or script that has been installed during the update process?

---

### Post by Sudofreak on 2010-03-09
I had the same problem, but got around it by uninstalling the
2.16.31-20 generic. Apparently my video card nVidia GeForce 7300 LE)
is not supported by the kernel.  Now I boot into 2.16.31-17 generic

---

### Post by djmokoia on 2010-03-10
thanks for your input. I know I keep asking the question but if it is the kernel version graphic card support then why can I manually startx after booting into recovery mode and why am I getting the same problem when trying to boot the older kernel version on the machine?

These two things don't make sense to me...

---

### Post by djmokoia on 2010-03-11
I just discovered that the sound card is no longer detected either! I think I am going to try reverting to an earlier kernel version as per your suggestion. If only it didn't take 3 hours to download everything on this crappy internet connection!

---

