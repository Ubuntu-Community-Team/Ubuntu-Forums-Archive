---
title: "My video is deconfigured when my system is updated - ubuntu 18"
date: 2021-06-20
forum: Installation &amp; Upgrades
---

### Post by net-alexander on 2021-06-20
I was trying to install a program to play (Lutris) and it asked me to install the nvidia drivers manually, I think the problem is that I disable the Nouveau nvidia driver in Ubuntu, This was one of the steps I followed to install (Lutris):




------




How to disable Nouveau nvidia driver on Ubuntu 18.04 Bionic Beaver Linux.
Instructions
Blacklist Nvidia nouveau driver
Open up terminal and enter the following linux commands:
```
$ sudo bash -c "echo blacklist nouveau> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"

```
```
$ sudo bash -c "echo options nouveau modeset = 0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"

```






Confirm the content of the new modprobe config file:




```
$ cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf





```it should show something like this:
blacklist nouveau
options nouveau modeset = 0




Update kernel initramfs
Enter the following linux command to regenerate initramfs:




```
$ sudo update-initramfs -u

```
Reboot
All should be ready now. Reboot your system:
```
$ sudo reboot

```
-----




I comment that whenever my ubuntu is updated I have to manually download an nvidia driver to the PC and run something like this:






```
sudo apt-get purge nvidia *

```
```
sudo apt-get autoremove

```
```
sudo reboot

```
```
sudo sh ./NVIDIA-Linux-x86_64-460.56.run

```
----
I would like that when ubuntu is updated that does not happen, before it did not happen, I am not interested (Lutris).




Help.

---

### Post by MAFoElffen on 2021-06-22
Noooooooooo.....

Yes, installing the NVidia binary drivers will break if a system updates. (From time to time) That is just a fact of life.

I have done support for the Linux graphics layer for years and years and way too long... Do not follow something that was probably written years ago (maybe over a decade ago) for Linux overall.

Here is the reality. You can certainly install the binary drivers straight from NVidia. Those assume that you know what you are doing and accept that they may not work for your specific combination of hardware and OS. It assumes that you know enough to figure out what you have and have the skills to recover from that manually if you have a problem. It also assumes that you are going to manually upgrade to a newer version of the binary drivers, every time a new driver comes out. And since it is installed outside of the normal OS system update channels, just updating the normal OS may result in a black screen, because it doesn't have any responsibility to look at what was installed directly outside of the OS update channels.

If you install the NVidia binaries, that just becomes a normal way of life that you have to understand and accept.

There is a better, easier, smarter way of life.

Add the Ubuntu Graphics Team PPA. From there you can add an appropriate driver that supports your GPU. Then, a normal system update is less likely to break your system. Determine, by Googling NVidia,.com and your GPU which drivers will work with it. Then select those from the PPA. The maintainers there apply any needed patches to make them work with Ubuntu. There are only drivers there that work with Ubuntu, so you don't end up using a driver that doesn't. (Note that an older driver may only work up to specific Kernel version.) There is a addition Graphics Testers Team there, that tests those drivers to ensure that. You are setup for success.

The graphics drivers in the 3rd Party Repo are less edgy and update as the kernel versions update. But are older versions. Not the latest and greatest. So just check what the app is looking for. The application's minimum spec's are going to say a GPU or better, a drivers version or newer.

AS long as an application sees that a specific GPU has the required graphics drivers installed, it has no idea, nor cares about how it was installed. It only cares that it IS installed.

That is just a smarter way to do it and ends up in a whole lot less work and frustration(s). It just makes more common sense and less effort over the years.

---

### Post by net-alexander on 2021-06-29
Could you give me an example? The uninstallation and installation procedure
nvidia driver manual that mentioned I run it right after
that my ubuntu 18 is updated, because when I restart the computer it allows me
see my desktop with a very bad resolution. Shouldn't I first blacklist the nvidia-nouveau driver?

---

### Post by MAFoElffen on 2021-06-29
go to wherever on  you extracted the Binary NVIDIA driver. Instead of using the command to execute that specific install script (because the name fallows a naming convention for that specific driver...) Add/append an --uninstall flag to that. Using that flag will uninstall what it installed.

---

