---
title: "Unity won't launch after 12.10 installation"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by Mogen317 on 2012-10-26
Hi,

After a new installation of 12.10 on a Lenovo x120e and a restart the Unity shell won't launch.

Installation of 12.10 amd64 yesterday went well.  I turned the computer off for the night and when I turned it on this morning I was presented with the login screen.  When I enter the password the screen flashes black and returns to the login screen.  I'm using the right password because if I enter an incorrect one a message in red font tells me so and the login screen remains.

If I choose guest access the computer brings me to the desktop but without the unity shell.  A right click will bring up the New Folder, Change Desktop, etc. menu.  Ctrl-Alt-T will open terminal.  I tried "sudo xinit --:1" but I can't use sudo on a guest account.

Any ideas?

---

### Post by dino99 on 2012-10-26
Boot on recovery mode (hold "shift" key down at bios end process)

Run this in terminal   ```
/usr/lib/nux/unity_support_test-*p
```

 it will test your hardware, make sure there is a YES in unity 3d support

---

### Post by Frogs Hair on 2012-10-26
If you have support for Unity and terminal access try the following. ```
setsid unity
```

---

