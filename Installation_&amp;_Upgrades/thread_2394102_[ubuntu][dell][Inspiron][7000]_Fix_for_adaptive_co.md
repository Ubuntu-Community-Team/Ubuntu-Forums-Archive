---
title: "[ubuntu][dell][Inspiron][7000] Fix for adaptive content brightness - auto brightness"
date: 2018-06-12
forum: Installation &amp; Upgrades
---

### Post by anandsahil on 2018-06-12
I bought dell inspiron 7570 and installed ubuntu 18 LTS, everything looks good but as soon as a started using it , i noticed a wired behavior  than when i move from a dark screen to a white screen , the colors are faded and the brightness increases slowly , this is ****** as it put so much strain on the eyes.
After struggling a lot a sequence of events fixed the issue.

1. Upgrading the Linux kernel you can do this by 

      > sudo apt-get update -y && sudo apt-get dist-upgrade -y && sudo apt-get upgrade -y && sudo apt-get autoremove -y

2. Upgrading nvidia drivers for the kernel . Sometimes the screen freezes while updating , just put your password and hit enter (4 times) it should work

       > sudo ubuntu-drivers autoinstall

3. Changing the grub file 

       > sudo vi /etc/default/grub
      
4. Find a line in the config 

          > GRUB_CMDLINE_LINUX_DEFAULT="quit splash"

5. Replace above line with 

        > GRUB_CMDLINE_LINUX_DEFAULT="quit splash acpi_backlight=vendor"

6. Run commad

     > sudo  update-grub

7. Restart your computer.


This should fix the auto content brightness issue. Also you should disable dimming option in settings.

---

