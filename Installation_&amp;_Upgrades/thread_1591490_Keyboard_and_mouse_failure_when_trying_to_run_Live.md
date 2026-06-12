---
title: "Keyboard and mouse failure when trying to run Live disk"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by fr.deniscarterssc on 2010-10-09
Keyboard and mouse failure when trying to run a live Ubuntu disk on an Acer Aspire M1641 desktop.
I was trying to show off the Ubuntu system to a colleague when to my surprise as it booted up both keyboard and mouse died. There was no response at all, the only option was to use the power button, rebooting into Vista all back to normal. I tried several other versions of Ubuntu going back 8.04 even Knoppix failed to get the keyboard and mouse working. Even after re installing the windows drivers and several more attempts even changing keyboard and mouse, I could not get any linux live disk to work.
Any suggestions to save face?

---

### Post by MichaelSammels on 2010-10-09
Are your keyboard and mouse PS/2 or USB? I remember when I used Ubuntu one time I was required to switch from PS/2 to USB until I had it installed (for the life of me, I don't know why).

If it was PS/2, then I'm afraid I don't know why your disc was being odd. :(

---

### Post by fr.deniscarterssc on 2010-10-09
Yes Michael I have tried both types of keyboard and mouse and still no joy. The Disks are not at fault they work fine on other machines. I am beginning to think there is something wrong with that particular Acer.:confused:

---

### Post by fr.deniscarterssc on 2010-10-10
I changed the bios boot option and disabled acpi the live disk worked  correctly and everything looked good. My Colleague was happy and asked  me to install ubuntu 10.04 as a dual boot with Vista. all seemed to go  well and easily.
Ubuntu worked nicely except for the wifi dongle. However, when trying to  close down it hung, needing to switch off using the power button.
on trying to boot into vista it would not! a message said ACPi required  to start windows. I changed back the bios and rebooted into vista and it  would not! this time a message said "cannot find file:Z\D2D\images\*. wsi when trying to determine UI language."
and recommended a recovery disk overwriting the C:\ dive.  not wanting  to do that and trying again chose the recovery mode choice on the boot  up menu Vista eventually loaded correctly. But Ubuntu will not as the  keyboard and mouse are once more inactive when using that OS.:(

---

### Post by MandeaSaracu on 2010-10-10
Yup, I had and still have this problem since the beta. Now I get the same error on the holy LIVE CD... here is the link to the forum topic I wrote at that time... Perhaps you can find some helpful info in there. But I have a desktop, not a laptop...
[http://ubuntuforums.org/showthread.php?t=1571059](http://ubuntuforums.org/showthread.php?t=1571059)

---

### Post by MichaelSammels on 2010-10-11
Have you tried previous versions of Ubuntu? It might be an idea to submit a bug report to Launchpad...

---

### Post by fr.deniscarterssc on 2010-10-19
Having been away for a few days the problem with the boot up is still there. I have tried all the recommendations so far without success.
Both windows vista and ubuntu boot up ok if one first changes the ACPI in bios = off for Ubuntu and on for Windows.
I cannot get grub to change I must be missing something in the script?
another quirk is that Ubuntu does not close down correctly now.
:(

---

