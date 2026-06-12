---
title: "Happy with the results !Asus Zenbook UX31-DH52 + Ubuntu 12.04 LTS"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Loan_Refi on 2012-04-27
Happy with the results !Asus Zenbook UX31-DH52 + Ubuntu 12.04 LTS 
Specifications
Operating System:*Windows 7 Home Premium (64-bit) Ubuntu 12.04 LTS x86_64
Display:*13.3-inch HD display (1600 x 900)
CPU:*2nd*Generation Intel Core i5-2557M Processor (Turbo Boost up to 2.3Ghz)
Graphics:*Intel UMA
Wireless:*802.11 b/g/n (@ 2.4GHz)
Bluetooth:*BT 4.0
Memory:*4GB DDR3
Storage:*128GB Solid State Drive
Camera:*0.3 megapixel
Speakers:*Stereo Speakers powered by Bang & Olufsen ICEPower®
Microphone:*Microphone
Card Reader:*SD Card
Input / Output:1 x Mic-in, / Headphone-out, 1 x mini VGA port for external monitor, 1x USB 2.0 ports, 1x USB 3.0, Micro HDMI
Battery:*6 cell
Dimensions:*12.8 x 8.78 x 0.12 ~ 0.71" (W x D x H)
Weight:*2.87lbs (with 6 cell battery)
Color:*Silver
User@Asus:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation QS67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
03:00.0 USB controller: Fresco Logic Device 1009 (rev 02)

I'm very pleased with the performance of my new Asus Zenbook running Ubuntu. The installation went smooth and since I just bought this Laptop from Sams Club I wanted to test Ubuntu 12.04 LTS right away so I went ahead and install Ubuntu + all my other applications I use.

These are the steps I took to accomplish all this;

