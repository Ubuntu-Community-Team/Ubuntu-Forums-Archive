---
title: "Trouble installing Dual Boot with new Ubuntu 18.04 server"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by petenoob on 2018-08-19
Not sure if it is me (probably) but I can't get the 18.04 server edition to recognize the space I left for Ubuntu Server OS when I am installing.

I have a 500GB hard drive. 

I have Windows 10 home. 

I want to dual boot. 

I turned off secure boot and fast start up.

I have Ubuntu Server 18.04 on a USB stick.

I boot the USB up, choose to install.

I get to this point and this is where it gets confusing, there is also one more option here for me "Use an Entire Hark Disk with LVM" which you don't see here : [https://tutorials.ubuntu.com/es6-bundled/src/codelabs/tutorial-install-ubuntu-server/img/191050aa2ace4675.png](https://tutorials.ubuntu.com/es6-bundled/src/codelabs/tutorial-install-ubuntu-server/img/191050aa2ace4675.png)

I select manual because I don't want to wipe my disk as I still want Windows, and I don't want LVM.

But when I get here then it gets weird: [https://tutorials.ubuntu.com/es6-bundled/src/codelabs/tutorial-install-ubuntu-server/img/426bf7def85590c3.png](https://tutorials.ubuntu.com/es6-bundled/src/codelabs/tutorial-install-ubuntu-server/img/426bf7def85590c3.png)

Because it seems that the installation does not recognize the "place" I want to install Ubuntu Server to, and all the Manual does is this just point me to WHOLE disk of 500gb to install UbunS18.04 ??

A few scenarios i have tried to get the install to look:

(a) 350gb with Windows 10 on. And 150gb unformatted free space. The install can't see the 150gb and want to install on the whole disk. 
(b) 350gb with Windows 10 on. And 150gb formatted in EX4. The install still can't see the 150gb and want to install on the whole disk. 

Plenty of guides for dual installing Windows and just Ubuntu 18.04 desktop but I haven't found any for Server yet. 

Truth be told, I am tempted to install the desktop version which is simple enough and then install the server separately and removing the GUI, but that could be opening another can of worms, for me anyway. 

EDIT: Or installing Ubuntu Server first, then reinstall Windows 10 home, as dual boot. Could be doable.

Pretty please help?

EDIT2: Looks like this guy has the same issue. It could be a bug? [https://askubuntu.com/questions/1032170/ubuntu-18-04-server-unable-to-see-windows-10-os-as-dual-boot](https://askubuntu.com/questions/1032170/ubuntu-18-04-server-unable-to-see-windows-10-os-as-dual-boot)

Maybe Ubuntu Server cannot be dual booted with Windows 10?

---

### Post by oldfred on 2018-08-19
Are you sure Windows fast start up is off?
Note that with Windows updates it turns it back on, so if you have rebooted Windows and it did updates, it may be back on again.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also is drive set for AHCI, not RAID nor some Intel SRT type setting? If not AHCI, be sure to add the AHCI driver to Windows first.

Post these:
sudo parted -l
sudo gdisk -l /dev/sda

---

