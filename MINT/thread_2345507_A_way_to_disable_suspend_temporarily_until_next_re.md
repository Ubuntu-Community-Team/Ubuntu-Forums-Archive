---
title: "A way to disable suspend temporarily until next reboot"
date: 2016-12-04
forum: MINT
---

### Post by John_Throw on 2016-12-04
I have a misbehaving usb controller it seems. Everything works fine except when its returned back to the host after running a virtual machine suspend will fail (screen will go black, but the fans stay on and you can't get out of it). This only happens if a keyboard is plugged in to the usb controller that is passed through to the VM. I'm not having much luck getting suspend to work. I've tried different USB controllers, different keyboards.

I like having suspend. But the VM isn't run that often. I'd like to turn suspend off temporarily in a script (so that I don't forget to do it) and then run that script to start the VM instead. But I can't figure out how to do this from the command line. Anyone know how I might accomplish this?

Solution:
This command changes the sleep timer on cinnamon:
gsettings set org.cinnamon.settings-daemon.plugins.power sleep-inactive-ac-timeout '0'
I reset to my desired value upon using the startup actions menu.
In ubuntu I believe the command uses gnome in place of cinnamon.

I'm using Linux Mint 18.

---

### Post by ajgreeny on 2016-12-05
What version of Ubuntu (or other DE version) are you using.

You may need to simply open the power-manager and stop the suspend option from running which should be possible from the config file for whatever power-manager you use.
In Xubuntu 16.04 which I use the config file is .config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml and mine reads

```
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xfce4-power-manager" version="1.0">
  <property name="xfce4-power-manager" type="empty">
    <property name="power-button-action" type="uint" value="3"/>
    <property name="show-tray-icon" type="int" value="1"/>
    <property name="logind-handle-lid-switch" type="bool" value="true"/>
    <property name="lock-screen-suspend-hibernate" type="bool" value="false"/>
    <property name="blank-on-ac" type="int" value="30"/>
    <property name="blank-on-battery" type="empty"/>
    <property name="dpms-enabled" type="bool" value="true"/>
    <property name="dpms-on-ac-sleep" type="uint" value="31"/>
    <property name="dpms-on-ac-off" type="uint" value="32"/>
    <property name="dpms-on-battery-sleep" type="int" value="5"/>
    <property name="dpms-on-battery-off" type="int" value="10"/>
    <property name="inactivity-on-ac" type="uint" value="150"/>
    <property name="general-notification" type="bool" value="false"/>
    <property name="hibernate-button-action" type="uint" value="2"/>
    <property name="sleep-button-action" type="uint" value="1"/>
    <property name="brightness-on-ac" type="uint" value="30"/>
    <property name="brightness-level-on-ac" type="uint" value="60"/>
    <property name="spin-down-on-ac" type="bool" value="true"/>
    [COLOR="#FF0000"]<property name="dpms-sleep-mode" type="string" value="suspend"/>[/COLOR]
    <property name="brightness-switch-restore-on-exit" type="int" value="-1"/>
    <property name="brightness-switch" type="int" value="0"/>
    <property name="presentation-mode" type="bool" value="false"/>
  </property>
</channel>
```
I think a script to edit the line shown above in red, and change suspend to nothing, would be able to do what you want, but I do not know **sed** well enough to tell you how to do that. The manual may help you so try that.

---

### Post by John_Throw on 2016-12-05
I'm using linux mint 18, cinnamon.

---

### Post by howefield on 2016-12-05
Moved to the "*MINT*" forum.

---

