---
title: "A few problems with my new install of ubuntu"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by jhhoward on 2006-08-24
I just installed kubuntu 6.06 on my laptop, a Zepto Znote 6214W laptop. ([http://uk.zepto.com/]("http://uk.zepto.com/"))

I had a few gripes with that I had to run up the install in safe graphics mode, but it seemed to be ok after installation.

I managed to get widescreen display resolution with nvidia drivers working, and the wireless networking seems to be working ok. I've installed all the necessary updates and used easyubuntu to install my codecs and drivers needed for playing MP3s, DVDs etc.

However, I have a few minor issues. Firstly, the GRUB bootloader shows two lots of the same ubuntu build (This is the only linux install I've done on this laptop). From what I can tell it shows the standard ubuntu boot, the safe boot, the standard boot again, the safe boot again, then the command shell boot, and then my copy of XP.

It isn't a big deal but I was wondering if there is any difference between them.

I had another problem where after starting ubuntu, the system kept freezing for about half a second every few seconds. The mouse pointer would freeze, but the more annoying thing was that whilst the system was frozen for the half a second, you couldn't type on the keyboard properly. If you pressed a key down just before a freeze, then after it unfroze it would be as if you had held the key down for the length of the freeze. This made it almost impossible to sudo anything as entering a password was so difficult.

This problem has mysteriously disappeared after I chose one of the other boot options. I suspected it might have been the video driver as it happened shortly after installing the nvidia drivers. However, the problem still occured in the 'command shell only' boot option.

Another problem is that the session switching has disappeared. When I first installed, you could switch session with ctrl+alt+f1/f2/f3/f4/f5/f6/f7

However, now when I do a switch, there is just a blank screen rather than a login prompt. When I shut down before, I think the screen used to go to a verbose type of mode which output all the shut down messages. Now it is just a blank screen.

It would be really useful to get the session switching back up, just so that I can do things in another terminal if I need to (e.g. kill the xserver or reboot if there is a major problem)

The GRUB bootloader is a bit messy with multiple instances of the same boot. I suspect I need to just edit the config file, but I'm not sure where I would find this.

Also, is there any way of doing power management on the CPU (I have Intel Duo Core processors) when I am running off the battery? In XP, it usually turns off one of the cores when running off the battery.

One last question, is there a more friendly interface for switching between wireless networks? I have found the only way is to go to Administration->Networking, entering the root password, going to wireless eth1, properties, and looking at the drop down box. This is a pain as I have to enter the root password whenever I want to switch networks which isn't ideal. I'm pretty sure it doesn't connect without opening this control panel as well.

Thanks in advance for any help or suggestions,

James

---

### Post by Scythe!? on 2006-08-24
The GRUB is not incorrect. As you updated your new install, you may have installed a updated kernel too. GRUB displays the kernels available, so if you kernel breaks, you have a spare and useable Ubuntu to fix the problem. I have limited my GRUB to show a max of 2 kernels, so I dont have lots of kernels on the menu. To do this type ```
sudo gedit /boot/grub/menu.lst
``` in the terminal.
Now scroll down until you see ```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2
```
as you can see, at the bottom of the code you see # howmany=2 this limits GRUB to display 2 Linux kernels.

---

