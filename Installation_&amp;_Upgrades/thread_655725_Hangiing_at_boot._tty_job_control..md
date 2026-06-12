---
title: "Hangiing at boot. tty job control."
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by TerabyteUK on 2008-01-01
I installed (finished installing with no problems) ubuntu via network install. (I don't have a CD drive)
I went to boot up my new installation

If I try to boot, the boot seems to hang at the very first orange bar.
If I try the 'recovery' option in grub, I get the error whos solution is here:

[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

It isn't  clear what has to be done from that post as they seem to refer to a live CD.

What exactly should I do in my situation.

There are 2 entries in grub, the first one (to boot ubuntu 704 normally), and the other, which brings up a load of text amongst which I saw that error message at the end.

After the message appears, some sort of debian prompt appears.

Any help appreciated.

---

### Post by Partyboi2 on 2008-01-01
When you get to the grub menu where you highlight recovery, instead of pressing "enter" press "e" to edit then highlight the line that starts with "kernel" then press "e" again then at the end of the line add break=top then press "enter" then "b" to boot. when you get to the command prompt type:
```
modprobe piix
```then "exit"
If this was successfully then when your desktop has finished loading open up a terminal (Applications>Accessories>Terminal)
then open up /etc/initramfs-tools/modules
```
gksudo gedit /etc/initramfs-tools/modules
```add 
```
piix
```then save and back in the terminal type
```
 sudo update-initramfs -u
```Reboot
Hope it works :)

---

### Post by TerabyteUK on 2008-01-01
ahar!

During that, I never got a desktop, I got a root command promt, but I carried out the instrucitons and used pico instead of gkedit.

Now, when I try to start ubuntu normally I get "Failed to start the X server (your grpahics interface). It is likely that it is not set up correctly. Would you like to view th ex server ouptut ot diagrnose the problem?"

In a grey box with blue background

(==) log file "/var/log/x...............
(==) using confi...
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

---

### Post by Partyboi2 on 2008-01-01
When that happens try logining into a terminal (Ctrl+Alt+F1-F6)
then try reconfiguring xserver.
```
sudo dpkg-reconfigure xserver-xorg
```If you haven't done it before, it can look pretty daunting, but its pretty simple. Just  read what you are being prompted to do and if unsure choose the default setting which is the option that it displays first.
Also what video card have you got?

---

### Post by TerabyteUK on 2008-01-02
yes, a bit of fiddling after installing the intel drivers
(see post here: [http://ubuntuforums.org/showthread.php?p=4056099#post4056099](http://ubuntuforums.org/showthread.php?p=4056099#post4056099) )

it did work!

---

