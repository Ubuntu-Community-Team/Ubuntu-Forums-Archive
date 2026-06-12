---
title: "Can`t Login after Nvidia Driver Update"
date: 2017-01-21
forum: Installation &amp; Upgrades
---

### Post by besi1 on 2017-01-21
Hello, if I have the nvidia driver in ubuntu 16.0.4.1 LTS via the driver manager and then restart I can not log into the system anymore I am always thrown back into the login window although the password is correct??

This is a bug and the error is longer known wiso do not fix the developer of ubuntu it can forward one to the developers ???

---

### Post by Bashing-om on 2017-01-21
besi1; Hello;

> **besi1 said:**
> Hello, if I have the nvidia driver in ubuntu 16.0.4.1 LTS via the driver manager and then restart I can not log into the system anymore I am always thrown back into the login window although the password is correct??

This is a bug and the error is longer known wiso do not fix the developer of ubuntu it can forward one to the developers ???

At the login screen use key combo ctl+alt+F1 to activate a console interface . Here enter your credentials - username and password ( no response to the screen when pass word is entered ) to log into the system.

Post back - Between code tags - the outputs of terminal command:
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
As a place to begin the problem isolation procedures .

[INDENT][INDENT]let there be light
[/INDENT][/INDENT]

---

### Post by efflandt on 2017-01-21
Besides Ubuntu version (which you did include) you should always state what graphics hardware you have (Nvidia chip or output of at least lspci related to graphics) and which nvidia driver package you are using. By "driver manager" do you mean "Additional Drivers"?

If you have a newer Nvidia card/chip (10xx series) and you need a newer driver than provided in standard repos, before using "Additional Drivers" you can add the graphics-drivers ppa:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```But if you have fairly old nvidia graphics, you may actually need an older driver.

---

### Post by johnstefnds on 2017-01-21
I faced the exact same problem which lead me destroying grub.... please help me I opened a topic here [https://ubuntuforums.org/forumdisplay.php?f=333](https://ubuntuforums.org/forumdisplay.php?f=333)

---

