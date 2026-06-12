---
title: "Nvidia Installation Error"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by covertcj on 2010-04-02
So, I recently downloaded the 64-bit Lucid Beta and installed the Nvidia drivers. Later, after deciding that 32 bit applications were too much of a hassle, I decided to reinstall Lucid with the 32 bit version.

I am not sure if that has anything to do with the following issue, but I thought it might be possible, as I have the same home directory for both installs (I partitioned it as a separate partition and simply didn't reformat it during the second installation).

Anyway, my problem is this: if I try to use the restricted hardware drivers GUI option, the install fails stating:
"Sorry, the installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log"

I am unsure of what to make out of this log file.

I also tried to install the most recent drivers manually, but that doesn't seem to work either.
I shut down gdm and ran "sudo sh /path/NVIDIA-*.run" and was given an error along the lines of the preinstall process failing.

I would attach the log file, but it is too large for the forum limit. 
I am running a HP Compaq 8510w. 
Any help would be greatly appreciated!

Thanks,
Chris

EDIT: I uploaded the log files to google docs (there are two, one was suffixed with a .1)
[http://docs.google.com/leaf?id=0B-94ZnuTRHpRNzMzNjQzOWQtMjE2ZS00NDM3LWI4NzgtNmFiMWE5NTQ3MGFj&hl=en](http://docs.google.com/leaf?id=0B-94ZnuTRHpRNzMzNjQzOWQtMjE2ZS00NDM3LWI4NzgtNmFiMWE5NTQ3MGFj&hl=en)

---

### Post by realzippy on 2010-04-02
Hello,
send the errorlog file as attachment (paperclip symbol).
The NVIDIA installer does not work in Lucid in the moment,have to use jockey (hardware drivers GUI option)...

---

### Post by realzippy on 2010-04-02
Edit:
sorry,wrong.
This could help:

2010-04-01 23:22:14,073 ERROR: update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.


Have you updated your system before installing nvidiadriver?

---

### Post by plun on 2010-04-02
Bug report....

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653)

Seems to be the Nouveau-c**p again.....;)

---

### Post by sdowney717 on 2010-04-02
> Gunnar Árni Hinriksson  wrote 11 hours ago:  	  #5

By blacklisting the nouveau driver I got rid of the problem, and got one ugly loading screen when booting ubuntu.
Seems that you can't remove the nouveau driver using the synaptic package manager and have to blacklist it instead.


Yes,for me also when I first upgraded to Lucid, I had to blacklist the nouveau driver to get nvidia driver to load.

---

### Post by covertcj on 2010-04-02
> **plun said:**
> Bug report....

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653)

Seems to be the Nouveau-c**p again.....;)
 
I tried blacklisting this as suggested in the bug report (added 'blacklist Nouveau' to '/etc/modprobe.d/blacklist'), but it didn't really seem to have any effect. I had updated and upgraded the system fully just before installing the drivers.

After some further testing, the drivers seem to work fine (I can activate desktop effects, etc.); however, I did notice that I still lose the nice high resolution TTY's and Ubuntu splash screen on boot up. Is that do to this issue, or just the way that the Nvidia drivers handle it (i really like the high resolution ;))?

Thanks for the help guys,
Chris

---

### Post by realzippy on 2010-04-03
*I did notice that I still lose the nice high resolution*

  so you can setup your high resolution and after reboot it is gone?

---

### Post by covertcj on 2010-04-03
> **realzippy said:**
> *I did notice that I still lose the nice high resolution*

  so you can setup your high resolution and after reboot it is gone?

Well, I don't know how to change the TTY / Splash screen resolution at all, but it is set down only with the graphics drivers active.

---

### Post by zenarcher on 2010-04-04
> **covertcj said:**
> Well, I don't know how to change the TTY / Splash screen resolution at all, but it is set down only with the graphics drivers active.

Here's how I fixed the splash screen resolution, if that helps...

[http://ubuntuforums.org/showthread.php?t=1446132](http://ubuntuforums.org/showthread.php?t=1446132)

Cheers,
zenarcher

---

### Post by Uncle Spellbinder on 2010-04-04
I got the same message when trying to load the driver for nVidia. But that's all it was...a message. Maybe the message is wrong? Because desktop effects are enabled and working fine, even after being told "*Sorry, the installation of this driver failed.*"

---

### Post by zenarcher on 2010-04-04
> **Uncle Spellbinder said:**
> I got the same message when trying to load the driver for nVidia. But that's all it was...a message. Maybe the message is wrong? Because desktop effects are enabled and working fine, even after being told "*Sorry, the installation of this driver failed.*"

Same here on three installs I have with Nvidia graphics cards.  I also got the "Sorry, the installation of this driver failed," then I got a result showing the driver was installed, but not activated.  However, Nvidia XServer Settings shows the Nvidia proprietary driver there and everything is working fine.

Cheers,
zenarcher

---

### Post by fedexnman on 2010-04-04
same here ! error message , but when i rebooted, the driver was installed, plymouth does'nt  jive well with nvidia drivers, im already missing the x-splash screen ! hope they get this stuff iron'd out by release time ??

---

### Post by sdowney717 on 2010-04-04
the nvidia driver I installed came from nvidia downloaded as a .run file
just make it executable
to install, exit to console login x cant be running
and use the installer like this
sudo ./nameoffile.run

If you dont like the name, you can rename it.

---

### Post by ratcheer on 2010-04-05
> **realzippy said:**
> Edit:
sorry,wrong.
This could help:

2010-04-01 23:22:14,073 ERROR: update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.


Have you updated your system before installing nvidiadriver?

I reinstalled using Apr 5 alternate iso, this morning. I immediately installed the nvidia proprietary driver and received this exact same failure. However, the driver was functioning, correctly, the nvidia-current.ko module was created, and xorg.conf indicated that the driver was in use. This is the first time I have received such an error and I reinstall Lucid and nvidia driver each week, as I am on the Xorg Proprietary Drivers testing team. I cannot find an exactly matching bug in Launchpad.

On a positive note, this is the first time in Lucid that the jockey GUI has informed me that **"This driver is activated and currently in use"**. Up until now, it has always told me that the driver was activated but not currently in use, even though it was being used (bug 522943).

---

