---
title: "Upgrade to 24.04 (from 23.10) failed to complete, UI all message up"
date: 2024-05-30
forum: Installation &amp; Upgrades
---

### Post by John_Manko on 2024-05-30
The installation didn't complete as normal, ending about 90% through.  Here is an error during upgrade (another one related to thunderbird-locale-en and thunderbird-locale-en-us occurred):

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293825&stc=1[/IMG]


After reboot:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293826&stc=1[/IMG]

I can mouse over the missing text and it appears, but as soon as the window loses focus it's gone again.

Also, I have two monitors, but a third "Unknown Display" is showing in Display Settings.  Additionally, in order to mouse from the left monitor to the right (include window dragging), I have mouse to the left off-screen, not the right as it should be (and vice versa).

```
&#10095; sudo apt update --fix-missing
Hit:1 http://us.archive.ubuntu.com/ubuntu noble InRelease
Get:2 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]                 
Hit:3 https://download.docker.com/linux/ubuntu jammy InRelease                                                             
Hit:4 https://apt.releases.hashicorp.com lunar InRelease                                                                   
Get:5 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]                           
Hit:6 https://updates.signal.org/desktop/apt xenial InRelease                             
Hit:7 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease                      
Get:8 http://security.ubuntu.com/ubuntu noble-security/main i386 Packages [69.1 kB]
Get:9 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [88.0 kB]
Get:10 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [24.5 kB]
Get:11 http://security.ubuntu.com/ubuntu noble-security/universe i386 Packages [20.8 kB]
Get:12 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [34.9 kB]
Get:13 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [13.4 kB]
Fetched 503 kB in 1s (633 kB/s)                                     
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done


&#10095; sudo apt install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

&#10095; sudo dpkg --configure -a
&#10095; sudo dpkg -l | grep ^..R
&#10095; sudo apt clean
&#10095; systemctl daemon-reload

```


Everytime I upgrade Ubuntu it's a *$%^& nightmare.  

Help would be appreciated.

---

