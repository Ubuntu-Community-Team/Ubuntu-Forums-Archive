---
title: "gdm3 not working on debootstrapped installation"
date: 2023-01-23
forum: Installation &amp; Upgrades
---

### Post by vendax on 2023-01-23
Hello forum!

I am writing some scripts that downloads ubuntu with debootstrap and using apt install to install stuff on top of it. I then use QEMU to try it out. This way, i am hoping to create a flavor of Ubuntu that is completely devoid of snap - my arch-enemy.

gdm3 installs fine when doing **apt install ubuntu-desktop-minimal**. But when trying to login with a created user of uid 1000 and guid 1000 it provides an error when the wrong password is used, which is expected, but when using the correct password it simply resets back to asking the username. So it will not leave gdm and enter the desktop, even though the provided username/password is correct.

How can i diagnose this and how can i install a working desktop system after starting with debootstrap? I have multiverse enabled in apt sources and the installation of gdm3 and others seems just fine.

Alternatively, i tried installing lightdm but when i install that with apt, it installs gdm3 too and i get a question which of the two i want to use. That wasn't really what i want. Is there an option not to use gdm3 but use lightdm or another alternative?

Thank you for your help! :)

---

### Post by MAFoElffen on 2023-01-23
When you created the user (after the debootstrap process), did you create an /home/UserName/.Xauthority file owned by the UserName and with permissions of 655? There's also an alternate way to do that...

---

### Post by vendax on 2023-01-23
No there is only a home directory which has correct permissions, and i made the user member of some groups in /etc/group.

I'll look into the .Xauthority thing, thanks!

---

