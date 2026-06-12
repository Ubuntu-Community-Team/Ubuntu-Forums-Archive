---
title: "Cannot boot into Ubuntu after CPU replacement"
date: 2024-09-16
forum: Installation &amp; Upgrades
---

### Post by linux-user-482 on 2024-09-16
Update: I switched back to 12600K and everything works as normal. The boot USB is still giving the same error. I found an open issue on Balena Etcher's Github page. [error: file `/boot/` not found Before Live Grub Menu · Issue #4142 · balena-io/etcher (github.com)]("https://github.com/balena-io/etcher/issues/4142") I'm not technical enough to understand it unfortunately.

Update #2: Switched to Ventoy and the USB is now bootable, but it's suffering the same issue on the new CPU. That is, the screen goes black after selecting Ubuntu from GNU Grub, and the fan spins to max speed before the computer shuts down, and it restarts. 

I replaced my CPU, going from Intel 12600K to 13900, but I'm now longer able to boot into Ubuntu (24). It's going into GNU Grub, and when I select Ubuntu / recovery mode, the screen goes black for a while and then the computer reboots. 
Grub Screen: [Imgur: The magic of the Internet]("https://imgur.com/a/3HwVwxK")



In grub, I found /boot/grub in (hd0,gpt2) and ran the following

```
set root=(hd0,gpt2)
set prefix=(hd0,gpt2)/boot/grub
insmod normal
normal
```

However this took me the grub menu again, and when I hit enter on Ubuntu, the screen went black for like 5 minutes, at which point I turned off the computer. 


After this, I tried to boot from a USB stick. My other machine is a Mac, so I followed these steps found here: [https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview)


When I tried to boot from from the USB, I got the follow error for both Ubuntu 22.04 LTS, and 24.04 LTS, which flashed for a brief second before returning me to GNU Grub

```
error file '/boot/' not found

```

In grub, I can see that after plugging in my USB, (hd1,gpt2)/ contains directories, like /home, /etc, /usr, /tmp, /snap as well as /boot/grub/

Note that I've used this exact USB and followed the exact procedure outlined in the link above to install Ubuntu a few months earlier without any issues.  The only difference is that I've upgraded the motherboard bios since then.


 Really stuck here, any help would be appreciated


**Additional Information**
After installing the new CPU, my RAM was situated incorrectly and gave no signal to the monitor incorrectly and I had to start and stop the computer several times before finding the issue. I'm not sure if this would have corrupted the bootloader. 


Motherboard used: Asrock Z690 mITX/ax

Recovery Mode Screen before reboot: [Imgur: The magic of the Internet]("https://imgur.com/a/Kvd0fIU")

[IMG]https://i.sstatic.net/lQuBISU9.jpg[/IMG]
[IMG]https://i.sstatic.net/lQuBISU9.jpg[/IMG]

---

### Post by him610 on 2024-09-17
Did you upgrade the AsRock motherboard firmware before you upgraded the CPU?

I missed that step last year when upgrading to a more recent model of CPU.
It was necessary to reinstall the older CPU, upgrade the firmware to latest release, then reinstall newer CPU before mine would boot.

---

