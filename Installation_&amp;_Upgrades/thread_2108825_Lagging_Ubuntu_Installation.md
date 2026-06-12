---
title: "Lagging Ubuntu Installation"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Konflict11 on 2013-01-25
I've installed Ubuntu in a dual boot configuration on my PC, alongside Windows 8.
The specs of my computer are:
1.8GHz Intel Core 2 Duo
2GB RAM
250GB Hard drive 

I installed Ubuntu using a USB - I followed the guide present on the Ubuntu site to properly configure a USB so I could install Ubuntu using it. 

However, now that I've installed Ubuntu, I have a few problems poblems.

First is the problem that Ubuntu is painfully slow. There is a delay before absolutely everything. Searching for something in the dash takes an age, the windows take forever to minimise, and simply hovering over the side bare takes long for the animations to occur. There is literally a five second delay between clicking the home folder, for example, and then then home folder itself opening. Searching in the dash is even worse! 
I've used dconf Editor to speed the animations, but it has not helped one bit. The updates have installed, so I'm not sure what the problem is. 

Also, there is an issue of where exactly Ubuntu installed. I prepared a partition before installing Ubuntu with the USB - 25GB in size. Using the Ubuntu installer, I selected install alongside Windows 8. I was expecting it to give me options to choose which partition to install Ubuntu on, the ability to edit partition sizes, etc, but nothing of the sort occurred. It simply installed - but to where I'm not 100% sure. I assume it installed on my C drive - the same location of Windows 8. This is not want I wanted to happen, since I wanted to install it on the partition I had previously prepared. 

I'm no expert on Ubuntu - I would classify myself as a newb. But, I have installed Ubuntu before on the very same computer - it worked flawlessly. No lags, no problems, I knew exactly where it was installed. I've also played around with the the Live CD, so I known my way around the basics. 

Can you help me fix these problems? I'm assuming that then installing of Ubuntu on the same partition of Windows 8 has caused these problems, although I'm unsure. I really want to use Ubuntu, as, I'm sure you've seen, my computer specs aren't brilliant, and I support then open source mindset of Ubuntu. 

Personally, I would start by in installing Ubuntu first - but I'm sure that there are better ideas out there. (That, and the fact that I'm not 100% sure on how to in install Ubuntu from the same partition as Windows 8 without messing up the data I have already on Windows 8).

(In fact, Ubuntu is so slow I'm having to write this message on a phone. So, apologies if any typos are present!) 

I look forward to your suggestions and responses. Thanks. :)

---

### Post by Bucky Ball on 2013-01-25
*Thread moved to **Installations & Upgrades***

Welcome to the forums. To answer your second question; when you get to the partitioning section of the install you need to choose 'Something Else' to manually partition and choose where you want things to go.

Ubuntu can not be installed to the same partition as Windows unless you have installed Wubi which installs inside Windows. The same drive, yes, but that would have zilch to do with Ubuntu running slow. No need to install Ubuntu first. 

You might want to try a lighter desktop environment and see if it makes a difference. If it does then Unity (the DE you are using now) is too heavy and the problem. You can try xfce by installing xfce4 from Software Centre, log out, choose it from the 'Sessions' pop-up, log in.

When you previously installed Ubuntu was it 10.04 which used Gnome or a more recent release using Unity?

---

### Post by Konflict11 on 2013-01-25
> **Bucky Ball said:**
> *Thread moved to **Installations & Upgrades***

Welcome to the forums. To answer your second question; when you get to the partitioning section of the install you need to choose 'Something Else' to manually partition and choose where you want things to go.

Ubuntu can not be installed to the same partition as Windows unless you have installed Wubi which installs inside Windows. The same drive, yes, but that would have zilch to do with Ubuntu running slow. No need to install Ubuntu first. 

You might want to try a lighter desktop environment and see if it makes a difference. If it does then Unity (the DE you are using now) is too heavy and the problem. You can try xfce by installing xfce4 from Software Centre, log out, choose it from the 'Sessions' pop-up, log in.

When you previously installed Ubuntu was it 10.04 which used Gnome or a more recent release using Unity?

It was actually Ubuntu 12.04 LTS! I know my computer can run the Unity interface without lagging - it has done so during 12.04. Unless the upgrade to 12.10 really added THAT much to make my Ubuntu almost unusable. 
Is there a safe way I can uninstall Ubuntu - without deleting my Windows 8 files? I'll reinstall it onto the partition which I had previously created for it, although, I'm doubting whether that would make a difference... Would anything be down to the fact that I used a USB to install Ubuntu? In the directory of the USB, I did notice Wubi... Again, I don't think that makes a difference, but I might as well contribute everything I know. :p

Thanks for the kind welcome! I'll try out XFCE4 if Unity doesn't operate smoothly. I'd prefer to remain on Unity, though, if that's possible. Hearing good things about Cinnamon DE - would that solve it?

Also, sorry for posting in the wrong forums! Seemed a little basic, so I thought it would best belong in the beginner forum!

---

### Post by Bucky Ball on 2013-01-25
No, USB install shouldn't make any difference. To uninstall Ubuntu you can boot from the install USB, get to a desktop, launch Gparted and simply delete the partition. 

You created a partition for Ubuntu? It needs to be EXT* (2, 3, or 4 but go for 4). You are better off leaving free space where you want Ubuntu to be then choosing 'Something Else' during the install and using the free space. The appropriate partition type can be created then.

---

