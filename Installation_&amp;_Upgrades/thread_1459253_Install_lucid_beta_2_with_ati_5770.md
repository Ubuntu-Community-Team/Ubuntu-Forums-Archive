---
title: "Install lucid beta 2 with ati 5770"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by s990we on 2010-04-21
How can I do this?
I can see the "boot menu" and the pink ubuntu splash but then the screen goes to sleep mode and then the "login sound" plays and Im left with a blank screen? (ctrl alt F1 dont do anything)

How can i install lucid or ati drivers when i cant see anything?

---

### Post by Mark Phelps on 2010-04-21
Lucid has problems with the ATI drivers right now.  Would hold off installing it until they get the ATI driver problem sorted out.

If you do an upgrade to 10.04 (which is what I'm guessing) and you have ATI restricted drivers installed, you'll most likely lose your display.  You would need to remove the ATI restricted drivers before doing the upgrade.

---

### Post by s990we on 2010-04-21
I got a new computer so it only have windows 7 now. But I cant even get into the ubuntu live thingy (live usb)

As soon as the live ubutu starts my screen goes blank



I was finnaly able to install lucid now :)

I installed lucid using alternate (text) installer. 
Then entering the installer again (after reboot) and selected rescue and set the root to the partition that lucid was installed on.
Then apt-get install openssh-server tightvncserver
Then rebooting and ssh from another computer and started a vncserver, connected to the vncserver (hostname:1)

Then I installed the proprietary drivers and rebooted.

Also, doesn't ubuntu have support for sata-6 hdd's?

I had to change to a sata-3 port when i installed. (and if I change back after installing it wont boot ubunut only windows 7)

---

### Post by valtra on 2010-05-06
Can you remove the restricted drivers after upgrading and get your display back? I must already have them installed as the system>administration>hardware drivers shows nothing

The "nomodeset" grub edit works to get my screen back but I have to do that every time I reboot.

---

