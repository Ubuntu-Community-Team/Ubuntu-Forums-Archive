---
title: "Upgrades Kill Ubuntu -- any advice?"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2008-02-05
Security Upgrade for 5 Feb 2008 and a reboot gave me a corrupt kernel. I have no GRUB menu because I am running only one OS. I onlly have one partition 188-gig, w/ 66-gig used.

Boot freezes at:
```
[33.588654] ..MP_BIOS bug; 8254 timer not connected to IO-APIC
[33.588654] kernel panic - not syncing: IO-APIC + timer does not work. Try using the 'noapic' kernel parameter
```

I'm pretty sure I have to Re-Install Ubuntu and turn off Auto-Upgrades if I want to keep using it.

QUESTION: can I get past the Boot freeze??? If not, how to rescue my old home partition. Most of my search on the Forums has backup info for a RUNNING copy of Ubuntu.

---

### Post by Partyboi2 on 2008-02-05
>  I have no GRUB menu because I am running only one OS. I onlly have one partition 188-gig, w/ 66-gig used.You should be able to get to grub menu by pressing ESC when you see something like "loading stage1_5" when you boot the system, then you should be able to try adding the noapic boot option by selecting the kernel to boot into and pressing "e" and selecting the kernel again and pressing "e" and adding noapic to the end and press enter then "b" to boot.
If adding noapic does not work try booting into recovery and see what happens.

---

### Post by Odrodzona-Sarmacja on 2008-02-05
First I want to say that we all here have been lately more or less screwed with this enforced autoupdate and iconnotifying and blinking irritating thing in Ubuntu 7.10. The most stupid improvement there was, really. Particularly sad thing, as Ubuntu ain't stable linux and we should not be presured by Ubuntu crew to install all their crapy unstable updates they are serving us from Ubuntu security's server. Even if that means less secure Ubuntu, hell is better then non-working and unbootable Ubuntu.

> **Unterseeboot_234 said:**
> QUESTION: can I get past the Boot freeze??? If not, how to rescue my old home partition. Most of my search on the Forums has backup info for a RUNNING copy of Ubuntu.

Sure you can. Use livecd to boot your computer with. Then copy contents of /home dir to some secure place (best would be pack it and then store the package) and when you are ready to go and installing Ubuntu anew make sure you have /home directory on other ext3 partition then the rest of ubuntu. It will save you lots of effort with constant reinstalations of ubuntu due to sudden update-crashes.

---

