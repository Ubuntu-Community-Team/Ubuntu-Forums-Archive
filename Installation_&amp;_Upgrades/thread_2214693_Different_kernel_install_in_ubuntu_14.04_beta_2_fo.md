---
title: "Different kernel install in ubuntu 14.04 beta 2 for Intel and AMD"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by hwreagan on 2014-04-02
I installed ubuntu 14.04 from a usb created prior to the release of beta 2 on March 28 onto a laptop having a dual core amd 3 or 4 weeks ago.  I have updated from the daily updates every day and the kernel has been upgraded/updated to 3.13.0-20-generic.

After the release of beta 2 on March 28 I created a DVD and installed it on my Desktop which has a dual core Intel.  After one of the daily update cycles on April 1 the kernel was updated to 3.13.0-21-generic.

I wanted both machines to be as equal as possible but  the software updater on the laptop amd never updates the kernel 3.13.0-20-generic to 3.13.0-21-generic.

Is there a reason for this difference?

---

### Post by bapoumba on 2014-04-02
Is linux-generic being held back on the laptop ?

---

### Post by hwreagan on 2014-04-02
If it  is I am not sure how it is being done,  I have not done anything to cause it to happen knowingly.  I have tried to perform everything the same on both machines except the Usb stik has to have update to be at the same update level as the DVD.  And I assume by doing updating from the daily files thay should be in sync.  Tell me what to look at and I will try to provide better info.  Thanks

---

### Post by bapoumba on 2014-04-02
> **hwreagan said:**
> If it  is I am not sure how it is being done,  I have not done anything to cause it to happen knowingly.  I have tried to perform everything the same on both machines except the Usb stik has to have update to be at the same update level as the DVD.  And I assume by doing updating from the daily files thay should be in sync.  Tell me what to look at and I will try to provide better info.  Thanks

Please post the output to 
```
sudo apt-get update
sudo apt-get upgrade
```
from the laptop.

I'm asking because here, any kernel upgrade is held back. I've looked around but do not know why, no one seems to either have this issue or see it as an issue. I just upgrade them individually.

---

### Post by ajgreeny on 2014-04-02
All of my various versions of the 14.04 *ubuntu OSs as VMs in VirtualBox have been updated today to 3.13.0-21, so there must be something diferent about your laptop.

I always install synaptic and use that for all package management, including updates, and I am uncertain if that might make any difference, or if it can somethimes pull in newer kernels when other methods do not, but it may be worth your installing and using synaptic, just to test that possibility.

---

### Post by bapoumba on 2014-04-02
> **ajgreeny said:**
> All of my various versions of the 14.04 *ubuntu OSs as VMs in VirtualBox have been updated today to 3.13.0-21, so there must be something diferent about your laptop.

I always install synaptic and use that for all package management, including updates, and I am uncertain if that might make any difference, or if it can somethimes pull in newer kernels when other methods do not, but it may be worth your installing and using synaptic, just to test that possibility.

I do not think synaptic should make any difference, but I may be wrong. Aptitude yes, but synaptic, I'm not sure.
Do you have the trusty backports enabled ? I have here and I was thinking that was the explanation. Once again, manually upgrading the kernel works fine. I have upgraded to 3.13.0-21 but am not running it yet as I have not rebooted. Will see this tomorrow.

---

### Post by ajgreeny on 2014-04-02
> **bapoumba said:**
> I do not think synaptic should make any difference, but I may be wrong. Aptitude yes, but synaptic, I'm not sure.
Do you have the trusty backports enabled ? I have here and I was thinking that was the explanation. Once again, manually upgrading the kernel works fine. I have upgraded to 3.13.0-21 but am not running it yet as I have not rebooted. Will see this tomorrow.

No backports enabled on any of my OSs, so that is not an answer.

---

### Post by bapoumba on 2014-04-02
> **ajgreeny said:**
> No backports enabled on any of my OSs, so that is not an answer.

Well, yes, it is, thanks. As my kernels are always kept back, and so are other packages sometimes, I was thinking to comment out the backports. You've convinced me to do it tomorrow :)

---

### Post by hwreagan on 2014-04-02
As a matter of fact I have alternately used Software Updater along with the term cmds of
 sudo apt-get updates
sudo apt-get upgrade

I am looking at the grub login statements and run Sysinfo to determine the version it this helps any to know why I see different versions.

---

### Post by hwreagan on 2014-04-02
The only thing I typically use Ubuntu Software center for is to install [COLOR=#000000]*synaptic package mgr.  *[/COLOR]The I use synaptic and gdebi to do the other installs except I do run Software Updater to install the daily updates along with the sudo apt-get update and upgrade term cmds. (On the last installation I did use Ubuntu Software center for a few of my installs and noticed it seemed to run faster than previous versions but I still prefer Synaptic.)
BTW, could someone explain  what the difference between using Software Updater and the sudo apt-get...  I am guilty of blindly using something without knowing the why!  Shame on me again!!! :) 
.

---

### Post by ajgreeny on 2014-04-03
So, what has happened this morning to you all?

