---
title: "Ubiquity not create user"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by bradley51253 on 2016-05-21
[COLOR=#111111][FONT=Ubuntu]I create my own distro for school computer and everything is good but ubiquity installer not create user :/
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I try to edit casper.conf file and lightdm but it doesn't help me ;/
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Maybe my live user is badly create or group/privilages is bad. After installation Live user not delete and new user from form in ubiquity not created.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I run files from /usr/lib/ubiquity/user-setup/ nothing execute.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My code to create live users:

```
[/FONT][/COLOR]
adduser liveuser
adduser liveuser sudo
adduser liveuser admin
sudo usermod -aG sudo liveuser
usermod -s /bin/bash liveuser
chmod 555 /etc/hostname
chmod 555 /etc/hosts
chown liveuser:liveuser -R /home/liveuser
[COLOR=#111111][FONT=Ubuntu][FONT=Consolas]echo "%liveuser ALL=(ALL) ALL" >> /etc/sudoers
[/FONT][/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]And casper.conf file shows like:
[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Consolas]USERNAME=liveuser[/FONT][/COLOR]
USERFULLNAME="Live session user"
HOST=live
 [COLOR=#111111][FONT=Consolas]BUILD_SYSTEM=Custom
[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Ubuntu]Additionally: The line HOST=live must be equal file hostname?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Can you help me to repair ubiquity user create ?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks :)[/FONT][/COLOR]

---

### Post by dpaulat on 2016-05-21
The live user should only be applicable when running from the LiveCD.  Have you rebooted from the hard drive?

---

### Post by grahammechanical on 2016-05-21
Are you using the OEM installation method?

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

> **System Restart**
After rebooting the system you will automatically log in with the temporary oem user.
[B]
Configuration[/B]
Now you can install additional software, drivers or configure the system as desired. When you're done doing that click on the **Prepare for shipping to end user** icon on the desktop.This removes the *oem* user on next boot. 

**End User's First Boot**

 Once  the computer was shipped to the end user and he finally boots for the  first time he will be taken to the system setup wizard where he will be  able to set his location, keyboard layout, user name etc. 




---

### Post by bradley51253 on 2016-05-22
> **grahammechanical said:**
> Are you using the OEM installation method?

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)


No, I'm not using this method because at first i need run live version.


Boot option which I try:

#1
```


label SchoolSystem
menu label SchoolSystem
menu default
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper


```

#2
```


label SchoolSystem
menu label SchoolSystem
menu default
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper  config quiet

```


#3
```


label SchoolSystem
menu label SchoolSystem
menu default
kernel /casper/vmlinuz
append boot=casper persistent initrd=/casper/initrd.lz quiet splash 

```

#4
```


label SchoolSystem
menu label SchoolSystem
menu default
kernel /casper/vmlinuz
append boot=casper noprompt  ignore_uuid initrd=/casper/initrd.lz quiet splash ---

```

#5
```


label SchoolSystem
menu label SchoolSystem
menu default
kernel /casper/vmlinuz
append boot=casper initrd=/casper/initrd.lz quiet splash ---

```


Any of this options not add user and not delete old (live) user after install :(

---

### Post by bradley51253 on 2016-05-22
Does anyone have any idea?  :)

---

### Post by bradley51253 on 2016-05-23
help :confused:

---

### Post by danjde on 2017-01-24
> **bradley51253 said:**
>  [..]

Any of this options not add user and not delete old (live) user after install :(

Hello Bradley,

I am in your same situation, with my own Ubuntu Gnome remix, Xenial based (for the previous Trusty based, the user creation works fine, but here I've used only JLivecd..)

Now (for the Xenial remix) I left from an Ubuntu Gnome iso and I've edit it using [Cubic]("https://launchpad.net/cubic") and then using [JLivecd]("https://github.com/neurobin/JLIVECD")
and now all works fine except for the Ubiquity user creation process.

Using Cubic I've made as you a custom user and delete the old "ubuntu-gnome" user and using JLivecd added new software and manually customized initrd.lz

I've ask to the Cubic team for a suggestion, without any reply and many time for any other questions to AskUbuntu without never never any answer/help.
I've write to some Ubuntu Live developer (also on Ubuntu Gnome mailing list), without never any reply.

My previous release was based on Fedora and then I remember that there was a greater collaboration with the developers. Just with "Ubuntu environment" I'm noticing a strange omerta.



In conclusion I still don't know how to fix the Ubiquity user creation problem, but if you want we can exchange our emails and keep in touch for future mutual help, which you don't get easily, how to see ...

ciao!

---

