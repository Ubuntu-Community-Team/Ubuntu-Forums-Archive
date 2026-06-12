---
title: "Purple screen of death"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by jamesbuhls on 2011-04-28
I just upgraded from Ubuntu 10.10 to Ubuntu 11.04 Natty Narwhal and now I've got a purple screen of death. The download and install process all went okay, but when I restarted the computer through the upgrade dialogue to complete the installation process the system never came back online. When I turn on my computer it goes through the standard boot screen (F2 and F12 options shown while it boots the HDD, ODD, and wireless modem), and then it goes to a purple Ubuntu screen and doesn't do anything at all. I let it sit like that for 30 minutes before turning off the power and trying to boot again, but the same thing happened. I can press CTRL-ALT-DEL and the system will reboot, but nothing I know to do will get me past the purple screen and the Ubuntu logo. Does anybody know what's happening here? :confused:

For what it matters, I'm using a Dell Studio 1 desktop computer. It's got a 2.5ghz Pentium processer, 4gb of RAM, and a 400gb HDD. I don't dual boot, and Ubuntu is the only OS installed.

---

### Post by raja.genupula on 2011-04-28
Hey man 
actually 11.04 need some more fixings 
if u wanna go for standard usage then just go for 10.10 . 

it is very nice to use ....i hope you already know much about it .

---

### Post by jamesbuhls on 2011-04-28
I've been using Ubuntu for almost a year so I'm familiar with the OS and comfortable working with it. I've never had a problem with it until now, and now that my computer might be or is toasted I can't do much with it. I have to use my wife's Mac to get on the forum and find help. I upgraded through the upgrade installer so I don't even have an install disc to boot from.

---

### Post by mikewhatever on 2011-04-28
You could try the recovery mode.;)

---

### Post by jamesbuhls on 2011-04-28
What is the recovery mode, and how do I access it? I wish I didn't have to ask, but I really don't know how to get there.

---

### Post by Hedgehog1 on 2011-04-28
Please do the following:

Using the Mac, download the correct Natty ISO for your PC (or better yet bit torrent it today - servers are swamped) and create a LiveCD from the ISO.

Next, boot off you LiveCD, select 'Try' and then use it to backup your data to an external hard drive or USB stick.

Next, click in the install 11.04 and select the upgrade option:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

This will repeat the COMPLETE upgrade with you having to wait on the swamped servers.

Hopefully, all will be well ofter this.

If not, we will still need you to have a LiveCD to do additional fixes.

***The Hedge***

:KS

**p.s. PSOD - Purple Screen Of Death - I like that!**

---

### Post by PatrickD-52761 on 2011-04-28
> **jamesbuhls said:**
> What is the recovery mode, and how do I access it? I wish I didn't have to ask, but I really don't know how to get there.

Hold down the SHIFT key while you're rebooting your computer.  This should bring up a GRUB menu with a list of the available kernels.  Choose the second one from the top (assuming that it's in the typical order). It should say Recovery Console or Recovery Mode beside it.  Either way, it will repeat the information from the option above it, along with more text.

When you do this, you'll be presented with more options. I would try the boot to root shell option.  You can try to do sudo apt-get update && sudo apt-get dist-upgrade (all on the same line with the two &&'s between the commands). This will probably fail, but it will give you a command to run to finish the upgrade.

Other options are to try an older kernel (although that may not work with the switch to Unity, but I'm not sure on this) when you boot to the GRUB menu, or the already recommended (and preferred) option of trying the LiveCD.

Hope this helps, and have a great day:)  (To note, I'm in the beginnings of the upgrade, so I may be in your shoes in about 4 hours).

Patrick.

---

