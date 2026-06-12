---
title: "What am I doing wrong? (failed to startup ubuntu on windows)"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by Cilac on 2010-11-08
First time Ubuntu user, I'm probably making a few common mistakes. 
Yes, I used google. No, google did not help me. Anyway.. :u

Got wubi and ubuntu 10.10 desktop.
Disconnected internet, installed it with wubi and iso in folder.
Rebooted and met the dual boot screen, aaand..
It says stuff about wubildr or something, and that windows failed to startup ubuntu.
I read some posts about partitions and grub and all that jazz, and I really don't understand any of it. I wouldn't be surprised if that was part of the problem.
Help?

I use Windows 7. :u

---

### Post by Cheesehead on 2010-11-08
I think you need to tell us all that stuff and jazz. Especially all the cryptic error messages.
That's usually the critical information that will enable us to help you.

For most users, wubi runs flawlessly the first time.

---

### Post by Cilac on 2010-11-09
lollll. I know, habits I should get rid of. Anyway..

Dual boot screen. I select Ubuntu and..

Windows failed to start. A recent hardware or software change might be the cause.
To fix the problem:
1. Insert your Windows installation disc and restart the computer.
2. Choose your language settings and click next.
3. Click "repair your computer"

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: Ubuntu\winboot\wubildr.mbr
 
Status: 0xc000000e
 
Info: The selected entry could not be loaded because the application is missing or corrupt.

---

### Post by ImaLamer on 2010-11-09
> **Cilac said:**
> lollll. I know, habits I should get rid of. Anyway..

Dual boot screen. I select Ubuntu and..

Windows failed to start. A recent hardware or software change might be the cause.
To fix the problem:
1. Insert your Windows installation disc and restart the computer.
2. Choose your language settings and click next.
3. Click "repair your computer"

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: Ubuntu\winboot\wubildr.mbr
 
Status: 0xc000000e
 
Info: The selected entry could not be loaded because the application is missing or corrupt.

So you installed Wubi from Windows and have been not been able to boot Ubuntu, but been able to boot Windows since (Vista or XP it looks like...)?

First, can you confirm there is a file at ```
C:\Ubuntu\winboot\wubildr.mbr
``` or is there a file at ```
C:\wubidr.mbr
```

I had an issue with the bootloader too, though slightly different one install of Windows ago. Since then I've decided to run Ubuntu from a dedicated partition, but I think I can help you here from what I went through.

Can you, before you reply, download and install EasyBCD from Neosmart? This will allow us to edit and view the way the Windows bootloader functions - we may be able to change where the bootloader is pointing. If anyone else has tips, feel free to step in as well :)

---

### Post by Cilac on 2010-11-09
I use Windows 7.

Downloaded EasyBCD. 

Yes, wubildr.mbr is there. :u

---

### Post by ImaLamer on 2010-11-09
Look in the EasyBCD main screen to see if both the Windows and Wubi entries are on the same disc, either their numbering or their unique ID will be the same - if possible, copy and paste it here into the code brackets (# on toolbar).

---

### Post by TheShoemaker on 2010-12-16
While I'm obviously not that guy, I'm basically at the same spot. I'm at the main screen (the first one when you open the application). 
```
There are a total of 2 entries listed in the bootloader.

Default: Windows Vista (TM) Home Basic (recovered) 
Timeout: 10 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Windows Vista (TM) Home Basic (recovered) 
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Ubuntu
BCD ID: {0af8d286-c31c-11dd-8793-e558f23cc042}
Drive: G:\
Bootloader Path: \ubuntu\winboot\wubildr.mbr

```But, you see, the issue is that the wubildr is in C:\wubildr, not the location it says. So should I shift it to that spot?

---

### Post by ImaLamer on 2010-12-16
Because editing the BCD config didn't always stick for me I'd try moving the .mbr file to where it is pointing to first. If that doesn't work then I would try editing the config. Don't actually move the file, just copy it to the path in the settings you pasted.

Hope it works for you :)

---

### Post by psusi on 2010-12-16
The short answer is: don't use wubi, do a proper side by side install.  The detailed answer is: wubi does not get along with Windows 7.

---