My systems have all been upgraded again in the past few minutes to kernel 3.13.0-22. Have yours also had this update?

---

### Post by bapoumba on 2014-04-03
> **ajgreeny said:**
> So, what has happened this morning to you all?

My systems have all been upgraded again in the past few minutes to kernel 3.13.0-22. Have yours also had this update?
I'll tell you tonight when I get back to my linux laptop.

Edit : yes.  3.13.0-22-generic.

---

### Post by hwreagan on 2014-04-03
[COLOR=#000000]
LOOK NO MORE--THE LIGHT JUST CAME ON


I have a Phd in Dumb! Here is what I have done and it is a wonder anything has worked I guess. Because I could not never get Grub Customizer installed in Ubuntu 14.04 I would log on to Ubuntu run Sudo apt-get udate and upgrade or I would run Software Updater. Sometimes and not every time I would log off of Ubuntu log, on to Mint 16 which had Grub custmoizer and run it there. This produce an out of sync set of files. It just so happened that the kernel was updated from 20 to 21 when I chose not to run the Grub C. from Mint 16. So some of the Grub files had 20 and some had 21 and /Boot segment was always one version behind until I just happen run the Grub C. while trying to research what versions were installed and how to delete them.....DUH Sorry to put all you guys through loops while I am sort of flying by the seat of my pants with Linux! Oh yes, the bottom is completely gone but I am getting there with your wonderful help and comments! Thank you one and ALL[/COLOR]

---

### Post by bapoumba on 2014-04-03
> **hwreagan said:**
> [COLOR=#000000]
LOOK NO MORE--THE LIGHT JUST CAME ON


I have a Phd in Dumb! Here is what I have done and it is a wonder anything has worked I guess. Because I could not never get Grub Customizer installed in Ubuntu 14.04 I would log on to Ubuntu run Sudo apt-get udate and upgrade or I would run Software Updater. Sometimes and not every time I would log off of Ubuntu log, on to Mint 16 which had Grub custmoizer and run it there. This produce an out of sync set of files. It just so happened that the kernel was updated from 20 to 21 when I chose not to run the Grub C. from Mint 16. So some of the Grub files had 20 and some had 21 and /Boot segment was always one version behind until I just happen run the Grub C. while trying to research what versions were installed and how to delete them.....DUH Sorry to put all you guys through loops while I am sort of flying by the seat of my pants with Linux! Oh yes, the bottom is completely gone but I am getting there with your wonderful help and comments! Thank you one and ALL[/COLOR]

Eheh, looks like Grub Customizer does not have a ppa for trusty 14.04 : [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer).

---

### Post by ajgreeny on 2014-04-03
My mistake; in spite of my earlier post, I do have backports enabled in my repos and was mixing it up with proposed.

---

### Post by grahammechanical on 2014-04-03
Last week I put in a new install of Trusty Tahr and it came with the 3.13.20 kernel but my long existing, daily updated Trust Tahr was still running on 3.12.17. There were a lot of packages being held back. I ran

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and that brought in all the held back packages including the 3.12.20 kernel. I did not update yesterday but today's update brought in the 3.13.21 kernel. I do not see this as anything to be concerned about.

Awhile ago a change was made in the method of putting out updates. Instead of pushing an update out to every user which meant that a bug in an updated package got pushed out to every user at the same time another method was used. It is called Phased Updates.

> *Phased Updates *[COLOR=#4F4F4F][FONT=Lato]are just like regular updates, with the only difference being that they are rolled out to users in gradual stages rather than to everyone at the same time. This staggered release approach is designed to improve the stability of Ubuntu.[/FONT][/COLOR]

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

> [COLOR=#29303B][FONT=Trebuchet MS]When a Stable Release Update is released to 13.04 it will have its phased update percentage initially set to 10%. A job is run, every 6 hours, in the data center that checks to see if there are any regression about the package, and if there are none then the phased update percentage will be incremented by 10%. [/FONT][/COLOR]

[http://www.murraytwins.com/blog/?p=127](http://www.murraytwins.com/blog/?p=127)

I am guessing that Phased Updates are no longer restricted to Stable Release Updates (SRU) but also to development versions like trusty tahr. In the past a SRU would be pushed out through the Proposed Repository (if enabled) but the Proposed repository is now being used in the development version to push out updates earlier to find out if they come with bugs before the update is pushed into the Main repository.

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-phased-updates](https://blueprints.launchpad.net/ubuntu/+spec/foundations-r-phased-updates)

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

See, Opting Out. Of course, a daily image will get the latest code. It is there to be tested after all.

Regards.

---

### Post by bapoumba on 2014-04-03
Thanks much grahammechanical, that must be it. As I have had a long break from the forums and linux news up to last summer, I have missed that. I'm sure that is what happens. At first, I did check to see if there were bug reports against the packages that were held back, but there were none. I've waited a couple days to install them since then, looking here before. I was more curious than worried.

I'm careful with dist-upgrades, it can remove lots of things that you need to keep. I apt-get upgrade <package_name> instead.

---

