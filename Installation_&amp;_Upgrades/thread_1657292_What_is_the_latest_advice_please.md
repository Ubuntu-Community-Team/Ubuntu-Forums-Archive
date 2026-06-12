---
title: "What is the latest advice please?"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-01-01
Is WUBI still regarded as suitable for  newcomers?

I used to recommend Wubi use for those newcomers who were not confident enough  to handle a normal installation process. 

After the recent experience of someone I helped, I have decided to *stop* recommending WUBI to newcomers. Which rather makes it irrelevant?

Are WUBI/Ubuntu/updates likely to be developed in future, in a way which is more suitable for the beginners it is targetted at?

Detail painful story:
I helped an acquaintance to install Ubuntu using WUBI and recently he has had a lot of problems apparently after Ubuntu updates.

He said 'when I booted and got the select between ubuntu and 7, when I selected ubuntu it gave a black screen for about 10 sec’s, then re-booted and gave me the choice again. Tried a few times, and decided to do my e-mails via 7'

He never got Ubuntu to work again, and after deciding (I do not know why) to do a partial repair/reinstall of Windows 7 attempt (a friend helped him) it seems he he did manage to uninstall Ubuntu. 

Unfortunately he continued to see the Ubuntu choice when he starts up, so he still *believes* that Ubuntu is not YET uninstalled (I know, I know......).  And when Ubuntu 'startup' choice is now made he sees error stuff........

I am aware of some current bug issues relating to WUBI and updates, and it is obvious that such problems as my friend has are a public relations advertising disaster, even though I will continue to try to help him the best I can.

---

### Post by Rubi1200 on 2011-01-01
Hi,
there is now a thread where Wubi users, and those who help them, can go to find information regarding the issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It is my understanding that, as of the time of writing, there is no "fix" available from the developers for the GRUB updates breaking Wubi installs.

Thanks to forum members bcbc and drs305 there are solutions as well as a Permanent Fix once Ubuntu is booting again.

If you would like to add your voice to the bug reports, see near the top of the thread for links.

The greatest obstacle right now is that many Wubi users do not have a LiveCD/USB to help them troubleshoot and fix the problems.

---

### Post by sanderd17 on 2011-01-01
I also stopped with recommending WUBI. The default install wizard is lots better than it used to be, and with a live CD they can try before they install.

In fact, I mostly recommend a live-USB. It boots faster than a Live CD, they can make some changes (if it's persistent) and it doesn't change anything to their computer. When they like it, it's easy to install.

---

### Post by bcbc on 2011-01-01
I think Wubi's great to try out Ubuntu. But - with the grub problems - you have to make sure they don't update grub-pc or grub-common (lock them in synaptic). 

Unfortunately, many people who go to ubuntu.com find the windows-installer prominently displayed - and there is no warning for them. 
So the best thing is to just get the problem fixed. I have a fix in package lupin - just got to figure out how to get it off my pc and into the repo's ;)

At the end of the day, a proper install is best, so if you can help someone install - that's what I'd do.

---

