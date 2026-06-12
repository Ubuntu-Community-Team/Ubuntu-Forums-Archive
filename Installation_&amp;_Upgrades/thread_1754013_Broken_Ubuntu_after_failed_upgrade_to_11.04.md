---
title: "Broken Ubuntu after failed upgrade to 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by Hinder on 2011-05-09
Hi,

this afternoon I tried to upgrade my Ubuntu 10.10 to 11.04 on my netbook. I choose the option to upgrade on the Update Manager. All packages had been downloaded, and the installer was busy to replace all the old packages.

During the update I noticed that my internet stopped working, so I disabled my wifi, so it couldn't interupt the upgrade. After a half an hour, I found out my internet worked again, so I pressed the wifi-button again on my laptop, so the wifi would turn on, but after that move my screen hanged, and the upgrade wasn't done yet. I pressed the powerbutton for 5 seconds, because there was nothing else I could do.. Everything just hanged, no mouse movement, no hard disk activities, just a frozen screen.

After this problem I rebooted, and I already knew what I was going to see, Ubuntu couldn't be loaded anymore (and it still can't).

Is there anybody who can help me to restore my laptop? There are really important things for college on the harddisk in the /home/ folder, but I was too stupid to forget to make a backup.. I mostly make backups of everything you can think of, but I thought it won't be neccessary.. damn..

I know that you can restore files using a live-usb (no cd, because it's a netbook), but I choose during the installation the option to 'encrypt' my documents.. So is it still possible to restore my documents, photo's etc. from the home-folder? I really need to get those things back..

PS. when I try to boot all I get on my screen is the text (in Dutch): 'Disk partition / is not ready or is not found - Keep waiting or press S to cancel mounting, or press M to recover manually' The manual recovery doesn't do anything at all, and by the way, booting in the 'recovery mode' won't work either.

Thanks so much in advance for any help!

---

### Post by Hinder on 2011-05-09
I have now a working live-usb, after the Universal USB-installer failed many times.. Unetbootin did it, but now it's asking for a username and a password in the live-mode on the login screen.. Where do I find those things? :confused: What the hell is going on..

---

### Post by Expander on 2011-05-09
My upgrade did also fail. If you have an external drive as USB harddisk or USB flash you can copy the important contents from your home directory. Do you get any screen saying something like this:

"Disk drive for /hdba/sda6 is not ready yet or not present"
"Continue to wait, or press S to skip mounting or M for manual recovery" 			 		

?

If so, just press M and you will get to the terminal. From terminal you mount your external drive and copy the contents over there.

---

### Post by Expander on 2011-05-09
Ok,i saw that you get that message. When you press M, you should get to the terminal, do you?

---

### Post by Hinder on 2011-05-10
Hi Expander, thanks for your reply.

I already fixed the problem, because I was able to recover my home-folder using a live-usb of Ubuntu Netbook-edition 10.10. I struggled with booting it, because it just won't work using the Universal USB Installer. Luckily, Unetbootin did the trick after several times.

After the live-usb was running, I tried to recover my files to another usb-drive, but some important folders were protected. But when I opened Nautilus using the terminal-command 'sudo nautilus', I was able to backup all important stuff.

After some struggling with the partitions, I reinstalled Ubuntu 10.10 netbook-edition correctly (during the installation the Windows 7-partition couldn't be found, so I had to manage my partitions manually). Now it's all working fine, but I'm gonna report the bug with my internal wifi-card, because my netbook hanged a few times after the fresh install.

Is your problem fixed by the way?

---

