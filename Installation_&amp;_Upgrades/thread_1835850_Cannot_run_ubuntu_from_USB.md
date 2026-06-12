---
title: "Cannot run ubuntu from USB"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by SW6 on 2011-08-30
Hi i am new to ubuntu and os installing stuff. I have windows XP installed on my PC. I am trying to test drive ubuntu from my pen drive to have a look around(for now).
I downloaded ubuntu-11.04-alternate-i386.iso and made my 2GB usb stick bootable using unetbootin-win-549.exe and made a reboot. A window with menu appeared and it shows options such as
Run Ubuntu from this USB
Install
Help

If i select the first option ie, "Run Ubuntu from this USB" a beep sound is heard and nothing happens.
Also at the bottom of the screen there is a line 
"Automatic boot in 5 seconds"
but the once the countdown reaches 0, it restarts counting down from 5 after a beep.
then I tried 'help' option , there are a list of options and at the bottom it says press f2 through f10 for details, or enter to boot. If I press enter, it would show: "could not find kernal image:/casper/vmlinuz

I dont want to install it on my hard disk, and I just want to run it from USB, But I cant. Can anyone tell me what I should do?

---

### Post by Iantos on 2011-08-30
most probably your pc is not set to boot from the USB stick, switch the machine on, and choose whether its F9, or F2, or F10, whatever option the BIOS gives you, press it in order to go to setup, and change boot options, make the USB stick the firsts> press esc> save changes and exit, restart your pc and see if it boots.

---

### Post by mörgæs on 2011-08-30
Your computer does boot from USB, so there is no need for changing the BIOS settings. 

How much memory does it have?

---

### Post by SW6 on 2011-08-30
Thanks alot for replies. I have 2Gb of RAM

---

### Post by mörgæs on 2011-08-30
When booting the USB stick shows a self-test option. How does that work?

---

### Post by YesWeCan on 2011-08-30
> **SW6 said:**
> Hi i am new to ubuntu and os installing stuff. I have windows XP installed on my PC. I am trying to test drive ubuntu from my pen drive to have a look around(for now).
I downloaded **ubuntu-11.04-alternate-i386.iso** and made my 2GB usb stick bootable using unetbootin-win-549.exe and made a reboot. A window with menu appeared and it shows options such as
Run Ubuntu from this USB
Install
Help
Hi there. The "alternate" ISO does not allow you to run a Ubuntu desktop, it only allows you to install Ubuntu to a drive. So you probably want to write the "desktop" ISO to your USB stick. :)

---

### Post by SW6 on 2011-08-30
Ok, if you are sure that the downloaded ISO will not work, I will try the desktop one, thank you. But are u sure that the other one will work fine? I dont want to waste another download of 700 mbs.
Disappointed

---

### Post by Hakunka-Matata on 2011-08-30
Welcome to the forums
**Alternate installer details**

 The text-based alternate installer can be downloaded from a [location near you]("http://www.ubuntu.com/start-download").  This installation CD is suited for computers unable to run the  graphical desktop based installation, either because their computer does  not meet the minimum requirements for the live cd or because their  computer requires configuration after the installation is complete in  order to use the desktop.


YesWeCan gives good advice, no need to question him.

---

### Post by YesWeCan on 2011-08-30
> **SW6 said:**
> Ok, if you are sure that the downloaded ISO will not work, I will try the desktop one, thank you. But are u sure that the other one will work fine? I dont want to waste another download of 700 mbs.
Disappointed
I'm sure the alternative won't run a live desktop. Hey, I just looked up the Ubuntu home page and I understand your frustration - it isn't crystal clear.

What I think you want to do is burn the "live" ISO to your USB stick and then boot it. Only the "desktop" version does both the "live" session and the installer. The "alternative" is the same size but drops the "live" to make space for extra installation features such as drivers and RAID and stuff.

There may be other things you need to do differently too, but you at least need the desktop ISO.

Have a read of this: [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by YesWeCan on 2011-08-30
> **Hakunka-Matata said:**
> YesWeCan gives good advice, no need to question him.
Thanks muchly for the vote of confidence! I try. :D

I am happy to be questioned, tho. Helps to stop me making too many screw ups. ;)

---

### Post by SW6 on 2011-08-30
Thanks again for helping me out. Specially to YesWeCan. I will soon  download the other ISO file and try it.

---

### Post by SW6 on 2011-08-31
ok

---

