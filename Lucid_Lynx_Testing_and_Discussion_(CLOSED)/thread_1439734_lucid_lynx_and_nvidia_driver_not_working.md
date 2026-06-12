---
title: "lucid lynx and nvidia driver not working"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sbodoz on 2010-03-26
Hello everybody,
some days ago I upgraded my linux box from karmic to lucid and everything went pretty smooth.
Then after a few days I started having no screen working and ubuntu always running in low-graphics mode.
I'm working everyday, for some hours, in order to solve the problem, but so far, even by checking some online resources, I didn't find out a proper solution.

Here's the thing:
- 64bit system
- kernel: 2.6.32-16
- nvidia driver: nvidia-current
- gfx card: integrated geforce6

Until karmic, I've always been able to use my DVI port, but now it doesn't work at all, and the few times I'm able to properly start gdm, it works only with VGA port.

Xorg log keeps saying "(EE) Failed to load the NVIDIA kernel module!"

then I keep REinstalling nvidia-current package, and everytime I do that I receive the message "module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed" and "warning: forcing reinstallation of alternative /usr/lib.. cause link is broken" but then the install goes through anyway.

After I reistall the nvidia-current package, I'm able to run X altho the resolution is low (I'm using a Samsung SyncMaster T240HD monitor), but I can set it to 1900x1200 and keep working.

Thing is, next time I reboot the computer, it goes all the way back. So no NVIDIA module, and so on.

I also tried activating the driver nvidia-173, but same error.

I would really love to have some hints or help from any of you if you can.

Thanks in advance,
Edoardo

ps: if you need any more informations just ask me

---

### Post by sbodoz on 2010-03-27
quick upgrade: it seems like nvidia module is not loaded every time I reboot the PC. Basically on every boot I get the text-only display and if I try "modprobe nvidia" it says "FATAL: Module nvidia_173 (or nvidia_current) not found.". So I have to reinstall it every time in order to get X working.

Can anyone help me with this?

---

### Post by Ilya Skorik on 2010-03-27
I am not assured, but it like known a problem, is linked to inclusion of opensource nouveau driver. But it do not work too.

And it frightens, This is beta1 of LTS.

---

### Post by sdowney717 on 2010-03-27
> problem, is linked to inclusion of open source nouveau driver

if true then blacklist the nouveau driver.
I could not get nvidia driver to install UNTIL I added nouveau to the blacklist list.
I use nvidia 195.30 driver

---

### Post by Ilya Skorik on 2010-03-27
> **sdowney717 said:**
> if true then blacklist the nouveau driver.
I could not get nvidia driver to install UNTIL I added nouveau to the blacklist list.

Yes, I do this, without succes. I use nvidia-current from apt. And nouveay do not working at all.

---

### Post by sdowney717 on 2010-03-27
download the .run installer file directly from nvidia
install it from the console window, not in x session
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

that screen shot shows 195.36-15 
I currently use 195.30 as I got some artifacts. Who knows why

---

### Post by Ilya Skorik on 2010-03-27
I will try it.

Now I have 2.6.32-17 kernel, nvidia-glx-185 driver from apt repo. Nouveau totaly disabled.

GDM not working after reboot. Nvidia driver work only if I do "rmmod nvidia;modprobe nvidia;" from console. Without this I see black screen, when try do "startx" from console.

---

### Post by sdowney717 on 2010-03-27
I never successfully was able to "startx", just in console do "sudo reboot"
and it worked.

rmmod nvidia;modprobe nvidia makes the nvidia driver work properly in the GDM gui?

