---
title: "Lucid Startup Message"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by PatK100 on 2010-03-03
Hello Team
 
 
Just installed Lucid on a Dell D610 laptop that has a broadcom wireless network adapter, I can see when I boot up the system there is a message coming out about this adapter but it goes to fast to read.
 
Is there anyway I can slow down the boot messages so they can be read or indeed can anyone tell me what the message is about the braodcom driver that is being output.
 
Mnay thanks
 
 
 
Pat

---

### Post by Kevbert on 2010-03-03
If you can't connect to wireless, it means that you need to install the firmware drivers which weren't installed by default.
What is the terminal output of
```
lspci 
```
Assuming that your using the standard b43 wireless adapter the drivers are attached. just extract them to your home folder and then copy the two directories to /lib/firmware

---

### Post by PatK100 on 2010-03-03
Thank you I will give it a go

---

### Post by PatK100 on 2010-03-04
You do not have permission to extract to this directory

But I am an Administrator - please explain what I am doing wrong

---

### Post by jrothwell97 on 2010-03-04
Even if you are an administrator, by default Ubuntu runs in "normal user" mode (it's more secure this way). You need to elevate it to give that particular program administrator permissions - the way to do this is put the word "sudo" beforehand, like so:

```
sudo lspci
```

It'll ask for your password, and when you enter it nothing will appear on the screen - no stars, no bullets, nothing. Don't worry, it's still going in - enter it as normal and press Enter, and it should work.

---

### Post by Kevbert on 2010-03-04
You can't extract to the /lib/firmware directory without giving administration privileges. That's why I suggested you extract to your home directory first. If you then want to copy the files with nautilus (the file manager) you can then use
```
gksudo nautilus
```
which will give you the ability to copy to any directory (graphically) via nautilus (or alternatively just use that command and you should be able to extract anywhere - I just found that out!)

---

### Post by PRC09 on 2010-03-04
I have the same laptop and the easiest way to install the wireless was just  connect via cable,do the updates and then check in System > Admin > Hardware Drivers and activate the driver.Reboot and the wireless works just fine. I have seen many people downloading this and that and extracting this here and move that there type of install but the drivers are readily available in the Hardware Drivers......

---

### Post by Kevbert on 2010-03-05
The problem with downloading hardware drivers is that a lot of people don't have the option of connecting to the web via a wired connection. The ideal option is the one suggested by PRC09.

---

### Post by PatK100 on 2010-03-15
All working now by connecting with a cable and doing the upgrade.

Many thanks


Pat

---

