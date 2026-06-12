---
title: "Grub menu gone after installing 22.04; unable to repair"
date: 2022-04-25
forum: Installation &amp; Upgrades
---

### Post by vaughn3 on 2022-04-25
My Lenovo ThinkPad has 2 SSDs with 3 operating systems: Ubuntu, Mint 19, and Windows 10.
Recently I updated the Ubuntu partition from 14.04 to 22.04. After doing so, the Grub boot menu no longer appears on a restart. It goes directly to the the Ubuntu login.
I tried the update-grub command, which produces a grub.cfg file with all 3 OS's as menu items. Running grub-install afterwards, however, didn't fix the problem.
I ran Boot-Repair and I've uploaded results of the diagnostic to [https://paste.ubuntu.com/p/FQf7TS3VjJ/](https://paste.ubuntu.com/p/FQf7TS3VjJ/)
The most interesting part of the summary is:
 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
Since this makes no sense, I wonder if it's returning a valid status.
I've tried rebooting from the installation media and running the actual Repair, but the status popup ran for over 10 minutes and did nothing, so I canceled it. I know it says "may take several minutes" but without any kind of progress indicator it's difficult to believe that anything is happening. I've also thought of trying to re-run the Grub install from my Mint installation but I can't get there. I can boot into Windows by doing an F12 to get that special selection menu during the startup but selecting the Mint partition does nothing. It just continues on to Ubuntu.
Do you have any other suggestions? 
Thanks!

---

### Post by tea for one on 2022-04-25
As you can boot successfully into Ubuntu, I think that you should first edit grub:-
```
sudo nano /etc/default/grub
```
Suggestion below
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu 
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
```

You have [COLOR="#0000FF"]hidden[/COLOR] instead of [COLOR="#0000FF"]menu[/COLOR] - see line 254
The last line GRUB_DISABLE etc is missing.

After you have edited Grub, please run
```
sudo update-grub
```

Any improvement?

---

### Post by vaughn3 on 2022-04-25
Wow, I was thinking I missed something really obvious. :-) Unfortunately, it still skips the menu.
Would there be something in the logs? I've been scanning through them, but not sure what I'm looking for.

---

### Post by ajgreeny on 2022-04-25
Is ***Faststart*** disabled in your Windows 8 system?  

I have no idea how to do that not having used Windows since XP days, and I'm not even completely sure it's even available as an option in W8, but certainly in W10 you can not dual boot with Linux if W10 uses Faststart as that means it is hibernated, not shutdown and grub can not boot hibernated Windows.

---

### Post by scubascooby on 2022-04-25
I have a similar problem and posted another issue earlier.  I am not getting the sign in or desktop but also there is no grub menu.


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='Ubuntu'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"


It bleeps but no menu.

---

### Post by vaughn3 on 2022-04-26
Not knowing what else to try, I reverted the install to 20.04.
The same problem occurred; I couldn't restore grub with a standard update-grub and grub-install.
Boot-repair gave me an interesting error, though:
Please create an ESP partition (FAT32, 100MB-250MB, start of the disk, boot flag).
I used gparted to check: yes, I do have such a partition at /dev/sda1 with the boot, esp, and hidden flags set.
It's 260 rather than 250MB but I can't imagine that'd be a problem.
I've retried, but it always shows this same error.
Should I go to Advanced settings and Reinstall grub?
"Use the standard EFI File" and "Restore EFI Backups" are also checked by default. Is it safe to try this?

---

### Post by ubfan1 on 2022-04-26
I think you have grub mixed up between the two linux OSes.  Start at the EFI partition, mount it somewhere if it doesn't mount at /boot/efi, and look at the UUID used in the .../EFI/ubuntu/grub.cfg file.  It should be the UUID for the Ubuntu partition, 9f7fa7e8-3dc6-4086-b38e-904853fc46f1, not the one for the Mint OS,da7ea84b-cffc-48f3-8222-03a719324235.  Next look at the /etc/fstab file for sda1 and ensure the root / UUID is also ...46f1.  I would think a grub-install should have fixed any problems but...

---

### Post by ubfan1 on 2022-04-26
Since the editing seems broken, the above /etc/fstab for sdb1 instead of sda1.

---

