---
title: "help installation"
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by Philip Marlowe on 2013-04-13
[COLOR=#101010][FONT=Ubuntu]tried 10 times, can you suggest step by step? can't find my specific issue.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]mio pc characteristic:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]cpu: amd a4 5300 2-core 3.4ghz socket fm2 1mb hd7480d 65w boxed[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]motherboard: e asus f2a85-m le socket fm2 amd a85x ddr3 sata3 usb3 matx[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]hard disk: western digital caviar blue 500gb 3.5'' 7200rpm 16mb sata3 wd5000aakx[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]ram: ddr3 g.skill sniper f3-14900cl9d-8gbsr 1866mhz (2x4gb) cl9-10-9-28[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]i made a partition of 35gb for ubuntu (where i tried to install few times, but every time, different versions, different issues (audio, video etc...)), another 35gb partition for win 8 (it's working great), 7gb swap partition, the rest is ntfs for shared data.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]i've no cd reader, i need usb ubuntu installation.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]let's start from the beginning: which ubuntu version you suggest? gimme the link, better torrent or direct? which tool, for the bootable usb key generation?[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]thanks[/FONT][/COLOR]

---

### Post by claracc on 2013-04-13
This link: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) provides all the information and also the isos ([https://help.ubuntu.com/community/GettingUbuntu](https://help.ubuntu.com/community/GettingUbuntu)) you require.

I would recommend the 12.04 LTS ubuntu release since it will be supported for 5 years, but it depends of what do you want, I suggest this link: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) for more inforamtion. About links to download isos, it depends on the speed of your internet connection. I have 30 MB wifi and can download a 700 MB iso in no more than 10 minutes.

---

### Post by fantab on 2013-04-13
@Philip Marlowe:
Did you get Windows8 pre-installed? 35GB for Windows8, IMO is too small. There MUST be atleast 25% of free space on your partition after installing everything Windows. Or else you may have issues.
Does your Mobo have UEFI or BIOS?
What is your Graphics card?

Like claracc, I would too recommend 12.04 LTS, right now the official version is 12.04.2, which comes with 12.10 '[hardware enablement stack]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack")'. My advice will be to go with version **12.04.1** [you can update after installing to 12.04.2]. It will be advantageous if you go with [.torrent download]("http://www.ubuntu.com/download/desktop/alternative-downloads").

---

### Post by Philip Marlowe on 2013-04-13
downloaded the 12.04 64 bit as you said, built the usb with unebootin from win, boot: unebootin menu, first raw "default" automatically runs but can't start giving me a message "invalid or corrupt kernel image"... help please

---

### Post by fantab on 2013-04-13
Sounds either a bad download or bad burn.

First check the integrity of your downloaded .iso with [MD5SUM CHECK]("https://help.ubuntu.com/community/HowToMD5SUM"). Then try to burn it again... try [Linux Live USB Creator]("http://www.linuxliveusb.com/en/download"), run this tool as 'administrator' from Windows.

---

