---
title: "Ubuntu won't boot after installation (UEFI)"
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by apollondigital on 2016-10-09
Hi,

I've installed ubuntu desktop 16.04 alongside with windows 8.1 and after lots of search around I could come up with a solution.
My laptop keeps booting windows as if I never installed ubuntu. No grub appeared on boot.
I've tried boot-repair (while live-usb) but nothing changed. Here are the results of it:
[http://paste2.org/c97x7v5O](http://paste2.org/c97x7v5O)

I have an HP envy laptop and BIOS is setted to UEFI mode with secure boot on.
Any suggestions would be appreciated.

Thanks in advance.

---

### Post by oldfred on 2016-10-10
HP typically requires a work around.

But you also need to turn Windows fast start up or always on hibernation off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

With Secure boot on, you will not be able to dual boot from grub menu, but should have not issues booting from UEFI boot menu using one time boot key.

       
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

Boot-Repair should have copied shimx64.efi to bootx64.efi. But you may still need to manually add an UEFI boot entry.
HP Probook 4545s Secure boot off, manually copy files.

 [http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

           
 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition 
sudo efibootmgr -c -d /dev/sda -p 2 -l *EFI*ubuntu//shimx64.efi -L "ubuntu" 
    
Also Boot-Repair sees all the HP utility .efi files and creates a new 25_custom in grub to add all those entries to grub menu. You may not need many or any of them. Back up 25_custom and edit at will.
        
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 

Other work arounds including the one suggested by Boot-Repair to edit Windows BCD and rEFInd are in link in my signature.

---