modprobe
[http://en.wikipedia.org/wiki/Modprobe](http://en.wikipedia.org/wiki/Modprobe)
when the kernel rquires a module, it actually runs modprobe automatically
Who knows, but perhaps you can edit a config file to fix this.
> Features

The modprobe program also has more configuration features than other similar utilities. It is possible to define module aliases allowing for some automatic loading of modules. When the kernel requires a module, it actually runs modprobe requesting it; however, the kernel has a description of only some module property (for example, a device major number, or the number of a network protocol), and modprobe does the job of translating that to an actual module name via aliases.

This program also has the ability to run programs before or after loading or unloading a given module; for example, setting the mixer right after loading a soundcard module, or uploading the firmware to a device immediately prior to enabling it. Although these actions must be implemented by external programs, modprobe takes care of synchronizing their executions with module loading/unloading.
[edit] Blacklist

There are cases where two or more modules both support the same devices, or a module invalidly claims to support a device: the blacklist keyword indicates that all of a particular module's internal aliases are to be ignored.[3]

There are a couple of ways to blacklist a module, and depending on the method used to load it depends on where this is configured.

There are two ways to blacklist a module using modprobe, employing the modprobe.conf system, the first is to use its blacklisting system in /etc/modprobe.d/blacklist

cat /etc/modprobe.d/blacklist
blacklist ieee1394
blacklist ohci1394
blacklist eth1394
blacklist sbp2


---

### Post by plun on 2010-03-27
Try this terminal command...

```
sudo jockey-text -e xorg:nvidia_current
```

It takes a while to fulfill...

Also file a bug if this is a solution.

---

### Post by Ilya Skorik on 2010-03-27
Drivers from nvidia site works fine.

---

### Post by sbodoz on 2010-03-27
thanks for the answers so far

I wasn't using the Nvidia installer simply cause on the page [http://www.ubuntu.com/testing/lucid/beta1#Known%20issues](http://www.ubuntu.com/testing/lucid/beta1#Known%20issues) it says: Because of the new alternatives system used for nvidia driver packages, the nvidia installer from NVIDIA's website currently doesn't work.

So I assume it does work instead?

and even if I removed (and purged) xserver-xorg-video-nouveau package, shoudl I blacklist that module anyway?

---

### Post by sdowney717 on 2010-03-27
yes, since you want to use nvidia, blacklist nouveau
It might redownload and try to use nouveau. 
Use the installer at nvidia site. It works fine.

You might see a few symbolic link errors, I simply clicked thru them and it installed and worked.

---

### Post by sbodoz on 2010-03-27
ok I removed all nvidia packages and installed the nvidia driver from nvidia.com
it doesn't work well tho, since evrytime I boot  the pc it says "unable to load nvidia module", then I reboot, and it works.. very odd.

---

### Post by sdowney717 on 2010-03-27
Did you blacklist nouveoauy? (nouveau)

---

### Post by sbodoz on 2010-03-27
yes I did

in my /etc/modprobe.d/blacklist.conf I have the line "blacklist nouveau"

---

### Post by id_crisis on 2010-03-28
this problem is solved on my computer...

What i did...


 open terminal>

run


1.  sudo apt-get purge nouveau*
2.  sudo apt-get install nvidia-current
3.   sudo nvidia-xconfig
4.  open blacklist.conf >>>> sudo gedit /etc/modprobe.d/blacklist.conf

     and add in last

blacklist nouveau


let me know...its worked or not... I am using latest kernel .....17 generic one

above work is not mine......i have read it somewhere in this forum.Thanks to original provider:)

---

### Post by realzippy on 2010-03-28
..strange.
On my machine nvidia-current runs fine without blacklisting nouveau.
Also it is the first time,FSAA and AF work...
Installed by restricted-drivers-manager;the NVIDIA.xxx.run indeed
does not work...

---

### Post by dino99 on 2010-03-28
on my end, with or without Nouveau does not change : jockey still says nvidia-current activated but not in use. I have no major issues in fact as i dont use effects, so it seems to be a jockey issue.

I've seen that drivers are identified by jockey as nvidia_xx instead of nvidia-xx everywhere else, strange.

---

### Post by id_crisis on 2010-03-28
its a bug .already in bug list.

---

### Post by sbodoz on 2010-03-28
update: every time I turn on my computer X doesn't start and log says "unable to load nvidia kernel module", and then if I do "modprobe nvidia" it says "cannot find module nvidia_current" even tho I installed the official nvidia driver from nvidia.com and not the ubuntu package. then if I do "sudo reboot", on next boot X works. odd.

---

### Post by nrdlnd on 2010-04-11
I'm running Lucid beta2. It's not possible to install Nvidia drivers with the "restricted-drivers-manager". It works fine to install Nvidia current with Synaptics though.

---

