---
title: "can't access gui part way through dist-upgrade"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by jbulcher on 2010-05-19
I am doing a dist-upgrade from 8.04LTS to 8.09. I use usb KVM switch, and I keep my eye on it so that I can respond to the usual configuration file prompts that pop up. For a while everything went fine, but suddenly I find that I can't use the keyboard to log in and check the progress (the mouse is completely unresponsive). Here's the kicker though: the computer is fine. I can use 'Ctrl-Alt F1' through F7, and the computer responds appropriately; it just doesn't do anything when the login screen is up.

I checked the /var/log/dist-upgrade/term.log, and if I understand it correctly, whether or not to keep /etc/mysql/my.conf is currently up for question. Is there any way to take back control of the computer without interrupting the upgrade? Not knowing very much about the install process, it seems like the GUI stopped polling for input.

Any help is appreciated. I tried googeling, but this problem seems pretty unique.

Thanks

---

### Post by jbulcher on 2010-05-20
Ooo, no one has any thoughts or workarounds? I'm not looking forward to today... There isn't any way to take over the GUI install process from the command line, is there?

---

### Post by jbulcher on 2010-05-20
Well, it looks like the matter was quite simple! Here's what I did:

[LIST]
[*]Rebooted the computer
[*]Logged in
[INDENT][*]While I could log into the gui, it complained about not being configured correctly and pretty much just gave me a blank screen.[/INDENT]
[*]Pressed [Ctrl-Alt-F1] to bring up a terminal session
[*]Entered sudo apt-get update
[INDENT][*]After complaining about pretty much everything, the output gave me the command to type in to fix the problem (I don't remember what it was). Running the command basically performed the rest of the upgrade from the command prompt![/INDENT]
[/LIST]

Thanks for a robust dist-upgrade process Canonical!

---

