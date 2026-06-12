---
title: "Upgraded to 12.10 from 12.04, on boot up get Title page then black"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by FMFCorpsman on 2013-06-13
I know there are tons of posts on this, and I have tried everything they have thrown at me. Most cases the circumstance isn't the same. I had loaded 12.04 fine and was using it. I did all necessary upgrades through the upgrade manager. Everything was operating normally. I decided to upgrade to 12.10 through the upgrade manager and things went smoothly. When the install was done, it had me restart which I did. The first time it restarted it came up to what I guess is the Grub Shell? It wanted my login and password and went to a terminal prompt. I don't know any command line so I could do nothing. So I rebooted, and never got it again. I get the Ubuntu title screen, then it just goes to that dark blue/black. I am on now only because I still have my live usb from 12.04 and used it to try Unbuntu. 

Attached is a picture of gparted. I have no idea what those media files are and if thats the problem or if its normal. The 60GB is /home and the 30GB is either /var or /temp.

I will continue to hop in and out of live usb to continue try things. Any help would be apprecited. Thank you

Jeff

---

### Post by FMFCorpsman on 2013-06-13
okay, so from the command line I have tried startx, sudo apt-get build-essential, sudo apt-get install ubuntu desktop. I have also tried ctrl-alt-f7. These are what I found in other recommendations, the others were mostly do to bugs caused by Nvidia cards which I don't have. Any other ideas would be helpful.

---

### Post by oldfred on 2013-06-13
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by FMFCorpsman on 2013-06-13
I had to reload boot-repair on another USB, but I got a report URL. 

[http://paste.ubuntu.com/5762846/](http://paste.ubuntu.com/5762846/)

I hope this helps me get some help now. It's as about as detailed as I can get at my level. Thank you

---

### Post by FMFCorpsman on 2013-06-13
> **oldfred said:**
> Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Sorry OldFred, never forgot your advice, just took me a while to find another USB and get boot-repair reloaded. I was just hoping there would be a quick command line fix before getting the boot-repair prepared.

---

### Post by FMFCorpsman on 2013-06-13
I ran boot-repair and selected recommended repair, it came up with a report summary: [http://paste.ubuntu.com/5762981](http://paste.ubuntu.com/5762981). Whatever it did it didn't work. It now boots into a menu that has Ubuntu, advanced options, a couple of recovery modes with linux 3.5xxx. I did see on one of the boot ups where it mentioned swapup failed, terminated 255. Don't know what that is, but I do know that I have no other ideas or alternatives. If there is anyone that can piece together the problem based on all the info I provided, I would be grateful. Thank you.

---

### Post by oldfred on 2013-06-13
If you get grub menu you have booted past where Boot-Repair can fix issues. It can add a nomodeset if needed.

Since you have grub in both protective MBR and efi partition which way are you booting? UEFI or BIOS mode.

What video card do you have.

With 12.10 I had to add kernel headers before I could get my nVidia drivers working. Not sure if that would apply for your or not.

At grub menu use e and remove quiet splash. Add nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by FMFCorpsman on 2013-06-13
It's a cheapy Dell Inspiron 15 3521 with an Intel HD graphics on the board. That's why I didn't bother with all the Nvidia posts. I don't think it's the issue. My [Laptop]("http://www.dell.com/us/p/inspiron-15-3521/pd?oc=dncwc59&model_id=inspiron-15-3521")

---

### Post by oldfred on 2013-06-13
I have nVidia, so do not know Intel well. 

I have saved these, which may be alternatives to nomodeset or other required boot parameters or both:
 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

   Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)
Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"

---

### Post by FMFCorpsman on 2013-06-13
[FONT=arial]Fred, as always thanks again for your research. I tried everything to no avail. Unfortunately there was nothing to do but reinstall. This time though, I wiped the drive. If I load 12.10 again, and the same thing happens, there is not a damn thing I can do to fix it at this point. Thanks again. Kind of funny how it's always the same few who help out lol![/FONT]

---

