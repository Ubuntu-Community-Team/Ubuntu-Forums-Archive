---
title: "Installing Ubuntu 16 in &quot;legacy mode&quot; means no BIOS acces, No USB booting"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by Finn bjerke on 2016-08-20
I can boot in EUFI mode or Legacy on my new Aces machine. I installled Ubuntu 16 and wiped oput Win10 by using "legacy mode" in bios. Now I have no bios acces and can not boot from USB, Ubuntu  16 works well but upgrading is a problem. Any suggestions.  

Win10 makes UEFI install almost impossible so dual boot is very difficult. I am not patient enought to read a lot of technical stuff, so legacy install semmed the easy solution, If you want to overrule WIN10 bios controle in UEFI mode things get complicated. 

I need BIOS acces

---

### Post by yancek on 2016-08-20
Did you get a user manual with the computer?  Might be a good place to start.  You could also post more specific information on exactly which Acer you have since they make many different models of Desktop. Laptop and notebooks.

---

### Post by oldfred on 2016-08-21
BIOS mode with UEFI is still UEFI, just emulation of the 35 year old BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

So you may still have fast boot setting on in UEFI. That assumes you have made no changes to system, so UEFI does not spend any time re-checking system. But then you also do not have any time to press the correct key(s) to get into UEFI/BIOS to change settings. 
Most will give you time with a full cold boot, not the warm reboot.
With a laptop you have to also remove battery & hold power switch for 10 sec or so to totally drainl all power. Then on boot immediately press correct key to get into UEFI.
      
 [http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8/653006#653006](http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8/653006#653006)

---

### Post by Finn bjerke on 2016-08-22
Thank you for kind advice, I found this solution:

1. Swtich off PC, no rebooting.
2. Press F2 
3. AFter F2 hit power botton.
4. In boot process press F2 in a "morse fashion" press - let go - press -let go. 1 secund for each
5. Et VOILA: BIOS is on, NOw find the function where you have F12 access to boot sequens enable that function. 


Problem:
Installing  UBuntu in UEFI mode is blocked by Windows since Acer has preinstalled  Windows i such a way, Guarantee is not valid when you install Ubuntu. 

oldfred  have a good point maybe its a fast boot problem, this "fast booting" in UEFI mode assumes  windows is present I guess. Changing that is probably possible but  complicated ? Maybe I could have fast acces turned off and install  Ubuntu in EuFI mode that way, I belive i tried that with no succes.   This new PC has the battery hidden away There is no direct battery  acces. so I need a screw driver to get the battery out. Annoying. However the power button seems to kill all and reboot.

---

### Post by Finn bjerke on 2016-08-22
This a solved problem how do I indicate that ?

---

### Post by sudodus on 2016-08-22
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by oldfred on 2016-08-22
Many with Acer have installed in UEFI boot mode.

 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162) 

      
 Screen shots of Solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

