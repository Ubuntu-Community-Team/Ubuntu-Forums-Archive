---
title: "Upgrade broke my system"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by calande on 2011-05-01
Hello,

I upgraded my system, rebooted and now I get this error message:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190669&stc=1&d=1304265105[/IMG]

Could you help me please?
Thanks,

---

### Post by calande on 2011-05-01
Any idea? :(

---

### Post by Rubi1200 on 2011-05-01
When the computer starts and you see the entry for Ubuntu, press "c" to drop to a prompt and then type this:

```
ls
```

Post back here with what the results are please.

---

### Post by calande on 2011-05-01
Thank you, there you go:

```
dev	lib	etc	sbin	proc	var
root	scripts	init	conf	sys	tmp
```

It seems the /boot directory is missing because it hasn't been mounted...What would you do?
Thanks,

---

### Post by calande on 2011-05-01
I also found that there is no /etc/fstab file...

---

### Post by Rubi1200 on 2011-05-01
Post the results of the boot script please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by calande on 2011-05-01
Thanks, I'm going to have to borrow a DVD drive then...My computer doesn't have one :(

---

### Post by Rubi1200 on 2011-05-01
If your computer is capable of booting from USB you can do it like that instead. In other words, use something like UNetbootin to create a bootable thumb drive, set BIOS to boot from the USB/Removable drive, and then...

---

### Post by calande on 2011-05-01
Good idea, thanks. I'm gonna try that...

---

### Post by calande on 2011-05-02
Ok, I did a fresh install. Running Ubuntu from USB thumb drive works properly, but from the fresh install, I only get a wallpaper, and every 2 seconds, a window pops up for a fraction of a second and disappears. I can hardly see the content. I only have the wallpaper. It seems Ubuntu is trying to display the desktop but cannot. What can I do? Thanks,

---

### Post by Rubi1200 on 2011-05-02
This could be a graphics issue. What graphics card do you have installed and how much RAM?

Have you tried starting with the Classic Desktop and does the problem occur there as well?

---

### Post by calande on 2011-05-02
The [Classic Desktop]("http://www.liberiangeek.net/2011/04/change-classic-ubuntu-desktop-ubuntu-11-04-natty-narwhal/") ? I don't have this option, as I can't go to GDM, I just have my wallpaper, nothing more. Ctrl-Alt-Backspace doesn't work as expected either, as I log in automatically :(

---