1. Unpacked Asus Zenbook and made a backup of Wind0ze 7 Home OS
2. Installed Ubuntu 12.04 LTS from a USB created on my old Laptop running Ubuntu 11.10
3. Once installation was completed I restarted the computer and proceeded to install all my applications
4. Before installing all my apps I enabled the appropriate repositories then sudo apt-get update & upgrade 
5. Once the update & upgrade was complete I then installed my following apps;
6. sudo apt-get install preload openssh-server nmap nbtscan arp-scan konqueror krusader shutter qalculate compiz compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager gparted inkscape gtk-recordMyDesktop k3b kdenlive mplayer vlc heirloom-mailx sendmail samba smbfs x11vnc xtightvncviewer gnome-do docky wireshark rdesktop cups-pdf gnome-shell gnome-tweak-tool
7. The INSTALL UBUNTU TWEAK
sudo add-apt-repository ppa:tualatrix/ppa  
sudo apt-get update 
sudo apt-get install ubuntu-tweak
8. INSTALL WINE 
sudo add-apt-repository ppa:ubuntu-wine/ppa
udo apt-get update
sudo apt-get update && sudo apt-get install wine1.5
9. Virtualbox Downloaded and isntalled from website;
[http://download.virtualbox.org/virtualbox/4.1.14/virtualbox-4.1_4.1.14-77440~Ubuntu~precise_amd64.deb](http://download.virtualbox.org/virtualbox/4.1.14/virtualbox-4.1_4.1.14-77440~Ubuntu~precise_amd64.deb)
10. NX Free Edition for Linux
Download the DEBs
wget [http://64.34.161.181/download/3.5.0/Linux/nxclient_3.5.0-7_i386.deb](http://64.34.161.181/download/3.5.0/Linux/nxclient_3.5.0-7_i386.deb)
wget [http://64.34.161.181/download/3.5.0/Linux/nxnode_3.5.0-7_i386.deb](http://64.34.161.181/download/3.5.0/Linux/nxnode_3.5.0-7_i386.deb)
wget [http://64.34.161.181/download/3.5.0/Linux/FE/nxserver_3.5.0-9_i386.deb](http://64.34.161.181/download/3.5.0/Linux/FE/nxserver_3.5.0-9_i386.deb)
11. Change your working directory to the location where you saved the package and install it by running from a console:
sudo dpkg -i nxclient_3.5.0-7_i386.deb
sudo dpkg -i nxnode_3.5.0-7_i386.deb
sudo dpkg -i nxserver_3.5.0-9_i386.deb
12. For security purposes I change the default SSH Port 22 in;
sudo vi /etc/ssh/sshd_config
I reduced the “LoginGraceTime” to 20 from 120
I added my self and nx to be able to ssh into my Laptop “AllowUsers Myself nx”
13. I restared SSH
sudo service ssh restart
14. I also changed the SSH Port for NX No Machine in;
/usr/NX/etc/node.cfg
/usr/NX/etc/server.cfg
15. Restart NX
sudo /usr/NX/bin/nxserver --restart
16. I Enable Gnome-Shell Themes in by following this turorial;
[http://www.noobslab.com/2012/03/howto-enable-gnome-shell-themes-in.html](http://www.noobslab.com/2012/03/howto-enable-gnome-shell-themes-in.html)
17. I like to use McBuntu Icons along with Plastiq Gnme-shell theme;
wget [https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz) -O /tmp/Macbuntu-10.10.tar.gz
tar xzvf /tmp/Macbuntu-10.10.tar.gz -C /tmp
cd /tmp/Macbuntu-10.10/
./install.sh force
18. here is a picture of the theme results;



I have 90 days in case I want to return the laptop, but I think I'm keeping it!!
Cheers!!

---

### Post by Northbankboy68 on 2012-04-27
Also happy with the install on my eMachines Netbook.  Installed via the upgrade from 11.10.  It took a long time but absolutely no snags - rock on Ubuntu team!

---

### Post by piperbarb on 2012-04-27
You're not alone!! I ran the 12.04 upgrade on both of my Dell laptops:  a new XPS17 (L702X) that I bought in march and had installed 11.10 and an older Inspiron 1525 also running 11.10.  Both upgrade installs ran perfectly.  Some of the little quirks that I encountered in 11.10 are now gone - especially connecting to my Seagate Goflex Home file server.  

12.04 is faster and I have not run into any problems. All the programs I had installed prior to the upgrade are working perfectly.  I am glad I installed the upgrade.

It was nice to read among all those problem installs, that some people have had perfect upgrades.

---

### Post by deckoff on 2012-04-29
Hi. at the asus user - I think about buying this laptop, and I really would like to use ubuntu - some other people report issues with trackpad and wifi n. Did you have any of these 
Thank you :)

---

### Post by Loan_Refi on 2012-04-30
Hi, I'm not aware of any issues with trackpad or Wifi N. Are there any particular features of the trackpad you're interested in making sure work? Such as 2 finger scroll etc. Here is a link were you can get more info on this subject;

[https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook)

This is what is says about Elantech Touchpad;

"Works out of the box. Multi-touch works in Ubuntu 12.04 LTS (kernel 3.2). Changes made in 3.2 were that the whole pad is the left button, there is thus no right button*. Click and drag is done by clicking anywhere on the pad and moving the finger. Right mouse is available as two-finger tap. Middle button is available as three finger tap.

* A revision to the synaptics driver restores click-pad functionality. See here for the Ubuntu package and instructions.

With the 3.2 kernel, there is a very simple solution to the very low sensitivity problem. You can just use synclient to setup the sensitivity you want (and many other things).

Here is an example script from Aurélien Jacobs and Marcus Möller. You can save it e.g. as ~/bin/touchpad_settings and add it as Unity startup script using gnome-session-properties.


# higher sensitivity
synclient FingerLow=9 FingerHigh=12

# faster speed and acceleration
synclient MinSpeed=1.5 MaxSpeed=3.5 AccelFactor=0.1

# 2 fingers scroll (can be also enabled in System Settings)
synclient VertTwoFingerScroll=1 HorizTwoFingerScroll=1

# faster coasting
synclient CoastingSpeed=10

# enable tap to click (2 fingers for middle click, 3 fingers for right click)
synclient TapButton1=1 TapButton2=3 TapButton3=2

# continue dragging movement when reaching the edge of the touchpad
synclient EdgeMotionMinZ=30 EdgeMotionMaxZ=40 EdgeMotionMinSpeed=100 EdgeMotionMaxSpeed=400
#"

Wireless
"Many users report that this works out of the box. Seems to work flawlessly, several megabytes per second."

My connection gives me 15mbps Download and 2.0 Upload however I'm hardly ever connected to an Ethernet Cable so my wireless speeds vary depending on my equipment such as access point or router etc.

Also, I rely heavily on "Keyboard Shortcuts" so for right clicking to copy and past I use Ctrl+C for copy and Ctrl+V to past and Alt+Tab to switch to the page I need past the content into. Two finger touch not click works for me to right click also.

Let me know if you need more info but I definitely recommend this laptop for either Ubuntu or Linux. I'm going to be installing MAC OS X for testing purposes ONLY inside Ubuntu with the help of Virtualbox.

:guitar:

---

### Post by kjbox on 2012-04-30
I just installed 12.04 on my UX31. Installation went smoothly but I have a problem with bluetooth.

Bluetooh turns on and off perfectly but neither of my devices can be detected. They are a mouse (CLiPtec model RZS830) and headphones (Bluedio model Q9). The set-up wizard searches ok but nothing detected. Both items work with windows so they are not the problem.

The documentation on [https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook) says bluetooth works out of the box. I am new to Ubuntu, so not sure if I should be doing something else other than turn it on and open the Bluetooth New Device Setup.

Any help/suggestions greatly appreciated.

---

### Post by Loan_Refi on 2012-04-30
kjbox, I'm sorry you're having trouble pairing your devices.

I just tried pairing my phone with my laptop via Bluetooth and it woks well. The Ubuntu Bluetooth Manager searched and found my phone with no problem. 

Unfortunately I don't have the same devices you have to test but I'm going to look them up in case there is a synch button to press in order to synch up or somenthing. I'll keep you posted...

---

### Post by Loan_Refi on 2012-04-30
kjbox, I looks like your devices should work right out of the box. I looked up your mouse info online and it looks like all you have to do is plugin your mouse and it should be discovered. 

I can only suggest one more thing which is to make sure your Bluetooth settings allow for discovery in Ubuntu. I'm sure you probably have it set up that way but just ckecking; click on your Bluetooth icon and make sure "visible" has a check mark on it. If it doesn't than add it and start the Blue tooth wizard again and hopefully it will discover you devices.

With a Nokia Cell Phone I check to see if I can discover my Asus Zenbook with the Bluetooth and I was able to see it. Here is a snapshot so you can see it works;

---

