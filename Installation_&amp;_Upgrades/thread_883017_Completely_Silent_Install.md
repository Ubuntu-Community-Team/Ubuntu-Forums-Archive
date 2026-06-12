---
title: "Completely Silent Install?"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Tauhshi on 2008-08-07
What would be the easiest way to customize an Ubuntu CD so that when the computer boots up from it, it automatically installs Ubuntu? I have a laptop that has a broken screen, keyboard, touchpad and USB ports, but I know that the computer boots up fine from an Ubuntu CD because I can hear the startup chime and all. I want to put Ubuntu on it with Transmission so that I can have a dedicated torrenting machine. The computer's internet connection works fine if the ethernet is plugged in, and it is able to connect to my network. So, the UbuntuCD would have to install automatically and then upon first boot (or before, I'm not picky) install and configure SSH and possibly VNC so that I can control the computer remotely.

---

### Post by GreenN00b on 2008-08-07
Here is a way to do it:
 - install virtualbox
 - install ubuntu on a virtual machine in virtual box
 - configure it the way you want it & add install sshd to have ssh access
 - install bootcd
 - use bootcdwrite to create an image for the system you just configured
 - write the image to a disk and boot the laptop
 - use the image to boot the laptop
 - ssh into the system running on the laptop
 - use bootcd2disk to write the system from the cd to the hdd on the laptop( you may have to partition first )

---

