---
title: "system freezes after login"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by plefno on 2005-06-27
I'm new to Linux and just installed Ubuntu 5.04 running kernel version 2.6.10.  After installing correctly, the system boots up to the login screen.  I enter my username and password, but then the system freezes up as it tries to load GNOME.  I am able to login to the failsafe terminal but not failsafe GNOME.  Any clues to what might be going wrong?  Thanks for your help.

P.S.  There is one error during booting.  There is a temporary error in the name generation, whatever that might be.

---

### Post by FLeiXiuS on 2005-06-27
Just out of curiosity does the whole system freeze or just X?  And the name generator this wouldn't be a DNS name would it?

You can test whether the whole system is froze by pressing ctrl+alt+F1.  From here see if you can restart GDM.  Login with your username / password then type..

$ sudo killallgdm; sudo gdm

What happens there?  If it works we'll start from there.  If not, trying starting X manually.

$ sudo killall gdm; startx

Just a few idea's to get the troubleshooting started.  Also, what is the exact error message at bootup?

---

### Post by plefno on 2005-06-27
The exact fail statement during bootup is: "Temporary failure in name resolution."  I don't have any networking setup at this point because I'm on a wireless connection.  I tried booting and pressing ctrl+alt+F1 when it froze and it remained frozen.  If I boot into the failsafe terminal and manually type "startx", it starts opening and gets to a black and white screen and the cursor is an "X" and it again freezes.

---

### Post by FLeiXiuS on 2005-06-27
What do the logs say?  

$ sudo cat /var/log/Xorg* |grep EE

This should echo all error results in Xorg.  I'm just wondering if it's something with your Xorg configurations.  Perhaps so, do you have your video drivers installed?

What are your systems specs?

---

### Post by plefno on 2005-06-27
This is the exact output I get when checking the log as you suggested:
    (WW) warning, (EE) error, (NI) not implemented, (?? unkown.
(II) Loading extensionMIT-SCREEN-SAVER
    (WW) warning, (EE) error, (NI) not implemented, (?? unkown.
(II) Loading extensionMIT-SCREEN-SAVER


I haven't done anything other than run the Ubunto 5.04 Installation CD.  I'm running on a AMD Athlon 3000+ with a Geforce 6200 AGP video card.  My network adapters are a Linksys interna Ethernet Card(which is not currently connected to anything) and a WUSB-11 Linksys Wireless USB adaptor.

---

### Post by GTar on 2005-08-09
I have the exact same problem. Everything has been working sweet and the I reboot this afternoon and freeze! Anyone have any more suggestions??

---

