---
title: "GeForce 6200 drivers on Lubuntu"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by DaDiRa on 2014-08-19
Hello! I just installed lubuntu on a really old system, and I'm trying to get the native resolution of the monitor, since I'm sure the GPU supports it. I guess what I have to do is dowload the latest GPU's drivers, since the highest resolution I can get from the monitor settings is 1024x768. I googled how to install it, but all the instructions are too complicated for me to follow. Can someone explain me from the very begining how to install the latest drivers?
Thanks in advance.

---

### Post by oldfred on 2014-08-19
Best just to install from repository. And repository should offer the correct legacy driver. Do not install any new one as that may not work.

       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Looks like it should be this one:
[FONT=arial]The 304.xx driver supports the following set of GPUs: [/FONT]

You then should be able to go to system settings, software & updates, and in additional drivers it should show a 304.xxxx driver.

I installed a newer one as my nVidia is 9600GT can current driver still supports that but they announced that 340.xx will be the legacy driver for my card.

---

### Post by DaDiRa on 2014-08-20
Is is okay if I download the .exe file and install through wine?

Edit: I made it the way you suggested. I just don't know which one to choose from the list, since it's not the same as yours.
[IMG]http://i.imgur.com/tQUKEvo.png[/IMG]

---

### Post by DaDiRa on 2014-08-20
I couldn't wait so I installed the first option but the resolution problem isn't solved. I think there is a possibillity that Lubuntu doesn't recognise my motion. Can I do anything about it?

---

### Post by oldfred on 2014-08-20
The 304.xx version should be the correct driver. Did you look on the nVidia site. Second link showed which driver applies to which card.
But update shows two different ones? 
I often install the updates one as that may include some extra fixes.

But uninstall one, before attempting to install another.

I think you have to either restart gui, by logging out and back in, or reboot to make sure it is working.

---

### Post by DaDiRa on 2014-08-20
Dah! I've made a mess again. I tried following this guide, but I messed up and ended up getting a "DOS" version of lubuntu. I followed the instructions at the end of the guide but didn't manage to fix it. I'm pretty sure that the reason I don't get the right resolution is not because of the drivers but because of the screen-OS compabillity. Should I make a new topic about it, or it's okay if you help me here? First of all I need to get out of the black-screen/terminal environment. If not possible, I guess I'm going to format the disk for the 7th time in two days...
 [http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/)

---

### Post by oldfred on 2014-08-20
Are you able to boot with recovery mode?
Should be second line in grub menu. Perhaps sub menu.
If you only have Ubuntu, you do not normally get grub menu, but have to hold shift key from BIOS until menu appears.

Is monitor so old it does not tell system X by Y and other settings it needs?
Then you may have to manual edit xorg.conf, but i have not done that since 2006 or 2007.

---

### Post by DaDiRa on 2014-08-20
I have accessed recovery mode and I have the following menu:
resume
clean dpkg
fsck
grub
network
root
system-summary
I have Lubuntu, by the way.
The monitor is not that old. It's a LG Flatron W1946. Once I have made it out of the blackscreen I will search for the monitor's drivers and if this doesn't work, too. As I said, I'm sure the OS can't detect the monitor because when I run xrandr I got that the maximum resolution is 1024x768, which it totally not true. Also, thanks for the immediate answers. It's really helpfull since I need the PC up and running as soon as possible.

---

### Post by oldfred on 2014-08-20
I have only booted into Lubuntu once or twice.

You may need to enable network, and run updates.
But  if you only can get to terminal then you may have to manually edit xorg.

This will revert you to whatever default it has.
       sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old

 sudo reboot
insert "nomodeset" as a boot kernel switch to be able to boot VESA

Or this:

 copy failsafe to xorg to use vesa as default
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

If then you can only get to command line, you could purge nvidia and reinstall nvidia or just revert to VESA.

OR:
 sudo apt-get install v86d hwinfo
sudo hwinfo --framebuffer
Match available size to monitor size or ratio
If monitor not correctly seen may have to manually update /etc/X11/xorg.conf in order to change the horizontal and vertical refresh rates

I think you also have nano, after backing up current xorg.conf
sudo nano /etc/X11/xorg.conf

---

### Post by DaDiRa on 2014-08-20
But, where I am supposed to write those commands? I get the terminal environment and it requires login. I have no idea what to type there, the password I set isn't working.

---

### Post by oldfred on 2014-08-20
It should be the same password. You do have to log in, if not your live installer, but your actual install.

Did you change password between different installs?
Is caps on or not on?

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by DaDiRa on 2014-08-20
> **oldfred said:**
> 
This will revert you to whatever default it has.
       sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old


Yeah, I had no idea I had to type the username :mad:
Anyway, I typed the command above and I got:
"Cannot stat '/etc/X11/xorg.cong' : No such file or directory"

---

### Post by oldfred on 2014-08-20
When I first typed xorg.conf, I also typed xorg.cong. 
I fortunately never make a typo, but sometimes my fingers do. :)

---

### Post by Jonathan Precise on 2014-08-20
I think xorg.conf does't exist anymore. (At least it doesn't on my system :()

---

### Post by oldfred on 2014-08-20
@Jonathan Precise
You are correct. My system does not have xorg.conf any more either. I knew they wanted to do away with it, but thought defaults & nVidia still used it.

---

### Post by DaDiRa on 2014-08-21
> **oldfred said:**
> When I first typed xorg.conf, I also typed xorg.cong. 
I fortunately never make a typo, but sometimes my fingers do. :)

No, that was a typo when I copied the text from the terminal
[COLOR=#000000]"Cannot stat '/etc/X11/xorg.conf' : No such file or directory"[/COLOR]
This is what I get. I get a similar message about the directory with the other commands do. What should I do? If format is faster I'm going to do it. But after that I'll need to fix the problem with the resolution.

---

### Post by DaDiRa on 2014-08-21
Okay, okay. I have finally made it. I typed the command from the link I sent and it is fixed. Not only the blackscreen, but the resolution as well! I got some system error messages. I hope they don't appear again.

---

