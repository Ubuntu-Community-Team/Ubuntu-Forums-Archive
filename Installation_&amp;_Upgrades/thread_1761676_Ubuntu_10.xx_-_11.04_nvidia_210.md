---
title: "Ubuntu 10.xx - 11.04 nvidia 210"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by atb-nl on 2011-05-18
Hello,
I have an problem with login in to a fresh installed Ubuntu with the nvidia drivers (graphics card nvidia 210),
so far I have installed Ubuntu 10.04,Ubuntu 10.10 and Unbuntu 11.04,they all seem to have the same problem. when I log in the screen goes black and the pc's hangs... I can switch to a terminal before I login and everything seems operational. I can login to Ubuntu with a fail save x session.

please help :)

---

### Post by dino99 on 2011-05-18
its time to watch your logs closely (/var/log, /home/user/.xsession-errors)

---

### Post by Blasphemist on 2011-05-18
> **atb-nl said:**
> Hello,
I have an problem with login in to a fresh installed Ubuntu with the nvidia drivers (graphics card nvidia 210),
so far I have installed Ubuntu 10.04,Ubuntu 10.10 and Unbuntu 11.04,they all seem to have the same problem. when I log in the screen goes black and the pc's hangs... I can switch to a terminal before I login and everything seems operational. I can login to Ubuntu with a fail save x session.

please help :)

In this thread, there is a troubleshooting flow that includes this issue. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Here are the steps most relevant to you. I made the description of what I think you'll use blue.
> Step 3. From the Grub Menu, try to boot in Rescue mode/low graphics.
- If Yes, look for addtional drivers and install recommended driver.
- If No, goto Step 4 to verify that linux kernel will boot.

Step 4. Can you boot a graphical Xseesion from a text console session? From the command line type 

```
sudo service gdm start
```
- Yes No black screen/No problem... should boot straight from the grub menu.
[COLOR="Blue"]- No. Reboot and start testing and changing gfx_modes and kernel boot graphical modes, still booting into the text console before you try to start an Xsession. Going this way, you will have more of a possible chance to be able to toogle between a graphical session or text terminal session (sometimes). ...and at a text console, at least you have the abilty to install files and make changes to config files. And if you can get back into a command prompt, you could then stop the gdm service that is locked.[/COLOR]

You can stop the gdm service via
```
sudo service gdm stop
```

Digging and opening up the hood:
If you can successfully boot grub, you are at least past point one. You can use grub as a jumping off-point- To test and see what graphical modes do work. Modes in Grub and where the linux kernel boots into does have a direct relationship to mode problems/successes when an Xorg Xsession starts.

Here, I can mention LiveCD'es. See post 3 for notes on using these techniques with a LiveCD. To me, a LiveCD in hand, is a very valuable diagnostics and recovery tool. If you can successfully boot and display a LiveCD on your PC... You are almost there.


---

### Post by atb-nl on 2011-05-18
> **Blasphemist said:**
> In this thread, there is a troubleshooting flow that includes this issue. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Here are the steps most relevant to you. I made the description of what I think you'll use blue.

Oke thanks for the replies,

I have installed the current drivers for my graphics card and I even tried to install the drivers from Nvidia.com but they both have the same outcome: the screen goes black and the pc hangs at the moment I login to the default gnome/unity sessions, this is in Ubuntu 10.04 and Ubuntu 11.04. (both ubuntu-desktop)

Can someone tell me what the problem is, is my graphics card defect or is it a problem between the Nvidia drivers and Ubuntu.
Because it worked before with Ubuntu 10.10, so cant I just downgrade the package that is causing the trouble?

ps.

I have also tried to install xbmc-live with Ubuntu server 10.04
but when I try to start xbmc-live with "xinit" it leaves an white square in the upper left corner of my screen and the pc hangs.
But I don't know if I installed this the correct way, so you can probably ignore this ps.

---

### Post by atb-nl on 2011-05-18
oke, I found out something new.

I can start a Xsesion with sudo service gdm start.
but this was clear because it loads the Ubuntu login screen when I boot. but when try to start an gnome session it hangs and I cant switch to a terminal. BUT I can log in to the machine with ssh.
so it doesn't hang completely it just doesn't listen to my keyboard any more, 

I tried to stop the Xsession with sudo service gdm stop through the ssh. but this doesn't work left it for 5 minutes before I terminated the command with Ctrl c

---

### Post by Blasphemist on 2011-05-18
Following the link I posted should allow you to get more detail. There is much about nvidia issues. Likely the change is kms is now enabled and it needs to be for natty and nvidia. Try this and look further into the link I posted.
> The "nomodeset" kernel bootline switch usually works for most nVidia cards, but now all.

Especially for nvidia cards, I usually just into a text mode by going to a text console via grub edit ('e") append " text " to the end of the kernel boot line and boot{"ctrl-x') and after a login, type 
```
sudo apt-get install nvidia-current  
sudo nvidia-xconfig
```
then try to start the GUI via
Code:
```
sudo service gdm  start
```


---

### Post by atb-nl on 2011-05-18
> **Blasphemist said:**
> Following the link I posted should allow you to get more detail. There is much about nvidia issues. Likely the change is kms is now enabled and it needs to be for natty and nvidia. Try this and look further into the link I posted.

oke, i have tried to read the link you gave me but I don't understand what grub has to do with the problem, grub is a bootloader and ubuntu boots just fine, only when I try to login to a normal gnome session it hangs.

this is my :0-slave.log file

in /var/log/gdm

```
gdm-simple-slave[1414]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
gdm-session-worker[1455]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
gdm-session-worker[1455]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
gdm-session-worker[1455]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "me"
gdm-session-worker[1455]: pam_unix(gdm:session): session opened for user me by (uid=0)
gdm-session-worker[1455]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0

```

it shows warnings and warnings aren't good... 

maybe this is my problem because I can start gdm, but when i login it hangs ...

---

### Post by Blasphemist on 2011-05-18
I know the post I referred to is long and complex. You really do need to follow it though. Kernel mode-setting is now enabled. **Kernel mode-setting (KMS) shifts responsibility for selecting and setting up the graphics mode from X.org to the kernel.** When X.org is started, it then detects and uses the mode without any further mode changes. Kernel mode-setting is controlled in grub2. 

If you'll walk through the troubleshooting information, it will help.

---

### Post by atb-nl on 2011-05-18
> **Blasphemist said:**
> I know the post I referred to is long and complex. You really do need to follow it though. Kernel mode-setting is now enabled. **Kernel mode-setting (KMS) shifts responsibility for selecting and setting up the graphics mode from X.org to the kernel.** When X.org is started, it then detects and uses the mode without any further mode changes. Kernel mode-setting is controlled in grub2. 

If you'll walk through the troubleshooting information, it will help.

Oke thanks. 
why doesn't Ubuntu or grub or whomever is faulty come with an update for this problem, because it isn't just Ubuntu 11.04 that is affected all the Ubuntu's I tried suddenly don't work any more. where it worked fine before.

ill keep reading the post thanks for your help ...

---