### Post by marmux on 2008-02-05
same here. ubuntu hangs on boot after updating the kernel with Update Manager.
but my system stops way before, at [3.something], not [33.something like yours.
After a while, it defaults to BusyBox, prompting "(initramfs)"...
Please help!

---

### Post by Unterseeboot_234 on 2008-02-05
Okay, when my Ubuntu had a Freeze, I found another thread on Error 33. I decided my error is different. I used LiveCD to boot. Then I System --> Administration --> Users and Groups... new user, username, password -->popup select priviledges Administrator.

Then, Menubar, far right shutdown button, Switch User [computer reboots]. username / password. (I'm still using LiveCD). I can see my large hard drive as an icon on the left side. I find my old username folder / inside is home, desktop and other things. Because I have networked to a PC XP box, I have full read / write priviledges to a 100-gig folder. I can access the network through Places --. Network. I have a graphical interface to drag folders and files into the XP box.

55 gig takes approximately 5.5 hours.

Looks like I'm going to lose all the WINE installation.

Looks like I will have to reinstall ia32, Flash, java all of that. The Codecs. The extra libs to build software. And those things take over 4 hours.

I will be reinstalling. I will have a question about the LiveCD desktop resolution of 1680x1050. I sure couldn't get that with ubuntu nVidia driver and the comquiz widgets. Moreover, the startup in the morning takes a least 10 minutes to stabilize to usuable buttons.

I have tried other Linux distros, but the wall every time is the nVidia driver. All these distros want a perfect custom driver before I get to use the distro. How can the LiveCD have the default graphics and the install not have default graphics?????

---

### Post by Odrodzona-Sarmacja on 2008-02-05
> **Unterseeboot_234 said:**
> Looks like I'm going to lose all the WINE installation.

No, you can be quite sure the wine installation won't be lost so long you copy contents of /home directory and reinstall it in new /home that is... Just you need to install wine program anew in ubuntu. Then it will automatically pick up all old settings and configurations from your /home directory. Nothing lost :)

>  Looks like I will have to reinstall ia32, Flash, java all of that. The Codecs. The extra libs to build software. And those things take over 4 hours.

The reinstallation will take a while, specially if you are on slow cable and specially if you use the slow medibuntu repository. However all settings and customizations will be saved in your old /home/user/.settings_program/ directories.

Next time have /home on different ext3 partition. It will save you approximatly 5.5 hours :D

Did you ever hear about distro called Suse? If Debian sounds too complicated to you, then maybe you should look into it. But you certainly should try first xubuntu :D

---

### Post by zvacet on 2008-02-05
Like **Partyboi2** say press **esc** button and you will see all kernels you have.Boot your old kernel and everything should be fine.No need to reinstall,just use old kernel.

---

### Post by Unterseeboot_234 on 2008-02-05
I would like to try to mod the GRUB. I do get the GRUB menu when I Esc-key when GRUB program scans. I have 3 choices and none looks like an old kernel

```
Ubuntu 7.10 kernel 2.6.22-14 generic
Ubuntu 7.10 kernel 2.6.22-14 generic (recovery mode)
memtest86+

```

The first choice gives me the original error "panic" no apic. The second choice gives me a command-line that loads until I get a root@root ~$.

If I go for the suggestion to "e" on the first choice, WHAT do I edit?

Thanks in advance, I do want to boot what I used to have. I will reformat this weekend when I have more time (too much junk).

---

### Post by Partyboi2 on 2008-02-05
> **Unterseeboot_234 said:**
> I would like to try to mod the GRUB. I do get the GRUB menu when I Esc-key when GRUB program scans. I have 3 choices and none looks like an old kernel

```
Ubuntu 7.10 kernel 2.6.22-14 generic
Ubuntu 7.10 kernel 2.6.22-14 generic (recovery mode)
memtest86+

```The first choice gives me the original error "panic" no apic. The second choice gives me a command-line that loads until I get a root@root ~$.

If I go for the suggestion to "e" on the first choice, WHAT do I edit?

Thanks in advance, I do want to boot what I used to have. I will reformat this weekend when I have more time (too much junk).
Highlight
> Ubuntu 7.10 kernel 2.6.22-14 genericpress e then highlight the entry looking something like this
> kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=*************** then press
e then at the end of the line add ```
noapic
``` so it will look something like:
> ********* ro quiet splash noapic then press enter then
b to boot.
If this works you will need to add it to the grub menu.list so that it boots with this option all the time. To do that open up grub menu.lst
```
gksudo gedit /boot/grub/menu.lst
``` look for  this:

> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro and add noapic at the end so it will look something like
```
kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro [COLOR=Red]noapic[/COLOR]
``` save and exit then in a terminal (Applications>Accessories>Terminal)
```
sudo update-grub
```

---

### Post by Unterseeboot_234 on 2008-02-06
I made a new partition, installed a fresh Gutsy. That installation wanted to update to the new kernel. I kept unchecking that option and allowed other updates. Then towards the end of my tweaking I had to go for the Restricted Drivers to get my nVidia driver. The Restricted Driver seems to be the problem. I got a dead computer after installing the graphic interface for the nVidia. I then went back to  PartyBoi suggestions. Here is my HowTo to anyone else.

1. If we only have one GRUB, we have to hit ESC to enter GRUB.
2. With multiple GRUB, we select with the up and down arrows for the GRUB to modify.
3. hit "e" to edit
4. use the up and down arrows to select the line that starts with "kernel/boot/..."
5. hit "e" to edit that line, add -- "noapic"
6. hit return
7. hit "b" (to boot)

I'm back to my original (and updated) Ubuntu install. I will save for another day the nVidia options panel. I still do not have any selectable options to change my Screen Resolution.

---

### Post by Partyboi2 on 2008-02-06
glad you are up and running again :)

---

### Post by Loneless on 2008-02-12
Hello. I'm new to Ubuntu. I downloaded the ISO file: "ubuntu-7.10-desktop-i386.iso"
Downloaded the InfraRecorder burning device, went into Actions--->Burn Image---> burned the ISO at 10x speed. Restarted my computer, pressed my F11 key to get boot options and booted from the CDRom. The Ubuntu main installation page came up, after this I clicked on the option to detect any errors, and I got this message: 

```
[33.588654] ..MP_BIOS bug; 8254 timer not connected to IO-APIC
[33.588654] kernel panic - not syncing: IO-APIC + timer does not work. Try using the 'noapic' kernel parameter
```

I went head and tried the first option (think it said Try/install Ubuntu) and same message came up. I am completely new to this so I'm not sure what to do. I did a search for 8254 timer and got this thread, so thought I would help. If anyone could lend me their assistance I would be most grateful. Be as simple as possible please because I am simple minded :lolflag: Thank you!

---

### Post by Partyboi2 on 2008-02-12
At the main menu of the live cd press F6 then at the end of the line add
```
noapic
``` then press enter.

---

