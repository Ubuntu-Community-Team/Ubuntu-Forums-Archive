---
title: "hosed active kernel and won't update now"
date: 2023-09-18
forum: Installation &amp; Upgrades
---

### Post by garyt53 on 2023-09-18
Wow, it worked!  Yeah, been awhile.

Hi Y'all

Haven't done anything REAL stupid in a while now, but I "accidentally" removed my active kernel in 14LTS in Synaptic (images only), realized it at last min, and rebooted into a misbehaving desktop.  Went to previous kernel and removed all of hosed kernel and tried to regain my deleted update....but nuthin.  So I broke something.  Terminal mentioned a file failed, I think "itools" or "iptools".  Searched the forums and ether and now here I am.  This had to have happened before don'tchathink?

Wouldn't need you if I had continued my backups but moved in here 2yrs ago and, well....I'm 70 and that move almost took me out, so I still haven't completely moved in.  If I do it'll be like Christmas 'cause I will find so many things I don't even remember I have! ha

Okay, will stay on the point now.  And thanks in advance, and especially the help you have provided in the past.  It should only take a few of these posts/replies to restore my upgrade module.

gt

---

### Post by jonathanmichael on 2023-09-18
[size=3][b][color=red]Note from forum staff:

Please do NOT follow this synthetic "advice" which is poor. The text below, now struck out, is unattributed output from an AI source, probably ChatGPT. The forum account has been banned, but this post has not been removed because it has drawn the attention of contributing members to this thread and has been referred to here.

Repeat: please do NOT give this post any credence.[/color][/b][/size]

[s]Hello,


It sounds like you're dealing with a kernel-related issue in your Ubuntu 14.04 LTS system. If you accidentally removed your active kernel and are experiencing problems, here are some steps you can take to recover:


Boot into a Working Kernel: It's great that you've already booted into a previous kernel that works. Make sure you are in a stable environment before proceeding.


Reinstall the Kernel: You can try to reinstall the missing kernel. In the terminal, run:


bash


sudo apt-get install --reinstall linux-image-$(uname -r)
This command will attempt to reinstall the kernel image for the currently running kernel (replace $(uname -r) with the actual kernel version).


Update Grub: After reinstalling the kernel, update the Grub bootloader to ensure it recognizes the new kernel:


bash


sudo update-grub
Check for Missing Dependencies: If you received an error related to a missing file called "itools" or "iptools," you may want to check for any missing or broken packages and try to fix them:


bash


sudo apt-get install -f
Perform System Updates: After resolving any issues with the kernel, it's a good practice to update your system to ensure it's up to date:


bash


sudo apt-get update
sudo apt-get upgrade
These steps should help you recover your system after accidentally removing the active kernel. If you encounter any specific errors during this process or have further questions, please provide additional details so that I can assist you more effectively.[/s]

---

### Post by MAFoElffen on 2023-09-18
@jonathanmichael -- 
Welcome to the Forum. As this is your first Post here, you must not have read the Forum Posting Guidelines...

Please go back to your Post #2, Select "Edit Post" > "Advanced Edit"... Select the text of the command blocks individually, then select the "#" icon, to wrap the commands in BB Format Code Tags.

Or, since you have shown a bit of skill will commands, you could add them manually like this:

[noparse]```

The commands
or output
that needs to be wrapped

```[/noparse]

It is a Forum Policy to wrap all commands ad raw output within CODE Tags. Not doing so does weird things to the Forums Software... Besides making it easier to read, and ID's such as being special.

Just trying to keep you out of trouble with the Admin's and Moderators.

