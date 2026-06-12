---
title: "Can't install ubuntu next to windows 8"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by MrGrutty on 2013-03-05
Hello guys.

I've been busy with this thing for quite a while now and still I can't get it to work. Here's the deal:

My computer is an ASUS A55DR. I bought it several months ago with Windows 7 preinstalled. I almost immediately installed Windows 8 on it (due to curiousity i guess) with the option to wipe everything on it and make a clean install.

I am trying to install the 64-bit version of Ubuntu 12.10  on my system next to Windows 8.
My laptop has a quad-core AMD A8-4500M processor and a HD RADEON 7640G + 6400M Dual Graphics video card.

When I boot up with the USB, I get a "GNU GRUB version 2.00-7ubuntu11" menu. It doesn't matter which of the options (try, install, OEM install, check disc) I choose. They all end in a black screen until I reset my computer.

I have already tried adding "nomodeset" to the options, but still nothing happens.
I have been searching for this "secure-boot" thing in my bios, but there really isn't anything related to it to find in there.

Please, can anyone help me further? If you need screenshots or whatever I will supply you. I just want to get this thing to work! (:

---

### Post by mastablasta on 2013-03-05
how did you create the USB? did you check andmake sure that image was good (MD5sum check)?
otherwise you could be using UEFI: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by MrGrutty on 2013-03-05
> **mastablasta said:**
> how did you create the USB? did you check andmake sure that image was good (MD5sum check)?
otherwise you could be using UEFI: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I created the USB using the Universal USB installer. Haven't checked it. How do I do that? Using the UEFI guide I get stuck at the third step. Can't find secureboot nor quickboot/fastboot in my BIOS' settings, so I guess I don't have that?

---

### Post by oldfred on 2013-03-05
If system was originally Windows 7 that was before secure boot. Only a few Windows 7 systems were installed with UEFI, most were the old BIOS even if BIOS was a combined UEFI/BIOS. 

How you boot install media is how it installs. But if Windows is in BIOS with MBR(msdos) partitioning you need to install Ubuntu in MBR mode. But if Windows is UEFI with gpt partitioning, you need to install Ubuntu in UEFI mode.

Post this:
       sudo parted /dev/sda unit s print

If it says gpt and first partition is efi then it is a UEFI install. If msdos and you just have 100MB (hidden in Windows) boot partition and main NTFS partition, then you have standard BIOS install.

---

### Post by MrGrutty on 2013-03-05
Hi. Thanks for answering. Where do I have to post that command? Have tried it in the GRUB command line, but it says it can't find command 'sudo'...

---

### Post by oldfred on 2013-03-05
From liveCD/DVD/Flash open a terminal and copy & paste into terminal. Then copy & paste back to a new reply.
 In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal
Unity just click on Ubuntu logo or first icon and type terminal in dash, then you get terminal icon to click on.

---

### Post by MrGrutty on 2013-03-05
Hi.

I think I can't acces the terminal you are referring to. I can only acces the GRUB command-line via the USB and the command prompt in windows. There is no ubuntu on my computer yet, so accesing the terminal that way is not possible atm.

---

### Post by JLeon85 on 2013-03-05
If you couldn't boot the USB then how did you set "nomodeset"?  You should be able to get to the Ubuntu terminal from that same menu.

---

### Post by MrGrutty on 2013-03-05
Sorry if I'm a bit unclear. I _can_ boot onto the USB and enter the GRUB menu. However when I acces the GRUB command-line and I enter the "sudo parted  /dev/sda unit s print" command, I get "error: can't find command 'sudo'. "

---

### Post by oldfred on 2013-03-05
No the terminal is not the grub command line. That only has limited grub only commands for booting.

So from live installer do you only get grub menu? Then you may need to add nomodeset.

At grub menu press e, then on the linux line replace quiet splash with nomodeset

---

### Post by MrGrutty on 2013-03-05
I already thought that. Adding nomodeset doesn't help. Have tried it again. I must say that the computer boots the USB in EFI and I don't even know for sure if Windows is installed in EFI or in BIOS. Maybe it helps if i boot the USB in BIOS too? Or just try the 32-bit?
This really sucks. It used to be so damned easy to install ubuntu on your computer and now microsoft ruins it.

---

### Post by oldfred on 2013-03-05
If you have the UEFI/BIOS, you should have settings in UEFI to turn UEFI on or off. Or it may be turn UEFI off and then another to turn BIOS/legacy/CSM/AHCI or maybe other names for BIOS boot.
How you boot live installer is how it installs, but you can boot live install either way to get to test system in live mode.

What computer is this?

---

### Post by MrGrutty on 2013-03-05
The only option regarding USB is the possibility to turn Legacy support off. No option to turn UEFI off.
Starting the live installer seems only possible via UEFI, but that doesn't seem to work in any way possible.

I have an ASUS A55DR. In my first post I have all the specs.

---

### Post by oldfred on 2013-03-05
If you turn legacy support on, you should see two boot options in the Ubuntu installer from the UEFI menu. One will be UEFI and the other BIOS.

---

### Post by tantocibo on 2013-07-06
Here is the solution: [http://goo.gl/JBEoB](http://goo.gl/JBEoB). You also have to set the 'Hitachi [...]' as primary boot option in BIOS (press ESC on boot to access to it) to load grub after installation. Cheers.

---

