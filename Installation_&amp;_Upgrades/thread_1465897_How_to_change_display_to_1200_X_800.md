---
title: "How to change display to 1200 X 800 ?"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by ASP__DEVELOPER on 2010-04-29
I have installed Ubuntu 10.4 on Virtual Box, i have installed it successfully, the only problem is when i check the display settings it only have 2 options : 600 X 400 and 800 X 600

and this makes it difficult to work on Ubuntu as 800 X 600 is half the size of my desktop

Please guide me how i can increase / configure the display settings so that atleast i can fit ubuntu screen into my screen size.

---

### Post by bmuluu on 2010-04-29
Start by installing the Virtual Box guest additions. 
If the guest OS is running, pressing <Ctrl + D> should mount
the Guest Additions CD into the virtual machine.
Run the installer - GUI or command line - whatever you prefer.
Reboot after installing the additions.
When you login you should be able to get into "true" full screen mode.

---

### Post by ASP__DEVELOPER on 2010-04-29
I did install the addition application, restarted the OS but still i don't see any display resolution 1200 X 800, tried pressing ctrl+D nothing happens, after installing i saw it updated mouse cursor now i don't have to press ctrl key again n again to enter into the ubuntu OS but still struggling with the resolution as it's too small, please guide me (here is the screen shot of my screen after installing the addition app)



[IMG]http://img94.imageshack.us/img94/3/ubuntu10.jpg[/IMG]

---

### Post by ASP__DEVELOPER on 2010-04-30
Anyone ? please help

---

### Post by bmuluu on 2010-05-04
I have not tried out the final version of Lucid in Virtual Box.
I tried out one of the alphas and it worked fine.

I installed the Virtual box additions
```
cd /cdrom
``````
./VBoxLinuxAdditions-<your-architecture-here>.run
```reboot the guest OS

On logging in, you can switch to full screen mode by pressing Host Key + F
or by going to the System >> Preferences >> Display and select your desired resolution.
(assuming that is what is used in Lucid).

After installing the Guest additions, you should pretty much have full display capability.

---

