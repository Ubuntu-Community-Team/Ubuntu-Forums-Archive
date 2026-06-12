---
title: "installed ubuntu, computer always boots windows 7"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by chris272 on 2014-08-03
Hello,
I am quite excited about trying out ubuntu. I installed it on my hard drive. It said installation succesfull, and that I had to reboot. When my computer booted, it went straight to windows. I understand that i need a grub bootloader. I made a boot repair disk, but that does not run. Was i supposed to extract the .iso before i burned it? Sorry, im a noob. Here is my partition screenshot.

<Base64 code removed>

---

### Post by chris272 on 2014-08-03
wow, it showed my screenshot when i attempted to post. i don't know why that text explosion happened.

---

### Post by chris272 on 2014-08-03
[ATTACH=CONFIG]255231[/ATTACH]

---

### Post by Doxie on 2014-08-03
There is a way to set up Ubuntu to switch back between Windows and Linux through a boot menu, one that was suppose to come in default on the ISO. No need to apologize, Ubuntu doesn't have the smoothest of installation processes compared to Windows CD installations and it can be quiet easy to get stuck because of it lol. 

When you were installing, did you select for a partial installation of Ubuntu, or as the default OS?

---

### Post by chris272 on 2014-08-03
i don't recall seeing that option. I just now managed to install boot-repair while operating from live usb. I ran it, clicked reccomended repair, and rebooted. Now grub screen pops up and i can run ubuntu from hard disk. I guess that means problem solved! Thanks, so much, for the quick reply!

---

### Post by coffeecat on 2014-08-03
> **chris272 said:**
> wow, it showed my screenshot when i attempted to post. i don't know why that text explosion happened.

You probably triggered a firefox bug by dragging and dropping an image into the message editor. Vbulletin doesn't support drag and drop for images and other browsers handle the problem more gracefully. I see that you've managed to use the vbulletin attachment manager for your image in a subsequent post. I've edited out the base64 code from your post.

Good luck!

---

### Post by Bucky Ball on 2014-08-03
Reboot the computer and try hitting the Shift key at boot. That should bring up a grub screen so you can select your OS.

If not, try Boot Repair again. You can boot and install using a Live Ubuntu boot. Here's how:

Use BR:
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

When creating the CD like you have, no, you don't extract the ISO first. Something else must have gone wrong. You need to burn a disk image using the ISO, not a data disk. Just a tip in case that's the problem.

---

