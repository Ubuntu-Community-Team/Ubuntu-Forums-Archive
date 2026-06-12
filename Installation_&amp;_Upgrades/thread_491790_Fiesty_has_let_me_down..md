---
title: "Fiesty has let me down."
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by nerrick on 2007-07-04
With all the hype surrounding Fiesty I am in a state of dismay.:(

I tries to install it on a tower that I have and it would not recognize a 3Com 905btx pci nic. Every other OS out there recognizes this card why wont Ubuntu. Previuos versions like 5.01 did.

So I break down and take out the 3Com card and Install a Linksys LNE100TX card as these are pretty popular. NOPE Ubuntu still has no clue that a netowrk card is present. 

I tried a nic out of a machine that I know works... Guess what... Yup... Ubuntu lets me down yet again.:(

Does anyone have any suggestions for me to resolve this issue and make me have the will to try Ubuntu again? Or should I just pack it in here in the Ubuntu world and stick with Fedora since I know it will see my hardware.;)

---

### Post by kevinlyfellow on 2007-07-04
Fedora is very different than Ubuntu, but it you don't mind using fedora, have fun.  You can always stick with edgy until gutsy is released or use another distro or whatever.  But do send bug reports!

---

### Post by kvonb on 2007-07-04
Sounds like there is something wrong with your computer because I use ONLY 3com 905b and c cards in my systems!

I have 7 systems using these cards, and all run Feisty.

I have 2x905cs in my server, and 2x905bs in my backup server, both running 7.04.

Try clearing the CMOS, maybe the interrupt assigns are causing problems, and also try using a different slot.

When the system boots, try reading which interrupt is being assigned to the netcard, you can hit the pause key to read it.  You might find that your system is piggybacking the netcard with another device, say the sound device.  If so, put the netcard in a different slot or try to reassign the interrupts in BIOS.

If that doesn't work, try disabling the conflicting device.

---

### Post by scxtt on 2007-07-04
i have an old linksys LNE100TX, works fine in feisty ...
```
scxtt@kubuntu [~]
:> lspci
01:08.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
```

---

### Post by evolving_monkey on 2007-07-04
I dual boot Ubuntu and XP on my main work PC, Ubuntu on a system I play with and now in the process of replacing Windows 2000 Server. I used 3com nics in two of the three and they work fine (used what I had from my parts graveyard).  I did try a couple of older 3com nics and they would either not be detected or continually loose network connections in Ubuntu and would not work at all in Solaris. In my main work system there is a on-board Intel nic that was detected and used with zero problems. The intel card was not detected by Solaris. But then Solaris had a problem with most of my hardware which is why it went away..  

I tried several distros before Ubuntu. Ubuntu was by far the easiest to install and typically supported all of my hardware from the start. It did not work with an SMC wireless card and a couple of old 3com nics. Other than that I have had no hardware problems.

 I found the hardware list for Ubuntu to be accurate with regard to nic cards. I would have to agree that if your nic is reported as working in the hardware list it might be something with your hardware, computer or the installation. I have noticed however that 3com cards can be problematic at times regardless of the OS (packet and connection loss) . I have heard that D-Link products tend to be more Linux friendly. I know this to be the case with wireless cards from personal experience. I have not tried any D-Link ethernet cards.

Now, when I have to break down and buy parts, I look at the Ubuntu hardware lists and buy accordingly.That way you don't waste money and at the same time you support the manufacturers that have the insight and forethought to support Linux. 

Please note:
This is solely based on my own personal experience and that experience may not be yours.

---

