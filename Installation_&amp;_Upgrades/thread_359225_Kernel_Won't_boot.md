---
title: "Kernel Won't boot"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by pardasaniman on 2007-02-11
Hello everyone.  I'm trying to give a new life to my 166mhz computer as a VOIP phone.  

I installed the ubuntu-server setup, but right after installing, and rebooting, it hangs after the message "starting up ..." .  This happens when I try to load the "recovery mode" option as well.  

Where should I go from here?

---

### Post by mr.v. on 2007-02-12
It sounds like your computer is likely using some pretty old hardware. It's possible that there's some kind of bizarre  hardware conflict that requires legacy support. I hate to say it, but you may want to try a distribution that uses a 2.4.X kernel (slackware or damn small linux come to mind). Damn Small Linux is less than 50MB, is incredibly fast, and has decent extensions (and will most likely run VoIP decently). It's a touch hard to configure DamnSmallLinux at first, but the community is pretty helpful. You may want to try that since it has a live-CD that is identical to the boot image so you'll know if you can boot with it. Slackware's also fast but not the most user-friendly.

---

### Post by pardasaniman on 2007-02-12
Thank you Mr.V .

I think I may end up doing exactly that.  Although this computer has booted kernel 2.6 before.

---

