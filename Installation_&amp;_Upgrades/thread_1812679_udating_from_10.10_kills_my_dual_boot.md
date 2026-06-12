---
title: "udating from 10.10 kills my dual boot"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by phobin on 2011-07-26
Hi, 

I'm running lubuntu 10.10 and windows xp sp3 on my think pad. Every time update lubuntu I can't dual boot, it just boots straight into lubuntu.

How do I set it so I can dual boot again?? 

Thanks 

Phil

---

### Post by Quackers on 2011-07-26
If you run ```
sudo update-grub
``` in the terminal in lubuntu is the Windows Loader found as grub.cfg is run?

---

### Post by phobin on 2011-07-26
hi, 

i've tried "sudo update grub" and i get the message "The update command takes no arguments". I've also tried upgrade and grub is the latest version.

I still can't dual boot, it just goes straight to lubuntu.

is there a way i can get my laptop to dual boot again??

thanks

phil

---

### Post by Quackers on 2011-07-26
The command is sudo update-grub (with a hyphen in between). Try that again :-)

If no good please open synaptic package manager and in the search bos enter "os-prober" without quotes. The os-prober will then appear in the main window. Does it have a green box to its left? In other words is it installed? Sometimes lubuntu can forget to install this package. It is the package which finds other installed operating systems. If it is not installed please right-click on it and select "mark for installation" then click on the green tick mark in the toolbar to apply the change.
Once installed please try sudo update-grub again in the terminal.

---

### Post by phobin on 2011-07-26
hi quackers,

Thanks for replying.

I've installed os-probe and ran sudo update grub and I still get the message

"The update command takes no arguments"

After installing os-probe i restarted my think pad and the grub screen appeared but without the option to boot into windows xp sp3.

Is there anything else i can do to get it to dual boot.

Thanks

phil

---

### Post by Quackers on 2011-07-26
From the error message it appears that you didn't use the hyphen in between update and grub ```
sudo update-grub
``` can you confirm that?

The fact that the grub menu appears briefly is not a good sign.
If update-grub is not picking up Windows it may be that there is a problem with it.

---

### Post by phobin on 2011-07-26
HI Quackers,


I was running the command:

sudo apt-get update-grub

which wasn't working. I tried sudo update-grub and it worked.

Thank you very much for your help, i appreciate it.

Thanks 

Phil

---

### Post by Quackers on 2011-07-26
You're welcome.
If update-grub picked up the Windows Loader you should now get a grub menu at boot giving you the choice of which OS to boot.
If that is now working please mark the thread as solved using Thread Tools near the top of the page. Thanks.

---

