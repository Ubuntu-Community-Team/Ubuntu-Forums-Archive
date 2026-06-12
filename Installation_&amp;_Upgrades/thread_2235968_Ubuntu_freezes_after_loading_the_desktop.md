---
title: "Ubuntu freezes after loading the desktop"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by puballday2 on 2014-07-23
Hi all.  I am completely new to ubuntu, and after windows ending support for XP needed an alternative for my dads old laptop, so decided to try Ubuntu.
Problem:  After installing, can boot to desktop, but then as soon as you move the mouse the entire system freezes and no key combination (tried ctrl/alt/F1) will do anything!
Please any help would be appreciated.
PS: also does not work from live disc.

System:
Acer Aspire 9300
AMD Turion 64 (2.2ghz)
Nvidia Geforce Go 6100
2 Gig Ram

Hope this helps, and thanks in advance.

UPDATE: I have tried a fresh installation and managed to boot into desktop and this time launch libre office but it crashed during loading :( oh and the screen went all funny...

---

### Post by puballday2 on 2014-07-24
Can anybody please help?

---

### Post by puballday2 on 2014-07-24
Guys if you can't/dont want to help me then thats fine, but if you could at least give me a clue as to what the issue may relate to (graphics/bios and so on) and/or point me to a guide that I can help myself with then it would be better than nothing; really do want to give this ubuntu a try but at moment its looking like a no-go :(

---

### Post by yancek on 2014-07-24
It might be a graphics card problem, common with nvidia as I know from personal experience.  You don't indicate which release of Ubuntu you are using, is it 14.04?  If it is click on the System Settings icon on the left panel, then in the new window click on Software and Updates and you should get a window with several tabs and on the far right is Additional Driver.  Click that and wait for it to finish.  There should be several options.  The one in use should have the radio button checked.  There should also be a recommended option.  You can click the radio button for that and click Apply changes.  Reboot to test it and make a note of the results.

---

### Post by puballday2 on 2014-07-24
> **yancek said:**
> It might be a graphics card problem, common with nvidia as I know from personal experience.  You don't indicate which release of Ubuntu you are using, is it 14.04?  If it is click on the System Settings icon on the left panel, then in the new window click on Software and Updates and you should get a window with several tabs and on the far right is Additional Driver.  Click that and wait for it to finish.  There should be several options.  The one in use should have the radio button checked.  There should also be a recommended option.  You can click the radio button for that and click Apply changes.  Reboot to test it and make a note of the results.
Hi, and thanks for the reply.  Yes sorry, it is 14.04.  The problem is, the freezing is that bad that I'm lucky if I even get the desktop to fully load (I set it to login without username/password) and even if it does load up, it 'may' let me move the mouse a little, but its literally a matter of seconds before the entire thing locks, it just won't let me do anything :(

Is there a way to stop it loading to the desktop, i.e. get it to command line, and then update the graphics from there?  If so, how?

Thanks again...

---

### Post by puballday2 on 2014-07-25
OK, just an update, I have it working!
What is was, ubuntu will never work on this laptop.  I decided to try Xubuntu, and it works, kinda.  It still freezes, but only after I tried to load a video on a news website.
It was stable enough though to do as you said, and download the propriety nvidia drivers (which was impossible uner standard ubuntu), and after a reboot everything is running perfect! 
Cheers!

---

### Post by RussellWing on 2015-01-24
Just added Ubuntu 14.04 to an Acer Aspire 9300.

Symptom 1: It seems to install fine but when you try and start the desktop session the display crashes (hangs with no cursor movement) almost immediately.
Symptom 2: No wifi is visible. 

Cause: Nouveau open source Nvidia drivers crash and no Broadcom firmware installed. The wireless controller uses a bcm 4311 [14e4:4311] and the standard drivers installed do not include Broadcom firmware.

Solution:
Switch off the laptop.
Connect via RJ45 network cable to your internet connection.
Power on the machine, and at the logon screen press CTRL-ALT-F1 (or F2) to bring up the command line

Log on with the account you created during the install process

Install the correct proprietary nvidia drivers
> sudo apt-get install nvidia-304
(details here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) specifically the section "Installation without X / from the console")

Install the Broadcom BCM4311 firmware
> sudo apt-get install firmware-b43-installer
(details here [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers))

restart the machine with > sudo reboot

All should now be working.

Please note the splash screen resolution is still sub-optimal.

---

