---
title: "Can't boot Ubuntu after install"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by Creain on 2010-11-02
Hi there.

I ran the installation from a CD, and the install works just fine. The PC reboots and starts loading Ubuntu. Just after splash screen I login, and then I get the standard background with my mouse cursor. Nothing else happens. I can move the cursor around, but can't do anything and there's nothing to click.
Browsing the forum I see that there is an issue with usernames with capital letters, but there was no such in the installation, though Ubuntu writes the username with the first letter in caps at the login screen.

Anyone know what the problem might be?

EDIT: I might want to add that I'm fairly new to Linux, I do know some of the basic shell commands though.

---

### Post by mörgæs on 2010-11-02
Hi, welcome to the forum.

You might need to add boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by Creain on 2010-11-02
Thank you for the answer. Didnt know about those :)
Since I wrote I tried running it live, but nothing happens there either. I will try the boot options and see if it gets me anywhere.

---

### Post by Creain on 2010-11-02
Tried some boot options, but without luck.
Logged on in safe mode(on it right now) and it all works fine, but still can't logon regularly.

---

### Post by tommcd on 2010-11-02
What version of Ubuntu are you using?
What boot options have you tried?
What video card do you have?
From the live CD, hit F6 when the CD boots, and try the options listed in that grey-colored box that are listed in the tutorial that was linked to in post #2 in this thread. They are listed under "F6" in that tutorial. Try each of the options, one at a time.
You can omit the "*Free software only*" option.

---

### Post by Creain on 2010-11-03
Im using Ubuntu Desktop 10.10.
I tried acpi=off and the one after. The rest I don't know much or anything about, so avoided those for now.
My video card is an ATI Radeon X1900XT.

---

### Post by tommcd on 2010-11-03
> **Creain said:**
> Im using Ubuntu Desktop 10.10.
I tried acpi=off and the one after. The rest I don't know much or anything about, so avoided those for now.
My video card is an ATI Radeon X1900XT.
There is no need to fear using those boot options. They only affect the current boot session, and do not make any permanent changes to the system.
Try using the **nomodeset** option This will disable kernel mode setting. For more info:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
Are you currently trying to boot from the Ubuntu live CD? Or are you booting from the Ubuntu you have installed on your computer?
Also, just to make sure that the Ubuntu CD that you burned is valid, boot up the Ubuntu live CD and run the option "*Check CD for Defects*". If that reports no errors, then the CD is good.

---

### Post by Creain on 2010-11-05
I have checked the CD for errors, and none were reported.
I have been trying to boot both from the CD (live) and from the harddrive. When I select boot from CD it just shows background and nothing happens, when from hdd i get login screen and login, after that i get the background and nothing else.

I will try the other boot options later when I get home.

---

### Post by Hashiru on 2010-11-05
Hi, I have had the same problem with booting from a live cd/usb. Using Plop boot manager solved this for me.

About booting from your harddrive, I honestly don't know how to solve that.

---

