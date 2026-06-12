---
title: "Not installing"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by aroog on 2010-12-18
hi, 

i am new to linux system. i downloaded ubuntu netbook 10 edition for my lap top.

once download and my usb disk is ***pleted i tried to install unbuntu on my laptop. the current window installed on my system is windows 7. 
i am unable to install Ubuntu OS on my laptop as there is a file error(cant remember the file name)that stops the installation.

can you please advise if the downloaded file was corrupted or else?

i need to know the answer very urgently.

thanks

---

### Post by Quackers on 2010-12-18
Wel***e to UF :-)
To check the downloaded iso file for errors

[https://help.ubuntu.***/***munity/HowToMD5SUM](https://help.ubuntu.***/***munity/HowToMD5SUM)

When booting from the Live cd/usb if you tap the F6 key you should get a screen with some options. Run the "check cd for errors" one.

Edit 
It appears that the letters c o m are being sensored! Please add them back in for the link address.

---

### Post by aroog on 2010-12-19
hey,

thanks.

i have checked my file that is not corrupted. now i am left with live CD option.

i will check it out and will post the results.

---

### Post by Quackers on 2010-12-19
If the MD5sum checked out ok but the cd reports errors, try burning the image again at a lower speed. The lowest possible is best :-)

---

### Post by aroog on 2010-12-19
hey i am trying to do it on usb...do you think usb is the problem?

---

### Post by aroog on 2010-12-19
it worked out at last.

os is installed on my system.

now i am facing another issue.

i dont know where ubuntu disappeared after installation.

i installed it along with Windows 7 in separate drive. and that drive is not visible as well.

any solutions?

waiting for response.

---

### Post by sikander3786 on 2010-12-19
> **aroog said:**
> it worked out at last.

os is installed on my system.

now i am facing another issue.

i dont know where ubuntu disappeared after installation.

i installed it along with Windows 7 in separate drive. and that drive is not visible as well.

any solutions?

waiting for response.
Do you mean you installed to a separte HDD or just a seperate partition?

If it was installed to a separate HDD, you might need to configure your Bios to boot from that HDD instead.

If the Ubuntu installation completed without any errors, it is supposed to be there where you installed it :-)

---

### Post by aroog on 2010-12-19
in separate partition.

---

### Post by sikander3786 on 2010-12-19
Ok. Boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us figure out any problems with Ubuntu or Grub (Ubuntu bootloader).

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

