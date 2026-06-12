---
title: "Will Re-installing Windows then back to Ubuntu fix my low graphics problem?"
date: 2014-10-29
forum: Installation &amp; Upgrades
---

### Post by mohamed2 on 2014-10-29
Hello,

I recently had this [error]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error") due to changed permission on my home directory. I followed the steps in the best answer and which seems to work with everybody, except me. I got to where I had to install the ATI drivers from the official website using wget command, I went to a tutorial that allowed me to replace the my existing driver to an older version from recovery mode since I have no access to the terminal. I reboot and I still have no access to the desktop, even after re-installing ubuntu-desktop. I'm not sure if I am doing something wrong or installing the wrong driver or there are conflicting files. 

Another thing I am afraid of is that when I type in CTRL+ALT+F1 to get to terminal, I can't login since I have no permission to access the user directory (initial cause of all problems). If someone can help me debug my progress, I would be more than grateful.  

So I was thinking if re-installing Windows will fix the graphics problem, and then I try installing Ubuntu again? If you suggest I must stay with the solution link I provided, please help me go through the steps...

Thanks!

---

### Post by grahammechanical on 2014-10-29
Why would re-installing Windows fix a problem in Ubuntu? What it would most certainly do is prevent you from loading Ubuntu. The install of Windows would put the Windows boot loader in charge of the boot loading process and the Windows boot loader will not accept the existence of Ubuntu.

From what you have stated, the problem of loading into failsafe X mode was "due to changed permission on my home folder." I do not think that re-installing a graphic driver would fix that. If the problem was caused by changed permissions on the home folder then fixing the permissions problem was the way to go.

From my experience, the easiest way to fix some difficult problems is to re-install Ubuntu. Think about it. Plan to back up your data.

Regards.

---

### Post by Frogs Hair on 2014-10-29
Reinstalling the other operating system will not likely repair any Ubuntu problems . I wouldn't suggest installing proprietary drivers from the web site due to problems like you are now having.My experience is with nVidia and Intel so you may have to wait for a user more familiar with AMD graphics. When using tutorials make sure they are applicable to Ubuntu version in use.

---

### Post by mohamed2 on 2014-10-29
> **grahammechanical said:**
> Why would re-installing Windows fix a problem in Ubuntu? What it would most certainly do is prevent you from loading Ubuntu. The install of Windows would put the Windows boot loader in charge of the boot loading process and the Windows boot loader will not accept the existence of Ubuntu.

From what you have stated, the problem of loading into failsafe X mode was "due to changed permission on my home folder." I do not think that re-installing a graphic driver would fix that. If the problem was caused by changed permissions on the home folder then fixing the permissions problem was the way to go.

From my experience, the easiest way to fix some difficult problems is to re-install Ubuntu. Think about it. Plan to back up your data.

Regards.

I tried the re-install ubuntu-desktop command then reboot, but the low graphics problem is still occurring and I have no access to the GUI and when trying to the login to my user folder, I am not allowed. I will try re-setting the permissions - if there was no graphics problem then I wouldn't get the error I provided in the link.

Thanks anyway.

---

### Post by mohamed2 on 2014-10-29
> **Frogs Hair said:**
> Reinstalling the other operating system will not likely repair any Ubuntu problems . I wouldn't suggest installing proprietary from the web site due to problems like you are now having.My experience is with nVidia and Intel so you may have to wait for a user more familiar with AMD graphics. When using tutorials make sure they are applicable to Ubuntu version in use.

I agree with the tutorials part. However, it seems many users are having the link I provided useful to them. I just want someone more experienced with this problem or Ubuntu to walk me through or provide me with a reasonable solution. I don't want to try installing different things on top of each other..but thanks for your advice.

---

### Post by ian-weisser on 2014-10-29
You misunderstood grammechanical

> **grahammechanical said:**
> the easiest way to fix some difficult problems is to re-install Ubuntu. Think about it.

> **mohamed2 said:**
> I tried the re-install ubuntu-desktop command then reboot, but the low graphics problem is still occurring

He meant a complete reinstall from whatever install media you originally used.
Merely reinstalling the desktop metapackage almost certainly wouldn't impact your problem. The AskUbuntu thread had this as one possible answer, so it's understandable that you tried it. No (additional) harm done.

If you want your system restored quickly and without further troubleshooting, a reinstall is in your future. Do be careful not to erase Windows or your data when you do that.

If you want to learn about your system and spend time troubleshooting, the go through a couple more solutions in the AskUbuntu question.

---

