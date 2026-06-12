---
title: "Grub Failed Boot Detection after Reboot Ubuntu Minimal"
date: 2021-05-05
forum: Installation &amp; Upgrades
---

### Post by acdhemtos on 2021-05-05
I installed Ubuntu minimal (from [http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/mini.iso)). Install was on only disk. And also no dual boot.

After booting in I logged in (not as root) and then rebooted. No problem in rebooting. I log in again and run :
sudo apt-get install i3 gnome-terminal pulseaudio

Now, after reboot, I was greeted with a blinking cursor, on pressing F12 it started showing logs. It was scrolling fast. But last 2 logs, before screen froze, were something along the lines :
grub failed boot detection

And was returned to a non-blinking cursor.

I have tried installing it again but still same result.

Please help. Thanks.

---

### Post by grahammechanical on 2021-05-05
Please change the link you have given. Clicking on it opens a download dialog box. I was just curious as to what exactly you downloaded. I had no wish to download it myself

Regards

---

### Post by acdhemtos on 2021-05-05
Sorry. Got the link from : [https://askubuntu.com/a/1233750](https://askubuntu.com/a/1233750)

---

### Post by grahammechanical on 2021-05-05
This then is the link to the download page of the 20.04 mini ISO image

[http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/)

As to the original problem I do not know what to make of it. To boot after the install and then fail to boot when re-boot is very strange. And then to repeat the problem with another install attempt. It is hard to work out what is going wrong. It is a few years since I tried the mini ISO image. 

Can you run a standard Ubuntu live session? If so then try this command:

```
sudo grub-install /dev/sda
```

And see if that improves things.

Regards

---

### Post by acdhemtos on 2021-05-13
I found the issue (kinda).

When I install gnome-terminal the list of dependencies is huge. And is not so big if I install VLC afterwards. But if i reverse the order of installation(in a fresh install) opposite happens.
My assumptions is that there were some files required for both packages which don't come with Ubuntu Minimal and installing them somehow overwrote grub files.

Running command along with following solved the issue and rebooted successfully.

```
sudo update-grub
```

Thanks for the help.

---

