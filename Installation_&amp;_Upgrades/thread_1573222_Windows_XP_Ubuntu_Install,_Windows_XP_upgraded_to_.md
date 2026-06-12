---
title: "Windows XP Ubuntu Install, Windows XP upgraded to Windows 7"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by Arcrave on 2010-09-12
I installed Ubuntu using the WUBI.EXE installer and everything worked fine until I forgot to uninstall Ubuntu before I upgraded to Windows 7 Ultimate. Now I am running Windows 7 and cannot access Ubuntu or get rid of it. So I have a partition on my harddrive with memory I cannot access. I want to somehow get rid of Ubuntu and give that memory back to Windows. I would greatly appreciate any help.

[NOTE::: I can see the Ubuntu boot option but I cannot access it]

Upon selecting the Ubuntu option (Windows is the boot manager BTW) I get this message.....

[COLOR="RoyalBlue"] Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

  1. Insert your Windows installation disc and restart your computer.
  2. Choose your language settings and click "next."
  3. Click "Repair your computer"
If you do not have this disc, contact your computer administrator or manufacturer for assistance.

  File: /wubidr.mbr

  Status: 0xc000000f

  Info: The selected entry could not be loaded because the application is missing or corrupt.[/COLOR]

However Windows Runs fine, I just cannot access Ubuntu.

---

### Post by Frogs Hair on 2010-09-12
Question : do you have an upgrade disk or a standard W7 disk ? If you a standard disk and can get into Windows you should be able backup files and reformat and install Windows.

---

### Post by Arcrave on 2010-09-12
I have a Windows 7 OEM install disk [standard]

I am wondering if there is a way to simply (without) reinstalling the OS to merge the two partitions, and erase Ubuntu.

---

### Post by Frogs Hair on 2010-09-12
You may want to check the Wubi support forum before reinstalling. [http://wubi-installer.org/support.php](http://wubi-installer.org/support.php)

---

### Post by Mark Phelps on 2010-09-12
> **Arcrave said:**
> I am wondering if there is a way to simply (without) reinstalling the OS to merge the two partitions, and erase Ubuntu.

NO, there is not a way to do this.

You didn't actually "upgrade" to Win7; you replaced XP with Win7.  So, your apps got removed -- one of them being the Wubi install.

When Windows apps won't uninstall, you sometimes have to reinstall them first because their uninstaller gets corrupted.  Have you tried the same with Wubi?

---

### Post by Arcrave on 2010-09-12
I have Wubi again, but I don't want to reinstall Ubuntu.... Thats the thing. See now im not sure if ubuntu is actually gone or if it is only an option on the boot screen and not actually there. If I got rid of windows xp though would that delete ubuntu?

---

### Post by wilee-nilee on 2010-09-12
> **Arcrave said:**
> I have Wubi again, but I don't want to reinstall Ubuntu.... Thats the thing. See now im not sure if ubuntu is actually gone or if it is only an option on the boot screen and not actually there. If I got rid of windows xp though would that delete ubuntu?

Any XP to W7 is a fresh install but there should be a old windows file in W7. If you have deleted these old windows=XP files then it sounds like the Ubuntu stanza is just in the W7 boot still. To look at the boot file in W7 just in start type msconfig, choose it in admin, and it will bring up the boot, and startup and other tabbed gui.

I would be concerned here about just telling you to remove a XP partition if it is still there rather then just the old windows file. Your boot may be and probably is in any XP partition still there. The bootscript in my signature will give us the information we need though to help you with more certainty. Post it in code tags as described.

---

### Post by Arcrave on 2010-09-12
Okay well the windows.old folder that was created has nothing in it cause i tranferred all my data and cleaned it out. But there was never the wubi file in it.

oh and there is nothing listed in the boot list, that you told me to get to. But then where did that memory go that ubuntu used to occupy? I have a 250GB but its max capacity lists as only 232GB

---

### Post by wilee-nilee on 2010-09-12
> **Arcrave said:**
> Okay well the windows.old folder that was created has nothing in it cause i tranferred all my data and cleaned it out. But there was never the wubi file in it.

oh and there is nothing listed in the boot list, that you told me to get to. But then where did that memory go that ubuntu used to occupy? I have a 250GB but its max capacity lists as only 232GB

There is a discrepancy in the way bits are counted, for example my external which is 320 gigs only is actually 298.
[ATTACH]169319[/ATTACH]

I'm not sure if that is whats going on here.

---

### Post by Arcrave on 2010-09-12
Yeah I know that. (I do not intend at all to sound rude btw) It's much bigger, I remember I gave away like 20GB to Ubuntu and this is waaay more than the discrepancy. When I had Windows only it was only a couple of GB difference.

---

### Post by wilee-nilee on 2010-09-13
> **Arcrave said:**
> Yeah I know that. (I do not intend at all to sound rude btw) It's much bigger, I remember I gave away like 20GB to Ubuntu and this is waaay more than the discrepancy. When I had Windows only it was only a couple of GB difference.

I just did a upgrade of XP to W7 pro, even after emptying out the old windows file I had a OS twice as big as when I wiped it and fresh installed the same W7 with no link to the original XP.

---

