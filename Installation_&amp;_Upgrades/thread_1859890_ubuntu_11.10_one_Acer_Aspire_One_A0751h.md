---
title: "ubuntu 11.10 one Acer Aspire One A0751h"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by prince_of_death on 2011-10-14
Hello everyone, this is my first post and i'm never to linux so any suggestion will be greatly appreciated. I downloaded the new ubuntu 11.10 and created a usb start up disk with unetbootin but when i try to boot from it it flashes some error messages thats a bit too fast for me to read and then it displays a command line mode like the terminal. i can run all my known terminal commands from there but i cant boot to the desktop GUI. can someone please help me.

---

### Post by adam.sullivan on 2011-10-16
Try "startx" which starts X11 (the gui for Linux).

If that doesn't work do: 

```
sudo apt-get update
```

That will try to update your installation and may pick up some missing drivers.

The Acer One has issues with Linux/Ubuntu because tehre are many different machines that Acer decided to name "Acer One" so these are good first steps (I own an "Acer One")

---

### Post by prince_of_death on 2011-10-17
thanks for the advice but i got it to work last night. i did quite a bit of research and got it to work. For anyone that is having this same problem this is what i did:

Step 1: boot from the live usb and as soon as it displays the   ubuntu color screen press 'F6'. this will take u to a boot option page where a pop up bar will appear due to F6 being presses. press 'Esc' key and go up to "try Ubuntu Without Installing" and edit the kernel string to add "poulsbo.asd=1 psb_gfx.asd=1" to the end then press enter.

Step 2: the live usb will then boot to the desktop GUI where you can start the installation.

Step 3: after installation reboot your system and at the GRUB menu press 'e' to edit the first kernel. (this is needed or it wouldn't boot to the desktop GUI)

Step 4: modify the kernel string after 'quiet splash' and add "poulsbo.asd=1 psb_gfx.asd=1" then press 'F10' to boot with the modified kernel

Step 5: it will now boot to the desktop GUI were you will now install the EMGD driver with :-
sudo add-apt-repository ppa:gma500/emgd-1.8
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf
(once the EMGD driver is installed you no longer need to edit the kernel at boot)

Step 6: this step might also be needed to prevent session from not being started.
sudo mv /etc/init/plymouth.conf /etc/init/plyouth.conf.disabled

Step 7: reboot and enyoy


This my first guide EVER.. and i'm still new to linux so i'm sorry i couldn't explain it better for persons that may need help.

---

### Post by Dulio on 2011-10-22
Thank you for the help it finally booted to the desktop got a little confused with the color screen part but then I knew what to do. I used unetbootin by the way.

---

### Post by davuvnik on 2012-02-09
> **prince_of_death said:**
> thanks for the advice but i got it to work last night. i did quite a bit of research and got it to work. For anyone that is having this same problem this is what i did:

Step 1: boot from the live usb and as soon as it displays the   ubuntu color screen press 'F6'. this will take u to a boot option page where a pop up bar will appear due to F6 being presses. press 'Esc' key and go up to "try Ubuntu Without Installing" and edit the kernel string to add "poulsbo.asd=1 psb_gfx.asd=1" to the end then press enter.

Step 2: the live usb will then boot to the desktop GUI where you can start the installation.

Step 3: after installation reboot your system and at the GRUB menu press 'e' to edit the first kernel. (this is needed or it wouldn't boot to the desktop GUI)

Step 4: modify the kernel string after 'quiet splash' and add "poulsbo.asd=1 psb_gfx.asd=1" then press 'F10' to boot with the modified kernel

Step 5: it will now boot to the desktop GUI were you will now install the EMGD driver with :-
sudo add-apt-repository ppa:gma500/emgd-1.8
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf
(once the EMGD driver is installed you no longer need to edit the kernel at boot)

Step 6: this step might also be needed to prevent session from not being started.
sudo mv /etc/init/plymouth.conf /etc/init/plyouth.conf.disabled

Step 7: reboot and enyoy


This my first guide EVER.. and i'm still new to linux so i'm sorry i couldn't explain it better for persons that may need help.

HI sorry for this dumb question but how do I edit the kernel string, I mean, is there a command or something?, the rest seems easy but once I press f6 I don't know what to do.

---

### Post by prince_of_death on 2012-02-14
Oh man i haven't have to do this more than once and i honestly don't know if i can remember right. You said you got as far as pressing "f6" well after you press that key you will be taken to a screen with popup box option. press "Esc" to get rid of the box then press the up or down key till you see the option "try Ubuntu Without Installing" then start typing "poulsbo.asd=1 psb_gfx.asd=1" on the keyboard. it will be added to the end of the string automatically. (i think) then boot the edited string. the option to boot will be displayed.
sorry for the confusing guide. i'm still new to all this. you should also know that there is a updated gma500 driver than EMGD 1.8. we are at EMGD 1.10 now also i heard someone put together a custom ubuntu 11.10 with EMGD 1.8 installed so if you can get that it will be alot easier for you because you wouldn't need all this confusing instructions.

---

