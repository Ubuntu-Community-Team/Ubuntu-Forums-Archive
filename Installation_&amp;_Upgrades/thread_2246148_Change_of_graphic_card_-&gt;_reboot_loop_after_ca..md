---
title: "Change of graphic card -&gt; reboot loop after ca. 1s into boot process"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by Christoph_Bernhard on 2014-09-28
I had a working 14.04.1 install when I exchanged my old Nvidia graphics card with a Zotac GT 630 Zone edition. Since then I cannot not boot into my existing ubuntu installation. It will spontaneously reboot after ca. 1s into the boot process. The normal kernel boot messages will fly by, than my machine reboots without freezing the screen. So it is very difficult to see anything meaningful.

I then filmed what is happening on the screen during the boot process. It seems that the reboot happens without any indication in the kernel messages that something is wrong.

This behaviour is the same whether I boot the existing installation, boot the installer image from a usb stick, or boot into a fedora install kernel.

What I urgently need is some ideas what I can do to narrow down the cause for the problem. BTW windows 7 works just fine after replacing the graphics card. This is a dual boot machine.

Ideas are very welcome.

Machine is a Gigabyte P55M UD2 Rev 1.0 with 8 GB RAM with i5 (no internal graphics engine), Zotac GT 640 Zone edition with 4 GB video RAM, Samsung 840 EVO 500 GB, 1 TB hard disk, DVD drive. BIOS is latest available version.

Christoph.

---

### Post by Christoph_Bernhard on 2014-10-01
I have some more information concerning the reboot problem: The reboot happens when the kernel says that it is freeing unused memory. No error message before the reboot happens.

I can avoid the problem if I boot with kernel boot parameter "maxcpus=1". That of course is not really acceptable in the long run since I lose about 3/4 of my CPU performance.

Does the above ring any bells with anyone? Ideas what the root cause might be are very much welcome...

Thanks,
Christoph

---

### Post by papibe on 2014-10-01
Hi Christoph_Bernhard. Welcome to the forums ):P

This is what I've done when face with s similar situation: If the computer just failed to get into graphic mode, you may be able to get a text mode prompt by pressing Ctrl+Alt+F1 or Ctrl+Alt+F2. If you can't do that, boot into recovery mode, and select a root prompt.

These are the steps I took in text mode:

[LIST]
[*]Remove (rename actually) your Xorg config file:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
[*]Get the list of Nvidia packages currently installed:```
dpkg -l  | grep nvidia
```
[*]Start purging the nvidia-* packages using this structure:```
sudo apt-get purge nvidia-304
```
[*]Remove all packages separately except for these two:```
nvidia-cg-toolkit
nvidia-common
```
[*]Then reconfigure nvidia common:```
sudo dpkg-reconfigure nvidia-common
```
[*]At this point you can reboot, and you'll be using by default the Open Source driver (nouveau).
[*]Go to 'Additional drivers' and reinstall the recommend Nvidia driver from there.
[*]When finish, create a new X conf file:```
sudo nvidia-xconfig
```
[/LIST]
Now restart so that the Nvidia driver can take effect.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Christoph_Bernhard on 2014-10-12
Sorry, took a while to respond. First of all, thanks for your suggestions!

Tried them more or less. I even did a fresh install of ubuntu 14.04 + install of vanilla nvidia drivers from nvidia website. Same result. The kernel will not boot at all. Instead the computer will reboot (pretty hard reboot given that there obviously are different depths of reboot: it seems the machine switches off completely for a couple of seconds before it comes back).

Still the only work-around is to boot with "maxcpus=1". Seems that there is some kind of race condition when more than one cpu is involved. Maybe someone has some ideas how to debug further. If it helps I can compile a fresh kernel with specific debug configuration.

Kind regards,

Christoph

---

### Post by sudodus on 2014-10-12
How was the graphics working during the installation? Is is working well in the live session? Can you check which graphics driver is used (when booted from DVD/USB)?

You should be able to check it with (either of) these commands

```
lspci -nnk | grep -i vga -A3

sudo lshw -c video | grep driver=

glxinfo | grep -i opengl

read -p "hardinfo - Look at the info about 'Display'"
hardinfo
```

---

