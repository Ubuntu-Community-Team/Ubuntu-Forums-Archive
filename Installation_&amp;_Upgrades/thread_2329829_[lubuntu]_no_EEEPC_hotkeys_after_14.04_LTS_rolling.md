---
title: "[lubuntu] no EEEPC hotkeys after 14.04 LTS rolling update"
date: 2016-07-05
forum: Installation &amp; Upgrades
---

### Post by steve234 on 2016-07-05
Hi there,

Ubuntu automatically maps my Asus EEE1000h laptop's hotkeys (function keys).

Some of the hotkeys for wifi and display have stopped working on my Laptop. The hotkeys for sound and brightness still work.

I recently updated (rather than upgraded) my machine via software update. Could that be the cause? 

How do I go about testing this / reinstating the hotkeys.

---

### Post by ajgreeny on 2016-07-05
What do you mean by
> I recently updated (rather than upgraded) my machine via software update.
which does not make a great deal of sense to me; are you still running 14.04 or have you now upgraded the system to 16.04?

Let's see the output of ```
lsb_release -dc && echo "Desktop:	$DESKTOP_SESSION" && uname -mrn
``` in terminal which will show us what you're using and the DE you now have.

---

### Post by Rex Bouwense on 2016-07-05
I too am using Lubuntu 14.04 on an ASUS EeePC 1000h.  When you say that the wifi hot key doesn't work, do you mean that you cannot toggle the Fn+F2 keys to turn the wifi off and on?  That should not have been affected by Lubuntu updates.

Ninja-ed by the master.  Sorry.

---

### Post by steve234 on 2016-07-05
Thanks both:

@ajgreeny - I just did the rolling software update to 14.04 - I'm still on 14.04

@rex - you are right, it's the fn+f2 combination that doesn't work, yet fn+f5, fn+f6 (brightness) fn+f10 (mute), fn+f11 and fn+f12 (volume) all work.  

I noticed this today and the only thing I've done with this machine recently is the softare update.

---

### Post by Rex Bouwense on 2016-07-05
steve234,
ajgeeny was asking you to provide some information to be sure what distro and what desktop environment you were using to better assist you in determining a possible solution to your problem.  Ubuntu or any one of its flavors, of which Lubuntu is one, do not use a rolling release.  From the information that you have provided you have merely updated the programs that are already installed. I want you to check to see if your wifi is enabled in your BIOS.  
Restart your netboot.  
Press F2.  
Scroll to the right to the Advanced tab.  
Press the "Down" arrow until you reach the "Onboard Devices Configuration" option. Press the "Enter" key.  
Press the "Down" arrow to "Onboard WLAN" then press the "Enter" key.  
If the "Disabled" option is highlighted, press the "Up" arrow to highlight the "Enabled" option, then press the "Enter" key.  
Press the "F10" key. Press the "Enter" key to save your changes and exit the BIOS.

Once that has been done check your Fn+F2 toggle to see if you can activate the wifi.  It may take a few seconds.  Also check to see if you have wireless enabled.  Right click the wifi icon and ensure that enable wifi is checked.

---

### Post by steve234 on 2016-07-05
Actually fn+f2 is disabling/enebling wifi but only in software (netmgr). Last week it was actually turning off the hardware too (the blue "wifi" light would go out on the eeeepc). Maybe there was something in the update?

I'll try cycling the bios options and report back (can't do that now as the system is busy dding my busted SD card in a last ditch attempt to reuse it).

---

### Post by steve234 on 2016-07-05
Wifi is enabled in BIOS (obvs as I've been using it). 

Guess I'll never know why the fn+f2 combo now just works in software not in hardware. It's a shame because turning off wifi hardware when working on the train was good for security and battery life!

---

### Post by vasa1 on 2016-07-05
> **steve234 said:**
> ... Maybe there was something in the update?
...
Records of recent updates can be found in */var/log/apt* and in */var/log/dpkg.log**

---

### Post by steve234 on 2016-07-06
Finally got it - at some point in the last week bluetooth had got turned on (via blueman) - the EEE1000h doesn't have a separate Bluetooth LED so uses the wifi one. Found this nugget in another thread:

"The *blue LED* is turned on if either of WiFi or Bluetooth are on"

I turned off bluetooth, now the wifi light cycles with the fn+f2 keypresses as it should.

Thanks all for your help - solved

---

### Post by Rex Bouwense on 2016-07-06
Occasionally it is the simplest of solutions.  Not often but occasionally.

---

