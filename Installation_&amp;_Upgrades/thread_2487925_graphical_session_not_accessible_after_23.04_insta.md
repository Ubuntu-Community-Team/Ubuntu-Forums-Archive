---
title: "graphical session not accessible after 23.04 install"
date: 2023-06-18
forum: Installation &amp; Upgrades
---

### Post by jeanr on 2023-06-18
Hello...

I have installed the 23.04 version without apparent issues. At boot, I have the followed notifications:

```
[ 0.669579] tpm tpm0: [Firmware Bug]:TPM interrupt not working, polling instead
[ 2.352468] nvme nvme0: failed to set APST feature (2)
/dev/nvme0n1p2: clean, 223008/15269888 files, 3558244/61050048 blocks
[ 4.486335]
[ 5.515755] Bluetooth: hci0: Malformed MSFT vendor event: 0x02 
```

Next: login screen is displayed, click on user icon, input password, enter... black screen displayed one moment, then back to login screen. No error message displayed, login is correct. Impossible to open a graphical session.

Then, Alt+Ctrl+F2 to open a terminal session (tty2), terminal session opened, user ok, password ok.

Then for example:

```
$ Thunderbird
Error: no DISPLAY environment variable specified...
```

I use Ubuntu since 2006. But there, I have not yet found a solution. Therefore, I need help !

Sorry for my approximate english, french spoken...

Thank you very much in advance,

Jean

---

### Post by grahammechanical on 2023-06-18
Ubuntu 23.04 and later versions default to using a Wayland session. There may be a conflict with your video driver. Is it a Nvidia video adapter? Is the system using a Nvidia driver or the open source Nouveau driver?

Try this:

At the login screen click the user name but do not enter the password. Click the cog icon that appears at the bottom right of the screen. There should be two options. Ubuntu & Ubuntu on Xorg. The Ubuntu option should be already selected. That is Ubuntu on Wayland. Select Ubuntu on Xorg. Now enter the password and see if that gets you to a working desktop.

If successful you can open Software & Updates>Additional Drivers tab and disable the proprietary driver. If that is the one being used. The open source driver will automatically load.

Regards

---

### Post by jeanr on 2023-06-18
Yes, it worked correctly...
I do not know how to flag this question as solved, please consider it is done
Thank you very much for your help

---

### Post by ajgreeny on 2023-06-18
Go to **Thread Tools** at the top of the thread and choose the 5th option, **Mark this thread as solved.**

---

