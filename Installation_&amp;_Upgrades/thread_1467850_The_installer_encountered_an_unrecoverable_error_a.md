---
title: "The installer encountered an unrecoverable error and will now reboot"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Sijomo on 2010-05-01
Hi,

I'm installing 10.04 using Wubi, Wubi finishes and asks if I want to reboot, I reboot and select Ubuntu. The installer seems to progress, however later the following pop-up appears

"The installer encountered an unrecoverable error and will now reboot"

Any suggestions?

---

### Post by GJMichels on 2010-05-01
I had the exact same situation occur.  Computer locked up with error mesaage with installer.  Now I'm just waiting for someone to find a work around.

---

### Post by stevehaig on 2010-05-02
I've had this problem too.  I have tried both 64 bit and 32 bit versions with the same problem.  Have had no such probs with any of the releases from 8.04 through to 9.10.

Steve

---

### Post by chouf on 2010-05-03
Same problem here when trying to install Ubuntu 10.04 (with wubi) from Windows 7 on my IBM T43. First phase of the installation goes fine, then after the reboot, I select Ubuntu but get the message "The installer encountered an unrecoverable error and will now reboot".

---

### Post by stevehaig on 2010-05-03
Have just managed to get to a desktop in Safe graphics mode.  Downloaded FGLRX via hardware drivers app.  Rebooted and got the same message again.  I have an ATI 4550 graphics card and wonder if this is the problem.  Managed to get wubi working on my wife's dell 1501 fine.
I did get an icon saying "install 10.04 LTS", will this protect my windows XP installation?  My wife would kill me if it went wrong!

Steve

---

### Post by Sijomo on 2010-05-06
FYI

1) I've previously successfuly installed earlier versions of Ubuntu on this computer using Wubi (none installed at present)

2) I'm using an IBM Thinkpad R52

---

### Post by opendevlite on 2010-05-07
im having the same problem, anyone has a work around with this?

---

### Post by faisu on 2010-05-10
i have same problem...   but i  had rectified ...
boot from CD , enter as live user and try to install from here   your problem will solve..


enjoyyyy


faisu.com

---

### Post by Toast2120 on 2010-05-11
> **faisu said:**
> i have same problem...   but i  had rectified ...
boot from CD , enter as live user and try to install from here   your problem will solve..


enjoyyyy


faisu.com

Having the same problem as stated above, can anyone quote what faisu said as being a possible solution. In the LiveCD now. Got a little bit further than last week as the system just crashed.

Can I install now? Is it safe, or may it screw my boot?

Maybe I should wait another two weeks...:(

---

### Post by thabo on 2010-05-13
Hi guys.
I encountered the same error. I've been using ubuntu for the past 4 years with any problems like it, but 10.04 kept causing this. The problem seemed to be errors with MD5 sum.
After burning 10 different cds without success I unplugged my router and plugged the pc directly into the modem. Downloaded ubuntu and the MD5 sum checked out. Installed without problems. 
Can't explain any of this but it might help someone.

---

### Post by dom96 on 2010-05-13
This might help, [http://ubuntuforums.org/showthread.php?t=1461157]("http://ubuntuforums.org/showthread.php?t=1461157")

---

### Post by dmaksimov on 2010-06-13
I had the same problem... but I hit esc before the ubuntu loaded and selected the acpi workarounds and it worked :)
hope his helps you...

---

### Post by SpotHT on 2010-06-13
Try to burn Ubuntu ISO file with InfraRecorder and install again with Wubi.

---

### Post by majabl on 2010-06-14
> **dmaksimov said:**
> I had the same problem... but I hit esc before the ubuntu loaded and selected the acpi workarounds and it worked :)
hope his helps you...

I want to add that this worked for me too.  The Wubi version of Ubuntu 10.04 is installing on my mother's IBM T42 ThinkPad as I type!

Let's just hope it works fine once installation completes....

Update: yep, no problems!

---

### Post by VanDamage on 2010-07-06
> **majabl said:**
> I want to add that this worked for me too. The Wubi version of Ubuntu 10.04 is installing on my mother's IBM T42 ThinkPad as I type!
 
Let's just hope it works fine once installation completes....
 
Update: yep, no problems!
 
Ubuntu newb here and I was experiencing the same error. This ACPI Workarounds bypass did the trick.
:D

---

### Post by WinRiddance on 2010-07-06
I've found tons of problem messages in several languages all over the internet, having to do directly with Wubi related issues, in particular regarding the installation of 10.04 Lucid. As a result I've never used the Wubi installer, **sticking to a direct installation** either with a bootable ISO CD or a USB stick instead. That would be my suggestion to anyone who's encountered problems with Wubi. Download and burn the ISO file or create a bootable USB stick to install Ubuntu with. I've never encountered any problems doing it that way and the installation is really pretty simple.

---

### Post by FuteballQueen on 2010-10-09
> **dmaksimov said:**
> I had the same problem... but I hit esc before the ubuntu loaded and selected the acpi workarounds and it worked :)
hope his helps you...


Thank you so much for sharing...i've spent like an hour researching on how to solve this issue. And esc then ACPI also worked for me :):guitar:
THANK YOU!

---

