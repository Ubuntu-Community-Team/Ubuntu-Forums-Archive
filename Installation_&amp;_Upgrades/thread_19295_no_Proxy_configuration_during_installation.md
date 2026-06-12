---
title: "no Proxy configuration during installation"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by ymeyer on 2005-03-11
I failed to install Ubuntu preview 5.04 probably because I am behind a proxy and no proxy configuration seems to be possible during the install followed. Apparently the last step of the installation requires a network connection which block the computer.
In addition this failed install destroyed my multiboot!
Similar problems? Is a workaround possible?

Thanks

---

### Post by mips on 2005-03-13
[http://www.ubuntuforums.org/showthread.php?t=7340&highlight=proxy](http://www.ubuntuforums.org/showthread.php?t=7340&highlight=proxy)

cheers
mips

---

### Post by ymeyer on 2005-03-14
Thanks, but this can work if Ubuntu start. This was possible  with previous release,  when you choose not to accept the updates during the installation.
In the last release their is no longer the possibility to refuse the network updates and the network connection fail due to the absence of proxy configuration.
I think that it is important for people working behind a proxy to give the possibility to configure the proxy early during installation.

---

### Post by mips on 2005-03-14
ymeyer,

I find this hard to understand. You are implying that every stand alone PC will not be able to install 5.04 without a network connection. It should be able to install fine on a standalone PC. 

Disconnect the LAN cable from the LAN card. Maybe if the installer sees the interface as being down/disconnect it wont attemp to auto configure the network settings.

Alternatively use the EXPERT install mode and skip the network section.

I'm sure I was prompted to retrieve updates from the network to which you can say NO.

Are you using the standard preview or the ARRAY6 version ? I also had a problem with the standard version grub installation, array6 worked fine 4 me. To fix my grub/dualboot problem I simply installed Warty and then my dualboot worked again. This might sound stupid(long way) but i did not know any better.

Try the array6 ISO image. much better and it does not try to install 350MB over the network during initial install.

Let us know how it goes.

cheers
mips

---

### Post by ymeyer on 2005-03-15
Many thanks Mips,

   You are right, I have not got any difficulties with array 6 to install Ubuntu. The problem is with the official preview.  I hope that this will be corrected in the definitive release.

---

### Post by mips on 2005-03-16
I'm sure it wont happen in the final release. The final release will more closely resemble the highest arry version.

cheers
mips

---

### Post by mikis on 2005-03-27
I'm on a computer with no network connection  -- it has network adapter, enabled but not connected, and plain modem. Installation takes like forever because of this (Testing Network Repository...). There should be "Skip" button on that screen, IMHO.

---

### Post by mips on 2005-03-29
What version are you running ? Warty, Hoary preview/array7/current ?

---

### Post by mikis on 2005-03-29
I'm running: Ubuntu 5.04 "Hoary Hedgehog" - Preview i386 Binary-1, downloaded as ISO image two weeks ago.

---

### Post by mips on 2005-03-30
Try the latest Array version (7 I think) or the Current version. The preview version does  seem to have the problem you mentioned.

Alternatively wait another week for the official release of Hoary, 6Apr05.

Cheers
mips

---

### Post by mikis on 2005-03-30
I think I'll wait for official release version.

Is there an easy way to upgrade from preview to final, as I'm on dial-up, and downloading full ISO is not an option?

---

### Post by mips on 2005-03-31
> Is there an easy way to upgrade from preview to final, as I'm on dial-up, and downloading full ISO is not an option?

You can use Synaptic Package manager which is under system on the toolbar as weel as the update manager. From the command line you can type:
sudo apt-get update
sudo apt-get upgrade

The upgrade would take you forever on dialup as the changes implemented between preview and final release will be huge. It will be on the order of a couple hundred megs of data.

I would advise you to download the .ISO once available, maybe a friend has broadband or something like that.

Your other option would be to get a FREE Hoary CD from Ubuntu by signing up for the shipit service at   [http://shipit.ubuntulinux.org/](http://shipit.ubuntulinux.org/)    only thing is you are going to wait a bit longer for the CD but hey it is for free.


cheers
mips

---

### Post by dhaneshr on 2005-04-11
[QUOTE=mips]I'm sure it wont happen in the final release. The final release will more closely resemble the highest arry version.

cheers
mips[/QUOTE]


Unfortunately, the problem *persists* even in the final version. I pulled out the Ethernet cable and after some time the installer proceeded to the next step ```
Testing Security Update Repository...
``` . I'm still waiting for this step to complete (hopefully) or else I may have to spend another afternoon re-installing Ubuntu as multiboot. This step has to have a **[COLOR=Red]SKIP[/COLOR]** button.

dhaneshr

---

### Post by buo on 2005-04-13
I want to confirm that there is a problem. I'm trying to install the 5.04 release.

I'm behind a proxy. The installation stops at "testing network repositories". I waited about ten minutes before restarting the machine.

There should be either:
  a) a way to skip this step (without forcing you to go to expert install)
  b) a way to set your proxy (without forcing you to go to expert install)
  c) a reasonable timeout, after which the installer assumes your network doesn't work and proceeds with the install.

