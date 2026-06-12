---
title: "Installation error after previous uninstall of 11.10"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by Bloozntooz on 2011-12-22
Hi all,

I'm at the foot of the learning ladder with Ubuntu.

I was running 11.04 on dual boot with Windows (Wubi installation) and I performed the upgrade to 11.10 which went fine. I was still getting the fans on my desktop running all the time so after some research in the forums I found a solution stating that the Drivers for NVIDIA need upgrading. I performed the Driver update check and there was an NVIDIA upgrade so I installed it. After rebooting the system stuck on root@ubuntu and waited. I rebooted again and tried Recovery mode but this also stopped in a similar fashion.
After messing around many times I ended up deciding to uninstall Ubuntu and reinstall the Wubi. I uninstalled from Windows XP pro Control Panel and it took barley 1 second before it said that the uninstall was complete (which seemed odd because it was so quick). I downloaded the Wubi from Ubuntu but now after it downloads all the required files I get an error every time in the installation, and a reference to a log file.

Attached is a screen dump of the error page I encounter, and the Wuib error log it refers to (as the upload limit for a txt file on this forum is only around 20kB, I have edited the log file to show only the last installation attempt - if previous info is required please let me know).

All help would be appreciated as to what my next step should be to reinstall Ubuntu.
Thanks in advance.

---

### Post by BC59 on 2011-12-22
Check if the folder Ubuntu was deleted from the Windows root directory C:\
You can clean Windows with [CCleaner]("http://www.filehippo.com/download_ccleaner") 
Try with CCleaner to delete the temp files and look if you can uninstall Ubuntu/Wubi.

---

### Post by BC59 on 2011-12-22
For more information go [here]("http://ubuntuforums.org/showthread.php?p=11350655").

---

### Post by bcbc on 2011-12-22
The install is successful. See [lpbug]862003[/lpbug]. It's a bogus error message.

---

### Post by Bloozntooz on 2011-12-23
BC59 / bcbc,

Thanks for your responses. Following the clearing of the Temp folder and manually deleting the leftovers from the c:\Ubuntu directory I was able to reinstall 11.10 using wubi - thanks a lot.

Going back to my original issue with the desktop fans running all the time in Ubuntu I tried to upgrade the NVIDIA driver again, but unfortunately I have come a full circle and ended up with Ubuntu hanging (flashing "_") during normal boot, and when booting in recovery I get the same "root@ubuntu#" (presumably this it GRUB?). So again I cannot access Ubuntu to disable this NVIDIA driver! Could you point me where to go for what I need to do (or should I uninstall again, reinstall a-fresh, and forget the NVIDIA driver upgrade and live with the fans running?).

Thanks for your patience and help.

Update: I found a solution that got me back into Ubuntu here: [http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled](http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled) (see 5th post) by purging the NVIDIA driver at the terminal prompt when booting in recovery mode. Still leaves me running without the proprietary Driver installed though, but at least I can use the OS again.

---

### Post by bcbc on 2011-12-23
Do you have an optimus (on demand) nvidia card? Those don't work in Ubuntu. Also that "root@ubuntu#" is a root prompt (not grub) and it's because your recovery mode is set to boot: "single" instead of "recovery nomodeset". You can edit this 'e' and change it to boot to the recovery menu instead (Ctrl+X) to boot. If you do this, you also need to delete the line "set gfxpayload=$linux_gfx_mode". See bug [lpbug]889650[/lpbug]

---

### Post by Bloozntooz on 2011-12-27
bcbc,

The NVIDIA card is a GeForce GT220 and it looks like quite a few people have had problems with this family of card from reading up on several forums. I will pursue more reading up on this rather than seeking the same help on this forum as already exists on others.

What you have mentioned regarding editing the 'e', well that has gone over my head, but I will take some time out to understand the 'what' and 'how' of doing what you said, although I do generally understand what you are meaning (I have always been a Windows person so this is new ground for me).

If I find a solution I will come back and post.

Thanks again for your help - appreciated.

---

