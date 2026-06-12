---
title: "Installing dapper flight 6 - mouse and grub problems"
date: 2006-04-21
forum: Installation &amp; Upgrades
---

### Post by rjs on 2006-04-21
G'day all,

My gf has an old computer made out of left over bits and pieces. She just got a nano and her box isn't new enough to use XP so she can't install iTunes. I said her iPod would work under linux. So we installed dapper (kubuntu) flight 6 (keeping the windows 98 partition) and it seemed to go all right but then when we rebooted all it would say is grub error 17 which google told us meant that grub cannot mount selected partition. After a few hit and misses we managed to restore the master boot record (thankyou sys rescue CD). So the first question is any ideas what we could do here? Searching on here and google brought up the idea of fidling with the BIOS to change the primary master from auto to LBA. Unfortunatley this didn't seem to help. We only had one 88gb HD with a ~30gb windows fat32 partition, a linux partition and a swap partition (presumably after sys rescue we only now have the windows partition). Elsewhere i have seen people say that we should look at grub.conf or boot/grub/menu.lst. How do we look at these if we can't load into linux because of the grub error? Can we do this with a liveCD or with sys rescue?
 
Anyway, next part of the story is that we dicided to use the liveCD to put stuff onto the iPod. The only way that i know how to do that is using amarok so we managed to mount the windows filesystem under /c but when we went into KDE we discovered the mouse wasn't working (nor was the ethernet but i think i have worked out how to fix that one). Now it is not impossible to use KDE without the mouse but it is darn hard, and we didn't manage to get the music from the computer to the nano. The mouse is a serial mouse and under windows is COM1 but that is about all i can tell. I seem to have found a lot of stuff on the net about microsoft intellimoise (and clones) and i'm not entirely sure what that is, but every search for serial mouse seems to bring that up. Any ideas how to find out more about the mouse? or ideas on how to get it to work?

I've never had any serious problems with Linux and was just starting to feel like i was understanding it. :( Oh well, if i figure this out both me and my gf will have learnt something new :)

Thanks,
-rjs.

---

### Post by jpkotta on 2006-04-21
You can use either the live CD or the install CD.  

For the install CD, select the option to rescue existing system.  Choose the partition that you installed to, and pick "execute shell in selected partition".  It will be as if you are in the installed system.

For the live CD, open a terminal and do this 
```
sudo su
mount /dev/hda1 /mnt
chroot /mnt

```
and like the above, you will be in the installed system.  Clearly, change the device to match the partition you installed to.

Once you're in the installed system, you can do things like edit /boot/grub/menu.lst.  ```
nano /boot/grub/menu.lst
```
To reinstall grub to the MBR, ```
update-grub
```

For mouse trouble, you would edit /etc/X11/xorg.conf.  Most mouse troubles I've had were fixed by specifying the correct mouse device.  For example, my mouse comes up on both /dev/psaux and /dev/input/mice on my laptop.  You can tell if the mouse is using a particular device if you do something like```
cat /dev/psaux
```and move the mouse around.  If you get gibberish, then the mouse is attached to that device file.

> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection


---

### Post by rjs on 2006-04-21
Thanks for the tips with grub, they sound good; i'll try them as soon as i can. Sorry i don't think i explained myself very well in my first question in regards to the mouse. I knew that i had to edit xorg.conf what i am not sure of is what to edit it to because i don't know how to find out about the mouse or even if i did, i don't know the relevent things i need to find out. The mouse works under windows 98 but i can't see it discribe the mouse anywhere (other than to say it's on COM1) and physically i can only tell that it is a two button serial mouse. Do i need to know anything other than wheather it is a serial/PS/2/USB mouse? There are a lot of fields in the mouse section of xorg.conf what else might i need to edit?

Thanks,
-rjs.

---

### Post by jpkotta on 2006-04-21
I've never used a serial mouse in Linux, but I'll guarantee that it will work.  The question is how to configure it.  

Try googling "serial mouse linux", I found a howto that seems to be what you want.

Another thing to look at is gpm.  It's a mouse driver for the linux console.  If you install it, it might automatically detect the mouse.  You can use the configuration of gpm to give clues to how to set up X.

---

### Post by rjs on 2006-04-21
Thanks. I tried that already and got confused, a second reading of the howto made slightly more sense. I guess i'll just have to cross my fingers and hope.

-rjs.

---

