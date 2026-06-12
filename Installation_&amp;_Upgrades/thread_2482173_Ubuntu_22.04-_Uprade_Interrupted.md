---
title: "Ubuntu 22.04- Uprade Interrupted"
date: 2022-12-22
forum: Installation &amp; Upgrades
---

### Post by desertwalker1 on 2022-12-22
Hey all. I've got a problem with the Ubuntu upgrade. I'm a very casual linux user. First, some background:

A while back I was upgrading to the latest version of Ubuntu. Unfortunately my laptop shut off and the upgrade was interrupted. I was able to restore the OS but now it keeps showing a 'Partial Upgrade' option. 
I believe this means I'm still on version 20.04?
It was working fine regardless however the current issue is in regards to Linux Mint. 

I want to install the latest version of Linux Mint and am going through the installation process on this same computer with the interrupted Ubuntu version. However, I believe the interruption may be hampering my efforts to do so. 

1) Firstly, after installing the iso for the latest version of Mint, I was unable to install libfuse2 in order to create a bootable drive for Mint through balena etcher. 
Here are the commands I used: 
"sudo add-apt-repository universe"
"sudo apt install libfuse2"
However, I got the following error indefinitely running in the terminal:*

2) In order to try and address this error I checked Software Updater. When I opened it, this is what appeared:

I clicked on 'Stop' and got the same old 'Partial Upgrade' message:

I've tried both 'Partial Upgrade' and 'Continue'. However, neither resolves the issue. When I clicked 'Continue' it gave me this:

Hence, I used the "sudo apt-get install -f" command as it suggested and got the following:

As for Software Updater- it merely goes back to the 'waiting for apt to exit' message box. I'm sure this is more simple than it seems to someone like me who has very little knowledge about this stuff. How can I get apt to actually exit and then be on my merry way to install any distro? I will greatly appreciate any advice/solutions to this problem. I hope I've explained this clearly.

Thank you.

---

### Post by #&amp;thj^% on 2022-12-22
wise choice to ask first, can you paste back what this returns from the terminal
```
ps aux | grep -i apt

```
Please no pictures, just the text from the terminal.

---

### Post by Frogs Hair on 2022-12-22
The failed to get exclusive lock error is a result of trying to use more than one package management tool at the same time.

---

### Post by desertwalker1 on 2022-12-23
> **1fallen said:**
> wise choice to ask first, can you paste back what this returns from the terminal
```
ps aux | grep -i apt

```
Please no pictures, just the text from the terminal.

Hi. Thank you for the reply. 

This is the output of that particular command:

root         853  0.0  0.1 129072  9568 ?        Ssl  03:08   0:00 /usr/sbin/thermald --systemd --dbus-enable --adaptive
root        2599  0.0  1.2 200348 103364 ?       SNl  03:09   0:01 /usr/bin/python3 /usr/sbin/aptd
aks1       19092  0.0  0.0   9560  2480 pts/0    S+   10:39   0:00 grep --color=auto -i apt

---

### Post by desertwalker1 on 2022-12-23
> **Frogs Hair said:**
> The failed to get exclusive lock error is a result of trying to use more than one package management tool at the same time.

Thank you for the response. Yes, I understand that vaguely. 

 Back when the upgrade was interrupted, the OS wouldn't boot. I was able to restore it somehow using the internet. Unfortunately I didn't take screenshots of the exact process. 

Ever since then the software updater has had issues. :P I probably should have created a bootable for 22.04 and re-upgraded but I've been using the same version for now.

---

### Post by Frogs Hair on 2022-12-23
> Thank you for the response. Yes, I understand that vaguely.  An example would be, if the software updater is running and encounters errors and you open the terminal and try and correct the problem. Logging out to kill the process and back in and then using the terminal commands to correct the problem can work in some cases.

---

### Post by desertwalker1 on 2022-12-24
If you mean restarting the computer and then trying the fix again with the terminal: I've tried and it hasn't worked yet. I'll give it another shot.

---

