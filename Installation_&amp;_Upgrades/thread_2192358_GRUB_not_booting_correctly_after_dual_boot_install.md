---
title: "GRUB not booting correctly after dual boot install"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by bdeonovic on 2013-12-07
Cross posted at askubuntu (because this article told me to post here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) 


I followed these instructions to dual boot windows 8 and ubuntu:


[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported?rq=1](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported?rq=1)


I was successfully able to install ubuntu. But then I couldn't boot into windows 8 


      "File: \Boot\BCD Status: 0xc000000c Info: the boot configuration data for your pc is missing or contains errors."


So I ran boot-repair in ubuntu.


But then when I restarted computer I get:


    error: invalid arch independent ELF magic
    grub rescue >


At the end of boot-repair I had this message:


    Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file! 


I have no idea how to do that. I am able to boot into ubuntu by hitting the F12 on startup, otherwise it goes to the screen with the invalid arch error. 


Here is the summary of the boot-repair: [http://paste.ubuntu.com/6535680](http://paste.ubuntu.com/6535680)


EDIT: Still not able to boot into windows 8 from grub screen btw I get:


    error: unknown command 'drivemap'.
    error: invalid  EFI file path. 


EDIT: A few more details: when I installed ubuntu I had my BIOS set to legacy mode (not UEFI) as suggested by the article above. When I installed Ubuntu I chose the "Install Ubuntu alongside Windows 8" option.

---

### Post by Bucky Ball on 2013-12-07
Welcome. When in Ubuntu could you try running:

```
sudo grub-install /dev/sda
```

... then reboot. The EFI boot files are definitely there for Win but I don't know a lot about that. Could have everything to do with it. :-k

---

### Post by bdeonovic on 2013-12-07
What does this do? I should mention that I have a 24gb msata SSD that is /dev/sda and my boot drive is a 1000gb HDD on /dev sdb. So should I do [COLOR=#000000][FONT=Ubuntu Mono]sudo grub-install /dev/sdb[/FONT][/COLOR]

---

### Post by oldfred on 2013-12-07
Grub is in efi partition, it does look like you originally installed in BIOS mode and Booted Boot-Repair in BIOS mode. You need to always boot in UEFI mode.



What Windows boot entry are you using from grub menu?
It looks like Boot-Repair added a new entry but labeled it recovery for some reason.
> menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root BA8D-DA66
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

Boot-Repair also ran its "buggy" UEFI rename of bootmgfw.efi.
That is only need for those systems that only boot bootmgfw.efi, and will not boot ubuntu from UEFI menu.

---

### Post by bdeonovic on 2013-12-07
Thank you for your response. 

Thats an interesting find. I am able to successfully boot windows from the recovery option in grub. What do you recommend me to do?

---

### Post by bdeonovic on 2013-12-07
How can I properly label the GRUB entries and get rid of some of the grub entries that seem to be duplicate

---

### Post by oldfred on 2013-12-07
I have instructions on editing 25_custom in the link in my signature.
Basically
       # Edit descriptions used by Boot-Repair or remove entire boot stanza
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
#Then do:
sudo update-grub

You have dual video, have you had boot issues or installed bumblebee?

---

### Post by bdeonovic on 2013-12-07
So I edit the [COLOR=#000000]bkup25_custom [/COLOR] copy and update-grub will know to use it?

---

### Post by oldfred on 2013-12-07
No grub only runs executable files that start with two numbers and and underscore. So the bkup file will not run. You edit the 25_custom. And backup is just in case you want something back you can copy it from the backup.

The 25_custom file was totally created by Boot-Repair and it not part of a standard grub. But you can create as many new files with extra info that you want like Boot-Repair did. Since grub processes in order, the 25_custom entries will be before the 30_os-prober entries.

Grub has only fixed the UEFI bug in os-prober with the very newest grub in 13.10, so you can turn off os-prober to eliminate those entries also. Later you can turn it on, if you get the new version of grub, but then would not need 25_custom.

 # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub
Or one liner
 sudo echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub 
sudo update-grub

      
 grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

---

