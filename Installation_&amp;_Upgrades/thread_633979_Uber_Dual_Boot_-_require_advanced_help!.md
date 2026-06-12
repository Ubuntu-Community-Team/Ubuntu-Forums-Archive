---
title: "Uber Dual Boot - require advanced help!"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by oucii on 2007-12-07
This is a continuation from another post...

I am trying to install Linux distro (Ubuntu) on a remote 1U Rack Server, but ONLY have RDP (remote desktop) access to it, through Windows.

So no POST BIOS OS Menu Choice
No outside OS partitioning.
Need dual boot Linux/Win.
Local datacentre staff cannot help. 

So with the help of VMware Worstation for Windows, Norton PartitionMagic, and WINGRUB, I have achieved the following!! :) (took me a while...)
(On test machine, not actual server yet, presuming as if it's all done through remote desktop connection to Windows)


1) Made an ext3 and swap partitions in Windows (no restarts)
2) From Windows, using VMware installed Ubuntu Linux with LIVE CD 7.04 on the those actual partitions (not virtual disks, didn't install GRUB because there is no need)
4) Installed and configured WINGRUB, which will boot ANY Linux kernel found on the drive.
5) WINGRUB works NTLDR, which allows me to set the default OS to either Ubuntu or Windows by modifying boot.ini and then restarting. Which then allows to dual boot, without physical access to POST BIOS. *tested and it works* 

6) Started Ubuntu up in VMware, proceeded to configure IP settings + remote desktop server for VNC to be able to access it when it boots in real, if it boots..

Now I am faced with a challenge…


> The problem was that x server failed to start
“Module Loader present
Markers: (--) probed, (**) from config file, (= =) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(= =) Log file: “/var/log/Xorg.0.log”, Time: Thu Dec 06 22:08:50 2007 (= =) Using config file: “/etc/X11/xorg.conf”
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
No screens found”


Ubuntu works and REAL boots (not VMware, actual hard boot) but with x not finding any screens. Probably because it was configured by VMware virtual hardware during installation. I need Ubuntu with graphics, because there is a lot that needs to be done once it’s running. Doing all through command line will be pain and hours of time because I am a Linux n00bie. So by also having access to Ubuntu through VMware in Windows, I am able to configure any files, install any drivers manually. Question here now...is NOT about VMware.. or booting, but specifically how to make the graphics work in this situation. What should be done to reconfigure xorg.conf in order for it to work on actual real video hardware? Any suggestions there?  

Server is 1U Rack, single 250GB HDD, AMD 5600 X2. Onboard VIA Chrome9 HC IGP graphics card, Onboard VIA Rhine II Fast Ethernet adapter.

By using VMware it's possible to configure things in Ubuntu, prior to a real boot.
If I will be able to somehow reconfigure the graphics (making GNOME work), that could potentially mean I could remotely dual boot Windows or Ubuntu (modify boot.ini from either system, to choose which one boots by default) and have access to both with RDP/VNC.

---

### Post by leonidas666 on 2007-12-07
Did you try 
```
sudo dpkg-reconfigure xserver-xorg
```
Otherwise, i think you actually don't need a x-Server running on the server, maybe you can do it all through vnc or with ssh -X.

---

### Post by oucii on 2007-12-07
Yes, x server is not necessary, but it would be nice to have a GUI :).

---

### Post by leonidas666 on 2007-12-07
> **oucii said:**
> Yes, x server is not necessary, but it would be nice to have a GUI :).

Yes, of course. That's why you could either use ssh -X (like this you can start a program on your server, but the display will end up on your local machine), or vnc (this will open the whole desktop on your local machine, but the programs will run on your server). I believe for neither option you need a x-server running at your server (you'll need a x-server running at your local machine, though). What is better depends on what you want to do. 
Maybe there's another way through rdp, but as i said, i don't know about this.

---

### Post by oucii on 2007-12-07
Yes sorry I am just trying to test this now, never used ssh, so reading about it. Will report back with results.

---

### Post by oucii on 2007-12-07
Well, the problem is indeed the same. VMware naturally sets up its own ethernet controller with it's own MAC address. So when I do boot into Ubuntu normally, there would be no way to connect to it, because it finds the actual/real ethernet card, and the new controller has not got the IP, Gateway, DNS settings configured, and there is no DHCP on the server that I will put it on. 

Is there anyway to manually add an ethernet card in Ubuntu, which is has not yet been connected?

---

### Post by lha on 2007-12-07
> **oucii said:**
> Well, the problem is indeed the same. VMware naturally sets up its own ethernet controller with it's own MAC address. So when I do boot into Ubuntu normally, there would be no way to connect to it, because it finds the actual/real ethernet card, and the new controller has not got the IP, Gateway, DNS settings configured, and there is no DHCP on the server that I will put it on. 

Is there anyway to manually add an ethernet card in Ubuntu, which is has not yet been connected?

Well, you really are trying to get an Über (difficult?) dual boot... Good luck with your project. :)

See [http://lists.debian.org/debian-powerpc/2005/04/msg00054.html]("http://lists.debian.org/debian-powerpc/2005/04/msg00054.html"). That thread should be of help for you. The trick that is proposed there can be adopted to allow Ubuntu to use one network configuration for VMware's virtual ethernet card and another configuration for the real ethernet card.

---

