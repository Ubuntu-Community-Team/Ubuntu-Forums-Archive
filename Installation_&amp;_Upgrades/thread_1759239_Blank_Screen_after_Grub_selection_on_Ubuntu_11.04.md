---
title: "Blank Screen after Grub selection on Ubuntu 11.04"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by sid.mallya on 2011-05-15
Hey guys ! I downloaded Ubuntu 11.04 yesterday. The ISO allowed me to install Ubuntu using Wubi and it worked just fine  in Windows (I used a virtual drive to mount the ISO). I liked it enough to want to replace Linux Mint on the Laptop with  it. 

After a LOT of trying, I was finally able to make the liveUSB of Ubuntu 11.04 32-bit version.

[http://ubuntuforums.org/showthread.php?t=1758304](http://ubuntuforums.org/showthread.php?t=1758304)

But the liveUSB drive still is causing major trouble. It displays the boot menu and if I select 'try Ubuntu without installing', I am greeted with a blank screen which just does not go away until I hard reboot the system. 

Also, the grub I am getting is NOT the purple one which usually is the default; instead, its a dark screen with a black-n-white titled Ubuntu logo. :confused:

So the question of using the NOMODESET doesn't arise at all. 

I am using Dell XPS 15 with dual OSes - Linux Mint and Windows 7. Both Mint and 7 are 64-bit OSes but I am trying to install Ubuntu 11.04 32-bit version.

---

### Post by MAFoElffen on 2011-05-15
> **sid.mallya said:**
> Hey guys ! I downloaded Ubuntu 11.04 yesterday. The ISO allowed me to install Ubuntu using Wubi and it worked just fine  in Windows (I used a virtual drive to mount the ISO). I liked it enough to want to replace Linux Mint on the Laptop with  it. 

After a LOT of trying, I was finally able to make the liveUSB of Ubuntu 11.04 32-bit version.

[http://ubuntuforums.org/showthread.php?t=1758304](http://ubuntuforums.org/showthread.php?t=1758304)

But the liveUSB drive still is causing major trouble. It displays the boot menu and if I select 'try Ubuntu without installing', I am greeted with a blank screen which just does not go away until I hard reboot the system. 

Also, the grub I am getting is NOT the purple one which usually is the default; instead, its a dark screen with a black-n-white titled Ubuntu logo. :confused:

So the question of using the NOMODESET doesn't arise at all. 

I am using Dell XPS 15 with dual OSes - Linux Mint and Windows 7. Both Mint and 7 are 64-bit OSes but I am trying to install Ubuntu 11.04 32-bit version.That error still applies to the purple screen error (same cause)... A purple screen, a black screen, a blank screen, a flashing cursor (sometimes), a stuck splash screen. etc. > where xorg is stuck at startup before the GDM login screen.

Please refre to the first 3 posts of this sticky and ask me any questions you'ld like: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by sid.mallya on 2011-05-16
I have tried most of what is present in the thread already. Anyway, I thought Ill give another distro of Ubuntu a try, and surprise surprise, it still doesn't work.

Same problem.

"Unable to mount /dev/sr0" then goes into initramfs with the error message, "unable to find (or mount) live filesystem"

---

### Post by sid.mallya on 2011-05-16
Bump !

---

### Post by MAFoElffen on 2011-05-16
> **sid.mallya said:**
> I have tried most of what is present in the thread already. Anyway, I thought Ill give another distro of Ubuntu a try, and surprise surprise, it still doesn't work.

Same problem.

"Unable to mount /dev/sr0" then goes into initramfs with the error message, "unable to find (or mount) live filesystem"
So this seems not a graphics problem...  

From what I'm hearing... This is rather a problem on how the usb boot image was created or how it's booting usb?

---

### Post by sid.mallya on 2011-05-17
Yes ! And I think there is some problem with the laptop regarding this. This same problem has occurred when I had installed Linux Mint on the system. I tried 9-10 times and suddenly it recognized the usb boot device and I was able to install it.

I have always used Ubuntu Startup Disk Creator for the purpose. Ill try booting Ubuntu 11.04 using a CD today. If that works, then there is something wrong with USB booting.

---

### Post by shannon.jacobs on 2011-05-18
I just upgraded two machines, and they are both seriously mucho deado. These two are ThinkPads, one is older under the IBM logo, while the second one is Lenovo branded. I was hoping to find some hint to proceed, but I'm obviously a fool for hoping that Ubuntu was not going to get worse this time around. I actually succeeded on an even older machine, but apparently because it rejected Unity completely.

Well, at least I'm not a perfect fool. I had already stopped relying on Ubuntu, and the two new deaders are actually only VMware Player emulators, though on two different machines.

In conclusion, I've been using Ubuntu for about 5 years now, and it peaked several years ago. To me it seems obvious that their financial model is fatally flawed, so just for grins, I thought of a better one. Here's the link in case you might find it amusing.

[http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html](http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html)

---

### Post by shantanu18 on 2011-05-18
When booting ubuntu from USB continuously press any arrow key. Select language. From grub menu press F6 and select "nomodeset" [x will appear].

Now select your desire option (try ubuntu or install). Hope this will help. Check your disk(USB) is it correctly write ubuntu or not (using check disk option).

---

### Post by sid.mallya on 2011-05-18
@Shannon,

Um, okay ? I don't see how that is related to my problem, but thank you for sharing your views ? :)

@Shantanu,

Like I said, the option was not being made available to me, cause the grub menu it was displaying was some old legacy version - not the purple one you'd think it would. 

@All,

Anyway, I was able to install Ubuntu 11.04 using a liveCD .. I think there is a problem with Dell XPS 15 and liveUSB .. I was faced with this problem earlier too. And I hardly think I am making a mistake making the liveUSB - monkeys can point and click ! xD

---

