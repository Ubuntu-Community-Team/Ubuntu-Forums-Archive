---
title: "How to tell OS to use a given swap partition"
date: 2018-05-24
forum: Installation &amp; Upgrades
---

### Post by ricardosilva on 2018-05-24
Hello!

I had on my laptop a dual-boot using grub for Windows and Ubuntu, and recently decided to install Kubuntu as well.
I now have a triple-boot and it is working fine. I used Kubuntu's ISO's automatic option to do the partitioning and installation, (that was a surprise, I thought it would be more complicated).
The only thing is that I realized that there was only one linux-swap partition, so I believe Ubuntu and Kubuntu were using the same linux-swap, and I understood this is not good. Sooner or later, by Murphy's law, I will boot one system with the other one suspended, and mess up the whole scheme.
So I have just created an additional partition for linux-swap (I am relatively new to Ubuntu, but getting some confidence with GParted, now).

My question is: I have no idea how to configure Kubuntu to use this new partition for swap, and leave the old one for Ubuntu.
I found a huge amount of questions on how to create a Swap partition, but I was able to do that. I could not find an answer to how to configure it.

Below is a screenshot of the current configuration, as seen on GParted:

[ATTACH=CONFIG]279826[/ATTACH]

---

### Post by kerry_s on 2018-05-24
ubuntu has moved on from swap partition to using a swap file.
swap is not saved when you reboot, you can not switch to another os leaving it suspended. you reboot into other os's.

your setup is fine leave it alone before you screw things up.

---

### Post by ricardosilva on 2018-05-24
ok, kerry, thank you for the information, I did not know that.
I will just delete the new partition I just created and resize the Kubuntu partition to use that space.
Thank you!

---

