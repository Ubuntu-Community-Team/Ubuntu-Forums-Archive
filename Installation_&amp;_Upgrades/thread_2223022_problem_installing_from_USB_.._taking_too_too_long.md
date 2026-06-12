---
title: "problem installing from USB .. taking too too long .. plzzz help"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by digvijay3 on 2014-05-09
I just downloaded the iso 12.10  and put the USB to boot. After starting Laptop the screen came with ubuntu written and 4 dots blinking .... its too long ..  this screen comes when i use any arrow key
[ATTACH=CONFIG]253018[/ATTACH]plz help.. it still going

---

### Post by sudodus on 2014-05-09
Welcome to the Ubuntu Forums :-)

The version 12.10 is at the end of life. Please select a supported version (12.04 LTS, 13.10 or 14.04 LTS) and a suitable flavour (Lubuntu, Xubuntu, standard Ubuntu or Kubuntu). LTS means long time support.

If you describe your computer, it will be easier to give relevant advice.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Use ***md5sum*** to check that the download was good, and use a reliable method to create the USB boot drive. See these links for details

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by digvijay3 on 2014-05-09
Hi man,,,  thanks for reply.....I have already taken the usb out and this time have put 64bit version. this time the Gui opened and I selected install ubuntu and different option till he says where are you .. I put kolkata as I am in India. After then the Gui is open with 4-5 icons on top right and mouse cursor. the USB stick is blinking....  is the installation going on?? How long will it take now?

cheers

---

### Post by digvijay3 on 2014-05-09
and my Laptop is Acer Aspire 5580 ..

---

### Post by sudodus on 2014-05-09
The cpu should be Intel core2duo, which is enough.

How much RAM is there?
What video chip/card is it? nvidia may need the boot option ***nomodeset*** to boot properly, and then you can install a proprietary driver.

The computer might work with standard Ubuntu, but maybe Xubuntu with a medium light desktop environment will work better. You can try either of Xubuntu 12.04 LTS and Xubuntu 14.04 LTS. But if you have less than 1 GB RAM, I would recommend Lubuntu 13.10 or 14.04 LTS instead. If you have less than 2 GB RAM I would recommend 32-bits and if you have more than 4 GB RAM I would recommend 64-bits. When 2-4 GM RAM the choice depends on how you use the computer.

---

### Post by digvijay3 on 2014-05-09
Intel graphics media accelerator 950, 2 GB Ram  .....  the usb stick is still blinking.. I have some icons on top right but nothing else.....

---

### Post by sudodus on 2014-05-09
Intel graphics is usually working with the built-in drivers.

There could be a problem with the wifi hardware, or something else, that can be fixed with one of the boot options. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You may have too low RAM, which can make the installation very slow (or even make it fail). 2 GB is possible but kind of low for standard Ubuntu. I would try Xubuntu 32-bits, which uses less RAM for the same task compared to 64-bits.

And as I wrote earlier, 12.10 is at its end of life, so I recommend that you get a supported version.

---

### Post by digvijay3 on 2014-05-09
right now i am using 14.10 64bit.. it booted and then i have this window with four icons on top right ...and a bg with mouse cursor nothing else...... the pen drive is blinking.. is the installation going on or its just stopped?

---

### Post by sudodus on 2014-05-09
It is hard to say if it has stopped, but at least it is not performing well considering the specs of your computer. I would interrupt it and

- download Xubuntu 14.04 LTS or 12.04 LTS
- check if the download was good (use md5sum)
- try to run a live session and then try to install
- check (if possible) that the USB drive can boot another computer, and maybe try another tool to make the USB boot drive
- try with some boot options

---

### Post by digvijay3 on 2014-05-09
trying xubuntu 12.04  finger cross:)

---

### Post by sudodus on 2014-05-09
Good luck :-)

---

### Post by digvijay3 on 2014-05-10
done and dusted..:)  All Good!!!! cheers!! Thanks a ton ....

---

### Post by sudodus on 2014-05-10
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

