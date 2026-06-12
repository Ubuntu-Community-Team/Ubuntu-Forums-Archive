---
title: "[SOLVED] Feisty Upgrade hangs...."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2007-04-21
I'm upgrading from Edgy to Feisty and I follwed the instrucctions [HERE]("http://www.ubuntu.com/getubuntu/upgrading") 

> Network upgrade for Ubuntu desktops (recommended)
  1. Open System -> Administration -> Update Manager
  2. A button on the top of the window will appear, informing you of the availability of the new   
     release
  3. Click Upgrade

The procedure starded well, I got 234 0f 1019 packages upgraded on a Dial-Up modem connection and then the connection to the server  was interrupted. 
I dialed again and connected again and followed the steps 1. through 3. 

But this time the "upgrade button" did not appear in the "Software Updates" window. 
What can I do?

---

### Post by Cariboo1938 on 2007-04-21
Hi all,
I try to keep this thread alive because the recommended upgrade [PROCEDURE]("http://www.ubuntu.com/getubuntu/upgrading") does not work at my computer. The Update Manager doesn't offer the upgrade button anymore. 
How can I proceed?

---

### Post by qamelian on 2007-04-21
> **Cariboo1938 said:**
> Hi all,
I try to keep this thread alive because the recommended upgrade [PROCEDURE]("http://www.ubuntu.com/getubuntu/upgrading") does not work at my computer. The Update Manager doesn't offer the upgrade button anymore. 
How can I proceed?

Have you tried clicking the Check button to refresh the Update Manager? This worked for me when I was in a similar situation upgrading from Dapper to Edgy.

---

### Post by Cariboo1938 on 2007-04-21
> Have you tried clicking the Check button to refresh the Update Manager?

Yes, I tried this all afternoon...no success...the upgrade button does not come up! 
Is it wise to restart the computer under such circumstances?

When I click the Check button I get the attached error message...

---

### Post by lalinux on 2007-04-21
if you have stuff on your current Ubuntu install you better save it somewhere first.  I did the auto upgrade recommended and my old kubuntu install was pretty much hosed.  I was able to pop-in a knoppix disk and save my files, and then went ahead and did a new kubuntu install.

When I do an Ubuntu install I can usually count on a good weekend of tweaking it to make it work especially in the area of monitor resolution, video card, multimedia .. etc  I don't think I have ever had a correct installation since version 4.x

I probably should have just followed the new install path to begin with because trying to fix the old one ate about 4 hours of my time.  Oh yeah, make sure to download a cd install for fiesty fawn.  It was more fiesty than I realized! :shock:

---

### Post by Cariboo1938 on 2007-04-22
The Update Manager still does not offer the "Upgrade" button as mentioned [HERE]("http://www.ubuntu.com/getubuntu/upgrading").
Because the upgrade procedure was interrupted (because of connection failure to the server)
I want to know if I could find out the state of the upgrade (there are already 234 of 1019 packages fetched). 
Would it help to  restart under such conditions?

---

### Post by qamelian on 2007-04-22
> **Cariboo1938 said:**
> The Update Manager still does not offer the "Upgrade" button as mentioned [HERE]("http://www.ubuntu.com/getubuntu/upgrading").
Because the upgrade procedure was interrupted (because of connection failure to the server)
I want to know if I could find out the state of the upgrade (there are already 234 of 1019 packages fetched). 
Would it help to  restart under such conditions?

A restart may help. Since your upgrade was still in the process of downloading files and hadn't yet installed anything, the only thing that has changed should be /etc/apt/sources.list.

---

### Post by Cariboo1938 on 2007-04-22
> **qamelian said:**
> A restart may help. Since your upgrade was still in the process of downloading files and hadn't yet installed anything, the only thing that has changed should be /etc/apt[SIZE="3"]**/sources.list**[/SIZE].Thanks man,
BTW I wonder if there is a special entry in the sources.list necessary for the upgrade? How would a working sources.list look like?

---

### Post by Cariboo1938 on 2007-04-22
> **qamelian said:**
> A restart may help. Since your upgrade was still in the process of downloading files and hadn't yet installed anything, the only thing that has changed should be /etc/apt/sources.list.

No, restart didn't help....Update Manager still doesn't offer the "Upgrade" button....is this because I'm on a Dial-Up connection? 
Help please!:confused:

---

### Post by Artemis3 on 2007-04-22
Check update-manager version from synaptic. If you have proposed repositories enabled, it might have upgraded the package to version 0.45.3. I found that this version doesn't show the button anymore (-c or -d do nothing). I downgraded it to version 0.45.2 and the button appeared again.

To downgrade a package from synaptic, select it and right click to choose "force version".