I'm off to try again after disconnecting the network cable to see if it makes any difference.

---

### Post by buo on 2005-04-13
Well, disconnecting the network cable sort of works. I was able to finish the installation, but now I have no network. I'm off to look for help on how to set it up.

---

### Post by buo on 2005-04-14
I tried the following:

* Normal install without net cable. The install insists on going to the network to "test network repositories" and hangs (I waited 20 minutes this time).

* Expert install, setting up the proxy and letting it go download packages from the net. Again it stopped and hanged at the same spot.

* Expert install, setting up the proxy but telling it not to go look for packages in the net. This allowed me to complete the install, but the result is less than satisfactory. The resulting system is not what I expected from ubuntu; for instance, sudo is not setup.

For the time being I've given up on ubuntu. Maybe it's an oddity of my network or something I'm doing wrong. If anyone needs more info or wants me to test something, let me know.

By the way, on exactly the same machine and network I installed (and I'm using) Debian Sarge with no trouble at all.

---

### Post by geek777 on 2005-06-17
[QUOTE=buo]I tried the following:

* Normal install without net cable. The install insists on going to the network to "test network repositories" and hangs (I waited 20 minutes this time).

* Expert install, setting up the proxy and letting it go download packages from the net. Again it stopped and hanged at the same spot.

* Expert install, setting up the proxy but telling it not to go look for packages in the net. This allowed me to complete the install, but the result is less than satisfactory. The resulting system is not what I expected from ubuntu; for instance, sudo is not setup.

For the time being I've given up on ubuntu. Maybe it's an oddity of my network or something I'm doing wrong. If anyone needs more info or wants me to test something, let me know.

By the way, on exactly the same machine and network I installed (and I'm using) Debian Sarge with no trouble at all.[/QUOTE]
 Almost 2 months later...same "Testing Network Repositories..." error remains.

That is to say...I am inside a large corp env. with proxy servers...I chose standard install (vs. server) of 5.04 Hoary and was never given an option to input an httpd_proxy, and my nix auto configed itself with dhcp.  

Test network repositories hung for > 30 mins...I yanked the cat5 cable out of the ethernet port and then it jumped to 75% complete...but seems to stay there also.

I will keep searching for a solution.

---

### Post by kLy on 2005-07-24
Still stuck here with the same thing also. Any help? I'm sure there are plenty of people stuck behind firewalls that need a proxy configured. Are none of them supposed to be able to install Ubuntu? I see that the same problem also persists in Debian 3.1-r0.

---

### Post by mips on 2005-07-25
Not pretty but give it a try...

[https://wiki.ubuntu.com/HowToInstallUbuntuWhenYouAreBehindProxy?highlight=%28Proxy%29](https://wiki.ubuntu.com/HowToInstallUbuntuWhenYouAreBehindProxy?highlight=%28Proxy%29)

cheers
mips

---

