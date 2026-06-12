---
title: "Possible to install Ubuntu remotely?"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by benjio123 on 2011-08-16
Ok, I have kind of an odd situation. I'm hours away from home and what I have there is a computer that was given to me by a friend just before I left. He already has ubuntu, SSH and VNC on it, and I have access to it from here. I can log on, and use it. Just before I left home, I popped in a 4gb flash drive in the usb port, and started a download of a fresh ubuntu iso.

What I want to do is copy the iso to the flash drive with startup disk creator, reboot (it'll boot off that drive) and install remotely, either via SSH or VNC (either way is fine, I plan on either install ubuntu server and adding xfce, or just installing xubuntu.
The problem is, once I reboot, it'll boot of the drive with ssh and vnc disabled, and I won't have access to it for another week :/

So what I need is either a way to create a non-graphical install disk that I can install via ssh terminal (ubuntu server).. or... a graphical startup disk (xubuntu) with at least ssh enabled at startup. I can install and enable x11vnc from the terminal and continue with the install if needed.

My gf is at home, but is not a techie at all.. The computer is headless, so pretty much all I can have her do is pull the jump drive when I need her to lol..
Anyway, thanks in advance for the help! This forum is great.

---

### Post by MountainX on 2012-06-04
There's an answer on ServerFault that will help in this situation:

**[How to remotely install Linux via SSH?]("http://serverfault.com/questions/208128/how-to-remotely-install-linux-via-ssh")**


He says, > Here is the outline of what I did:
  
[LIST=1]
[*]Run debootstrap on an *existing* Ubuntu server
[*]Transfer the files to the *swap* partition of the RHEL 3.4 server
[*]Boot into tha swap partition (the debootstrap system)
[*]Transfer the files to the original root partition
[*]Boot into the new Ubuntu system and finish up the installation with tasksel, apt-get, etc
[/LIST]
  I tested the method in a VM and then applied to the server. I was lucky enough that everything went smoothly :)


---

