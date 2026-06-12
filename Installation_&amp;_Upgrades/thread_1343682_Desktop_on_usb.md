---
title: "Desktop on usb?"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by footloose143 on 2009-12-02
[COLOR=black][FONT=Verdana]I tried creating a USB Boot stick with persistence mode and am able to boot from my USB, I've created a new user and am able to save files to user account. This serves my purpose of my Desktop on USB but what I wanted to get rid of is the initial boot of Live mode.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Whenever I boot from my USB it takes me through all the install Screens like *[FONT=Verdana]Select Language[/FONT]*, Then a menu where I need to select *[FONT=Verdana]Try ubuntu without making changes to your computer. [/FONT]*Is there a way I can customize these and get direct to use my account which I created earlier? I don’t wanted to install it on my pendrive as I wanted to use this on my windows for some data transfers.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Any advises?[/FONT][/COLOR]

---

### Post by darkod on 2009-12-02
So you want to use the same usb stick for windows data transfer and ubuntu installation but which would take you to your desktop similar to a desktop installation? Is that right? What's the capacity of the stick?

---

### Post by footloose143 on 2009-12-02
Thanks darkod for quick reply its 8 Gigs..

---

### Post by darkod on 2009-12-02
Depending how much of the 8GB you want to dedicate to the transfer function, you can actually create partitions on it, but only in ubuntu. Dedicate the first partition as ntfs for windows files, and windows will be able to see only the first partition anyway.
You can actually install ubuntu with the usb stick as the target, but that is a lot more space consuming than the 700MB for the startup stick.
The basic desktop installation before adding any software is around 2.7GB I think. You do not have to dedicate swap partition but depending on the amount of RAM on the computer(s) where you are planning to use it, you might need to create swap file on the usb installation.
I know you can run it from the stick, but I haven't tried it myself and can't tell you how fast it's working etc. Plus you have limited 8GB  space in total.
The only other option I see is the current one, starting with the stick and Try Ubuntu option. I'm not aware that you can skip the language selection and Try Ubuntu process. But this option is taking only 700MB from your stick plus the space you dedicated for the documents/settings.
It's up to you to decide depending what you need. You might try the installed on usb stick option and if you don't like it, go back to startup stick. It's a bit of work but that's how you learn. :)

---

### Post by darkod on 2009-12-02
See here:
[http://ubuntuforums.org/showthread.php?t=379572](http://ubuntuforums.org/showthread.php?t=379572)

---

### Post by footloose143 on 2009-12-02
[COLOR=black][FONT=Verdana]Thanks for this link I tried similar steps before but that would partition your usb drive and wont be recognized by windows. One other option I had in mind is to use gPartition and leave the first partition for windows as you suggested, since it wont recognize the significant partitions and use the rest for ubuntu, I tried that but it takes around 4 gigs for installation which I cant spare. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I really liked the option of Live Boot disk install using persistence mode as it takes about only a CD size for my install but I have to go through all the screens every time I try to login, May be I have to customize the LiveCD myself :( [/FONT][/COLOR]

---

### Post by darkod on 2009-12-02
You will adjust slightly the instructions for your case. First plug in the stick in computer with working ubuntu, open Gparted and create the first partition on the stick as ntfs with the size you want. That way windows will read it. The rest of the stick remains for ubuntu. You can also skip creating the swap partition because you can create swap file inside ubuntu (similarly to windows using a swap file and not partition). On google there are plenty of giudes for swap file vs swap partition.
The main thing is to create first ntfs partition and that will be readable from windows.
Yes, this way it will take more space on your stick. It's up to you.

---

### Post by footloose143 on 2009-12-02
Thanks, Correct. Let me see if I am able to configure the LiveCD myself with the required boot parameters instead of getting to GUI mode and boot me direct to default user else I'll have to live with it.

---

### Post by phillw on 2009-12-02
> **footloose143 said:**
> Thanks, Correct. Let me see if I am able to configure the LiveCD myself with the required boot parameters instead of getting to GUI mode and boot me direct to default user else I'll have to live with it.

As darkod says - use gparted to slice your usb stick. For things linux & pendrives the people over at [http://www.pendrivelinux.com/]("http://pendrivelinux.com")  have done some quite wonderful things with pendrives - and they're legal - lol
You can even have a pen-drive either dual-boot win & ubuntu, or even multi boot -- a task not that easy on a hard -drive, never mind a pen-drive ;-)

Regards,

Phill.

---

