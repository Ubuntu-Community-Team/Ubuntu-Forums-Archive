---
title: "Trouble upgrading from 16.04 to 18.04 - GUI crashed"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by texpat on 2018-09-16
During the upgrade the screen went black because that's what its supposed to do after no input is received from keyboard or mouse for a set time. Problem is, I can't get the GUI back. Somehow it seems the graphics won't come back on. If I move the mouse I can see it briefly flickering over the otherwise black screen but I cant use it. I can also not get a tty using CTRL + ALT + Fx.

I *can*, however ssh into the machine, so my hope is someone might help me use a command that resets the graphics without resetting the whole computer. I tried issuing a 'reboot' which it tells me it won't do because the machine is in process of being updated (I could force this, but I'd rather not). I assume the upgrade is stuck waiting for user input via mouse/keyboard - "replace current config or use the old one" sort of thing.

I greatly appreciate any hints as to how to get the graphics back without interrupting the upgrading process, if that is possible. This is on Xubuntu.

Thanks for reading.
Tx

---

### Post by texpat on 2018-09-17
Solved this by issuing ```
sudo service lightdm restart
``` over ssh.

---

