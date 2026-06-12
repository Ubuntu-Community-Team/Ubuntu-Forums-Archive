---
title: "Slow boot time after trial boot installation"
date: 2019-09-28
forum: Installation &amp; Upgrades
---

### Post by gioisco on 2019-09-28
I had Ubuntu 18.04 LTS in dual boot with Windows 10. It worked fine.

Today I installed Debian 10 without bootloader and I gave in Ubuntu
```
sudo update grub
```
to detect and make Debian bootable.

After Debian boot, I reboot again in Ubuntu and it was very slow: more then 2 min! Before Debian installation, the time boot was abaut 30 seconds.

What can I do? :(

---

### Post by Dennis N on 2019-09-28
1) I would want to see if it happens again when I reboot the computer. 
2) I would press escape key during boot to exit the splash screen and see if any message related to the slowdown appears: systemd might have a start job running that delays your boot - often set with 90 seconds time delay. It will display a message beginning with: "A start job is running..."; or a message might say it is waiting for something - find out what.

---

### Post by gioisco on 2019-09-28
1) it happens again :(
2) if I press esc during boot, I see only a black screen :(((

Is there a way to see splash log after boot?

---

### Post by Dennis N on 2019-09-28
>  if I press esc during boot, I see only a black screen
Bummer. Looks like they've got some code now to prevent the ESC trick working*. After login, you can use terminal and type **dmesg** to see some kernel startup messages, or **journalctl -b** to see systemd journal of most recent boot. Look for any large time delays between lines in the output (which is long!).
--------------------------------------------------------------------------------------------------
*An alternate method to see boot messages was to select Ubuntu in grub menu, press 'e' to edit, and remove 'quiet splash' from the line starting with linux, then F10 to boot - this also failed on mine to display any messages - just a blank screen, then login screen.

There is a console mode that should display messages** on boot, but as an ordinary user, I've actually never used it myself, so can offer no advice on this. Read here (OLD, but may still be accurate):
[http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/](http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04/)

**not sure messages will be any different than the other commands - may not be too useful to do this.

---

### Post by gioisco on 2019-10-02
I finded my issue with **journalctl -b**.
Debian changed the UUID of swap partition and Ubuntu failed to start it, after waiting timeout.
Thanks :)

---

