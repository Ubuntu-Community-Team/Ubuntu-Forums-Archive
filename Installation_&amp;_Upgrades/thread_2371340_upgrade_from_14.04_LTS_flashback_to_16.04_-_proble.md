---
title: "upgrade from 14.04 LTS flashback to 16.04 - problems, possible solutions"
date: 2017-09-13
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2017-09-13
Hello,

recently I upgraded my ubuntu box from 14.04 LTS flashback mode to 16.04. The upgrade went smoothly.

At first reboot the flashback mode was not selected, so I had to do so.

In the meantime I faced some issues which I will post here along with solutions if available:

1) window decorations
in order to change it to a more light colored version the following command was provided:
```
gsettings set org.gnome.metacity theme Radiance
```
I could not change it from Applications->System Tools->Preferences->Tweak Tool->Appearance (window option is not there)

2) Adobe reader was installed prior to upgrade and is still visible under Applications->Office, yet I could not choose it as an application for pdf files. In order to do so I typed:
```
sudo gedit /etc/gnome/defaults.list
```
and in the search box I typed:
> pdf
and the first result was:
> application/pdf=evince.desktop
which I changed to:
> application/pdf=AdobeReader.desktop
this also made it the default application

3) Alt+Shift change language indicator applet
still no solution to this one - even though I can change languages I cannot see the change in the applet

4) bluetooth is enabled at startup, yet it is not deactivated
still no solution to this one

5) power off panel button has no option for reboot
still no solution to this one

6) plymouth theme
in order to change the text ubuntu logo into something more fancy I did the following:
from synaptic I installed plymouth-themes and then typed the commands:
```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/solar/solar.plymouth 100
sudo update-alternatives --config default.plymouth
(chose theme)
sudo update-initramfs -u
```
when shutting down everything is as normal. During boot up I cannot see the splash

7) boot time is longer than before

Regards!

---

### Post by Claus7 on 2017-09-13
Hello,

> **Claus7 said:**
> 

5) power off panel button has no option for reboot

Indicator applet complete has reboot option

> **Claus7 said:**
> 
6) plymouth theme
During boot up I cannot see the splash

with 2nd boot splash is ok

Regards!

---

### Post by Claus7 on 2017-09-13
Hello,

> **Claus7 said:**
> 
4) bluetooth is enabled at startup, yet it is not deactivated


the solution [here]("https://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup/696226#696226") did not work.

Instead I followed both answers mentioned [here]("https://askubuntu.com/questions/744640/best-way-to-deactivate-bluetooth-on-system-startup-with-systemd-and-not-upstar") which were:

```
sudo systemctl stop bluetooth.service
sudo systemctl disable bluetooth.service
sudo systemctl status bluetooth.service
```

and

```
gsettings set org.blueman.plugins.powermanager auto-power-on false
```

[EDIT]
In order to make bluetooth working as before I did the following:
1) I added 
/etc/init.d/bluetooth start
to the /etc/rc.local file (before exit 0 line)
2) I have the blueman-applet command enabled at startup applications

Every time the system boots I can see the applet on top of my panel and when I turn bluetooth on, I can send files to my devices. Only step (2) didn't allow me to send files to my devices (options were grayed out). 
[EDIT] 

Regards!

---

### Post by Claus7 on 2017-09-14
Hello,

> **Claus7 said:**
> 
3) Alt+Shift change language indicator applet


actually this is not solved, yet bypassed, since I have seen that it is a bug and no solution from dconf-editor seems to work. 

I opened synaptic and installed gxkb.
Then, I edited the file .config/gxkb/gxkb.cfg
from: layouts=us,ru
to the desired layout (layouts=us,gr), for your own check also /usr/share/gxkb/flags

In order to work I logged out and back in.
In case we do not have to issue the command every time we start the computer then I went to Applications->System Tools->Preferences->Startup Applications and added the gxkb command. Alt+shift is working as normal.

EDIT
I came across this thread: [https://ubuntuforums.org/showthread.php?t=2183739](https://ubuntuforums.org/showthread.php?t=2183739), which had exactly the same problem as mine.
I was able to overcome the issue by disabling NumLock before editing the shortcut keys. NumLock seems to be Mod2 button.
Then I went to:
Applications->System Tools->System Settings->Keyboard->Shortcuts->Typing
and
the Switch to next group is: Alt+Next Group (this is displayed if pressed Alt+Shift)
the Switch to previous group is: Shift+Next Group (this is displayed if pressed Shift+Alt)
for the very first attempts I had to press first Alt or Shift and then Shift or Alt to change language. After a little while, things were working as normal, without caring which button was pressed first.
EDIT

Regards!

---

