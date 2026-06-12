---
title: "CANNOT delete ubuntu OS and try to reinstall another.  0xc000000e"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by blinkinstantaneous2 on 2010-06-07
Hi,

I want to be help on this problem I have with Ubuntu Linux. I tried to install the right way with GET UBUNTU DESKTOP EDITION and follow the 1st step to download and extract it in my flash drive. I then go into "install" and did another extraction and click on "install" label, I think. :confused:The problem happened there, when the system said it cannot find Wubildr. I said this to myself "This is tough to install"[-X so I deleted the ubuntu OS application on my flash drive.:oops: I restarted the laptop before where it asked me to choose between "windows" OS or "ubuntu" OS. I had a DOS screen-like, therefore different from what is shown on the website. Back to the story, I deleted the Linux Ubuntu OS, but that did not clear the OS off my system when I turn on the laptop power. Now my problem is I cannot get rid of the Ubuntu OS when I turn on the laptop. The message i got "wubildr.Mbr , Status" 0x000000f, info : the selected entry could not be loaded because the application is missing or corrupt. The whole message when I turn on the laptop is hereafter ==>


Windows Boot Manager

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows Installation disc and restart your computer.
2. Choose your language settings and then click "Next."
3. Click "Repair your computer."

If you do no have this disc, contact your system administrator or computer manufacturer for assistance.
    File:\Ubuntu\winboot\wubildr.mbr
    Status:0xc000000e
    Info: The selected entry could no be loaded because the application is missing or corrupt.


You can contact with me at [<snip>]("http://ubuntuforums.org/member.php?u=1091235") if a remedy is found for this. Thank you very much.

---

### Post by darkod on 2010-06-07
You installed wubi inside windows, and whether this is the right way or not, it depends on the opinion. I don't use wubi.

Wubi is installed inside windows similar to any software application. It creates registry keys, etc. If you want to remove it, you need to go into Programs and uninstall it like that.

Because you only deleted the ubuntu folder, now it's complaining that it can't find the boot files needed.

---

### Post by blinkinstantaneous2 on 2010-06-10
So darkod, do you know of any way that I can fix this problem that I have of it wanting me to choose which OS to start when I first turn on the computer?  I deleted the ubuntu folder in the flash drive and I thought it was installed (everything separate from the hard drive but on the flash drive only) in there so it was easily cleared but long and behold, it was not.  darkod or anyone help me find a way to clear this OS problem so that I do it right the next time with Ubuntu.  Thank you.

---

### Post by llawwehttam on 2010-06-10
As you've done this I can talk you through a fix, its a bit long but it WILL work.

Firstly you have to repair your Windows boat-loader.
I guess you use windows xp, if so follow these instructions, if not ignore them and tell me what os you use..

Put the windows cd in your cd drive and boot from it as if you were going to reinstall. When you get the choice press 'r' for repair. You should end up at a command line similar to dos.

From there you need to type the following. You may get a warning, this is normal.

```
fixboot C:
fixmbr
```once you have done this you can reboot and it should get you into windows.

Once in windows you may have a few bad registry entries from the ubuntu install because you did not uninstall it properly. To fix this install ccleaner (free off the internet) and use the add/remove programs part in the tool's section, find the ubuntu/wubi entry and press 'delete' or 'remove entry'. Don't try to run the un-installer as you probably removed it as well.

Once you've done that run the registry cleaner, scan for errors, press fix errors, and then fix all errors. This should get it back to the way it was before.

---

### Post by darkod on 2010-06-10
I think this should help you:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Look in the content, section 4, How do I manually uninstall wubi. I'm not sure but I think deleting the registry key will make the program go away from the Programs list. Since the folder is already deleted, that would be it.

---

### Post by blinkinstantaneous2 on 2010-06-11
I am using vista not XP........thank you.

---

### Post by blinkinstantaneous2 on 2010-06-12
does anyone know how to fix this OS problem that I have.  I said I have vista premium not XP so that you will know right off hand.  Please help with this issue of unable to erase or clear away the Ubuntu OS when I turn on the computer.  I cannot go into Ubuntu OS either as it is one of the option besides Windows.  I would like to be help on this and then maybe try to install Ubuntu Linux again later. HEEEEEEEEEEEEEEEELP!!!!!!!!!!!!!!!!

---

### Post by PRC09 on 2010-06-13
Below are the 2 links that should get you booting Vista again.The first is the link for the recovery disks if you dont have the original Vista disk....




[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