@GaryT53... The last post will help... but with some modifications to his commands. He didn't read the details of your Original Post, to notice that you are now booted on the the next in line, earlier kernel, which you then removed, the remnants of what was the default/hosed kernel. So the shortcut of using anything with the expanded variable of 
```

$(uname -r)

```
...is going to point to the booted (older) kernel, which is still working and does not need repair, and [COLOR=#ff0000]you do not want to mess with[/COLOR]. That would **not** be the kernel you need to reinstall. For 14.04.5, it ended with something like linux-image-linux-image-3.13.0-24-generic or linux-image-4.4.0-134-generic, depending on the installed hardware stack... I can't remember.

14.04 LTS went end of life in April 30th 2019... there were no updates to it after that date. Unless you are on ESM, it is insecure and the version of the browser would get many errors, because it does not have current SSL Certs. Why are you still using it? Sentimental Reasons? Old Hardware? Even if you have ESM, that ends in 7 months. About the same time 24.04 LTS is released.

Before advising on a repair, is there a reason why this cannot be brought up as something more current, that would currently be supported? You could do a backup of your data and migrate to a newer release that would be secure. Right?

---

### Post by garyt53 on 2023-09-26
Hi Jonathan !

Your reply was so fast.  Mine taking a week really looks bad.

Did what you suggested and it recreated the damaged kernel 244 even missing internet and other apps.  The terminal history of that is as follows:

```

garyt@garyt-8400p:~$ uname -r 
4.4.0-244-generic 
garyt@garyt-8400p:~$ sudo apt-get update 
[sudo] password for garyt: 
Ign http://mirrors.accretive-networks.net trusty InRelease 
Ign http://mirrors.accretive-networks.net trusty-updates InRelease 
Ign http://mirrors.accretive-networks.net trusty-backports InRelease 
Err http://archive.canonical.com trusty InRelease 
  
Ign http://extras.ubuntu.com trusty InRelease 
Err http://security.ubuntu.com trusty-security InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Ign http://dl.google.com stable InRelease 
Err http://mirrors.accretive-networks.net trusty Release.gpg 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates Release.gpg 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://archive.canonical.com trusty Release.gpg 
  Could not resolve 'archive.canonical.com' 
Err http://extras.ubuntu.com trusty Release.gpg 
  Cannot initiate the connection to extras.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) [IP: 2620:2d:4000:1::19 80] 
Err http://security.ubuntu.com trusty-security Release.gpg 
  Could not resolve 'security.ubuntu.com' 
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty InRelease 
  
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://mirrors.accretive-networks.net trusty-backports Release.gpg 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Ign http://mirrors.accretive-networks.net trusty Release 
Ign http://extras.ubuntu.com trusty Release 
Err http://dl.google.com stable Release.gpg 
  Cannot initiate the connection to dl.google.com:80 (2607:f8b0:400a:801::200e). - connect (101: Network is unreachable) [IP: 2607:f8b0:400a:801::200e 80] 
Ign http://mirrors.accretive-networks.net trusty-updates Release 
Ign http://mirrors.accretive-networks.net trusty-backports Release 
Ign http://extras.ubuntu.com trusty/main amd64 Packages/DiffIndex 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err http://ppa.launchpad.net trusty Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Ign http://dl.google.com stable Release 
Ign http://mirrors.accretive-networks.net trusty/main amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty/restricted amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty/universe amd64 Packages/DiffIndex 
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex               
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                  
Ign http://mirrors.accretive-networks.net trusty/multiverse amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty/main i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty/restricted i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty/universe i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty/multiverse i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-updates/main amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-updates/restricted amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-updates/universe amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-updates/multiverse amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-updates/main i386 Packages/DiffIndex 
Err http://dl.google.com stable/main amd64 Packages                
  
Ign http://mirrors.accretive-networks.net trusty-updates/restricted i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-updates/universe i386 Packages/DiffIndex 
Err http://dl.google.com stable/main amd64 Packages                            
  
Ign http://mirrors.accretive-networks.net trusty-updates/multiverse i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/main amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/restricted amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/multiverse amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/universe amd64 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/main i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/restricted i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/multiverse i386 Packages/DiffIndex 
Ign http://mirrors.accretive-networks.net trusty-backports/universe i386 Packages/DiffIndex 
Err http://dl.google.com stable/main amd64 Packages                
  
Err http://dl.google.com stable/main amd64 Packages                
  
Err http://dl.google.com stable/main amd64 Packages   
  Cannot initiate the connection to dl.google.com:80 (2607:f8b0:400a:801::200e). - connect (101: Network is unreachable) [IP: 2607:f8b0:400a:801::200e 80] 
Err http://extras.ubuntu.com trusty/main amd64 Packages 
  Cannot initiate the connection to extras.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) [IP: 2620:2d:4000:1::19 80] 
Err http://extras.ubuntu.com trusty/main i386 Packages 
  Cannot initiate the connection to extras.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) [IP: 2620:2d:4000:1::19 80] 
Err http://mirrors.accretive-networks.net trusty/main amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty/restricted amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty/universe amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty/multiverse amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty/main i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty/restricted i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty/universe i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty/multiverse i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/main amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/restricted amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/universe amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/multiverse amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/main i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/restricted i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/universe i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-updates/multiverse i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/main amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/restricted amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/multiverse amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/universe amd64 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/main i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/restricted i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/multiverse i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Err http://mirrors.accretive-networks.net trusty-backports/universe i386 Packages 
  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 
Ign https://esm.ubuntu.com trusty-infra-security InRelease 
Ign https://esm.ubuntu.com trusty-infra-updates InRelease 
Ign https://esm.ubuntu.com trusty-infra-security Release.gpg 
Ign https://esm.ubuntu.com trusty-infra-updates Release.gpg 
Ign https://esm.ubuntu.com trusty-infra-security Release 
Ign https://esm.ubuntu.com trusty-infra-updates Release 
Ign https://esm.ubuntu.com trusty-infra-security/main amd64 Packages/DiffIndex 
Ign https://esm.ubuntu.com trusty-infra-security/main i386 Packages/DiffIndex 
Ign https://esm.ubuntu.com trusty-infra-updates/main amd64 Packages/DiffIndex 
Ign https://esm.ubuntu.com trusty-infra-updates/main i386 Packages/DiffIndex 
Err https://esm.ubuntu.com trusty-infra-security/main amd64 Packages 
  Could not resolve host: esm.ubuntu.com 
Err https://esm.ubuntu.com trusty-infra-security/main i386 Packages 
  Could not resolve host: esm.ubuntu.com 
Err https://esm.ubuntu.com trusty-infra-updates/main amd64 Packages 
  Could not resolve host: esm.ubuntu.com 
Err https://esm.ubuntu.com trusty-infra-updates/main i386 Packages 
  Could not resolve host: esm.ubuntu.com 
Reading package lists... Done 
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/alexmurray/indicator-sensors-daily/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/atareao/atareao/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/blue-shell/firefox-kde/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/diesch/testing/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/heyarje/libav-11/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/nrbrtx/sysvinit-backlight/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/saiarcot895/myppa/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/Release.gpg  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/Release.gpg  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/Release.gpg  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'archive.canonical.com' 

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Cannot initiate the connection to extras.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) [IP: 2620:2d:4000:1::19 80] 

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/alexmurray/indicator-sensors-daily/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/atareao/atareao/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/blue-shell/firefox-kde/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/diesch/testing/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 
 
W: Failed to fetch http://ppa.launchpad.net/heyarje/libav-11/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/nrbrtx/sysvinit-backlight/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Cannot initiate the connection to dl.google.com:80 (2607:f8b0:400a:801::200e). - connect (101: Network is unreachable) [IP: 2607:f8b0:400a:801::200e 80] 

W: Failed to fetch http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/saiarcot895/myppa/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu/dists/trusty/Release.gpg  Could not resolve 'ppa.launchpad.net' 

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  Cannot initiate the connection to extras.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) [IP: 2620:2d:4000:1::19 80] 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/main/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/restricted/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/universe/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  Cannot initiate the connection to extras.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) [IP: 2620:2d:4000:1::19 80] 

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages  Cannot initiate the connection to dl.google.com:80 (2607:f8b0:400a:801::200e). - connect (101: Network is unreachable) [IP: 2607:f8b0:400a:801::200e 80] 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/multiverse/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/main/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/restricted/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/universe/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty/multiverse/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/main/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/main/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/dists/trusty-backports/universe/binary-i386/Packages  Cannot initiate the connection to mirrors.accretive-networks.net:80 (216.127.35.166). - connect (101: Network is unreachable) 

W: Failed to fetch https://esm.ubuntu.com/ubuntu/dists/trusty-infra-security/main/binary-amd64/Packages  Could not resolve host: esm.ubuntu.com 

W: Failed to fetch https://esm.ubuntu.com/ubuntu/dists/trusty-infra-security/main/binary-i386/Packages  Could not resolve host: esm.ubuntu.com 

W: Failed to fetch https://esm.ubuntu.com/ubuntu/dists/trusty-infra-updates/main/binary-amd64/Packages  Could not resolve host: esm.ubuntu.com 

W: Failed to fetch https://esm.ubuntu.com/ubuntu/dists/trusty-infra-updates/main/binary-i386/Packages  Could not resolve host: esm.ubuntu.com 

W: Some index files failed to download. They have been ignored, or old ones used instead. 
garyt@garyt-8400p:~$ sudo apt-get upgrade 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Calculating upgrade... Done 
The following packages will be upgraded: 
  iucode-tool 
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 29.6 kB of archives. 
After this operation, 1,024 B of additional disk space will be used. 
Do you want to continue? [Y/n] y 
WARNING: The following packages cannot be authenticated! 
  iucode-tool 
Install these packages without verification? [y/N] y 
Err http://mirrors.accretive-networks.net/ubuntu/ trusty-backports/multiverse iucode-tool amd64 1.0.3-1~ubuntu14.04.1 
  Could not resolve 'mirrors.accretive-networks.net' 
E: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/pool/multiverse/i/iucode-tool/iucode-tool_1.0.3-1~ubuntu14.04.1_amd64.deb  Could not resolve 'mirrors.accretive-networks.net' 

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
garyt@garyt-8400p:~$ sudo apt-get upgrade --fix-missing 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Calculating upgrade... Done 
The following packages will be upgraded: 
  iucode-tool 
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 29.6 kB of archives. 
After this operation, 1,024 B of additional disk space will be used. 
Do you want to continue? [Y/n] y 
WARNING: The following packages cannot be authenticated! 
  iucode-tool 
Install these packages without verification? [y/N] y 
Err http://mirrors.accretive-networks.net/ubuntu/ trusty-backports/multiverse iucode-tool amd64 1.0.3-1~ubuntu14.04.1 
  Could not resolve 'mirrors.accretive-networks.net' 
E: Failed to fetch http://mirrors.accretive-networks.net/ubuntu/pool/multiverse/i/iucode-tool/iucode-tool_1.0.3-1~ubuntu14.04.1_amd64.deb  Could not resolve 'mirrors.accretive-networks.net' 

garyt@garyt-8400p:~$ 

```

Hope I did that right.  Let me know.  Back on fully functional previous kernel 243 that won't update to 244.

The reason I have not migrated above 14LTS is I tried....twice.  And lost sooo much of my customizations I just reinstalled the BU.  Was really squeezed when, unlike Win, you folks provided free updates for older versions and everything was going so smooth till I deleted the current ver 244 in Synaptic.  Kinda like what's happened to the world lately huh.

Please advise, and if I've done anything wrong here (it's been so long).

