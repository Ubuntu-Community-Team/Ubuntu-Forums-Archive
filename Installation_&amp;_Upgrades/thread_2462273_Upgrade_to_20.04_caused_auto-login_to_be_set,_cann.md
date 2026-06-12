---
title: "Upgrade to 20.04 caused auto-login to be set, cannot change desktop env"
date: 2021-05-17
forum: Installation &amp; Upgrades
---

### Post by dhfx on 2021-05-17
[INDENT] 					About a month ago I successfully (or so I thought) upgraded Ubuntu 18.04 with (separately-installed) LXDE to  20.04. Subsequently I accepted an "upgrade" requiring a reboot, and  when I rebooted I found that auto-login had somehow been enabled, bypassing the login screen which offers a choice of desktop session types.

I have since (in a previous thread) learned that the LXDE that I installed under 18.04 is not compatible with 20.04, so I purged it (as much of it as I could) and installed XFCE - anything to get away from the default Gnome desktop. But without the login screen I have no way of switching to an XFCE session.

My user account (GUI) does not show auto-login enabled. So what I want to do is find a way to either (1) disable auto-login from the command line, or (2) set the default desktop environment from the command line, by editing the appropriate config file.

Any suggestions will be appreciated.
[/INDENT]

---

### Post by Xian on 2021-05-18
Can you run the command below so we can confirm your display manger:

$ cat /etc/X11/default-display-manager

For example:

```
cat /etc/X11/default-display-manager
/usr/sbin/lightdm

```

---

### Post by dhfx on 2021-05-19
$ cat /etc/X11/default-display-manager
/usr/sbin/gdm3

---

### Post by deadflowr on 2021-05-19
Check /etc/gdm3/custom.conf.
You should have entries for 
```
AutomaticLoginEnable=True
AutomaticLogin=username
```
either remove those or add a # symbol to the front of them to disable.
(Or edit it and change True to False)

Then try reloading gdm 
```
sudo systemctl restart gdm3
```
and see if it stays on the login screen  long enough to switch desktops.

---

### Post by dhfx on 2021-05-27
Apologies for delay in responding. I looked at /etc/gdm3/custom.conf, and it has both of the AutomaticLogin lines, and BOTH are commented out.
Edited /etc/gdm3/custom.conf to uncomment & set
     AutomaticLoginEnable=False
and ran cmd
   sudo systemctl restart gdm3
Cmd had no effect. Rebooting also showed no change in behavior.

Anyone have any further suggestions?

---

### Post by deadflowr on 2021-05-27
Switch display managers.
install another like lightdm then reconfigure the system to use that one
Try
```
sudo apt install lightdm
```
then run
```
sudo dpkg-reconfigure gdm3
```
it will show entries for all installed display managers.
select/highlight lightdm and select Ok

Then reboot.
If done properly you will have Ubuntu's old unity-greeter.
The sessions can be selected by clicking on the icon in the username login box's top right corner.
(The default icon should be Ubuntu's logo)

---

