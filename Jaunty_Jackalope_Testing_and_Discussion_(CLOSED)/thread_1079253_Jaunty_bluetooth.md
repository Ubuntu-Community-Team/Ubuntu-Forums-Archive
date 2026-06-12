---
title: "Jaunty bluetooth"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-02-24
Has anyone tried to send files to a PC via bluetooth in Jaunty Kubuntu? I've just tried to send a file from my SonyEricsson K800i phone and the PC receives the file and then the file disappears into the ether!   I can't find the received file anywhere and have sent the file a couple of times more with the same result. In Dolphin there's no sign of it.

---

### Post by Exilant on 2009-03-06
i just tested it, and the files turn up well-hidden in ~/.kbluetooth4/
bluetooth in kde4 just doesn't seem to be there (hopefully yet)

---

### Post by Kevbert on 2009-03-06
Thanks for that Exilant.  You may find you get a few other problems with bluetooth, such as using Send To (which comes up with an error, if you use gnome/Ubuntu, I'll need to check this with Kubuntu, if it has the option). This is a known issue, but drag and drop works.

---

### Post by lcohen999 on 2009-03-07
Try using the blueman project.

I have had much better luck with it...

---

### Post by Enicko on 2009-04-11
I'm running Jaunty Ubuntu 64 on a W500.  

I downloaded the bluetooth file manager and the bluetooth proximity from the add/remove menu.  They both work, but both seem to have the same effect of causing a freeze that I can't get out of without hard rebooting via the power switch.

I sent an mp3 from my Blackberry to the machine and it hung up a couple seconds later.  Had to hard reboot with the power button.

Blue proximity is cool, I want to use it next week at an open meeting scenario, but I'm afraid I'll have to wait until it's stable.

---

### Post by rykel on 2009-04-12
Hi all,

Yes, I second the recommendation to use Blueman ([http://blueman-project.org](http://blueman-project.org))... although I have not exhaustively tried it out yet, it was able to browse the files on my Nokia 6121 Classic mobile phone.

HOWEVER, Network Manager does not seem to work with it in Jaunty, although it is supposed to! Hence, I cannot use my phone as a 3G modem to provide internet connectivity to my laptop yet.

Hope that helps!

---

### Post by densou on 2009-04-18
:(

Broken as well with dongle+dad's Samsung X-670 (Jaunty can add it but nothing works -drag'n'drop, explore folder, file transfer, etc- meanwhile phone can't do anything torwards that terminal)

It worked fine on both Hardy and Intrepid. :o

---

