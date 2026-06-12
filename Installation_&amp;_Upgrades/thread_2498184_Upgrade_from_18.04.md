---
title: "Upgrade from 18.04"
date: 2024-06-03
forum: Installation &amp; Upgrades
---

### Post by adrianciu-101 on 2024-06-03
Hi,
I'm new in this community and in ubuntu. I have problem to update my system in offline state. I need to ugrade system to 22.04 or will be great to 24.04. I try to:
- use apt-offline but i have errors,
- to create an *offline mirror* of the ubuntu package repositories but it didn't work
Can you tell me how can i upgrade it?

---

### Post by yancek on 2024-06-03
>  to create an *offline mirror* of the ubuntu package repositories but it didn't work

You need to be informative as 'didn't work' doesn't tell us anything.  Specific problems, warning or error messages.  There are numerous online sites explaining how to do this such as the one at the link below.   Your primary problem is likely that you waited a year too long to do this as support for 18.04 ended in April, 2023 and any updating would have been much simpler prior to that date.

  [https://louwrentius.com/how-to-setup-a-local-or-private-ubuntu-mirror.html](https://louwrentius.com/how-to-setup-a-local-or-private-ubuntu-mirror.html)

Did you read the information at the Ubuntu site below on the process?

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by filiprybar on 2024-06-07
open terminal(press Ctrl+alt+T)
type:
sudo do-release-upgrade -d
or
sudo apt update && sudo apt upgrade -y

---

### Post by yancek on 2024-06-07
filiprybar

As indicated in the thread title, the OP wants to update from 18.04 which has not been supported for over a year and the standard update/upgrade commands won't do the job.

---

### Post by Dennis N on 2024-06-07
I suspect that you can upgrade, but maybe not offline. I have Ubuntu 18.04 enrolled in Ubuntu Pro and get the upgrade offer every time the software is updated (image attached from today 7 Jun 2024). It seems to me that if they entice you to get into the Pro support, they have to give you an off ramp to a later version. 

I have not tested the upgrade, and don't plan to at this time. Maybe later.

---

### Post by adrianciu-101 on 2024-07-04
> **filiprybar said:**
> open terminal(press Ctrl+alt+T)
type:
sudo do-release-upgrade -d
or
sudo apt update && sudo apt upgrade -y

I don't use an environment with the Internet, so I need an offline solution



I tried the following things:
- mirroring (it's work but i can't download distr-upgrade-all)
- apt-offline (work only with installed repo)
- rsync but i have errors:
> 
sudo rsync --recursive --links --perms --times --compress --progress --delete rsync://archive.ubuntu.com/ubuntu/dists/bionic/main/dist-upgrader-all  /archive.ubuntu.com/ubuntu/dists/bionic/main/dist-upgrader-all
rsync: [Receiver] safe_read failed to read 1 bytes: Connection reset by peer (104)
rsync error: error in rsync protocol data stream (code 12) at io.c(282) [Receiver=3.2.7]

someone have solutions?

---

### Post by currentshaft on 2024-07-04
The "offline solution" is to back up your important files and re-install the operating system from scratch.

You should already be taking backups, so the latter part should be very easy.

---

### Post by adrianciu-101 on 2024-07-05
> **currentshaft said:**
> The "offline solution" is to back up your important files and re-install the operating system from scratch.

You should already be taking backups, so the latter part should be very easy.



your solution is not an option, I have too much VM to upgrade

---

### Post by vanadium on 2024-07-05
When offline (why did you not include that in the title of our post?), it becomes highly technical and convoluted to upgrade a system. You would need to create your own repository of 20.04, then adapt the update scripts to use your local repository. After the upgrade, you would need to repeat that all over again to move to 22.04, and finally to 

Your only realistic option for an upgrade without internet connection is to make sure the backup of your user data is complete, proceed to a fresh install of 24.04 using an installation DVD or USB, and restore the user documents to the newly installed system. You will then be good for another five years. To update the system with bug fixes etc, you can do an in-place reinstallation using DVD/USB of the future "dot" updates. That preserves user files and user- and system configuration.

You could consider delaying the upgrade until 24.04.01 has appeared. There, initial bugs of the new Ubuntu LTS release will have been ironed out. 

This is the easiest and most foolproof option. It will ensure that you will have a new clean system without a chance of issues due to leftovers from the previous version.

---

### Post by adrianciu-101 on 2024-07-05
I know that I have to go to 20.04, then to 22.04 and finally to 24.04. I use this guide


[https://louwrentius.com/how-to-setup-a-local-or-private-ubuntu-mirror.html](https://louwrentius.com/how-to-setup-a-local-or-private-ubuntu-mirror.html) 
I encountered problems because I can't download distr-upgrade-all, I don't know why rsync gives errors like this:
> sudo rsync --recursive --links --perms --times --compress --progress  --delete  rsync://archive.ubuntu.com/ubuntu/dists/bionic/main/dist-upgrader-all   /archive.ubuntu.com/ubuntu/dists/bionic/main/dist-upgrader-all
rsync: [Receiver] safe_read failed to read 1 bytes: Connection reset by peer (104)
rsync error: error in rsync protocol data stream (code 12) at io.c(282) [Receiver=3.2.7] 			 		
I'm still fighting but I have no ideas anymore

---

### Post by currentshaft on 2024-07-05
> **adrianciu-101 said:**
> your solution is not an option, I have too much VM to upgrade

This does not logically follow. One of the advantages of using VMs is how easy they are to port between systems.

---

