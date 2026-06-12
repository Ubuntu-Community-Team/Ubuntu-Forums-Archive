---
title: "Dual boot not working"
date: 2022-05-06
forum: Installation &amp; Upgrades
---

### Post by markbartok on 2022-05-06
I uninstalled Ubuntu and re-installed Kubuntu in dual boot environment with Win10.  Had it working for a couple of days but now it will not boot into Windows (Ubuntu and Windows options are presented in the boot selection list); Kubuntu works just fine.  When I select Windows the system returns to the dual boot selection menu.  
I just ran Boot-Repair and "uploaded" the output to the paste.ubuntu.com link but am uncertain about next step to repair the system.  
TIA for your assistance

[https://pastebin.ubuntu.com/p/bcZbkNtgnX](https://pastebin.ubuntu.com/p/bcZbkNtgnX)/

---

### Post by tea for one on 2022-05-06
This might be worth a try:-

Disable Secure Boot in your UEFI Set-Up
Edit Grub where the text is blue
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR="#0000FF"]menu[/COLOR]
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[COLOR="#0000FF"]GRUB_DISABLE_OS_PROBER=false[/COLOR]

```
```
sudo update-grub
```
When you update Grub, is Windows 10 found?

More info here [https://www.omgubuntu.co.uk/2021/12/grub-doesnt-detect-windows-linux-distros-fix](https://www.omgubuntu.co.uk/2021/12/grub-doesnt-detect-windows-linux-distros-fix)

---

### Post by oldfred on 2022-05-06
Did Windows do an update.
That may have included an UEFI update which resets UEFI to defaults and may have turned Windows fast start up back on.
Those were all settings you had to do before initial Ubuntu install.
Check settings.

You should be able to directly boot Windows from UEFI boot menu using systems boot key just after vendor logo. Often f12, but varies by brand of system, but same key you use to boot USB live installer.

---

### Post by markbartok on 2022-05-07
tea for one:  
Thanks for this.  Made the grub modifications and disabled Secure Boot.
Windows was found during update-grub execution.
Restart presents Grub menu.  (Ubuntu and Windows)
Select Windows and that Boot process appears to start (NumLock cycles on and then off)
Windows is NOT launched; Grub menu is re-displayed.

---

### Post by markbartok on 2022-05-07
> **oldfred said:**
> Did Windows do an update.
That may have included an UEFI update which resets UEFI to defaults and may have turned Windows fast start up back on.
Those were all settings you had to do before initial Ubuntu install.
Check settings.

You should be able to directly boot Windows from UEFI boot menu using systems boot key just after vendor logo. Often f12, but varies by brand of system, but same key you use to boot USB live installer.


I believe Windows DID an update recently; CHKDSK showed up (I let it run and complete) a couple days ago and that was when the no-Boot-to-Windows began.
Selecting WINDOWs in the F12 menu does not launch Windows.  The Grub menu is re-displayed.
I searched my BIOS and UEFI setting and have not found the Windows fast start option for disabling.  I'll start reading the recommendations in the link you provided.
In the meantime, any other ideas?

thx,

---

### Post by oldfred on 2022-05-07
Windows fast start is a Windows setting. It sets the hibernation flag.
But if Windows does not boot directly from UEFI, that is a Windows issue.
Grub only boots working Windows that is not hibernated.

Boot-Repair cannot fix Windows issues, but may show something in its report.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by markbartok on 2022-05-07
> **oldfred said:**
> Windows fast start is a Windows setting. It sets the hibernation flag.
But if Windows does not boot directly from UEFI, that is a Windows issue.
Grub only boots working Windows that is not hibernated.

Boot-Repair cannot fix Windows issues, but may show something in its report.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


This link?:  [https://pastebin.ubuntu.com/p/bcZbkNtgnX](https://pastebin.ubuntu.com/p/bcZbkNtgnX)

---

### Post by oldfred on 2022-05-07
Back in post #2 tea for one suggested you turn off UEFI Secure Boot.
Report shows this:
> SecureBoot enabled but mokutil says: SecureBoot enabled

But Windows should boot with UEFI Secure Boot on, so not sure what Windows issue is.
Can you boot Windows in its safe boot mode, I think it is f8. 
Otherwise better to ask in a Windows forum for help.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by tea for one on 2022-05-07
The boot-repair report in post 1 and post 7 are the same file.

---

### Post by markbartok on 2022-05-07
> **tea for one said:**
> The boot-repair report in post 1 and post 7 are the same file.

Apologies.  I was away from the desktop when last reply was sent. 
NEW Boot-repair URL:  [https://paste.ubuntu.com/p/stbMfgX9VC/](https://paste.ubuntu.com/p/stbMfgX9VC/)

Will try Safemode Boot now and report back.

---

### Post by oldfred on 2022-05-07
New report does have UEFI Secure Boot off.
Nothing in report highlights any issues. So must be something internal to Windows.

---

### Post by markbartok on 2022-05-07
I have not been able to figure out a Safe boot mode.  I HAVE found the way to a Command Prompt and have access to the C: drive

---

### Post by oldfred on 2022-05-07
Back with Windows XP I used to be able to run a variety of repairs. Not sure what is most current now.
Pretty sure chkdsk, but it always required parameters and they changed with Windows 7 and maybe again?

---

### Post by markbartok on 2022-05-07
Being new to this dual-boot world myself, it seems complicated.  Looks like something in the /FIXMBR or /FIXBOOT realm may work.
I truly appreciate your assistance.  (& glad I didn't just push the Boot-repair "fix it" button.)
Cheers,

---

