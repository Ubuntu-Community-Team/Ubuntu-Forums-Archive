---
title: "Installation hangs (14.04.1)"
date: 2015-01-10
forum: Installation &amp; Upgrades
---

### Post by axd2 on 2015-01-10
I'd like to set up dual boot Win7 and ubuntu on a new computer with uefi (I'm afraid I'm not familiar with uefi, so I'm not sure which uefi settings I should choose). I installed Win7 first, I can delete and reinstall it if necessary.

Then I tried to install 14.04.1 from DVD. Depending on which uefi settings I choose, I can choose "Try Ubuntu without installing" / "Install Ubuntu" /...
 or choose extended options like nomodeset, but whatever I select it always ends up the same: A boot animation ist displayed ("ubuntu" with 5 color changing dots unter it) and the computer seems to hang while the animation still is running.

Thanks in advance for any help!

---

### Post by sudodus on 2015-01-10
Welcome to the Ubuntu Forums :-)

First you must be able to get the boot work with the live system in the DVD.

- Did you check with ***md5sum***, that the download was good? - [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
- Did you burn the DVD with lowest possible speed?
- Did you check that the DVD is good at the first menu (below 'Try Ubuntu')?

Is the only thing you see after pressing the Enter key selecting for example 'Try Ubuntu without installing' that you get the 5 dots? You can continue with [boot options]("https://help.ubuntu.com/community/BootOptions"): Select it again, then press the Escape key. You get a line. Go to the end of that line (move the cursor with the arrow keys). Remove  the two boot options **quiet splash**. Boot and describe what you see, and if there is some error output or what is that last output (text to the screen).

In the grub menu when booting into UEFI you press the ***E key*** to set the boot commands and edit the 'linux' line: and remove **quiet splash**. Continue booting with ***ctrl + X***

-o-

[I][B]Please specify your computer
[/B][/I]
- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give good advice. Otherwise we can only guess.

-o-

Please read this link and links from it to prepare for booting into UEFI mode and installing Ubuntu.

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)[URL="https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI"]
[/URL]
particularly these two links: a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

---

### Post by axd2 on 2015-01-10
> **sudodus said:**
> Did you burn the DVD with lowest possible speed?

After burning another DVD with lowest speed (1x) everything works as expected. :)

Thank you very much!

---

### Post by sudodus on 2015-01-11
You are welcome :-)

---

