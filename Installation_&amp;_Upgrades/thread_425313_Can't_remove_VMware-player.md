---
title: "Can't remove VMware-player"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Thingymebob on 2007-04-27
So I attempted installing vmware player for no particular reason (just to mess around with) and got the following error

```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I know the issue is something to do with the the madwifi driver etc.... But to be honest, I 'aint that fussed about it and don't want to be messing around with the driver source so decided to just remove it.

When attempting to remove VMware-player I get the following error:
```
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Anyone any ideas of a solution as i'm tired of going through the whole vmware-player install every time I use apt.

---

### Post by zvacet on 2007-04-28
```
sudo apt-get remove --purge program_name
```

program_name =exact vmplayer name

if this don´t work delete vmplayer folder in **etc**

---

### Post by skillet on 2007-04-28
I'm having the same problem... I've been reading about some uninstall script? but I cant find it anywhere on my system. its supposed to be in /usr/bin

---

### Post by KyleYankan on 2007-04-30
I'm getting a similair error. I tried this:

```
kyle@Brandy:/$ sudo apt-get remove --purge vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vmware-player*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 159406 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
kyle@Brandy:/$ sudo apt-get remove --force --purge vmware-player
E: Command line option --force is not understood
```

Then removed /etc/vmware as root, ran the above command and got the same result.

---

### Post by Thingymebob on 2007-05-01
apt-get remove --purge fails in the same way as plain apt-get remove, haven't attempted deleting folder in etc yet although from KyleYankans response I'm guessing this isn't going to work either.

---

### Post by Thingymebob on 2007-05-01
Should have tried this sooner, sorry everyone!
Reboot in single user (Recovery Mode)
```

apt-get remove vmware-player
```
and it disappears quite happily:oops:

---

### Post by speakman on 2007-05-15
Or just:
```
sudo killall vmnet-natd
```

And then:
```
sudo apt-get remove --purge vmware-player
```

Did it for me...

---

### Post by greew on 2007-05-26
> **speakman said:**
> Or just:
```
sudo killall vmnet-natd
```

And then:
```
sudo apt-get remove --purge vmware-player
```

Did it for me...

Yeah.. this did the trick! Thanks a lot!

---

### Post by Andrej_BB on 2007-05-31
I removed the /etc/vmware folder

and ran apt-get remove --purge vmware-player
got this error
> 
(Reading database ... 
dpkg: serious warning: files list file for package `vmware-player-kernel-modules-2.6.20-16' missing, assuming package has no files currently installed.
185355 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player


---

### Post by codeslicer on 2007-06-02
> **speakman said:**
> Or just:
```
sudo killall vmnet-natd
```

And then:
```
sudo apt-get remove --purge vmware-player
```

Did it for me...

Thanks!

---

### Post by skibum58 on 2007-06-13
Slightly off the thread point, I wanted to keep my functioning VMPlayer (ver. 1, from the Applications | Add/Remove menu).  However, every time I wanted to install something else, it would trigger an attempted re-install of the player.  I would decline every overwrite request, and the player kept funtioning (thank God), but it was a growing annoyance.

I found the solution at:
[https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957/comments/8](https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957/comments/8)
and 
[https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957](https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957)

I'm still pretty nooby, and it's not for the faint of heart, but it worked to solve my 
"VMWare Player half installed state" problem.  It involved finding and turning off the script which was triggering the installation routine.

It got that way because I botched a couple of VMPlayer installs, including ver. 1 and the ver.2 tarball from VMWare, before I got it working (hint - using the "Run from Terminal" option if you get Ver.1, when you're setting up your link to the executable, works for me.).

A similar approach may be necessary for other offending scripts which keep triggering whatever program is it that's running in Applications | Add/Remove (aptitude?).

Old Skibum

---

### Post by joeups on 2007-07-13
Yes, I tried the above mention steps and they worked for me as well.  Thank you very much.:guitar:

---

### Post by hockey97 on 2007-07-18
HI I installed VMware on my sisters laptop, It never installed properly, now when I click on updates or  download packages it give me an error saying reinstall VMware player, when I download the package again and try installing it, it gives me an error you don't have permission or a cruppted file.

I need some way to delete the files that I installed that didn't install fully, becuse of that it locked up my update manager and packages manager.

---

### Post by hockey97 on 2007-07-19
HI I tried installing  VMware and it failed at the end, so now I get errors in terminals and also in, packages manager and   manager,  the error's say that the VMware didn't install properly reinstall VMware, and when I go download VMware again, and try installing it,  I get a new error saying I don't have permission to the file ro the file is cruppted.

It's my sister's labtop, I put it on, but she has only windows programs that she uses, and are used to using, 

she had windows xp, but we decided to put ubuntu on hers becuse I have it on my computer, and she went on some indian website and downloaded some song samples, and those samples had attached viruses, and they were deep in memory, and after I delete it then after reboot it came back.

I have tried the stuff you guy's said up in the this fourm, and still got the same error's..

---

### Post by itismike on 2007-08-05
Hi hockey97,

It's been two weeks, so you've probably already moved on...just wanted to suggest that the installation sounds like it may have been corrupted and you may want to just reinstall Ubuntu (after backing up /home of course).  It only takes a few hours to get up to speed again.

Good Luck!

---

### Post by Badjaccur on 2007-10-01
Using Gutsy Gibbon:
After installing and removing vmware-player I got a broken software index and nothing helped for me until I found this page: [http://www.webservertalk.com/archive291-2006-7-1588624.html](http://www.webservertalk.com/archive291-2006-7-1588624.html)

> On Wed, 19 Jul 2006 18:33:59 -0700, Bitey
> <bitey@batcave.rafters> wrote:
> This message is usually caused by an error in a package install or
> remove script. The scripts are found in
> /packagename.*

It looked like in my case the script called vmware-player.prerm in /var/lib/dpkg/info wouldn't let me uninstall vmware-player. So I added "exit 0"  above "set -e" and saved the file. After that I tried to use apt-get to gently remove vmware-player and it worked! Huzzah! This is what I did: 

$ sudo nano /var/lib/dpkg/info/vmware-player.prerm
Add "exit 0" above the "set-e" (Indeed, without the quotes)
Save file: Ctrl-O
Exit nano: Ctrl-X
$ sudo apt-get remove vmware-player

Good luck!

---

### Post by oxygala on 2007-10-07
great trick! congrats!

---

