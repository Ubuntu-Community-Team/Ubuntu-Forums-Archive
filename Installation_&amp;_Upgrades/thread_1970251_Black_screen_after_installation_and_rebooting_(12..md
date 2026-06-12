---
title: "Black screen after installation and rebooting (12.04)"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by ubontik on 2012-04-30
Black screen after installation and rebooting (12.04). I can see only white mouse cursor.

Thanks

---

### Post by whatthefunk on 2012-04-30
Try booting in safe mode.  Does that work?

---

### Post by ubontik on 2012-05-01
Yes I was able to boot in recovery mode. But when I tried to restart again in normal mode no changes.

---

### Post by whatthefunk on 2012-05-01
What kind of graphics card do you have?

---

### Post by ubontik on 2012-05-03
Presario F700, NVIDIA nForce

---

### Post by djrose007 on 2012-05-03
I'm quite new to Ubuntu and love the difference.
However, I also have this problem, can't find the graphic card details but in the System Settings I find a reference to NVIDIA.

I've tried using 'Ubuntu with Linux 3.2.9-24-generic' and also same + 'Recovery Mode'. Same as above, reverts to blank screen next reboot.
What does work is if I select 'Previous Linux Version' but you have to do a power reset and start up again to get to this menu.

Is it possible to revert to the previous version of Ubuntu, which seemed to work fine. (11.10 was it?)

---

### Post by whatthefunk on 2012-05-03
> **ubontik said:**
> Presario F700, NVIDIA nForce

Ok, its most likely a graphics card driver issue.

Boot in recovery mode and get into a terminal.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
```

Then reboot.  Should work.

---

### Post by ubontik on 2012-05-05
I reinstalled of USB  stick. The installation completed successfully. I tried to check for additional drivers, selected **recommended. **After rebooting I ran into the same problem.

---

### Post by whatthefunk on 2012-05-05
> **ubontik said:**
> I reinstalled of USB  stick. The installation completed successfully. I tried to check for additional drivers, selected **recommended. **After rebooting I ran into the same problem.

Yes, dont select the recommended driver.  The problem is that the newest nvidia driver doesnt work on many cards.  This is why you have to add the new ppa and install an older driver, as I showed you in my previous posts.

---

### Post by ubontik on 2012-05-08
Thanks alot [whatthefunk]("http://ubuntuforums.org/member.php?u=1202558")

So, I typed in the suggested code, and I got a green dot next to recommended driver. On bottom it says "The driver is activated but not currently in use"

---

