---
title: "Trouble installing Ubuntu using USB"
date: 2017-08-05
forum: Installation &amp; Upgrades
---

### Post by richard7893 on 2017-08-05
I created a USB bootable of Ubuntu 16.04.2 LTS. I am trying to install it on a Toshiba Satellite- A215. I am able to run the USB bootable just fine. I am unable to install it permanently though (I've tried this at least 5 times). What has been happening is that once the installation says it has been completed, a prompt comes up telling me to restart my computer. So I click the button that says to restart the computer at the dialog box. The computer actually never restarts though. It either stays frozen on a screen that says 'Ubuntu' or it goes to a blank screen with blinking cursor that never shuts down or restarts itself. I have to push the power button on the laptop to get off these displays. When I turn the laptop back on and the computer begins to boot-up, I only get a blank screen with a blinking cursor. Does anyone know what to do to fix this? Any help would be appreciated.

---

### Post by TheFu on 2017-08-05
Google found this: [https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)
If yours has a Radeon GPU, that support is problematic after 14.04.

I don't have a toshiba, but I do have a radeon GPU on a system. Rather than fight with it, I turned it into a non-desktop machine. No GUI.  That might not work for you.

There are some things that can be done for the "black screen" after install.  [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by ubfan1 on 2017-08-06
Since you can run the install media successfully, run it and see what video driver is being used:
lshw -C video
That should give you a starting point.  I'd assume the wireless problems have been fixed, since much of the a215 help has been written, so that should not be an issue.

---

### Post by RobGoss on 2017-08-06
What are the specs for your machine it will help in trouble shooting your issue

How does the live USB perform?

---

### Post by BenginM on 2017-08-06
Did you checked the hashes of the live iso image ..[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

did you connected to the internet before the installation ...!

check these steps and try again.

---

### Post by richard7893 on 2017-08-06
Hey all it is working now. I followed the instructions on this website

 [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)
 
I'm having trouble powering off my computer though. I posted this in a separate thread in General Help titled "[COLOR=#000000]Can't power off Ubuntu 16.04.2"  so here goes: 
[/COLOR]
[COLOR=#000000]I have issues whenever I attempt to shut down my computer. Whenever I shut it down (using the GUI), the computer takes me off the main screen to the Ubuntu splash screen with the dots that illuminate one by one. This screen will not go away and the only way to shut down the computer is to hold the power button on the laptop. I do not wish to continue doing this because I am afraid of what it will do to my laptop. I have also tried shutting it down using different commands from the terminal, but I run into the same problem. Does anyone know how to fix this? Should I be worried that my laptop may be damaged if I hold the power button down at the splash screen to turn it off? Any help would be appreciated.

PS How do I change my post so that I will be notified by email of any response I receive? [/COLOR]

---

### Post by RobGoss on 2017-08-06
When creating a new post you should see something like this at the bottom of your post, _**Subscribe to this thread and notify me of change**_ if you click this option you should receive emails when someone responds to your thread

---

### Post by ubfan1 on 2017-08-06
Try the esc key when hung up on the dot screen during shutdown to get to a text screen with possibly errors, or some indication of what's hanging.

---

### Post by richard7893 on 2017-08-06
[COLOR=#000000]I usually select this, but in my initial post I did not so I've been having to check back on the forum for responses. Is there a way to notify me by email of posts made to this thread after the fact?

Also I did try esc on the splash screen, nothing shows though.[/COLOR]

---

### Post by BenginM on 2017-08-06
Go to settings in the top panel , then General settings -> Default Thread Subscription Mode: instantly using e-mail .

---

