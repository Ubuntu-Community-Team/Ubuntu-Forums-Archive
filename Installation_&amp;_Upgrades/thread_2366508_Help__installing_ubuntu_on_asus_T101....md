---
title: "Help : installing ubuntu on asus T101..."
date: 2017-07-18
forum: Installation &amp; Upgrades
---

### Post by sayyas on 2017-07-18
Hi ...
Device: asus T101HA
Status: After installation the screen is black ..
System: Windows
Linux: ubuntu 17.04
When I try to install Ubuntu via USB flash on the device nothing is ever shown .. During my search I found that someone installed it via the HDMI cable .. But after the installation system appeared on the big screen did not appear on the screen of the laptop .. Only a black screen ... and the GURB look like the picture below ...
You can help and thank you very much ..
[IMG]https://photos.app.goo.gl/0MR9nxFhsmdCMJtr2[/IMG]

---

### Post by BenginM on 2017-07-18
Salutations! and welcome the forums.

this machine has an Integrated Intel HD Graphics , it might not be the cause ..

did you checksum the hashes of the iso before you burned it to the usb . and which tool/method did you use!

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by sayyas on 2017-07-18
> **Sary.sa said:**
> Salutations! and welcome the forums.

this machine has an Integrated Intel HD Graphics , it might not be the cause ..

did you checksum the hashes of the iso before you burned it to the usb . and which tool/method did you use!

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

yes i checked the iso [COLOR=#333333][FONT=Ubuntu]md5[/FONT][/COLOR] ... i used the external dvd reader and usb flash ... and i tried with linux mint it gives me the same results ...

---

### Post by yancek on 2017-07-18
You mention having windows but since they have been selling operating systems for 35 years, you need to specify the version you have.
I'm not sure I understand your problem as "After installation the screen is black" and later indicate you can't even correctly boot the installer for Ubuntu.  So what is it, the screen is black after you installed windows?

Have you tried booting the usb on another computer?
How did you put Ubuntu/Mint on the usb drive, what specific software did you use?

---

### Post by sayyas on 2017-07-19
> **yancek said:**
> You mention having windows but since they have been selling operating systems for 35 years, you need to specify the version you have.
I'm not sure I understand your problem as "After installation the screen is black" and later indicate you can't even correctly boot the installer for Ubuntu.  So what is it, the screen is black after you installed windows?

Have you tried booting the usb on another computer?
How did you put Ubuntu/Mint on the usb drive, what specific software did you use?

Im sorry .. its windows 10 .. i installed the Ubuntu via HDMI cable using pc screen .. installation progress goose on by the pc screen .. on the laptop nothing shown only black screen .. but i can control the laptop by the pc screen ..... hope its clear now ..
and i tried my usb flash on anther pc ..its ok ..
i put the ubuntu iso by using the (Rufus) using 
partition scheme : MBR BIOS or UEFI
 thank you

---

### Post by BenginM on 2017-07-19
these seems like a whole different issue  .. unplug the HDMI from the laptop .. what's the problem now! you can't see ubuntu's desktop from the laptop screen ..?

---

### Post by sayyas on 2017-07-22
> **BenginM said:**
> these seems like a whole different issue  .. unplug the HDMI from the laptop .. what's the problem now! you can't see ubuntu's desktop from the laptop screen ..?

exactly ...!!!
the ubuntu is setup-ed as i can see throw the HDMI ... but nothing shown on laptop screen ..

---

### Post by BenginM on 2017-07-22
Based on your description, it seems like you have it set to display as an extended desktop. it really depends on the settings , "System Settings" and select "Displays" set it to "mirror displays" ... any change!

---