### Post by MAFoElffen on 2023-01-24
In this post:  [https://ubuntuforums.org/showthread.php?t=1743535&p=11404605#post11404605](https://ubuntuforums.org/showthread.php?t=1743535&p=11404605#post11404605)
 or... this is what I add to my scripts to add users after a debootstrap or rsync install: 
```

username=YOUR_USERNAME

adduser $username

cp -a /etc/skel/. /home/$username
chown -R $username:$username /home/$username
usermod -a -G adm,cdrom,dip,lpadmin,lxd,plugdev,sambashare,sudo $username

```

---

### Post by vendax on 2023-01-24
Thank you that was helpful.

When updating my scripts it complained that the groups lpadmin lxd and sambashare did not exist. I do not know what the former two do, but of course i would like to make the user member of sambashare.

Problem is: samba is not installed yet. So the group does not exist, so i cannot make the user a member of that group. Is there a way to do it anyhow, and it only having any effect for when samba is installed?

I would like to prevent having to mess with the user groups etc elsewhere in my script, but do it much like you do.

I could create the groups myself of course, but i would not know what group id it normally has and i would like to follow convention here.

My scripts are running now again, thanks a lot, i will report the result shortly.

---

### Post by MAFoElffen on 2023-01-24
From my scripts, in the intial config after the debootstrap and chroot...
```

addgroup --system lpadmin
addgroup --system lxd
addgroup --system sambashare

```

---

### Post by vendax on 2023-01-24
Thank you again! My scripts finished and i tried out the new .iso with QEMU.

It behaves different now, but still does not work. After i entered the password and hit enter, the masked password keeps being displayed and it kind of freezes. I switch to the serial console and login with user account and i can see with **ps auxw | grep gnome** the following processes:

gdm-wayland-session
gnome-session-binary
gnome-shell
gjs (2x)
gnome-sessoin-failed

The last one is kind of telling i guess. Something not right with gnome. Where can i find logs? The ~/.Xauthority file now exists, is empty, us owned user:user and chmod 600. Directories seem to have been created in the user homedir like Documents Downloads etc.

So something works, but there is an error with gnome.

**dmesg** shows more errors, not sure they are related. Twice a **segfault of gsd-power**. Not sure that is relevant; maybe that driver does not work inside QEMU?

---

### Post by vendax on 2023-01-24
Some more info:

/var/log/gdm3 is empty

/var/log/syslog has more info

It continuously tries to start upower.service and says Main process exited, failed with result 'exit-code' and Failed to start Daemon for power management. systemd continuously tries to restart it, but fails.

Then gsd-power segfaults error 4 in libupower-glic.so.3.1.0
gsd-power invalid (NULL) pointer instance
g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
up_client_get_devices_full: assertion 'IP_IS_CLIENT (client)' failed
gnome-session: gnome-session-binary: WARNING: Application 'org.gnome.SettingsDaemon.Power.desktop' killed by signal 11

I guess this is what is blocking the login. QEMU might be to blame here because obviously it is not a real system so power drivers do not work. How could i best approach this problem?

---

### Post by MAFoElffen on 2023-01-24
Could you please post your Qemu script (startup command) or Domain XML?

---

### Post by vendax on 2023-01-24
```
kvm -kernel $KERNEL -initrd $INITRD \
-cpu max -smp 8 -m 8G \
-rtc base=utc -no-reboot \
-nic user,model=virtio-net-pci \
-vga virtio -display gtk,show-cursor=on \
-virtfs local,path=$ROOTPATH,mount_tag=root,security_model=passthrough,id=root,multidevs=remap \
-append "root=root rw console=ttyS0"
```
I use 9proot as you can see, not sure if that is related. vga virtio may be related, but the issue is with upower?

---

### Post by vendax on 2023-01-24
Linux kernel used is 5.16 self-compiled on amd64, to enable stuff like 9p and other virtio things.

---

### Post by MAFoElffen on 2023-01-24
> **vendax said:**
> 
```

kvm -kernel $KERNEL\
 -initrd $INITRD \
-cpu max \
-smp 8 -m 8G \
-rtc base=utc -no-reboot \
-nic user,model=virtio-net-pci \
-vga virtio \
-display gtk,show-cursor=on \
-virtfs local,path=$ROOTPATH,mount_tag=root,security_model=passthrough,id=root,multidevs=remap \
-append "root=root rw console=ttyS0"
```
I use 9proot as you can see, not sure if that is related. vga virtio may be related, but the issue is with upower?

'kvm' executable there is just a wrapper for qemu-system-x86_64. For example
```

qemu-system-x86_64 \
  -kernel arch/x86_64/boot/vmlinuz-6.2-rc3-generic \
  -smp cores=1,threads=2
  -append "console=ttyS0" \
  -initrd initramfs.img \
  -m 1024 \
  -enable-kvm \
  -serial stdio \
  -cpu host \
  -display qxl \
  -vga virtio

```
But to boot an image I do more like:
```

qemu-system-x86_64 \
  -drive "file=/data/KVM-VM/lunar-server-cloudimg-amd64.img",format=qcow2" \
  -drive "file=/data/KVM-VM/user-data.img,format=raw" \
  -device rtl8139,netdev=net0 \
  -enable-kvm \
  -cpu CPU \
  -m 2G \
  -netdev user,id=net0 \
  -serial mon:stdio \
  -smp 2 \
  -vga virtio

```

---

### Post by vendax on 2023-01-25
I changed kvm to:

qemu-system-x86_64 -machine pc,accel=kvm,usb=off,dump-guest-core=off --enable-kvm

No change in behavior. When trying to do startx manually i also read about FBDEV missing. Maybe my custom compiled kernel is it fault. My kernel config does not state anything about FBDEV. Just a bunch of stuff to enable virtio and virtualization stuff.

In general i like logfiles, where can i see why gdm3 is simply not booting? I would like to see something like:

gdm3: user tried to login
gdm3: verifying username/password combination... seems valid!
gdm3: trying to start gnome..
gdm3: error because gnome binary missing or whatever..

I understand i may have depleted your inventory of helpful insights, is there a place i could go to get more specialized help? I really hope to fix this and be able to use my debootstrap scripts to update my old system now. Everything works, all apt install just works and applications work. Only X does not work. :(

---

### Post by MAFoElffen on 2023-01-25
I have time, love to help, and am curious with what you are trying to do.

And you are using xorg right?

I do KVM/Qemu a lot for testing... I create permanent VM Guests... For that same cloud image, I do
```

sudo virt-install \
  --name lunar-server-cloudimg-amd64 \
  --memory 1024 \
  --disk /data/KVM-VM/lunar-server-cloudimg-amd64.img,device=disk,bus=virtio \
  --disk /data/ISO/cloud-init.iso,device=cdrom \
  --os-type linux \
  --os-variant ubuntu22.04 \
  --virt-type kvm \
  --graphics none \
  --network network=default,model=virtio \
  --import

```
But that doesn't have X... Is console.

Then I use Network Manager to tweak the config of the machine. I don't need to fight a viewer or VM Manager when I'm testing scripts and configs.

For graphics I usually use Display Spice and Video QXL... And when I'm testing I use the Network Manager Viewer. Why are you directly booting the kernel instead of booting from Grub2?

For ideas on fixing "Graphics Issue"? My Sticky: [https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535) I have a few. LOL

---

### Post by vendax on 2023-01-25
MAFoElffen,

**Thank you very much** for your continued support! I did not see a like button but many kudo's to you!

I was kind of panicking that i was not able to fix this in time. All my progress depended on this blocker. I'm not very familiar with Linux, i come from BSD.

I seem to have hit the nail: **Ubuntu 22.04 LTS apparently defaults to using Xwayland over Xorg**. When seeing graphical output from gdm3 if i click the user icon, i see a cogwheel at the bottom right corner that allows Ubuntu on Xorg option, where the first is simply called "Ubuntu".

When selecting Xorg it just boots to the desktop just fine. Problem solved. :D

Remains the question why Wayland is not working. I am now going to boot a real system with this setup and see if Wayland works there. I would love both to work, but only if it is not too much work.

```
cat /var/log/syslog | grep -i wayland
```
Errors can be seen. I have to type by hand so no copy-paste. But the first error is with activation of **org.freedesktop.systemd1**  :

> 
-> activate org.a11y.Bus
-> activate org.freedesktop.impl.portal.PermissionStore
-> activate org.gnome.Shell.Notifications
-> activate org.a11y.atspi.Registry
-> fails to activate org.freedesktop.systemd1 with message: **failed: Process org.freedesktop.systemd1 exited with status 1**
-> activates org.gnome.ScreenSaver with success

systemd Reached target GNOME Wayland Session.
systemd starting GNOME Shell on Wayland...
systemd [EMAIL="org.gnome.Shell@wayland.servic"]org.gnome.Shell@wayland.servic[/EMAIL]e: Failed with result 'protocol'.
systemd Failed to start GNOME Shell on Wayland
.. blahblah more failure messages

gnome-shell: Connection to xwayland lost
I feel the reason why it is failing is in another logfile. Any hints?

---

### Post by MAFoElffen on 2023-01-25
What you were saying before about want the gdm log to be more foregoing:
> Apparently you can run gdm in debug mode by un-commenting **Enable=true** in **/etc/gdm/custom.conf**
While tracing down your log results, I saw that and thought to share... Try that please.

Still looking through the things... looking through dbus-run-session types of errors...

---

### Post by MAFoElffen on 2023-01-25
Here is a default /etc/gdm3/custom.conf file:
```

# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Uncomment the line below to force the login screen to use Xorg
WaylandEnable=false

# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1

# Enabling timed login
#  TimedLoginEnable = true[daemon]
# Uncomment the line below to force the login screen to use Xorg
WaylandEnable=false

#  TimedLogin = user1
#  TimedLoginDelay = 10

[security]

[xdmcp]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

```
under [daemon], where it says
```

[daemon]
# Uncomment the line below to force the login screen to use Xorg
#WaylandEnable=false

```
Please change to 
```

[daemon]
# Uncomment the line below to force the login screen to use Xorg, default written there is commented with a value of false
WaylandEnable=true

```
You would think that with this commented, that the default of true would be followed, but lets try to force the default.

---

### Post by vendax on 2023-01-26
Ok, so i have /etc/gdm3/custom.conf with
```

[daemon]
WaylandEnable=true
AutomaticLoginEnable=true
AutomaticLogin=username

[debug]
Enable=true
```
It works, because of the automatic login. But i expected it to fail, because i explicitly set WaylandEnable=true. Looking under Settings -> About it says X11 windowing system. ps seems to agree with no wayland processes active.

So the custom.conf works because it does automatically login. But both the wayland and the debug does not seem to be working.

How does the debug option work? I expected it to create files under /etc/log/gdm3 but even with sudo this directory is empty.

---

### Post by MAFoElffen on 2023-01-26
Post #1 says you went with Ubuntu Minimal... Other posts say you were thinking about using LightDM...

I use LightDM. Logs for LightDM are under /var/log/lightdm. 

GDM3 supposedly has it's log under /var/log/gdm3... But I don't even see that directory on this machine. I tried on another. I see directory /var/log/gdm3, but see no log files there. In fact, using find, I do not see gdm.log anywhere on the system.

I think you might have better luck doing 
```

journalctl _UID=1000

```
I know with me installing Ubuntu Desktop minimal and Ubuntu Server minimal, that while doing testing on them, sometimes I have to install some basic Linux utilities, because they were missing. Just an observation.

---

