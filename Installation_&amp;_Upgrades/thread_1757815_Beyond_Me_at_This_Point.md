---
title: "Beyond Me at This Point"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by rebornjumpman on 2011-05-13
A friend of mine has seen me use Ubuntu and decided he was ready to take the leap from Windows 7 to Ubuntu.  He was attempting to install on a Toshiba NB205 netbook.  First he tried to partition his drive to run both OS's side by side, and when that failed he tried to overwrite the entire disc with Ubuntu and got a message about an unknown file system.

I attempted to help and completed an install of Maverick desktop (I seem to have misplaced my netbook iso).  I did everything the same as I did on my Acer, but now it drops to a shell saying something about problems with the root device.

To be honest, I have no idea of what this means, and if I have an idea it's probably wrong.  Any help would be awesome.  He's moving to Europe in a month and I would love to have Ubuntu up and running for him before he leaves.

---

### Post by Quackers on 2011-05-13
Does the message mention BusyBox and ends with a initramfs prompt?

---

### Post by rebornjumpman on 2011-05-13
Yeah

---

### Post by Quackers on 2011-05-13
Leave the initramfs prompt there for a few seconds then try typing 'exit' and pressing enter and see if it boots.

---

### Post by lmarmisa on 2011-05-13
Try to boot the netbook into Ubuntu Live CD, open Firefox and visit the page 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You have to run the script Boot Info Script and post the results here. Follow the instructions of the page.

---

### Post by rebornjumpman on 2011-05-13
Update:

I tried entering "exit" and nothing happened.  I haven't yet tried the live cd thing Imarmisa mentioned, but I tried adjusting the computers SATA settings in BIOS.  It gets farther now (to the Ubuntu loading screen), but it's taking forever.  I don't think the mechanical specs are that far off from my acer which flies with Ubuntu.  It's been sitting at the loading screen for about 10 minutes with no end in sight.  Any suggestions?

---

### Post by Quackers on 2011-05-13
After you typed "exit" (but without the quotes!) did you press enter?

I've seen several threads where Toshiba's need the acpi=off boot prompt to be able to boot. Maybe this is one like that.
It could even be a graphics problem.

What did you change the SATA settings to and from what?

---

### Post by rebornjumpman on 2011-05-13
Another Update:

It has progressed after 15 minutes at the loading screen to the login screen, but after five minutes of waiting there are no users to select.  I am infinitely perplexed.

---

### Post by rebornjumpman on 2011-05-13
I changed the SATA from "AHCI" to "Compatibility".  I did hit enter after typing exit without the quotes.

---

### Post by lmarmisa on 2011-05-13
This link could help you:

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)

---

### Post by rebornjumpman on 2011-05-13
Awesome, for whatever the reason after restarting the machine about six times, it's up an running smooth (though a little slow.  I'm about to run the upgrade to 11.04 for him.  Thank you both for your help.  I will reply to this thread if any other weird things happen.

---

### Post by Quackers on 2011-05-13
Hmm interesting. Thanks for the progress report.

---

