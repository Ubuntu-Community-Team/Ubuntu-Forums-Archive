---
title: "After Upgrade to Lubuntu 18.04, update fails"
date: 2018-08-17
forum: Installation &amp; Upgrades
---

### Post by BlueAZ on 2018-08-17
Hello,   I have Lubuntu on a little Toshiba netbook, and I love it!  I just upgraded to Lubuntu 18.04 via Software Updater; it worked like a charm!  So grateful to have it working, as my desktop died, so I'm shopping for components with the netbook.  Seemed like all was well, then Software Updater popped up with a kernel update.  I directed it to Install ( yes, connected to internet ;)  and it started to, but then it just disappeared.  So i tried the T: sudo apt-get update and this is what I got:
blue-TOSHIBA-NB255:~$ sudo apt-get update
[sudo] password for blue: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]    
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Fetched 172 kB in 2s (90.6 kB/s)                                               
Reading package lists... Done

Then it returns to ...:~$  and I don't know what to do next.  Do I have to manually add these sources?  If so, how?
Many Thanks!!

---

### Post by Dennis N on 2018-08-17
after **sudo apt-get update**, you need to run **sudo apt-get upgrade**.

---

### Post by tea for one on 2018-08-17
> **BlueAZ said:**
>                   
Fetched 172 kB in 2s (90.6 kB/s)                                               
Reading package lists... Done

After the package lists were read, did you not see something like this comment:-
> 
4 packages can be upgraded. Run 'apt list --upgradable' to see them

```
sudo apt update
``` - checks the sources to see if there are any newer versions of your installed packages

```
sudo apt upgrade
``` - downloads and installs the packages.

---

### Post by BlueAZ on 2018-08-17
Ah... thank you!  Done!

---

### Post by BlueAZ on 2018-08-17
Added note for anyone having this issue, I did have to run the sudo apt-get update and sudo apt-get upgrade commands a couple times before I got the Terminal to prompt me with 'apt list --upgradable'.  Did that.  Then I checked with Software Updater and it asked me to do a ReBoot.  All done, but when I check Software updater now it tells me my cached software list needs to be refreshed; I tell it to and it does.  But then it asks again...

---

### Post by geofftf on 2018-08-18
A fresh install of 18.04 should fix the problem.

---

### Post by BlueAZ on 2018-08-18
This installation is now working perfectly!!  After another reboot.  A fresh install would have been nice, but I just didn't have time.  The upgrade is plenty good for this little backup netbook.  Kudos to the developers!!  I shall now mark this SOLVED!!!

---

### Post by BlueAZ on 2018-08-23
OK, now it's getting annoying.  There's a new kernel version to update to, but Lubuntu Software Updater is again crashing without installing it.  I went through the same (above) steps in Terminal, but it's still not installing.  it just lists the sources it's available from without giving me any option to install them.
Could someone please direct me in how to install the Bionic sources so my system will update properly?
Many Thanks!

---

### Post by Impavidus on 2018-08-24
I don't get the problem exactly. Can you run these two commands and show the output? First to check for updates:```
sudo apt update
```Then to install the updates```
sudo apt upgrade
```It should be possible to do this via the GUI, but if you have problems, the terminal is easier, not least because it allows easier communication with us.

---

### Post by sdreelin on 2018-08-24
I have the exact same issue after upgrading to 18.04. The issue is anytime an elevation in privledges is needed, the app requesting it closes. Since kernel updates require elevated privledges, when it tries to pop up the box to authenticate, it closes instead. Synaptic Package Manager which requires it upon start does the same thing and when I tired to install a package using GDebi, it also closes when prompting for privledges. It seems to also be related to the LXDE desktop in my case. I installed the newer LXQt desktop and logged in using that and the prompts work. That said, that desktop doesn't render well on my ancient PC.

---

### Post by BlueAZ on 2018-08-24
> **Impavidus said:**
> I don't get the problem exactly. Can you run these two commands and show the output? First to check for updates:```
sudo apt update
```Then to install the updates```
sudo apt upgrade
```It should be possible to do this via the GUI, but if you have problems, the terminal is easier, not least because it allows easier communication with us.

OK, thanks!  I was using command [HTML]sudo apt-get[/HTML]  And it wasn't working.  Using command [HTML]sudo apt[/HTML] did work.  is this a permanent change in commands?
I still don't see the Bionic sources in Software and Updates.  How do I get them to load?
Thanks again

---

### Post by Impavidus on 2018-08-24
apt and apt-get do more or less the same. apt is newer. It's a bit smarter, but apt-get is more stable in the sense that it shouldn't change in future versions of Ubuntu. But either should work. So what does sudo apt update tell you? And what's in your sources? See the file /etc/apt/sources.list and the directory /etc/apt/sources.list.d.

---

### Post by weltering on 2018-11-23
+1 on this with respect

After upgrade software updater GUI closes automatically on clicking "Install Now" after message "starting service" or some such.
CLI update, upgrade and dist-upgrade work without any problems.

Just FYI

:guitar:

---

