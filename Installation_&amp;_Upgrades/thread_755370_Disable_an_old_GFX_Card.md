---
title: "Disable an old GFX Card?"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by Simscape on 2008-04-14
I have a nVIDIA GeForce 6200 256MB PCI Card, and an old intergraded Intel 845G card.
I need to disable the old one, its causing my system to malfunction, I can't set any video settings.
Can anyone help? Thanks.
Oh yeah, by the way, this is a FRESH installation of 8.04.

---

### Post by Pumalite on 2008-04-14
Get into BIOS and make sure your new card is recognized and well configured.

---

### Post by Simscape on 2008-04-14
> **Pumalite said:**
> Get into BIOS and make sure your new card is recognized and well configured.

My BIOS is Phoenix BIOS 4.0 Release 6.0, and there is nothing about video cards in there, except whether I want to use PCI or Onboard.
And, of course its set to PCI.

Is there some drivers I need for it? it said it was in restricted use of hardware, enabled, but not in use.
^^Thats only because it could not find any open source drivers though^^

---

### Post by Pumalite on 2008-04-14
You have to check the box then (in use) and then reboot.

---

### Post by Simscape on 2008-04-14
I guess I could have looked on the site... I found a driver for Linux, I'll DL it and see if that works out, be back in a little while.

---

### Post by Simscape on 2008-04-14
> **Pumalite said:**
> You have to check the box then (in use) and then reboot.
It was already checked.

---

### Post by Pumalite on 2008-04-14
Try to install the appropriate driver downloaded from the site. If you need help, let me know.

---

### Post by Simscape on 2008-04-14
Alright, thanks, I do need help, Ubuntu says it can't open the install thing. (Sorry IDK what its called)
I get this in the terminal:
> cody@cody-desktop:~$ sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
[sudo] password for cody: 
sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run
cody@cody-desktop:~$ sh NVIDIA-Linux-x86-169.12-pkg1.run
sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run
cody@cody-desktop:~$ 
What do I do? (Driver download : [http://www.nvidia.com/object/linux_display_ia32_169.12.html]("http://www.nvidia.com/object/linux_display_ia32_169.12.html")

---

### Post by Pumalite on 2008-04-14
Make sure you have build-essential:
sudo aptitude install build-essential
Keep you driver on your Desktop.
Go to Virtual Terminal
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-xxxx.run
Accept License
Let the driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file
Then: startx

---

