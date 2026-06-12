---
title: "Install with no internet connection"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by jwn-2 on 2017-04-21
To save unnecessary costly downloads I have managed to install Ubuntu 14.04 LTS and all necessary software without any internet connection on a new computer just by using the install disk and the software package (.deb) files from my old computer. Everything installed and worked perfectly well without any internet connection. However, the moment I connected to the internet after installation about 250Mb of downloads immediately took place in the background. That is still a considerable amount of downloads. It was NOT software updates, because no .deb packages were saved in /var/cache/apt/archives/. Can anybody please tell me what were downloaded, where was it saved on my computer and can I back it up so that it does not have to download next time again?

---

### Post by RobGoss on 2017-04-21
Hello and welcome to the forum, you can do a complete installation of Ubuntu without any internet connection but your system will not be fully updated with the latest security updates, with that said you will need to run the updater to install the latest updates to have the system on the latest updates

250Mb Doesn't seem like a lot considering what software was updated

---

### Post by jwn-2 on 2017-04-21
250Mb IS a lot if you have only 2Gb available for the month. Can't I just copy those security files from somewhere on my old computer to the new one?

---

### Post by RobGoss on 2017-04-21
> **jwn-2 said:**
> 250Mb IS a lot if you have only 2Gb available for the month. Can't I just copy those security files from somewhere on my old computer to the new one?

I'm not really sure how you would do that  seeing there probably system updates along with security updates maybe someone else has better knowledge how to accomplish this

---

### Post by Impavidus on 2017-04-21
I'm not sure how things work exactly, but I noticed that not all downloaded .debs are stored permanently in /var/cache/apt/archives. Maybe a difference between running **apt upgrade** and the update manager? I just installed 11 updates, but the number of files in that directory remained at 38.

You won't get 250MB of updates every month. There's always a big bunch of updates right after installation, especially if the disk image you used is old. 14.04 is quite old, even 14.04.5 is 9 months, so, apart from the stuff you managed to copy from another computer and the updates that have been replaced by newer updates, you installed at least 9 months worth of updates.

---

