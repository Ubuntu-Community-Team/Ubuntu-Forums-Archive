---
title: "After installation, machine boots to a black screen"
date: 2016-11-27
forum: Installation &amp; Upgrades
---

### Post by testarosa16 on 2016-11-27
Hi all
I have an old Fujitsu siemens L1310G laptop. I've tried to install Lubuntu 16.04. After what seemed to be a successful install I rebooted the laptop and now it just boots to a black screen. There doesn't seem to be any hard drive activity, the hdd led doesn't flicker. I can boot into recovery mode though.

Where do I go from here? I'm new to installing linux os so please give easy to follow instruction. Thanks in advance :D

---

### Post by Bashing-om on 2016-11-27
testarosa16; Hello; Welcome to the forum .


With a wired internet connection !

There are a number of ways we can gain access to the system, Here maybe the easiest and more direct for your use case .

Let us "suppose" that there is no graphic's driver available and try and install a driver.
Boot into that recovery console ; and choose "enable networking" .
Next is to gain a terminal;
select the "root" terminal .
On this interface execute:
```

mount -o remount,rw /

```
to remount the operating system read and write to be able to execute:
```

ubuntu-drivers autoinstall

```
where it is hoped the system will install the appropriate driver .

execute:
```

reboot

```

And we see what happens .

[INDENT][INDENT]all good now ?
[/INDENT][/INDENT]

---

### Post by WEPrechaun on 2016-11-27
Hello. Running Xubuntu 16.04LTS 64bit on an old HP 6735s laptop with a similar issue. However, mine doesn't always boot properly. It'll start fine, WiFi light changes from orange to blue back to orange, CAPS lock light goes solid, then booting seems to stall. Thoughts? Thank you.

---

### Post by Bashing-om on 2016-11-27
WEPrechaun; Hey;

You should start your own thread as the causation can be from any number of reasons on your issue.

Might get some hints if ya boot to terminal ( at the login screen ctl+alt+F1) . and see what it takes to start the GUI from terminal.

[INDENT][INDENT]when all else looks bleak
[INDENT][INDENT][INDENT]terminal time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

