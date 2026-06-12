---
title: "Error: Microcode &quot;bcm43xx_microcode 5.fw&quot; not available og load failed."
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by Pesch on 2007-11-22
I get this error message while installing Ubuntu 7.10 on my Compaq Presario laptop.

I use a live-disk that i recived from ubuntu.com.

Can anyone help me please?

---

### Post by Pesch on 2007-12-06
anyone???? =(

---

### Post by tachyon4 on 2007-12-30
I've got the same problem.

I've tried to run Ubuntu 7.04 and 7.1 from CDs.  I've tried burned CDs and the CD that came from my friends computer.  None of them work.

I have an HP Pavillion Entertainment PC.

From what research I did, it seems like the file has to do with a wireless connection.  But I don't know how to solve the problem.

If anyone has had this problem in the past or knows how to solve the problem, I would appreciate a response and I'm sure Pesch would too.

Thank You.

---

### Post by koniu on 2008-02-19
Hello guys,

Had same problem with my PC, and it looks like its related to the Broadcom wireless card driver, which is not distributed with Ubuntu kernel. To fix it, go to System->Administration->Restricted Drivers Manager. You should find your wireless card driver marked as "Not in Use". Check it, follow instructions for online installation, done. 

Source, just in case : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

Hope it helps,
Koniu

---

### Post by Don1500 on 2008-02-27
I have the same error message and no wireless connection.

I am running a Dell D620 (Runs "out of the box" according to this site) 
I have no wireless connection and it will not set one up.
I have a Broadcom 4311 wireless card.
Output from iwconfig =>
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr|off   Fragment thr|off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Output from lspci |grep net =>
ubuntu@ubuntu:~$ lspci |grep net
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)

Anyone have a suggestion?

---

