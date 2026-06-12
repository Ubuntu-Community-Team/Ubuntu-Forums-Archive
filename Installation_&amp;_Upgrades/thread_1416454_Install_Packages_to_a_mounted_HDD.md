---
title: "Install Packages to a mounted HDD"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by [3w`Sparky] on 2010-02-26
I want to install some packages to a hdd from booting a live cd 

eg add something lets say gparted for example to the hdd install of ubuntu 

but 

while i'm booted from a live cd or if the disk has been put into another linux box



any ways of doing this ?

---

### Post by sisco311 on 2010-02-26
You can chroot into an existing Linux installation:
[list=i]
[*]mount the root ("/") partition:
```
sudo mkdir /var/chroot
sudo mount /dev/sda1 /var/chroot

```


[*]mount the virtual filesystems & enable the network:
```
for i in dev dev/pts proc sys etc/resolv.conf; do sudo mount --bind /$i /var/chroot/$i; done
```


[*]type:
```
sudo chroot /var/chroot su - username
```
to change to a shell inside the chroot.
NOTE: you are logging in as user: username.


[*]inside the chroot install the application(s) or run any other command:
```
sudo apt-get update
sudo apt-get install gparted
``` 

to run a GUI application:
[list=a]
[*]allow your user to connect to the X server & run the GUI app:

outside the chroot type:
```
xhost +SI:localuser:**username**
```
inside the chroot run the app:
```
sudo synaptic
```

OR


[*]run the application(s) in a separate window:
outside the chroot type:
```
Xnest -ac :2
```
inside the chroot type:
```
export DISPLAY=127.0.0.1:2.0
```
start a window manager:
```
metacity &
```
run an application, i.e the panels:
```
gnome-panel &> /dev/null &
```
[/list]

[*]exit from the chroot:
```
exit    #or press Ctrl+d
```

[/list]

---

