---
title: "Help – usb 3 fails to run, but usb 2 works fine"
date: 2017-12-19
forum: Installation &amp; Upgrades
---

### Post by masterbel2 on 2017-12-19
I have a 32gb usb 3.0 which I wish to install and run ubuntu on. I've tried using the command line and using Etcher for the process (as outlined here: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx) And here: [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick?_ga=2.46038628.1572343202.1513643177-123091299.1511907198](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick?_ga=2.46038628.1572343202.1513643177-123091299.1511907198))

EDIT: I'm trying to install ubuntu-16.04.3-desktop-amd64.iso on a 2015 MacBook Pro

The error I'm getting is as follows:
```

usb 2-1: device not accepting address 2, error -62
usb 2-1: device not accepting address 3, error -62
usb 2-1: device not accepting address 4, error -71
usb 2-1: device not accepting address 5, error -71
usb usb2-port 1: unable to enumerate USB device


BusyBox v1.22.1 (ubuntu 1:1.22.0-15 ubuntu 1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(unitframs) Unable to find a medium containing a live file system

```

After this it just hangs.

((There may be errors my reproduction of the error, I had to write it out by hand and then reboot the computer to send this))

When I tried to do this on a 4gb usb 2 it worked fine, but the storage capacity and speed are far too slow for my liking. 


If it's at all relevant, I also tried to install ElementaryOS using the same process with exactly the same results. Any ideas? I can't find anyone else having this same problem, no one else seems to have trouble with usb 3.0

((also if someone can enlighten me how to link words that would be muchly appreciated))

---

### Post by TheFu on 2017-12-19
Not all USB3 ports/chips are compatible with all USB3 devices, especially when booting.  Try different USB3 storage.  I wish I could say that brand-X worked, always, but IME, cheap works just as well as name brand flash drives.  It is a complete crap-shoot as to which will or will not work with any specific machine.  I have some USB3 devices that work everywhere, except on my laptop.  Of course, the laptop is where I need them to boot.  The other places, I don't.

---

### Post by masterbel2 on 2017-12-20
Okay, I'm a little annoyed because I bought the usb for the purpose, but if it's the hardware at fault nothing much I can do?
Thanks for the reply :)

---

