---
title: "Instlux - fallen at the first gate - login incorrect?"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by cheddarpaul on 2007-03-13
Hi all, I am COMPLETELY new to Linux / Ubuntu but with all the good press its getting lately, I have decided I wanted to try it.

I have a very old Toshiba Tecra laptop which wont CD boot, doesnt have usb or a floppy, so I have looked at instlux as my answer.

I have followed all the instructions and successfully installed Ubuntu onto my very old laptop. Now when I come to log in I get the dual boot screen. I select Ubuntu, kernel 2.6.15-28-386 and then, I get my problems. 
 
Firstly I get a message in the log "ACPI: Unable to locate RSDP" - but it seems to carry on booting up. 
 
Secondly, I get asked for the ubuntu login: and password. Now I thought I had left the login as ubuntu during the installation process, but obviously, as it wont let me login with ubuntu and the password I thought I used, I am doing something wrong. 
 
Is there anyway around this? 
Ta

---

### Post by Big_Croc7 on 2007-03-14
For the first issue, try adding the following to the kernel line in the grub menu (this is the first menu that appears at boot-up; hightlight the Ubuntu option, then press 'e'): add -noacpi on the end; though if it's working anyway, I'd leave it for now :-)

For the second, a quick way of finding out the username (possibly not the recommended way, but I think it's ok) is to select the recovery option at boot up, then type the following:
```

cd /home
ls

```
This shows the files & folders underneath the /home directory; If your installation is ok, you should have a single folder there - this is your username. :)

---

### Post by cheddarpaul on 2007-03-15
Hey thanks for that.  I followed what you said, found my username and password and then went on to follow the rest of the 'instructions' I have cobbled together for instlux.

Now I get to my login, type in my ubuntu login and Password and get back to another line

paulc@ubuntu: ~$


I am trying to get to the desktop, which I thought would appear and then let me begin to play with it...

What oh what am I doing wrong?

This is a dual boot machine with Win2k and Ubuntu.

Ta

---

### Post by cheddarpaul on 2007-03-16
I have tried startx but get back a "command not found" error message.... any ideas what I am doing wrong?

---

### Post by Big_Croc7 on 2007-03-16
hmm... not sure; it sounds like the Xserver - the package that handles graphics - isn't installed, or isn't installed properly; I'm not familiar with the instlux route, so can't provide much more help.  One thing you could try is the following:
```
sudo aptitude install ubuntu-desktop 
```
 - that will install the ubuntu-desktop package, which includes the xserver, gnome and loads of other stuff and should make sure everything's there (it may take a while though, if it needs to download packages from the internet - could be ~300Mb download or something).  It should be safe, if it's there already it shouldn't change anything.

---

### Post by cheddarpaul on 2007-03-16
I aint connected to the internet, so when I tried sudo aptitude install ubuntu-desktop I immediately got back to the command line.

How can I remove ubuntu from my laptop and then try the install again?

---

### Post by Big_Croc7 on 2007-03-19
The easiest way to start again, from scratch, is usually to delete the partition; you can do this from windows if you're familiar with fdisk (if not, you might make your system unbootable - not recommended in this case! be careful not to delete the bootloader).  I can't really help anymore as I've never tried the instlux route; maybe someone else can.
As an aside, is there really no other way to boot the machine except the hardisk? That seems quite a, um, risky design!

---

