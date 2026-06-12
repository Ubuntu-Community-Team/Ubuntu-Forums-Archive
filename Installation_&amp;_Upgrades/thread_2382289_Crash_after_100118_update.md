---
title: "Crash after 10/01/18 update"
date: 2018-01-11
forum: Installation &amp; Upgrades
---

### Post by stuart_jones2 on 2018-01-11
Hi, I updated yesterday morning and since then the following happens,
the desktop starts and goes to the boot options page after that it just stays on a pink screen, left it over half an hour and no change just stuck.
Unfortunately I fly to Spain tomorrow morning. 
Using 16.04 on a Packard bell imedia s, I had the hard drive partitioned when I bought the PC so Windows 10 sits on the other side, but I very rarely use it.

---

### Post by ajgreeny on 2018-01-11
It sounds as if you may have been caught by the update to kernel 4.4.0-108 which did exactly what you're seeing on many machines.

See where I give what seems to be the solution to this problem.
[https://ubuntuforums.org/showthread.php?t=2382157&page=2&p=13728989#post13728989](https://ubuntuforums.org/showthread.php?t=2382157&page=2&p=13728989#post13728989)
In a nutshell, boot to the previous kernel 4.4.0-104 from grub then run another update to get kernel 4.4.0-109 which is a good version, then when you're sure all is well after a reboot remove all the 4.4.0-108 packages.

If that turns out not to be the problem we shall have to look a bit further.

---

### Post by stuart_jones2 on 2018-01-11
Thanks agreeing,
I should have said in my original post that I am a novice with ubuntu. But I have managed to get the computer going again with your suggestion through the boot menu. But  how do I get rid of the old update? And how do I update specifically to this other one?
Many thanks for your help and time so far

---

### Post by Impavidus on 2018-01-12
You can upgrade to 4.4.0-109 using whatever method you always use for normal upgrades. For example, using the terminal:```
sudo apt update
sudo apt upgrade
```But the update manager or synaptic work too.

After succesful installation of 4.4.0-109, you can uninstall 4.4.0-108:```
sudo apt purge linux-image-4.4.0-108-generic linux-image-extra-4.4.0-108-generic linux-headers-4.4.0-108 linux-headers-4.4.0-108-generic
```

---

### Post by ajgreeny on 2018-01-12
Run the three commands ```
sudo apt-get update
sudo apt-get install linux-generic
sudo apt-get dist-upgrade
``` one by one in terminal and you should get the new kernel 4.4.0-109 as well as any other updates available for your system.

Don't worry about the **dist-upgrade** command; it does not move you to the next Ubuntu version but simply pulls in the most recent kernel of your kernel series.

---

### Post by Geoffrey_Arndt on 2018-01-12
Important thread as this is affecting a lot of users (see ZDnet and other articles online).

Would someone please update the Title to better represent the issue (as 10/01/18 is really confusing for US-Canada users - - Jan 10 2018 is clearer ).

Good advice by ajgreeny as it fixes the issue - - - - on my System76 Sable AIO it took a half dozen attempts to get the new patch/kernel to download - - seems the main servers took a big hit.

---

### Post by Drowz0r on 2018-01-13
Got caught by this one too. Couldn't find any useful resources that made it simple enough to get around this online either. Thanks for the info.

---

### Post by stuart_jones2 on 2018-01-23
Thanks for your help ajgeeny and Impavidus, sorry for the delay in replying, but have been away for 10 days. Followed your instructions and all now seems to be running fine. Thanks again for your help

---

