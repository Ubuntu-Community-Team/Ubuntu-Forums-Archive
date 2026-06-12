---
title: "Update breaks Ubuntu 13.10"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by acidblue on 2013-11-19
I did a fresh install of 13.10 recently with no problems, but today I did an update and after a re-boot I get a blank screen with a blinking cursor.
The keyboard is not working and I cant get to a command prompt.

I am using an older Nvida 8400GS video card, I dont know if the update changed the driver. 

What do I do now???

EDIT:
After poking around I discoverd I am using the nvidia-173 driver which is the same driver i was using before the update, so I dont think thats the problem.
I think the problem lies with "lighdm", I am able to get to the grub screen and choose Ubuntu to boot, but everything goes black when it gets to the login screen(lightdm).

Ive tried "safe mode" am abie to get to a root command prompt, but thats about it, it just wont go into a 'safe graphical mode'.

Is there a way to disable lightdm???
I have tried 'service lightdm" start and stop, but get an error, 'service not available' or somthing like that.

I would try to uninstall lightdm and re-install it but I cant get my network to work. there is an option for it in safe mode but it's not working, like I said i can 
only get a root command prompt, how do i enable wireless networking from the CLI??

---