[https://bugs.launchpad.net/update-manager/+bug/108541](https://bugs.launchpad.net/update-manager/+bug/108541)

---

### Post by m.musashi on 2007-04-22
I know this isn't very helpful but running a dist-upgrade on dial-up sounds like asking for trouble. See if you can get an .iso from someone, backup all the improtant stuff and do a fresh install. If you can't get an .iso, PM your address and I'll mail you one :).

EDIT: okay, another thought. I can't remember the command but I think you can do an upgrade from a terminal by typing
```
sudo apt-get dist-upgrade
```
That may not be the exact command but I think it is. If not, maybe someone can correct me. Anyway, that might get the upgrade going again. The downloaded packages should be cached so it should continue from where it left off.

---

### Post by Cariboo1938 on 2007-04-22
> **Artemis3 said:**
> Check update-manager version from synaptic. If you have proposed repositories enabled, it might have upgraded the package to version 0.45.3. I found that this version doesn't show the button anymore (-c or -d do nothing). I downgraded it to version 0.45.2 and the button appeared again.
To downgrade a package from synaptic, select it and right click to choose "force version".
[https://bugs.launchpad.net/update-manager/+bug/108541](https://bugs.launchpad.net/update-manager/+bug/108541)Thanks Artemis,
It looks like downgrading the Update Manager to version 0.45.2 will solve my problem. 
Can you, please, give me a hand and explain to me more detailed how to do that? 
Sorry, but I don't know where I can get revision 0.45.2.
Thanks in advance
Cariboo

---

### Post by Cariboo1938 on 2007-04-22
> **m.musashi said:**
> I know this isn't very helpful but running a dist-upgrade on dial-up sounds like asking for trouble. .............Thanks m.musashi, for the comment....I totally agree...finally I found someone in my area with high speed Internet...I'll take my box there and try it again.
BTW, what do you think about Artemis3's experience...interesting, isn't it?

---

### Post by m.musashi on 2007-04-22
Actually, I don't know much about that. In my experience the dist-upgrade hasn't worked well. It died on my breezy to dapper (or was it dapper to edgy) upgrade and I haven't tried it since. I installed my /home on a separate partition and now I just install the new release fresh. It takes 20-30 minutes and I'm good to go - same desktop, theme and such. I do have to add back anything I installed but that is usually just a few things. Ubuntu comes with most of the stuff I need anyway.

---

### Post by Cariboo1938 on 2007-04-23
Thanks all...Problem solved....the "Upgrade" button is back again.:) 
```
sudo mv .update-manager .update-manager.old
```
I found the solution[ HERE]("http://ubuntuforums.org/showthread.php?t=416558&page=2&highlight=no+update+button")

The better solution is to update the "Update Manager" to version 0.45.4! Possible since Apr. 23. '07!

---

### Post by Cariboo1938 on 2007-04-25
With the "Update Manager" version 0.45.4, I could finish the the Feisty upgade.....but then the disaster began...
I got a lot of Error messages concerning NVIDIA issues (see txt attachment). while reporting this as I was asked to do, I somehow ended up with a black screen and command prompt. The Upgrade procedure was not finished yet. I re-booted and X-window server didn't start anymore. ```
sudo dpkg-reconfigure -phigh xserver-xorg, startx,

```
didn't work 
and editing /etc/X11/xorg.conf showed that neither my monitor nor my graphic card weren't detected properly. 
But  in /var/log/Xorg.0.log "Chipset GFORCE FX 5200" is probed (See Pictures XorgLog).
And the "envy" remedy didn't work because it seems not to be supported by the ..20 kernel (See Picture Envy).
I'm so frustrated that I'll take an Ubuntu break and wait 10 weeks for the shipment of a CD.:lolflag:

---

### Post by Cariboo1938 on 2007-04-25
Because I'm addicted to Ubuntu I couldn't stay away from it for longer than 5 hours.

I started booting kernel 2.6.20-15 generic (recovery mode). I connected to the Internet with command "pon" and tried to finish the Edgy to Feisty Upgrade by using ```
sudo apt-get dist-upgrade
``` and got this screen info - see pictures DistUpgrade... Then I tried ```
sudo apt-get upgrade
``` and got the screen info - see picture Upgrade.
:confused: If anybody reads this and can help me, would really save an "ADDICT's" life! 
I need to get back to my beloved Ubuntu GUI!!!:confused:

---

### Post by Cariboo1938 on 2007-04-25
Any ideas? ](*,)

---

### Post by m.musashi on 2007-04-25
Well, I'd say you have a bit of mess. I really wish I could help but I don't have any idea how to fix that. I tend to wimp out whenever I get things rather messed up and just reinstall. That would be my personal suggestion here. If you can't download the iso, take a trip to the local library and download it there (or a friend's house)

---

### Post by Cariboo1938 on 2007-04-25
> **m.musashi said:**
> Well, I'd say you have a bit of mess. I really wish I could help but I don't have any idea how to fix that. I tend to wimp out whenever I get things rather messed up and just reinstall. That would be my personal suggestion here. If you can't download the iso, take a trip to the local library and download it there (or a friend's house)Thanks m.musashi, for your advice...I have to learn to be patient...I have a seperate /home partition, so I should be save for a new installation..ok.

---

### Post by jdorwart on 2007-05-17
Open a terminal under Applications-accessories.


Type sudo apt-get update  (enter)
Type in your password

The system should update it's sources.

Type sudo apt-get upgrade (enter)
type in your password

the system should update all packages.

jeff

---

### Post by papikondalu on 2007-05-31
Try 

sudo aptitude dist-upgrade

I've had a better success in resolving dependency problems with aptitude than with apt-get.

-PK

> **Cariboo1938 said:**
> Because I'm addicted to Ubuntu I couldn't stay away from it for longer than 5 hours.

I started booting kernel 2.6.20-15 generic (recovery mode). I connected to the Internet with command "pon" and tried to finish the Edgy to Feisty Upgrade by using ```
sudo apt-get dist-upgrade
``` and got this screen info - see pictures DistUpgrade... Then I tried ```
sudo apt-get upgrade
``` and got the screen info - see picture Upgrade.
:confused: If anybody reads this and can help me, would really save an "ADDICT's" life! 
I need to get back to my beloved Ubuntu GUI!!!:confused:

---

### Post by Cariboo1938 on 2007-06-26
Thanks ervery body, for the thougths and inputs....though nothing worked...I must have messed it up...
I ordered a CD and when it is shipped I do a new installation..for me, the case is closed. :popcorn:

EDIT:
I did a New Installation of Feisty which worked flawless! Then, in November I upgraded with the Ubuntu 7.10 Alternate CD. Beside a few minor issues, like Gnome-ppp GUI not working properly, Hibernate not recovering, Packet writing is still an issue...I'm quite happy with Gutsy now!:KS

---

