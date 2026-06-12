---
title: "Problem with upgrading to 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by mito551 on 2011-05-09
I'm much of a newbie to Linux, I don't know what can be done in my case. 

I was upgrading from 10.10 to 11.04 with terminal. When terminal asked about mime.types (it asks what to do with it) I chose showing me the differences between the new and the old versions. and then I couldn't get out from the "showing differences menu"! so, I shut down the terminal. and now I'm afraid to reboot the computer. can someone possibly say, what i am to do next 
is it okay to reboot my computer. or do i have to do smth first?:confused:

Oh, and i almost forgot, when i sudo do-release-upgrade i says that i have latest version and doesn't do anything. update manager isn't showing up neither

---

### Post by mikewhatever on 2011-05-09
I don't know if rebooting at this stage is safe or not, but it seems that there isn't a second option. Keep an Ubuntu livd CD ready to get access to your files, in case the computer refuses to boot.

---

### Post by mito551 on 2011-05-09
Yeah, I've already thought about that, but still... well, alright i'll try rebooting it... :???:

---

### Post by mito551 on 2011-05-09
Ok, rebooting was better idea, than sitting and waiting for smth. I got the "The disc drive for / is not ready yet or not present" error, then found fix on the internet (using "mount -o remount, rw /" in manual recovery, if somebody asks). Next, I tried to start configuring dpkg and it continued upgrading ubuntu. And asked about mime again)))
Reboot from manual recovery aaaaaaand.... it gave me only a shell! No X! What I am supposed to do know?

---

### Post by mito551 on 2011-05-09
Ok, I got some logs and through them I managed to know that problem concerns my nvidia video card and it's driver. After it tried about dozen of ways booting rebooting. Nothing did help. So, desperately I installed prboom from recovery console. With installing prboom it also installed drivers for my video card. A bit ridiculous, isn't it? But now it works! Thanks to the one that responded, you helped me, really. Even thought you did nothing, but responded. Thanks

---

### Post by mikewhatever on 2011-05-09
Glad you got it sorted, and thanks for the update.

---

