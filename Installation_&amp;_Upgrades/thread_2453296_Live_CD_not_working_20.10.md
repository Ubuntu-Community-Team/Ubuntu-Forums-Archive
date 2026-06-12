---
title: "Live CD not working 20.10"
date: 2020-11-06
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2020-11-06
I had an issue with an upgrade from 20.04 LTS to 20.10, so I thought I would just reinstall over the failed upgrade.  I have a dual boot pc with windows.  

I burned a live cd and after the check it would not load, had to shut down and use the ubuntu basic graphics or something like that.  Went through the install process using the overwrite the existing 20.10.....   then I got an error.

Executing ‘grub-install/dev/sda’ failed
This is a fatal error

So, I burned another disk from the windows side and got the same issue with only loading the live cd with basic graphics....

Any suggestions?

d

---

### Post by claven123 on 2020-11-07
So I ran boot repair....
Did the recommended repair.
It asked me to.
sudo chroot “/mnt/boot-sav/sda6” dpkg —configure -a
sudo chroot “/mnt/boot-sav/sda6” apt-get install -fy
sudo chroot “/mnt/boot-sav/sda6” apt-get purge -y grub*-common shim-signed

I ran the commands, hit forward, then a pop up comes up

GRUB is still present. Please try again.

I have no other options(after trying again)

d

---

### Post by garvinrick4 on 2020-11-09
Will it still boot into Windows? Live CD will boot up and work fine?

---

### Post by ajgreeny on 2020-11-09
So we know what we're dealing with go to Boot-Repair in my signature and follow the instructions to run just the **Boot-Info** script.

**Do not run default repair**,  jus the script and post back here the Pastebin link you get. This should give us many more clues.

---

### Post by sudodus on 2020-11-09
1. Please check with sha256sum that the iso file was downloaded correctly.

2. Please check that you burned the iso file correctly - Did the built-in check finish without errors?

3. Please specify the graphics chip/card: brand name and model.

Maybe you need the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) [FONT=Courier New]**nomodeset**[/FONT] (in the installed system too).

---

