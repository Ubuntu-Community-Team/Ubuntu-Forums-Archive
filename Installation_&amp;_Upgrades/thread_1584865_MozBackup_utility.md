---
title: "MozBackup utility"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2010-09-29
I am looking for a program to save accounts and settings of thunderbird to a flash drive. For I want to reload windows and ubuntu, due to slowness of opening up files. I found MozBackup utility works but it is for windows.

Is there something similar for ubuntu? Tried to find it in synapse under morzilla and thunderbird.

---

### Post by lovinglinux on 2010-09-29
There is [TEBE]("http://softwarebychuck.com/tebe/tebe.html"). I haven't used it yet (I use webmail) and is a beta, but I use FEBE for Firefox from the same developer and is very good.

---

### Post by Camilia on 2010-09-29
Well I downloaded but can't figure out what to do with the download.

---

### Post by lovinglinux on 2010-09-30
> **Camilia said:**
> Well I downloaded but can't figure out what to do with the download.

Rename the downloaded zip file to xpi and drag it to Thunderbird window or open it with Thunderbird.

---

### Post by Camilia on 2010-09-30
> **lovinglinux said:**
> Rename the downloaded zip file to xpi and drag it to Thunderbird window or open it with Thunderbird.

Did both still no difference. Just read that it is not [compatible]("http://www.dslreports.com/forum/r24624099-Re-Thunderbird-312-Released") with Thunderbird 3, which I have.

---

### Post by lovinglinux on 2010-09-30
> **Camilia said:**
> Did both still no difference.

Sorry, I haven't used Thunderbird in a while.

Go to "Tools >> Addons" and click the "Install" button on the left-bottom corner, select the xpi file and click "Open", then "Install Now". It should install the extension and prompt for a restart.

---

### Post by Camilia on 2010-09-30
> **lovinglinux said:**
> Sorry, I haven't used Thunderbird in a while.

Go to "Tools >> Addons" and click the "Install" button on the left-bottom corner, select the xpi file and click "Open", then "Install Now". It should install the extension and prompt for a restart.

All I can find that is compatible is MozBackup and it is for windows os. Guess I will go into windows and try it with outlook. Windows seems to have a monopoly on some programs.

---

### Post by Camilia on 2010-09-30
> **lovinglinux said:**
> 
Go to "Tools >> Addons" and click the "Install"

Did and pasted TEBE in search. Got note already installed or incompatible. Just read that TEBE is [incompatible]("http://www.dslreports.com/forum/r24624099-Re-Thunderbird-312-Released") with thunderbird3, which I have. 

Googled backup and found mozbackup. It is for windows, though. I also have windows though. Seems windows has a monopoly on some programs. I am thinking easiest to go to windows side and use mozbackup. 

Having windows and ubuntu causes problems at times. Thus at times have to reload. Perhaps after next reload I should use what you are using with TEBE. What do you use?

---

### Post by lovinglinux on 2010-09-30
> **Camilia said:**
> All I can find that is compatible is MozBackup and it is for windows os. Guess I will go into windows and try it with outlook. Windows seems to have a monopoly on some programs.

Just install TEBE as I recommended on my previous post. I have tested the extension installation and it is working. Make sure you get the latest TEBE version.

Alternatively, you can simply copy the folder ~/.thunderbird, since it contains all settings and e-mails. There is no need for a backup utility.

---

### Post by Camilia on 2010-09-30
I am so totally confused! I have tried to do everything you suggested and nothing has worked. 

I downloaded TEBE. Renamed the downloaded zip file to xpi. Dragged it into Thunderbird window and opened it with Thunderbird. I did Tools > Addons. TEBE was not there, thus did search for in that window. Got no matching addons. I found thunderbird in hidden files. I tried to copy it to CD and it failed. 

Tried to download TEBE and got this message:
To install the downloaded file, rename the .zip to .xpi and open in Thunderbird (Tools > Add-ons > Extensions > Install) Now I have TEBE in thunderbird. I want to save to DVD. I think I need to specify address. What would it be?

---

### Post by lovinglinux on 2010-09-30
> **Camilia said:**
> I am so totally confused! I have tried to do everything you suggested and nothing has worked. 

I downloaded TEBE. Renamed the downloaded zip file to xpi. Dragged it into Thunderbird window and opened it with Thunderbird. I did Tools > Addons. TEBE was not there, thus did search for in that window. Got no matching addons. I found thunderbird in hidden files. I tried to copy it to CD and it failed. 

Tried to download TEBE and got this message:
To install the downloaded file, rename the .zip to .xpi and open in Thunderbird (Tools > Add-ons > Extensions > Install) Now I have TEBE in thunderbird. I want to save to DVD. I think I need to specify address. What would it be?

[LIST]
[*]Download [this version]("http://softwarebychuck.com/xpis/TEBEbeta(20100727_120000).zip"). Rename it to **tebe.xpi**
[*]Open Thunderbird
[*]Click "Tools > Add-ons > Install"
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=170919&stc=1&d=1285893662[/IMG]

[LIST]
[*]Browse the folder where you saved the file** tebe.xpi** and select it, click open and then "Install Now" to confirm the installation. 
[*]Click "Restart Thunderbird"
[*]Click "Tools > TEBE > TEBE Options" to configure TEBE.
[*]Click "Directory" to configure the folder where you will save the backup.
[*]Click "Tools > TEBE > Perform Backup" to generate the backup.
[*]Burn the backup to a DVD.
[/LIST]

---

### Post by Camilia on 2010-09-30
> **lovinglinux said:**
> 
[*]Click "Tools > TEBE > Perform Backup" to generate the backup.
[*]Burn the backup to a DVD.
[/LIST]

At directory have options
Backup destination directory
Use timestamped directories
Thus thinking I need to type something in the backup destination directory slot. What?

Oh, resized the window and I see I just click browse. Almost there! The option for CD not available, thus saving to documents. Then will drag to flash drive. Doing this for may not have enough on flash drive. Okay got it on the flash drive. Now to re-download windows and ubuntu. Then with what do I open the folder(

---

### Post by TAspr on 2011-05-29
> **lovinglinux said:**
> 
[LIST]
[*]Download [this version]("http://softwarebychuck.com/xpis/TEBEbeta%2820100727_120000%29.zip"). Rename it to **tebe.xpi**
[*]Open Thunderbird
[*]Click "Tools > Add-ons > Install"
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=170919&stc=1&d=1285893662[/IMG]

[LIST]
[*]Browse the folder where you saved the file** tebe.xpi** and select it, click open and then "Install Now" to confirm the installation.
[*]Click "Restart Thunderbird"
[*]Click "Tools > TEBE > TEBE Options" to configure TEBE.
[*]Click "Directory" to configure the folder where you will save the backup.
[*]Click "Tools > TEBE > Perform Backup" to generate the backup.
[*]Burn the backup to a DVD.
[/LIST]


Not for nothing, but I do not see a way to install it, even if I did.

See my pic as well.

---

### Post by lovinglinux on 2011-05-29
> **TAspr said:**
> Not for nothing, but I do not see a way to install it, even if I did.

See my pic as well.

TEBE doesn't work with FF 4.

---

### Post by Camilia on 2011-11-10
Thanks for all your help and patience.

---

