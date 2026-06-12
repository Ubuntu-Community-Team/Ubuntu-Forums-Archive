---
title: "Ubuntu Live only boots with nomodeset?"
date: 2018-12-27
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2018-12-27
I have been trying to use 'Try Ubuntu without installing' from a USB containing 16.10, but when I do the screen just stays on but black, apart from 3 or 4 distorted coloured lines across the top. To get beyond this I have edited the grub options to include nomodeset.

This let's me into Ubuntu Live, but there is some distortion, for instance, if I go into the power settings to turn off the blank screen option, sometimes I will have to move my cursor to different parts of the screen before that part of the window actually loads. Also, the reason I am in the power settings at all, is that once the screen turns off, I cannot get back into Ubuntu Live, so if I am doing long operations like

```
dd if=/dev/urandom of=/dev/sda bs=1M
```

...the screen will put itself asleep. I have been able to manage so far, but now I want to use hdpram to securely erase and SSD, which is 'frozen', and one suggested way to resolve this is to put your system to sleep and wake it - but I cannot wake Ubuntu Live.

Is there something I can try, perhaps different options from nomodeset?

---

### Post by Bashing-om on 2018-12-27
dusf; Well ...

1) 16.10 is End_Of_life and has no support - the software repo no longer exists.
2) The boot parameter 'nomodeset' defeats Kernel Mode Setting and thus one can expect ACPI issues.
3) Depending on what the graphic's chip set is, maybe install a proprietary video driver (once a supported release is at hand).

[INDENT]it is what it is
[INDENT][INDENT]and ain't what it ain't
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2018-12-27
Run the command in a console session instead
Just run something like ctrl + alt + F2 and enter the username ubuntu and hit Enter.
The live session user runs passwordless.

you can set it to boot in text mode as well, though it's a liitle convoluted because of systemd now:
[https://askubuntu.com/questions/943696/boot-without-gui-from-live-cd]("https://askubuntu.com/questions/943696/boot-without-gui-from-live-cd")

---

