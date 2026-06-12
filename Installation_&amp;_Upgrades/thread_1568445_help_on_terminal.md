---
title: "help on terminal"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by esphera on 2010-09-05
HI!

Bear in mind that I'm a complete novice on Linux, and forgive me for not having patience if this kind of thing is already discussed on the forums.

OK. I want to install some things and after some research some people say to open terminal and use sudo apt-get ... but terminal asks me for a password, but i can type anything! I don't know if this is a bug or...

Please help!

Thanks

---

### Post by presence1960 on 2010-09-05
> **esphera said:**
> HI!

Bear in mind that I'm a complete novice on Linux, and forgive me for not having patience if this kind of thing is already discussed on the forums.

OK. I want to install some things and after some research some people say to open terminal and use sudo apt-get ... but terminal asks me for a password, but i can type anything! I don't know if this is a bug or...

Please help!

Thanks

The typing of your password is not visible in the terminal. Just go ahead and type your password on the keyboard and hit Enter.

To install the software package homebank you would type in terminal ```
sudo apt-get install homebank
```

---

### Post by esphera on 2010-09-05
thanks! :) that makes sense... other thing... i'm getting the boot screen on a very low resolution.... i had it sorted when i first booted ubuntu but now its messed up... any thing i can do to restore that lovely boot screen with my monitor highest definition?

thanks!

---

### Post by dirghrabadia on 2010-09-05
On the top left, go to System-->Places-->Monitors and change the resolution from there.

---

### Post by krimzonstarr on 2010-09-05
In order the change the resolution of the bootloader/GRUB screen, some CLI work is the best way. I will walk you through it.

1. Open a terminal and type
```
gksu gedit /etc/default/grub
```

2. Once the editor and file opens, find lines resembling these
> # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

3. Delete the # in front of the line GRUB_GFXMODE=. Edit the resolution to your desired values.

4. Save and close gEdit.

5. In a terminal, run the following command to update your bootloader
```
sudo update-grub2
```

Hope that helps. There is also a very well written guide to modifying your GRUB settings: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

