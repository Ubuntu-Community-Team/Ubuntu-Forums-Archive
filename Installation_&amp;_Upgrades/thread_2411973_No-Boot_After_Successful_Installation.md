---
title: "No-Boot After Successful Installation"
date: 2019-02-06
forum: Installation &amp; Upgrades
---

### Post by farwest2 on 2019-02-06
**Summary**: No-Boot After Successful Installation.

**Issues:** "Reboot and select proper Boot device" error and frozen Unetbootin screen preventing me using the computer. 

**Solved (Edited): **USB Preparation is very crucial. I had prepared by trusting to UNetbootin and it was spoiling files in USB, therefore it was not installing files in Boot partition correctly which was resulting failed boot. 
This time I prepared USB with Etcher, reinstalled, this time it successfully booted the computer and Kubuntu works. 

 **Info:** I am a new Ubuntu user (started with Kubuntu), trying to establish Kubuntu on computer without Windows. Computer is i7 version of Asus N53SN which is a little old, therefore no Secureboot, it had Win7 before I delete it. 

**Story:**
After following Manuals, Guides carefully, I successfully installed Kubuntu 18.04. 
After the very first installation, it booted well and I was able to use and experience Kubuntu first time.

When I tried to install and download multiple programs, Kubuntu got frozen. So I wanted to restart the computer manually. Then, I received Initframs errors after that point. I solved it by reopening UEFI and reinstalling with USB again. 

However every time I boot, I start to get "Reboot and select proper Boot device" errors afterwards. 

In order to solve this error, I re-arranged Boot order by putting "ubuntu" to top. Didn't work. I put Harddrive to top, no success. I closed UEFI totally and tried all those, no success again. Reopened UEFI and tried again, no success. 
When UEFI is open, booting by plugging USB, I see a different screen than "Reboot and select proper Boot device" error:
1-If USB is on top, Grub2 screen to install Kubuntu.
2-If USB is on below while "ubuntu" or "Harddrive" are on top, Unetbootin screen is seen. 

By approaching with number (1), I made Bootrepair with "Recommended-Repair", booted, received same "Reboot and.." error again with all the above steps tried. 

Then I tried booting with Unetbootin screen (2), it makes booting by letting me see Kubuntu opening window, but after, screen gets frozen with this screen that you can see in picture in the attachment. Then it waits like forever as a frozen screen. I am able to reboot by Ctrl+Alt+Del from that screen after.

I browsed internet and couldn't find a solution for me or maybe didn't understand well due to my inexperience/illiteracy with suggested commands or terminology. 

Therefore I would like to get your consultation, I hope I can fix this and say goodbye to Windows permanently. Thanks.

---

