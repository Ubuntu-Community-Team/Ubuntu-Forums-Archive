---
title: "How to setup a net console preseed file?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by dmadon on 2011-10-20
Hi there,

I am trying to setup a preseed file to automatically boot and install Ubuntu server using the net console mode on a box without screen and keyboard. I have found an [outdated documentation]("https://help.ubuntu.com/community/Installation/NetworkConsole") that doesn't work with the 11.10 release. I have tried adding a few more variables to my custom preseed file (grabbed from a [FONT=Fixedsys]debconf-get-selections[/FONT]) but I always get  stuck with the "[!!] Select a Language" window.

Does anyone know what is the variable I need to set in my preseed file to pass this step?


Many thanks,
Dominik

---

### Post by Ranseyer on 2011-10-21
Hi, 

i have a problem like you. I dont wanna see any questions. (My Goal: Remastered Alternate-DVD)

I'm using this config and the installer asks only for "keyboard" and "keyboard" variant. So this preseed works for the language questions. 


> label install
  menu label ^xxx Installation
  kernel /install/vmlinuz
  append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/easyvdr.seed locale=de_DE console-setup/ask_detect=false console-setup/layoutcode=de localechooser/translation/warn-light=true localechooser/translation/warn-severe=true initrd=/install/initrd.gz quiet --
Im shure the are a lot of wrong entries:
> #d-i     keyboard-configuration/layout   select  Deutsch
#d-i     keyboard-configuration/variant  select  Deutsch
#d-i     keyboard-configuration/unsupported_options      boolean true
#d-i     keyboard-configuration/toggle   select  No toggling
#d-i     keyboard-configuration/layoutcode       string  de
#d-i     keyboard-configuration/ctrl_alt_bksp    boolean false
#d-i     keyboard-configuration/unsupported_config_layout        boolean true
#d-i     keyboard-configuration/compose  select  No compose key
#d-i     keyboard-configuration/switch   select  No temporary switch
#d-i     keyboard-configuration/modelcode        string  pc105
#d-i     keyboard-configuration/altgr    select  The default for the keyboard layout
#d-i     keyboard-configuration/unsupported_layout       boolean true


# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/modelcode string pc105
d-i keyboard-configuration/layoutcode string de
# To select a variant of the selected layout (if you leave this out, the
# basic form of the layout will be used):
#d-i keyboard-configuration/variantcode string dvorak

console-setup   console-setup/layoutcode        select  de
console-setup   console-setup/modelcode select  pc105
console-setup   console-setup/layout    select  Germany
console-setup   console-setup/variant   select  Germany


Do you have automated the keyboard questions ?

---

### Post by dmadon on 2011-10-21
Thanks Ranseyer! I have just passed the language question.

Now I have to solve the keyboard problem :(.

---

### Post by dmadon on 2011-10-22
Finally, I got my setup that goes straight to the ssh connection to finish the installation (I want to install a network box without keyboard nor screen). Here is the command I used:
> 
[...]
default netconsole
label netconsole
     menu label ^Install Ubuntu Server through SSH
     kernel /install/vmlinuz
     append noprompt initrd=/install/initrd.gz file=/cdrom/preseed/ubuntu-netconsole.seed netcfg/get_hostname=NEWMACHINE locale=fr_CH console-setup/ask_detect=false console-setup/layoutcode=us console-setup/modelcode=SKIP translation/warn-light=true localechooser/translation/warn-severe=true keyboard-configuration/modelcode=SKIP keyboard-configuration/layout="English (US)" keyboard-configuration/variant="English (US)" debian/priority=critical quit --
[...]


---

### Post by Ranseyer on 2011-10-22
> keyboard-configuration/modelcode=SKIP keyboard-configuration/layout="English (US)" keyboard-configuration/variant="English (US)"


Thanks. This worked for me.

---

