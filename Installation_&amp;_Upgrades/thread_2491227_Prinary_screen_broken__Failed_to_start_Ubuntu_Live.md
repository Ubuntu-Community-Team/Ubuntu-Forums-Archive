---
title: "Prinary screen broken :: Failed to start Ubuntu Live CD installer"
date: 2023-09-30
forum: Installation &amp; Upgrades
---

### Post by pavelekh on 2023-09-30
Hello,

I am installing Ubuntu 22.04 Desktop from flash drive on Acer Aspire laptop with broken primary screen. So, I can not see BIOS etc.
I connected external monitor via HDMI port (laptop does not have VGA).
I found that Ubuntu is the only Linux distribution from what I have tried (tried Debian, Fedora, Mint) that actually redirects images during installation to HDMI monitor. So, I want to proceed with it.

Unfortunately, installation fails with message: [FAILED] Failed to start Ubuntu live CD installation.
This is the picture of the screen:
[IMG]https://i.ibb.co/qgtrgnw/PXL-20231001-032155189.jpg[/IMG] 
Before this screen it displays the following messages:
```
x86/cpu: SGX disabled by BIOS
Integrity: Problem loading x.509 certificate -65
Integrity: Problem loading x.509 certificate -65
nouveau 0000:01:00.0 fifo: fault 00 [READ] at 00000000000 engine [PHYSICAL] client 07 [HUB/HOST_CPU] reason 0d [REGION_VIOLATION] on channel -1 [000000000 unknown]

```
Is there anything I can do to use this laptop in this situation? Thanks

---

### Post by TheFu on 2023-10-01
You could setup a non-GUI boot and use a serial cable terminal connection.  [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)  I have a USB-serial cable that works with other OSes (BSD), but I've never tried Ubuntu without a GPU.
I think all stock Ubuntu releases require a VGA/VESA GPU until you change the startup settings.  A bit of a chicken and egg problem.

You won't start with any GUI, but post install of an Ubuntu Server, you might be able to load a GUI and connect an external monitor.  IDK.  Just throwing out another idea.

---

### Post by MAFoElffen on 2023-10-01
Go into the BIOS Setup of the laptop.

Enable SGX. That message is telling you that it is dsabled in the BIOS settings. It will ot prevent it from booting, but would be better if you did enable it.

The next two messages said a security certificate failed. While i your BIOS, disable Secure Boot.

The fourth error message... I have never seen before. Sorry.

---

### Post by MAFoElffen on 2023-10-01
I like what TheFu suggested, but the caveat to that during an install is fairly limited to adding these two boot parameters to the kernel boot line:
```

console=tty0 console=ttyS0,115200n8

```
And what is not documented there, is that via a serial console, you will see the cursor in the upper right of your screen, and if you just watch it, it will do nothing, and most people will mistakenly think that the session is locked up. At that point, you have to press the <Enter> key to initialize the session. Note that many modern laptops & desktops do not come with serial ports these days. I have used USB/Serial adapters for this and they do work without any kind of configuration. You do need a null serial cable to connect to another computer and either use the CU command i a terminal session or use a serial terminal console app such as minicom.

There is one more way that I have done on the Server Edition Live Installer media. It is a Live Image Environment (LIE). When you get past the language and keyboard settings panels, use the Help button to drop to a root prompt...
```

sudo apt update
apt install -y openssh-server
# After the install, make sure these two services are running:
systemctl status ssh
systemctl status sshd
# set a temporary password for the root user in the live environment
passwd  
vi /etc/ssh/sshd_config
# Set: PermitRootLogin yes
ip a
# get the IP address from the output of the last command...

```
Then connect to the live installation session via ssh from another computer, with user  "root" at the IP address from the output...

Example:
```

ssh root@10.0.0.97

```

But remember to correct the things I pointed out in the previous post, in BIOS, before doing any of this...

---

### Post by pavelekh on 2023-10-02
Thank you for you answers.
I will try the serial console idea. 
But how do I change BIOS settings without the screen? @MAFoElffen

---

### Post by MAFoElffen on 2023-10-03
I just reread that, and thought to myself... That isn't going to work for that. The BIOS settings are only going to direct to the primary (broken) screen.

Have you thought about replacing the screen? Unfortunately, the cost of having it replaced at a shop is more than the price of a new budget Laptop. But if done yourself, with used parts from EBay... Just thinking of other solutions.

---

