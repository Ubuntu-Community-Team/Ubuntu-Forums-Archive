---
title: "Live CD. Launch to terminal without desktop."
date: 2015-07-31
forum: Installation &amp; Upgrades
---

### Post by jorge24 on 2015-07-31
Hi,

I've been struggling with a bug with nouveau and my typical dual GPU laptop. Nouveau crashes after some time. Some times at startup and some times after 1 minute. I managed to workaround that by installing lubuntu with the mini image, installing after that linux desktop and right after that installing nvidia propietary drivers and configuring the sytem to use them always. I've managed to play some games for hours without problems so I think that it works fine.

Now the problem is that my Windows was updated (I have dual boot) and, like everyone else, it broke my grub. I saw some simple fixes for this, but all them require launching a live CD and writting some commands in the command line, BUT I CAN'T LAUNCH A LIVE CD because all live CDs start with desktop, and that means nouveau and that means crashes everywhere. I've searched everywhere how to launch a command line just from a live CD, but is impossible. All I see is "launch desktop and open command line" or "the alternate install...", but I don't want to install. How can an open source thingy don't have a direct command line option just in case something goes wrong? Even Windows has! xD

Now the question, what is the command line I have to add to the live CD when I press F6 so nouveau is not launched and I enter directly to the terminal?

---

### Post by NathanRodriguez on 2015-07-31
This alternate have a text installer: [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)
It should provide you a shell where you can mount your boot disk and repair grub.

---

### Post by jorge24 on 2015-08-01
> **NathanRodriguez said:**
> This alternate have a text installer: [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)
It should provide you a shell where you can mount your boot disk and repair grub.
Oh, didin't think of that.

Finally managed to repair it by disabling splash, so nouveau don't has to write any graphic until desktop is loaded, and when the mouse is shown I instantly press CTRL+ALT+F2 to show the console, and when nouveau crashes, instead of freezing my screen with a stack dump and showing a "reboot needed" message (or something like that), simply shows the error but I still can write to the console.

Btw, for the future (because the above method is ******. Sometimes dumps stack altough nouveau crashes when in terminal), how can I show the shell while installing? (Without achieving install, of course).

Thank you for your reply.

---

### Post by Bashing-om on 2015-08-01
jorge24; Hello;

I believe - best of my recall - that if one boots the liveDVD to the boot options screen, and here exercise the F6 option one can change the boot parameters. Replace the terms "quiet splash" in the boot line with the term "text" and one will boot to a terminal .

However, in 15.04 using systemd as the init system, I do not know what that boot parameter would be.
[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many paths to 1 end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jorge24 on 2015-08-01
> **Bashing-om said:**
> jorge24; Hello;

I believe - best of my recall - that if one boots the liveDVD to the boot options screen, and here exercise the F6 option one can change the boot parameters. Replace the terms "quiet splash" in the boot line with the term "text" and one will boot to a terminal .

However, in 15.04 using systemd as the init system, I do not know what that boot parameter would be.[INDENT][INDENT]'buntu[INDENT][INDENT][INDENT]many paths to 1 end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Yes, removing splash and adding text was one of the things I already tried. Does nothing in Lubuntu 15 (And also I think in Lubuntu 14, but now I don't remember if I've tried it with that version).

---

### Post by sudodus on 2015-08-03
You can also try the boot option ***nomodeset*** together with ***text***

---

