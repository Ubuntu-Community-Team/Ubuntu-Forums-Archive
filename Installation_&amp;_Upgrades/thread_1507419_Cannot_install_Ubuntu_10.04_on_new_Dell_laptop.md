---
title: "Cannot install Ubuntu 10.04 on new Dell laptop"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by hersco on 2010-06-11
I am trying to install Ubuntu 10.04 from a CD on a new Dell Latitude E6410.  I am using nomodeset and acpi=off (checking them from the <F6> menu and I add pnpbios=off and remove the quiet and splash options.

Everything seems to go well until I get the message "mmc0: Unknown controller version (2).  You may experience problems."  Then, after "Setting sensor limits," the screen goes blank, the CapsLock and ScrollLock lights flash for maybe 10-15 seconds, and the computer shuts itself down.

I have been able to install version 9.04 from an old CD, but then it doesn't seem to set up my network correctly.  All help appreciated.

---

### Post by davidmohammed on 2010-06-11
you may have the dell variant that has an intel chip not a nvidia chip.  Can you boot by editing you boot string to say

i915.modeset=0

or

i915.modeset=1

i.e. don't check the nomodeset - below this you'll see the boot string.  Add the above immediately before quiet splash--

e.g.

i915.modeset=0 quiet splash --

---

### Post by hersco on 2010-06-14
No luck.  It seemed that i915.modeset=off got just a smitch farther, but then the monitor went to this screen with colored squares at random points, and it still ended up with the caps lock and scroll lock lights flashing, and nothing else on the screen.  I also got an unstable clocksource message and "setting clocksource jiffies" (I still got rid of the quiet and splash options).

At this point, I am inclined to give up and to switch back to my previous laptop (it was an office machine, and they had offered me a new machine, but the old one was not that old, and it had a working version of 9.04 on it, with networking.  They keep the old machine for two weeks before reimaging it.

---

### Post by davidmohammed on 2010-06-14
i've got that clock message - I use noapic as well as i915.modeset=1

other suggestions - try nolapic, noacpi or acpi=off

---

### Post by hersco on 2010-06-15
So are these options mutually exclusive?  Can I try them all at once, or should I try every possible combination?  What is the difference between noacpi and acpi=off anyway?  And should I try them with each choice for i915.modeset, and also with nomodeset?  I'd rather not just throw spaghetti at the wall until something sticks if I can avoid it.

I think I just checked acpi=off when I successfully installed Ubuntu 9.04.  If I had a working network connection, I would probably just use that to upgrade to 9.10 and then to 10.04, but unfortunately I do not have a working connection yet.

---

### Post by davidmohammed on 2010-06-15
if you've definitely got intel graphics then its worth trying

i915.modeset=0 or i915.modeset=1.

If you've got other graphics then use nomodeset

nomodeset and i915.modeset are mutually exclusive

in combination, you could add noapic.

for example ... i915.modeset=1 noapic quiet splash --

Generally I try to avoid adding using acpi=off unless desperation creeps in - you generally get no fan control etc.  However sometimes its worth adding it and then investigating via the system kernel logs what are the acpi issues you have with your PC.

try booting using recovery mode and dropping to terminal when requested.

type lspci | grep VGA

That will tell you what type of graphics you have and therefore what is the most suitable boot option.

When you do get to a desktop then sorting out the wireless should be hopefully be through the hardware drivers screen. System kernel log, although cryptic, will give an indication why your wireless is not connecting.

---

### Post by hersco on 2010-06-16
What does "boot using recovery mode" mean?  And what do you mean by "dropping to terminal"?  I can choose "Try Ubuntu without installing" and maybe add "single" to the bootstring, but I still need to get the other parameters right, I think.  The installation CD does not have a "recovery mode" option.

I did boot to 9.04 to try the lspci command: it responded:

00:02.0 VGA compatible controller: Intel Corporation Device 0046 (rev 02)

I assume this means Intel graphics, but what does it tell me about which other options I should use (and whether I should use i915.modeset=0 or 1)?

Would it make more sense to simply use 9.04 and figure out why the networking (neither wired nor wireless) isn't working?

---

### Post by dargaud on 2010-06-16
Same problem here. The Graphic card is a Nvidia NVS 3100M (70.18.53.00.04, 512Mb 1440x900).

Edit: [Solved here]("http://ubuntuforums.org/showthread.php?t=1511166")

---

### Post by kidzer0 on 2010-07-12
The issue I'm having is it looks like it's going to install - shows the Ubuntu screen with the 4 dots underneath - they light up red a few times.

Then black & the caps lock & scroll lock keys just blink.:-k

---

