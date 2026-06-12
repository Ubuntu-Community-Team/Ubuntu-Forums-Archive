---
title: "Ubuntu 10.4.1 Blank Screen Noob help!"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by jetaddict on 2011-02-12
Hey all, first time poster and Linux noob here. I have searched this and many other forums looking to resolve this issue; to no avail. Maybe someone has a solution:
I have an old HP s7600n slimline running an AMD64 and Nvidia card. It was running Windows, and I opted to install Ubuntu after having no issues with the install in my old Emachines. After finally determining I needed to run it with nomodeset at the main screen, the install screen comes up and everything runs smoothly. Here is where the issues begin. Upon reboot, the screen immediately goes blank. I can't get into GRUB (as other posted solutions suggest) after reboot to alter the proper command lines to eliminate this problem. I ran Ubuntu from the disk, and tried to install the required Nvidia drivers first, then went back and rebooted: no luck. I re-installed it and again, no luck. I altered the command line on the main CD screen (the one where you can select install, run from CD, etc.) and eliminated "quiet splash" and replaced it with nomodeset as well-zippo. 
Since you are speaking to a total Linux noob here, any help anyone can give me would be awesome. If there is a way I can get into GRUB and fix this issue so it works on the reboot after my install, I think I'd be in business, but the whole thing just reverts back to the default I guess. I have already erased the hard drive and replaced it with Ubuntu, so I am pretty much screwed. I guess I should have tested it before I started. It worked so flawlessly on my other computer, I guess I ASSumed it would be OK.:(
Thanks in advance!

---

### Post by Rubi1200 on 2011-02-13
Hi and welcome to the forums :-)

After installing on first reboot, as the computer boots hold down Shift to bring up the GRUB menu.

When the entry for Ubuntu is highlighted, press "e" to edit. Use the same procedure as before and remove quiet splash and use nomodeset, then "Ctrl" + "x" to boot.

In Ubuntu, install the requisite drivers.

---

### Post by jetaddict on 2011-02-13
You are the man....amazing. After researching this for almost 3 days now, this was the first thing that actually worked. Thank you! 
I'll install the drivers now, and see if it works on reboot. I already tried rebooting it once, and it blank screened on me- is there a way to PERMANENTLY alter the command line so it stays in NOMODESET?

---

### Post by Rubi1200 on 2011-02-13
If the drivers install, assuming no issues, then you won't/shouldn't need to set any permanent parameters.

However, if that does not work, here is what to do:

boot again as per the previous instructions

go to Applications > Accessories > Terminal

run this command:

```
 gksudo gedit /etc/default/grub
```find this line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"change to look like this:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"Save and then run this command:
```
sudo update-grub
```That's it, no need to set parameters at boot time again.

---

### Post by jetaddict on 2011-02-13
Worked like a charm. Once the driver was in, I was able to reboot with no issues. Thank you again!

---

### Post by Rubi1200 on 2011-02-13
No problem, you are more than welcome :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

