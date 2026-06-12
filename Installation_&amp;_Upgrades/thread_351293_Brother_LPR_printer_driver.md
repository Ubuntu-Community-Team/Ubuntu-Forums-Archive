---
title: "Brother LPR printer driver"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by theiceage05 on 2007-02-01
Hello there " Ubuntu Forums "
:confused: 
Can anyone help me install my Brother MFC420cn printer networked/cabled to my SMC Barricade wireless router.
These are all the instruction from Brother to install the LPR driver.  My problem comes at the end.


Installing and using a Brother printer driver into a Linux based system using the LPD service (lpr)

A wide range of Brother printers are able to print on a Linux based system using the LPD service. To learn how to install a driver on a Linux based system which uses LPR commands, please refer to the following document.

Note:
* If you plan to install the CUPS Wrapper driver later, you DO NOT have to edit the "/etc/brprintcap" file. Also, if you receive the error: "lpd/lprng is required", please ignore it.
   1. Make a temporary directory on your HDD and download the LPR driver to that directory.
   2. Log in as root user or use the "su" command.
   3. When the driver has been downloaded run the relevant RPM file from the command prompt:
      rpm -ihv --nodeps xxxx.rpm* (for non-Debian Users)
      dpkg -i --force-all xxxx.deb* (for Debian Users)
      *where xxxx.rpm/xxxx.deb is the name of the RPM/DEB file.

This will install the Brother printer driver onto your computer and configure it to use the USB interface.
If you are using a USB interface, you do not need to make any further modifications and you can print from your Linux application.
If your computer is connected over a network you MUST edit the /etc/printcap file.

Ensure that the :rm and :rp lines read as follows:
:rm=xxx.xxx.xxx.xxx\   (Where I changed it to my printer IP address of 192.168.2.100)
:rp=lp\

THIS IS WHERE I HAVE A PROBLEM; the "ldp" file does not exist in this directory.  It does exist somewhere in other diretories.  I have try the command line with the other directory, but I keep getting the error message..."root@theclonedpc:/usr/lib/cups/backend# restart lpd"  "bash: restart: command not found"

THESE ARE THE INSTRUTIONS GIVEN BY BROTHERS
When you edit the /etc/printcap file you MUST restart the lpd service.
To do this enter:
/etc/init.d/lpd restart
at the command prompt.

HERE IS THE WEB PAGE
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html).

Your help is greatly appreciated](*,) 
TheIceAge05

---

### Post by dirtydan on 2007-02-02
THIS IS WHERE I HAVE A PROBLEM; the "ldp" file does not exist in this directory. It does exist somewhere in other diretories. I have try the command line with the other directory, but I keep getting the error message..."root@theclonedpc:/usr/lib/cups/backend# restart lpd" "bash: restart: command not found"

When you get the error "command not found" try it again with sudo in front of it, I don't think it matters what directory you're in.

I have this same printer and what I found was that once the drivers were installed it was easier to install it as a new network printer than to change it from the usb one that seems to be the default set up.

---

### Post by theiceage05 on 2007-02-02
Hello there; "dirtydan"

Thanks for the help; but it did not work.
Here is a "Cut & Paste" of the terminal session.......
theiceage05@theclonedpc:~$ sudo rm /usr/lib/libbrcompij2*
theiceage05@theclonedpc:~$ ls
Brother Printer LPR Driver            Desktop
Brother Printer LPR Driver~           mfc420cnlpr-1.0.2-1.i386.deb
cupswrappermfc420cn_1.0.0-1_i386.deb
theiceage05@theclonedpc:~$ sudo dpkg -i --force-all mfc420cnlpr-1.0.2-1.i386.deb
(Reading database ... 94111 files and directories currently installed.)
Preparing to replace mfc420cnlpr 1.0.2-1 (using mfc420cnlpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc420cnlpr ...
Setting up mfc420cnlpr (1.0.2-1) ...

theiceage05@theclonedpc:~$ sudo gedit /etc/printcap
theiceage05@theclonedpc:~$ sudo /etc/init.d/lpd restart
sudo: /etc/init.d/lpd: command not found
theiceage05@theclonedpc:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
theiceage05@theclonedpc:~$ restart
bash: restart: command not found
theiceage05@theclonedpc:~$ 

If you see something missing, let me know.

Thank you again.
TheIceAge05

---

### Post by dirtydan on 2007-02-17
Sorry that it's been awhile but I just got my printer working again today. I had it working with the 32 bit version of Hoary Hedgehog, since I have a 64 bit machine I decided to try the 64 bit version of Edgy Eft.

I followed the instructions from the Brother web page. I didn't edit the printcap file because I installed the cups wrapper. I had to install a file "ib32stdc++6" to get it to work with the 64 bit version.

---