gt

---

### Post by garyt53 on 2023-09-26
oops, code wrap backslash should be slash huh

---

### Post by garyt53 on 2023-10-05
Hi -

Again, trying to recover kernel I mistakenly removed in Synaptic overdoing the clean up after upgrade, I tried your suggestions and reinstalled kernel in terminal and still broken...works but still skewed with no network connect and won't upgrade.  Backup kernels work but still won't upgrade anymore either.
[B]
How 'bout I try the fix broken from the recovery option of the faulty kernel at boot?  Could that wreck the backup kernels I still have working[/B]?

At 70 my life has become so dependent on this thing....too old to go running around to get things done now.

gt

---

### Post by coffeecat on 2023-10-05
@garyt53, please read the addition I have made to post #2. I'm sorry you have been misled and had your time wasted by a spammer who attempted to slip in under the radar by posting superficially plausible rubbish generated by AI. Please disregard that post. It has only served to distract you.

With regard to your 14.04 installation, you have already been told that it is now unsupported and also a security risk if exposed to the internet. I note that you have previously experienced problems upgrading to a supported release. Notwithstanding that, the only sensible advice, imo, that anyone can offer in your situation is for you to back up your personal files and to make a fresh installation of a supported release. If you need help with customisations, or anything else, you are very welcome to start a new thread for that.

By the way, I am much older than 70 and this is what I would do if in your situation, without regard to my age.

---

### Post by garyt53 on 2023-10-05
This thread unsolved but closed by poster.

garyt53

---

### Post by garyt53 on 2023-10-22
**Solved, by simply restarting/enabling snapd!**  Hope this helps someone else if they are careless enough to clean up the running kernel by mistake. ha

---

