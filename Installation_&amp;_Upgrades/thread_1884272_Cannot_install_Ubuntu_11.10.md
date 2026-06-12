---
title: "Cannot install Ubuntu 11.10"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by startgame412 on 2011-11-21
Hi, I'm trying to install Ubuntu 11.10 using wubi but when It is trying to load the installer, I get an out of range message on my monitor. I also tried to run Ubuntu in live CD mode but still get the same result. I was able to install Ubuntu 11.04 with no problems. I have an HPE 410t computer with Intel i5 quad processor running at 2.9 Ghz and a 22 inch AOC LCD/TV monitor combo that supports resolutions up to 1920x1080. Anyone else have this problem when trying to install ubuntu 11.10? Thanks.

---

### Post by Sonsum on 2011-11-21
> **startgame412 said:**
> Hi, I'm trying to install Ubuntu 11.10 using wubi but when It is trying to load the installer, I get an out of range message on my monitor. I also tried to run Ubuntu in live CD mode but still get the same result. I was able to install Ubuntu 11.04 with no problems. I have an HPE 410t computer with Intel i5 quad processor running at 2.9 Ghz and a 22 inch AOC LCD/TV monitor combo that supports resolutions up to 1920x1080. Anyone else have this problem when trying to install ubuntu 11.10? Thanks.

It sounds like ubuntu is booting with a monitor resolution higher than your monitor supports. 

Perhaps try booting into safe graphics mode. I found these instructions on another thread:

"right after you select "ubuntu" from the menu, press ESC. It should show up a menu entry, then select the one that says "safe mode". If only 1 option is available, select that one, and press ESC immediately afterwards, and you should get the correct menu. If there's still only 1 option after the 2nd menu, press "e" to edit, and at the end of the line that says "kernel" remove "quiet" and "splash", add "single", press enter, and press b to boot."

---

### Post by startgame412 on 2011-11-21
Hi, thanks for the reply. I tried using safe graphics mode but it still does not work. Instead of getting out of range message when using safe graphics mode, the monitor just says no signal and turns itself off. I can't get to a terminal. Thanks.

---

### Post by majedaly on 2011-11-21
I had these problems many times installing UBUNTU. I guess the iso image just does not fit every hardware architecture.
You can try the alternate installer here
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
if the alternate installer doesn't work for me, I would go for the minimal install CD. The minimal install CD would provide a more robust way, as it is only 12 MB, then you download the rest from the apt during install. it is very easy, and GUI based.
Full instructions can be found here
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Sonsum on 2011-11-21
> **majedaly said:**
> I had these problems many times installing UBUNTU. I guess the iso image just does not fit every hardware architecture.
You can try the alternate installer here
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
if the alternate installer doesn't work for me, I would go for the minimal install CD. The minimal install CD would provide a more robust way, as it is only 12 MB, then you download the rest from the apt during install. it is very easy, and GUI based.
Full instructions can be found here
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Unfortunately, I do not believe WUBI works with anything but the default LiveCD, which is what the OP is using.

Back to the original posts, is there any way you could try using a different monitor for at least the installation? That would rule out your TV and afterwards, you most likely would be able to use your TV again.

Also, does your computer have a graphics card, or is it just using the integrated i5 one?

---

### Post by startgame412 on 2011-11-21
Hi, thanks for the replies. Passing nomodeset as a kernal argument gets past the intial screen and now I can see the splash screen but after the splash screen when loading the gi/desktop environment, I again get the out of range message. Not sure what type of graphics card this computer has but I know its an ATI Raiden HD 5450 card with 512MB of VRAM. Thanks.

---

### Post by Sonsum on 2011-11-22
I'm glad that you've made some progress. Unfortunately, I don't know much about ATI graphics cards. Although my apartment mate uses one in his desktop and I remember him talking about the latest driver giving him issues. 

Hopefully, someone familiar with these sorts of things will come along, for I think I've done all I can.

---

