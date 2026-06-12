---
title: "Authentication Problem After Sudo Command"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by here4help on 2012-08-24
I just updated the Ubuntu OS 10.04 (linux-image-2.6.32-42) on my system and in trying to issue a sudo command in the Terminal Application, I could not proceed further as keystrokes got frozen when I tried to key-in my password as required.

What could have happen and how can I resolve this?

Another issue that, infact,  happened during my earlier upgrade before the last two (or 3 - just can't) remember is: my Windows Headers/Titles in the GRUB booting list were inter-changed. Initially, they were in this order as the last two lines:
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

The first one (dev/sda1) was the main Windows loader whilst the second one was the Recovery Drive. These have inter-changed as follows:
Windows  Recovery Environment (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

The first of these is still the main windows loader eventhough it carries the title Recovery Environment, whereas the last line (Windows Vista (loader)) is now rather the recovery drive in real terms.

How can I get these resolved?

Thanks for any assistance you may provide.

---

### Post by deadflowr on 2012-08-24
What happens when you type a simple command like sudo apt-get update, and then blindly enter your password. If upon entering the password and pressing enter the update process runs, this is normal. Running a sudo command doesn't show the keystrokes of the password.

For part two what does it look like when you run:

```
sudo update-grub
```

You can copy and paste the output using the Code # tags in the reply box.

---

### Post by here4help on 2012-08-24
> **deadflowr said:**
> What happens when you type a simple command like sudo apt-get update, and then blindly enter your password. If upon entering the password and pressing enter the update process runs, this is normal. Running a sudo command doesn't show the keystrokes of the password.

Wow, I was rather expecting keystrokes as I have been so used to. Thanks a million.

> **deadflowr said:**
> For part two what does it look like when you run:

```
sudo update-grub
```You can copy and paste the output using the Code # tags in the reply box.

There was no change as far as this is concerned.

Is there a way I can change the titles/headings in the /etc.grub.d?

---

### Post by here4help on 2012-09-19
> **here4help said:**
> Another issue that, infact,  happened during my earlier upgrade before the last two (or 3 - just can't) remember is: my Windows Headers/Titles in the GRUB booting list were inter-changed. Initially, they were in this order as the last two lines:
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

The first one (dev/sda1) was the main Windows loader whilst the second one was the Recovery Drive. These have inter-changed as follows:
Windows  Recovery Environment (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

The first of these is still the main windows loader eventhough it carries the title Recovery Environment, whereas the last line (Windows Vista (loader)) is now rather the recovery drive in real terms.

How can I get these resolved?

Thanks for any assistance you may provide.

Can anyone help me out with this?

---

### Post by darkod on 2012-09-19
Open /boot/grub/grub.cfg and copy those two titles in /etc/grub.d/40_custom.

Change the titles as you want them to be in the 40_custom file. Change only the title names, not the other commands.

Disable the auto OS prober with:
sudo chmod -x /etc/grub.d/30_os-prober

Recreate new grub.cfg with:
sudo update-grub

They should still be at the end in the new grub menu, but with the edited titles.

---

### Post by grahammechanical on 2012-09-19
I use a great little utility called Grub Customizer to keep my boot loader menu in order as well as other things.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

Regards.

---

