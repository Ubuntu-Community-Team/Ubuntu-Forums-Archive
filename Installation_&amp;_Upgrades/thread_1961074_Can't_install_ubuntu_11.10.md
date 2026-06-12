---
title: "Can't install ubuntu 11.10"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by killer0ne on 2012-04-18
I have tried to instll ubuntu on my old laptop running win 7 for a week now, but all of my attepts have been unsuccessful so far. I have never used it before so it is very new to me. I have burned 2 discs with different isos and both didn't even get to the installer. First time i saw the installer was with unetbootin and the it showed some error about my cdrom not being able to unmount. I even bought a 4gb usb to install with livelinux and that gave me the same error. My old laptop has an intel 945 motherboard. Please help.

---

### Post by javierc on 2012-04-18
some computer have it so that a virus can't write to the boot sector, the side effect is that you can't install a operating system.

so go to your BIOS and see if that option is there, to disable it

---

### Post by codemaniac on 2012-04-18
Hello killer0ne,
Welcome to the UbuntuForums .!

Cannot you just go ahead with the Unetbootin installer , it should give you a option like install ubuntu in its menu .
Intel 945 is compatible with Linux , so there should be no issues with the chipset and all .

---

### Post by killer0ne on 2012-04-18
> **codemaniac said:**
> Hello killer0ne,
Welcome to the UbuntuForums .!

Cannot you just go ahead with the Unetbootin installer , it should give you a option like install ubuntu in its menu .
Intel 945 is compatible with Linux , so there should be no issues with the chipset and all .

when i use unetbootin installer it gives me the cannot unmount cdrom or something like that and then it just won't install.


> **javierc said:**
> some computer have it so that a virus can't write to the boot sector, the side effect is that you can't install a operating system.

so go to your BIOS and see if that option is there, to disable it

i have installed win 7 on it 2 times(before it had vista), so that's not the issue.

---

### Post by codemaniac on 2012-04-18
Can you post the exact error message you are having ?
That would help shooting the trouble .

---

### Post by killer0ne on 2012-04-18
[http://imageshack.us/photo/my-images/815/img1310p.jpg/](http://imageshack.us/photo/my-images/815/img1310p.jpg/)

that's the error

---

### Post by codemaniac on 2012-04-18
By any chance seems like your both installation media(cd rom and usb) trying to mount at the same place . :/

---

### Post by killer0ne on 2012-04-18
the error message is from when i was trying to install with unetbootin

---

### Post by codemaniac on 2012-04-18
Are you using sanDisk flash drives , they are known for some issues in U3 Launckpad .See the Ubuntu usb install known issues .Still i feel that somehow both your media's are trying to mount at the same placeholder (/CDROM) .

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by lisanels47 on 2012-04-18
What version of Linux?  Try a ubuntu 11.10 install on a flash drive.  I've never seen the screen you have in the message.

---

### Post by tmaranets on 2012-04-18
Try a liveCD. Your motherboard should be suitable for Linux.

---

### Post by killer0ne on 2012-04-19
I am trying to install 11.10. I don't think it's the flash drive's problem(it's a kingston), because i get the same error when trying to install with unetbootin. But after my first attept to install with my usb it just would't boot afterwards. I'll try to install using a cd again.

---

### Post by codemaniac on 2012-04-19
KillerOne , last thing you should check if kingston comes with some pre installed autorun programs like in sandisk .If so you need to remove them .

A snippet from the link i have shared with you earlier .the link below(known issues section) .
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

"Natty Narwhal 11.04 is having issues with USB flash drives from SanDisk that have U3 Launchpad. You can either use another brand or use either u3-tool from Ubuntu Repositories or SanDisk's U3 Launchpad Removal Tool to remove U3."

---

### Post by killer0ne on 2012-04-19
The issue is still the cdrom, even when trying to install with the kingston flash drive and with unetbootin.

---

### Post by killer0ne on 2012-04-21
I installed an older version 10.10 and then upgraded to 11.10 but it crashes after boot. yay another problem

---

