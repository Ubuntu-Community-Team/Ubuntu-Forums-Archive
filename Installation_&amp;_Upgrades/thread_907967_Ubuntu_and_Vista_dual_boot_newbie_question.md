---
title: "Ubuntu and Vista dual boot newbie question"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by skooby249 on 2008-09-02
Hi my name is Simon, I am new to Linux and I have just installed Ubuntu as a dual boot setup on my desk top running XP, All appears to be good so far. I would also like to install it onto my new laptop which is running Vista at the moment and wondered if anyone has had any problems with a dual boot setup with vista. Any feedback would be appreciated. Thanks Simon.

---

### Post by manishtech on 2008-09-02
Congrats Simon for trying out this wonderful operating system. Hope you have a fine time ahead. If you have any problems feel free to drop out here and people are always ready to help out others. :)

As far as I know there is no problems dual booting Ubuntu with Vista. We have installed many many Ubuntu copied and dual-booted with Vista in our College's "Linux Users Group". Just some steps to be taken before booting from the Ubuntut CD
1. Goto VIsta and do a filesystem check on the partition which you want to resize.
2. Degragment the partition until you have right half completely free. Do it again and again till you see all the blocks quite closer.

Start ubuntu installation but better try out manual partition.. I understand it tough, but you know you are doing and nothing will be messed up. Using other options may something resize other partitions which you didn't expect.

Finally I can say that dont loose hope if something doesnt work, come back here such that we can help you. :D

---

### Post by jeyaganesh on 2008-09-02
I   have dual boot of Ubuntu and Vista. I never had problem with dual booting.

---

### Post by skooby249 on 2008-09-02
> **jeyaganesh said:**
> I   have dual boot of Ubuntu and Vista. I never had problem with dual booting.
Thanks for your input as it is a new laptop and i am not all that familiar with Vista anyway, but I will give it a go. Thanks

---

### Post by skooby249 on 2008-09-02
> **manishtech said:**
> Congrats Simon for trying out this wonderful operating system. Hope you have a fine time ahead. If you have any problems feel free to drop out here and people are always ready to help out others. :)

As far as I know there is no problems dual booting Ubuntu with Vista. We have installed many many Ubuntu copied and dual-booted with Vista in our College's "Linux Users Group". Just some steps to be taken before booting from the Ubuntut CD
1. Goto VIsta and do a filesystem check on the partition which you want to resize.
2. Degragment the partition until you have right half completely free. Do it again and again till you see all the blocks quite closer.

Start ubuntu installation but better try out manual partition.. I understand it tough, but you know you are doing and nothing will be messed up. Using other options may something resize other partitions which you didn't expect.

Finally I can say that dont loose hope if something doesnt work, come back here such that we can help you. :D
Thanks for your reply to my post,I am also new to the world of forums. I will have to do a bit of reading up on ubuntu though as the machine i have installed on to was my network printer server, and now I can not even see this machine on my network.this machine  can see the other machines though. I will work on it. Thanks for your support.
Simon Lavallin

---

### Post by manishtech on 2008-09-02
As I mentioned I have got some 48 installations on new laptops of freshers of my college. It had Vista before and it did happily work with Linux.

I suggest you to better try out a LiveCD to see how much support it has. The installation process is outlines in the 2nd post of this thread.

---

### Post by caljohnsmith on 2008-09-02
> **manishtech said:**
> Congrats Simon for trying out this wonderful operating system. Hope you have a fine time ahead. If you have any problems feel free to drop out here and people are always ready to help out others. :)

As far as I know there is no problems dual booting Ubuntu with Vista. We have installed many many Ubuntu copied and dual-booted with Vista in our College's "Linux Users Group". Just some steps to be taken before booting from the Ubuntut CD
1. Goto VIsta and do a filesystem check on the partition which you want to resize.
2. Degragment the partition until you have right half completely free. Do it again and again till you see all the blocks quite closer.

Start ubuntu installation but better try out manual partition.. I understand it tough, but you know you are doing and nothing will be messed up. Using other options may something resize other partitions which you didn't expect.

Finally I can say that dont loose hope if something doesnt work, come back here such that we can help you. :D
Just a word of caution: if you use anything other than Vista's HDD manager to partition your HDD, unfortunately, you'll almost surely run into problems. It's because Vista keeps its own partition table of the HDD which is independent of the HDD's master partition table in the MBR. So for the special case of getting Ubuntu to dual boot with Vista, it is best to go into Vista and create/resize/reconfigure partitions rather than using Ubuntu's gparted partition editor. :)

---

### Post by manishtech on 2008-09-02
> Just a word of caution: if you use anything other than Vista's HDD manager to partition your HDD, unfortunately, you'll almost surely run into problems. It's because Vista keeps its own partition table of the HDD which is independent of the HDD's master partition table in the MBR. So for the special case of getting Ubuntu to dual boot with Vista, it is best to go into Vista and create/resize/reconfigure partitions rather than using Ubuntu's gparted partition editor.

Yeah! I think I forgot this. We asked them to create new partition by resizing the Vista partition from Vista itself. We told them not to resize it with gparted.

---

