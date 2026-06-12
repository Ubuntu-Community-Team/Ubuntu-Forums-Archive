---
title: "Ubuntu 18.04 freezes on shutdown"
date: 2018-06-25
forum: Installation &amp; Upgrades
---

### Post by dev3 on 2018-06-25
I have a Lenovo Legion Y520 with i7 Processor & a Nvidia Graphics card, on which I've installed Ubuntu 18.04.

I've managed to get Ubuntu Running, but I'm facing the following problems:

1)The system just freezes when I shutdown or reboot. Even If I give the command: sudo shutdown now, it Just freezes. I either have to press the Powerbutton, to reboot it, or Get somebody to help me with typing the REIBUS command, since this laptop has a KeyPad, and the PrtScreen button only becomes active when you press the Fn key on the lower left hand corner.

2)The system freezes whenever the 'Welcome to Ubuntu' window tries to send the information to the server.

I've tried the following:

a)Following the information given here: [https://ubuntuforums.org/showthread.php?t=2358728](https://ubuntuforums.org/showthread.php?t=2358728) modified the Grub; That did not seem to help

b)Installed the Nvidia drivers. That too did not help.

Right now I'm at my wit's end on what to do, since I've never had these kinds of problems with Ubuntu in my 7-8 years of using it on other hardware. I've looked at the other threads with similar issues, but none of them seem be of any help to my situation.

---

### Post by qarmas on 2018-09-24
Hey! Did you find any solution? I have the very same problem on my Lenovo Legion Y520.
Although I have an i5 CPU and running Ubuntu Mate 18.04 through Legacy support.
I managed to dual boot with Windows 10 though I have to manually change the BIOS-settings to first run UEFI-mode to be able to start Windows 10. And vice versa to start Ubuntu.

During the installation process of Ubuntu Mate 18.04, I was asked to install GRUB boot loader onto some partition. I wasn't sure what to choose so I just chose the defaultly selected option, which I guess is the partition where my Ubuntu OS is installed.

Whenever I shut down or reboot from either the GUI or the terminal emulator the system freezes.
I also tried modifying the GRUB following the instructions in the thread you posted - nothing works.

BTW is the REIBUS method optimal? I mean, is it in any form harmful for the system/data/cofigurations/hardware to use that method to reboot/shutdown the PC?

Thanks!

---

### Post by davisd7796 on 2018-09-28
Another Lenovo Y520 here, tons of errors and apparently zero responses because nobody knows where to begin with a distro that can't even force init 0.  What's the point of open source again?  18.04 is the buggiest dog of a release I've seen since I started using Hardy, and only one kernel update so far?  I should have known this would be a rollback when it couldn't even reboot following the install.  And this claims to be an LTS???  Ubuntu has never tried quite this hard to become my least favorite distro.  Might be time to finally jump ship.

---

### Post by wildmanne39 on 2018-09-28
Hello davisd7796, if you need help please start your own thread instead of posting in someone else's especially an old thread that is unanswered, please stick to the issue, just because you are having an issue does not mean 18.04 is a disaster, I have been using it on three different computers since testing began with almost no issue and long before it was released all my issues were resolved, remember there are millions of people that use Ubuntu and only the ones that have an issue ever post the other people never post to say it is working great. 

Also note the all of you in this thread have the same computer so it is likely an issue with the specific computer model.

---

