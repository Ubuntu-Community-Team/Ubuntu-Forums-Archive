---
title: "Ubuntu as MS Virtual Server Guest - Linux Additions"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by mkong on 2006-04-06
Excuse the novice posting.

I've gotten ubuntu installed on MS Virtual Server as a guest OS, and have downloaded and installed the MS Linux VM Additions which were released a few days ago.  I was able to covert the RPM to DEB packages via Alien and install them (no errors)

Now it appears I'm stuck on installing/compiling the kernel module to get this to work.  When I run the '/etc/init.d/vmadd -start', I get kernel module not found.

I did some digging on compiling kernel modules, and really only found articles on compiling the kernel.  I did do a 'sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4' to get the development sources started.

I was able to go to /lib/modules/vmadd/module and do 'sudo make', which created a vmadd.ko module. 

This is where I'm stuck on what to do next.  Tryed doing 'sudo modprobe vmadd', and got 'module not found'.

Can anyone possibly provide some suggestions.  It appears I'm very close, but I'm a novice and kinda stuck.

Thanks for any help.

---

### Post by ranf on 2006-04-06
Makefiles usually have a target named `install'. 

Did you try this?
```
sudo make install
```

---

### Post by mkong on 2006-04-06
Response is:  'No rule to make target `install` '

---

### Post by ranf on 2006-04-06
Then you need to copy the .ko file to somewhere under 
`/lib/modules/$(uname -r)' (I just don't know where it belongs.)

What is this module supposed to do?

---

### Post by mkong on 2006-04-06
It's the Virtual Machine additions for Linux produced by Microsoft for MS Virtual Server.  It was built as RPMs for RedHat and Suse, but that I converted to .deb files with Alien.  

They increase performance of the virtual machine while it's running, sync time with the host, provides driver support, etc.

---

### Post by uhdean on 2006-08-10
Check out the VMAdditionsForLinux-README.txt. Instead of using alien to convert the .prm to a .deb file just follow the instructions for "nstalling Through Shell Script":


1. First use "sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4' to get the development sources started.

2. Go to the VMAdditions directory on the CD-ROM.
     # cd VMAdditionsForLinux

3. Run the script:
     # ./vmadd-install.run all

4. Start the vmadd service   
    # /etc/init.d/vmadd start
    # /etc/init.d/vmadd-scsi start (This will error since you are using VPC 2004 and not Virtual Server)

5. Restart X (Ctrl+Alt+Backspace) or restart the computer

The mouse cursor with have 2 small XXs but the mouse, keyboard and time synch with the host machine will work similarly to the Virtual Machine Additions do on Windows OSes.

THese instructions worked for me on Ubuntu 5.04

---

### Post by goodwill on 2007-11-15
Sorry this is not working, the latest VMAdditions is indeed a kernel patch, which does not have something other than RPM install. The install.sh included is just calling rpm basically.

---

