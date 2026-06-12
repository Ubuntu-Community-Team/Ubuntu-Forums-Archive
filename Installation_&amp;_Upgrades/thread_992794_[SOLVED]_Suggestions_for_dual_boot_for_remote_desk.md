---
title: "[SOLVED] Suggestions for dual boot for remote desktop"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by cyberfin on 2008-11-25
I hope someone can pitch in to tell me if I'm on the right track for this.

Basically I would like to make a dual boot with my normal ubuntu installation and another one for a different ubuntu installation (I've yet to decide on exactly which version/flavor)

As a main pointer, my current install is used for work, and therefore has to remain as unaltered as possible. I've obviously thought of creating another user, etc. for the other installation, but as it will involve some level of experimenting I want to completely rule out the "human mistake factor", taking me to the conclusion of making a separate install on another hd all together and set it up as a dual boot.

So far, no mystery. But as the title suggests, I also need to access remotely to both desktops. So, my thought was to go ahead with the two installs but my doubt was on how to be able to boot into one desktop or the other as this is a selection made from the grub menu upon boot.

I came to think of making a script that would comment/uncomment either install from the grub list while logged in to one of the desktops. That way, when giving the reboot command, the other install would would be booted, and I could access remotely again to the alternate desktop.

Am I on the right track, or is there a simpler way of doing this?

Thank you for your input.

EDIT: Just want to point out that I don't need a complicated dual boot option with windows/linux solutions, as some threads suggest; this is for two ubuntu boots and I therefore assume has a prettier solution. (I hope/whish/pray/believe)

---

### Post by cyberfin on 2008-11-26
*bump Anyone, please?

---

### Post by Zack McCool on 2008-11-26
Why not the simplest of options...   Since you plan to use this remotely, simply install VirtualBox, and install a second copy of Ubuntu (for your personal use) in a Virtual Machine.  This will allow you to access either version without constant reboots...

If that is unworkable for some reason, the next best option would be to have 2 copies of menu.lst, each already set up for a particular defaiult, and before you reboot you can simply copy the one you want into /boot/grub/

---

### Post by cyberfin on 2008-11-26
Thanks for the reply Zack.

I have already installed ubuntu ultimate edition with virtualbox, but the fact is I need a proper install tu use the graphics card and the processor. I like the idea of the menu.lst but would love if someone could tell me if there is any way of making a script to either exchange two versions of the menu.lst or if there is a way of commenting/uncommenting the necessary lines in the file.

I know I might be being picky, but I think this might be interesting for more than one user out there, and would also be useful for any future installs.

Again, thanks for any input.

---

### Post by Zack McCool on 2008-11-26
The impression I got was that you were planning on using this remotely, which would mean that you wouldn't get the advantage of the video card's acceleration features...

As to writing a script to swap the file, sure.  You can write a script to do anything you could do manually at the terminal shell.

For instance, let's say you want to have 2 versions to boot to.  We'll keep them in /home/user and the names will be menu.personal and menu.work.  Configure those as needed.

Now, you need 2 scripts for reboot.  Let's call them rebootpersonal and rebootwork.

```

#!/bin/bash
# rebootpersonal
# Reboot the PC with the personal use copy of Ubuntu
sudo cp /home/user/menu.personal /boot/grub/menu.lst
sudo reboot

```

```

#!/bin/bash
# rebootwork
# Reboot the PC with the work use copy of Ubuntu
sudo cp /home/user/menu.work /boot/grub/menu.lst
sudo reboot

```

make both of those scripts executable: ```
 chmod +x /home/user/reboot* 
```

Now, to run them, type /home/user/rebootpersonal to reboot to your personal copy.  To streamline that a bit, either add an alias for the command, or add the directory you keep the scripts in to your path.

If you just reboot without running a script, the system will boot the same as it did the last time you rebooted.

---

### Post by cyberfin on 2008-11-26
Fabulous, this is exactly what I was looking for. As for the remote/local access, I use both more or less equally, therefore I prefer a proper install.

Thanks again.

---

### Post by Zack McCool on 2008-11-27
No problem.  I am glad to help whenever I can...

---

