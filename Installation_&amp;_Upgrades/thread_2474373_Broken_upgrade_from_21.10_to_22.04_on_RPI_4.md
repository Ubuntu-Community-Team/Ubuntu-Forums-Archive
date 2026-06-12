---
title: "Broken upgrade from 21.10 to 22.04 on RPI 4"
date: 2022-04-27
forum: Installation &amp; Upgrades
---

### Post by blers27 on 2022-04-27
I upgraded to 22.04 from 21.10 on my Raspberry Pi 4. using "do-release-upgrade -d". There were a kernel warning along the way, and now when I boot, I cannot connect to any network connection at all. I am looking at logs when I mount the microSD on my PC running Ubuntu Desktop and it seems to be booting fine with services running.

I am suspecting something going on with the kernel and should restore an older/working version, but problem is this a pi running Ubuntu and is headless...

---

### Post by #&amp;thj^% on 2022-04-27
Can you now run this on that Pi
```
sudo apt update
sudo apt full-upgrade
```
EDIT: just saw no internet. sorry about that
MORE: I believe the problem is that with 5.13 they introduced a linux-modules-extra package and the USB storage drivers ended up in that package rather than linux-modules.

Juerg Haefliger (juergh) wrote on 2022-

The workaround for now is to manually install linux-modules-extra after upgrading to 5.13 but *before* rebooting.

---

### Post by blers27 on 2022-04-27
> **1fallen said:**
> Can you now run this on that Pi
```
sudo apt update
sudo apt full-upgrade
```
EDIT: just saw no internet. sorry about that

yeah unfortunately I cannot even SSH into it anymore. I have to mount the microsd card to another system to look into the files.

---

### Post by #&amp;thj^% on 2022-04-27
> **blers27 said:**
> yeah unfortunately I cannot even SSH into it anymore. I have to mount the microsd card to another system to look into the files.
if you do a manual install, please take note of my last edit.
FWIW I do feel for you. :(

---

### Post by blers27 on 2022-04-27
> **1fallen said:**
> if you do a manual install, please take note of my last edit.
FWIW I do feel for you. :(

Oddly enough I see 5.15 in /boot/ so I am a bit confused on which one is running. What's even more confusing is I think 5.13 was already installed.

There are .bak files in there but I'm not sure if I should be toying with them and restoring them that way.

---

### Post by #&amp;thj^% on 2022-04-27
If you are lucky enough to have a Grub menu, select the older 5.13 installed kernel.
any difference?

---

### Post by blers27 on 2022-04-27
> **1fallen said:**
> If you are lucky enough to have a Grub menu, select the older 5.13 installed kernel.
any difference?

yeah im very unfortunate to not have a grub with this system or a backup. Sigh.

---

### Post by #&amp;thj^% on 2022-04-27
It's been a while since I ran rpi-update on anything, but poking through the code (it is a bash script), it looks like it copies the contents of** /boot/ **into** /boot.bak/** and** /lib/modules/$(uname -r)/** to** /lib/modules/$(uname -r).bak/**.
Copying the content of those** .bak **directories back to the originals should undo the update.

---

### Post by blers27 on 2022-04-27
> **1fallen said:**
> It's been a while since I ran rpi-update on anything, but poking through the code (it is a bash script), it looks like it copies the contents of** /boot/ **into** /boot.bak/** and** /lib/modules/$(uname -r)/** to** /lib/modules/$(uname -r).bak/**.
Copying the content of those** .bak **directories back to the originals should undo the update.

I actually am not seeing any .bak directories, but am seeing some bak files in the boot partition. Where do you see this rpi-update bash script?

---

### Post by #&amp;thj^% on 2022-04-27
from here:[https://www.codegrepper.com/code-examples/shell/sudo+apt+upgrade+on+ubuntu+error](https://www.codegrepper.com/code-examples/shell/sudo+apt+upgrade+on+ubuntu+error)
that led to here:[https://gist.github.com/andrewpmiller/1f4ba7599db5070c6a4a](https://gist.github.com/andrewpmiller/1f4ba7599db5070c6a4a)

and the rest is I test platforms and firmware on Linux. (Arch Mainly)
If you can't see those viewed from your other machine then things got really hosed during the release upgrade..
Sorry I recommend a clean fresh install.
EDIT: those may be enough** " bak files in the boot partition" **can you post those here:
```
**cd /boot && ls -a**
.              initramfs-linux-amd-fallback.img       initramfs-linux.img
..             initramfs-linux-amd.img                System.map-5.17.5-AMD
amd-ucode.img  initramfs-linux-fallback.img           vmlinuz-linux
efi            initramfs-linux-hardened-fallback.img  vmlinuz-linux-amd
grub           initramfs-linux-hardened.img           vmlinuz-linux-hardened


```
That of course is just an example.

---

### Post by blers27 on 2022-04-29
> **1fallen said:**
> from here:[https://www.codegrepper.com/code-examples/shell/sudo+apt+upgrade+on+ubuntu+error](https://www.codegrepper.com/code-examples/shell/sudo+apt+upgrade+on+ubuntu+error)
that led to here:[https://gist.github.com/andrewpmiller/1f4ba7599db5070c6a4a](https://gist.github.com/andrewpmiller/1f4ba7599db5070c6a4a)

and the rest is I test platforms and firmware on Linux. (Arch Mainly)
If you can't see those viewed from your other machine then things got really hosed during the release upgrade..
Sorry I recommend a clean fresh install.
EDIT: those may be enough** " bak files in the boot partition" **can you post those here:
```
**cd /boot && ls -a**
.              initramfs-linux-amd-fallback.img       initramfs-linux.img
..             initramfs-linux-amd.img                System.map-5.17.5-AMD
amd-ucode.img  initramfs-linux-fallback.img           vmlinuz-linux
efi            initramfs-linux-hardened-fallback.img  vmlinuz-linux-amd
grub           initramfs-linux-hardened.img           vmlinuz-linux-hardened


```
That of course is just an example.

Ended up reformatting and reinstalling server services, the path I initially wanted to avoid. Tbh the bak files actually didn't do anything and I think things really got hosed down during the release upgrade when I dug around. Thanks for the support before!

Lesson learned: back up before doing a release upgrade, especially over SSH!

---

