---
title: "Alternate Installer CD-ROM Error"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by nlvivar on 2006-06-08
I have already installed the "Desktop" version of the Dapper CD-ROM for i386 on my Dell Inspiron 7500 laptop with a Toshiba CD-ROM drive XM-1920B. The "Desktop" version works fine, except for some CD-ROM mounting odd behaviour.

I would like to use LVM partitioning, and so I am trying to install using the "Alternate install CD."

I have checked the MD5SUM on the iso file, and it all checks out. I have burned the iso image twice onto CD. On both CDs I get the same following behaviour when I boot up.


I select to install, choose my language, etc, and then the installer checks the CD-ROM. Sometime during the CD-ROM check the following message screen pops up:

//begin message
[!!] Detect and mount CD-ROM
Error reading Release File
The CD-ROM does not seem to contain a valid 'Release' file, or that file could not be read correctly.

You may try to repeat CD-ROM detection but, even if it does succeed the second time, you may experience problems later in the installation

<Continue>
//end message


After choosing <Continue>, I get the next message:

//begin message
[!!] Detect and mount CD-ROM
Installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. the failing step it: Detect and mount CD-ROM
<Continue>
//end message


After choosing <Continue> on that screen I get the "Ubuntu installer main menu" where I "Choose the next step in the install process." At that point, I chose <Detect and mount CD-Rom>.

I then get the following message:

//begin message
[?] <Detect and mount CD-Rom>
Some PCMCIA hardware need special resource configuration options in order to work, and can cause the computer to freeze otherwise. For example, some dell laptops need "exclude port 0x800-8ff" to be specified ghere. these options will be added to /etc/pcmcia/config.opts. See the installation manual or the PCMCIA HOWTO for more information

For most hardware, you do not need to specify anything here.

PCMCIA resource range options:

___________________________________________________

<Continue>
//end message


What is going on here?

I don't think that it is the CDs that I have burned or my burner (1) since I have already burned the "Desktop" successfully without any problems, (2) since I have burned two "Alternate" CDs with the exact same behaviour from each, and (3) I have prior to this installed and run Fedora Core 5 with the same methods and equipment. I don't think that it is my CD-ROM for the same reasons.

Also, what does the last message mean? Where do I find the "installation manual or the PCMCIA HOWTO for more information?"

Any help would be greatly appreciated.

Thanks. -Noel

---

### Post by nlvivar on 2006-06-09
Well, after some experimenting I found out that I need to turn off DMA on my CD-ROM. So I put in "ide=nodma" in the advanced option line <F6>.

However, it did not stop the last "PCMCIA resource range options" message screen from popping up.

So I guess the only unresolved questions are:
1) How was I supposed to know that I should turn off DMA? Should there be some documentation somewhere? I think that I pieced it together after reading online someone's account of installing Debian on his Inspiron.
2) What does that last message screen mean about the "PCMCIA?"

Thanks.

---

