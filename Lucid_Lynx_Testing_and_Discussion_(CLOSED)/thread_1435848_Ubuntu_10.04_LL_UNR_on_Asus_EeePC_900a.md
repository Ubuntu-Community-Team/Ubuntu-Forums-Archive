---
title: "Ubuntu 10.04 LL UNR on Asus EeePC 900a"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sven6210 on 2010-03-22
[COLOR=black][FONT=Verdana]While under Ubuntu 9.10 KK I still had to tweak the microphone AND the WiFi-button Ubuntu improved once more. With 10.04 LL I only needed to tweak the WiFi-button, the microphone worked out of the box very well (incl. Skype).


[/FONT][/COLOR]**[COLOR=black][FONT=Verdana]WiFi/wireless key on the  keyboard[/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]I was able to switch the  wireless off but when switching it on I had to restart the computer  before I was able to reconnect to the wireless network.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]All I had to do was pass the  following parameters to the kernel command line:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]pciehp.pciehp_force=1  pciehp.pciehp_poll=1[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The detailed steps:[/FONT][/COLOR]
 You might consider a backup copy of the file [COLOR=black][FONT=Verdana]/etc/default/grub before you start with the changes.[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]1. sudo gedit /etc/default/grub[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]2. edit the line with  GRUB_CMDLINE_LINUX_DEFAULT and change it to:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]GRUB_CMDLINE_LINUX_DEFAULT=”pciehp.pciehp_force=1  pciehp.pciehp_poll=1 quiet splash”[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]3. sudo update-grub2[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]4. Restart the system[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Now you can toggle  WiFi/wireless on and off - you get reconnected to the wireless when you  switch it on again.[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]With this change my Asus  EeePC 900a works very well with Ubuntu 10.04 LL beta1.
[/FONT][/COLOR]

---

### Post by Gato Verde on 2010-04-06
My wireless has not worked on my EEE 1005hab since updating to 10.04.

Do you think this fix would work on my netbook too?

If yes, Could you clarify the steps for a user who is new to using the command line?

Thanks

Todd

---

### Post by Sven6210 on 2010-04-06
Dear Todd,

If your WiFi is not working at all this modification will not help you at all. The additional parameters only helps to automatically reactivate WiFi after it has been switch off with the hotkey.

Is WiFi activated in your BIOS? You should first check that.

Best regards

Sven

---

### Post by josephellengar on 2010-04-09
> **Gato Verde said:**
> My wireless has not worked on my EEE 1005hab since updating to 10.04.

Do you think this fix would work on my netbook too?

If yes, Could you clarify the steps for a user who is new to using the command line?

Thanks

Todd

Same problem.  eeepc 1005ha-p.  Just upgraded from 9.10 to 10.04 beta and now my wifi no longer works.  Has anybody had any luck?  Any help would be much appreciated.

---

