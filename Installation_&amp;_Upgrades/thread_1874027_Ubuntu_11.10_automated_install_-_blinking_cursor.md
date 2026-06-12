---
title: "Ubuntu 11.10 automated install - blinking cursor"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by kidintraffic on 2011-11-02
I am currently trying to setup a fully automated deployment method of Ubuntu 11.10 from a local web server. I am following the basic steps in this article [http://www.deployvista.com/Home/tabid/36/EntryID/65/language/en-US/Default.aspx](http://www.deployvista.com/Home/tabid/36/EntryID/65/language/en-US/Default.aspx) to get everything up and running. I currently have a WDS server for Windows deployments and have integrated a PXE boot menu to allow for Linux deployments. 

I have my web server up and running, which hosts the extracted alternate ISO cd. The deployment goes all of the way through, like I want, but when the system reboots, it goes to a black screen with a blinking cursor. At this point, I am out of ideas as to what to check for.

Here is my kickstart file:
```

  #System language
  lang en_US
  #Language modules to install
  langsupport en_US
  #System keyboard
  keyboard us
  #System mouse
  mouse
  #System timezone
  timezone America/New_York
  #Root password
  rootpw --disabled
  #Initial user
  user ubuntu --fullname "Ubuntu" --iscrypted --password $1$SCOXweI4$drrBtag3Am7IBIKztnx.00
  #Reboot after installation
  reboot
  #Use text mode install
  text
  #Install OS instead of upgrade
  install
  #Use Web installation
  url --url http://server/oneiric
  #System bootloader configuration
  bootloader --location=mbr
  #Clear the Master Boot Record
  zerombr yes
  #Partition clearing information
  clearpart --all --initlabel
  #Disk partitioning information
  part swap --recommended
  part / --fstype ext3 --size 1 --grow
  #System authorization infomation
  auth  --useshadow  --enablemd5
  #Network information
  #network --bootproto=dhcp --device=eth0
  network --device eth0 --bootproto dhcp
  services --enabled=network
  #Firewall configuration
  firewall --enabled --trust=eth0
  #X Window System configuration information
  xconfig --depth=32 --resolution=1024x768 --defaultdesktop=GNOME --startxonboot
  #Package install information
  %packages
  @ ubuntu-desktop
  
``` In order to get the install to finish, I have to remove the @ Ubuntu-desktop line. When that is removed, the system goes to the black screen with a blinking cursor after a reboot. With that line in the kickstart file, the install will fail with the error:
> “Installation step failed. An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and install software.” The system will deploy and boot to a gui login screen if I keep the kickstart file as shown above and by removing these lines:
```

  #Use Web installation
  url --url http://server/oneiric
```  My test deployment is going to a VM.  Installing directly from the ISO works without a hitch and like I said, removing my web server from the kickstart file results in a successful automated deployment.

Any ideas as to what I should be looking for or what I need to change?

---

