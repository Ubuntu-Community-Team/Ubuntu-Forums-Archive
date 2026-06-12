---
title: "Upgrade hangs at setting up landscape-common"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by michaelharg on 2008-11-01
I have been trying to upgrade to 8.10, everything was going fine then the upgrade tool has stopped on "setting up landscape-common"

I have tried ctrl-c and that brought up a message saying canceling could leave the system in a broken state so I haven't proceeded.

What should I do??

Thanks

---

### Post by prshah on 2008-11-01
> **michaelharg said:**
> I have been trying to upgrade to 8.10, everything was going fine then the upgrade tool has stopped on "setting up landscape-common"

Check through the other virtual desktops to see if a dialog box is waiting for your input. Sometime, the upgrade / update seems stalled, but actually it has popped up a dialog box on another virtual desktop, and will not proceed until that dialog box is attended to. Typical symptoms include window responsiveness (eg, window can be moved around) but it will not accept focus, and clicking on it seems to produce no effect.

---

### Post by michaelharg on 2008-11-01
I tried all that, no windows on any other virtual desktop. What will happen if I ctrl-c out? All my stuffs backed up, should I just reinstall a'fresh? Not a very stable upgrade route though :(.

Thanks

---

### Post by Vex on 2008-11-01
I've got the same problem, peforming an upgrade, and almost complete, but now it's stuck on:

'Setting up landscape-common (1.0.23-0ubuntu0.8.10.1) ...'

---

### Post by prshah on 2008-11-01
> **michaelharg said:**
> I tried all that, no windows on any other virtual desktop. What will happen if I ctrl-c out? All my stuffs backed up, should I just reinstall a'fresh? Not a very stable upgrade route though :(.


Well, I had an [interrupted Hardy upgrade]("http://ubuntuforums.org/showthread.php?t=780531"), but it recovered beautifully, I assume Intrepid will be the same. Feel free to review the thread and see if it is for you... warning; it's not for the faint of heart, but definately worth a try before reinstallation.

---

### Post by Vex on 2008-11-02
Well, I just killed the landscape-common processes that were running, which then allowed the upgrade to continue. It complained about not having configured landscape-common properly, but the upgrade did eventually complete, and it seems to be working nicely.

---

### Post by pinkunicorn on 2008-11-09
Same thing happened to me as well on a Thinkpad that I am upgrading from 7.10 through 8.04 to 8.10. After killing four processes that seemed to be related to landscape-common, the upgrade continues its slow way forward.

---

### Post by LNCPapa on 2009-04-24
This worked perfectly for me as well - upgrading from Intrepid to Jaunty had the same issues.  Killing the processes (multiple times) finally allowed the installation to proceed.  Thanks guys.

---

