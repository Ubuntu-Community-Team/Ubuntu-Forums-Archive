---
title: "Ubuntu 10.04 RC Installation Problems"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by lordjubblydave on 2010-04-24
I am having trouble installing the 10.04 RC

On my desktop the installer just crashes with a fatal error, before you get to the first screen of the installation process, where you choose to run as live cd or install.

On my Laptop i am trying to Install alongside my current 9.10 installation and i keep getting the errors illustrated in the screenies.
[IMG]http://i306.photobucket.com/albums/nn253/lordjubblydave/Screenshot-1-1.png[/IMG]

[IMG]http://i306.photobucket.com/albums/nn253/lordjubblydave/Screenshot-2.png[/IMG]



It is all probably down to my stupidity, but if it is not then this is very worrying 1less than a week before release.

---

### Post by stardustdk on 2010-04-24
I don't get it... why didn't you upgrade instead?? 10.04 is almost finished anyway and it is LTS (!).

Well, as it says: Too many prime partitions.

My suggestion: Prime for / (root) partition and ONLY for /.
Else use logically partitions for eg. /home

Best regards

---

### Post by leithanne on 2010-04-24
Could you, or someone, please expand on your suggestion? How would one implement that?

I'm having the same issue, trying to dual boot my existing 9.10 with a new 10.04. I was hoping to use half my drive for the stable LTS, and the other half to play with the latest and greatest to come down the pike. And I also want to keep 9.10 up and running while I take my time customising 10.04.

---

### Post by stardustdk on 2010-04-25
In Wiki you can see this:

> [http://en.wikipedia.org/wiki/Master_boot_record#MBRs_and_disk_partitioning](http://en.wikipedia.org/wiki/Master_boot_record#MBRs_and_disk_partitioning)

If you *want* to, use two prime partitons, and two logic's (/home and swap).

I still suggest you to stay with LTS, i am getting **too** many bugs in the non-LTS releases to my taste. Even 10.04 beta2 i felt more stable than 9.10.

Best regards

---

### Post by stardustdk on 2010-04-25
The easy way to set up your harddrive: gparted.

It is GUI software.

In terminal: sudo aptitude install gparted.

In Synaptic: search for gparted and install it.

You will thereafter find GParted in System->Administration.

From that software, you can setup the harddrive to your needs.

Best regards

---

### Post by leithanne on 2010-04-25
Thank you. I installed and took a quick look at Gparted. Will give it a try tonight. Worst that can happen is that I'll mess it up, and end up formatting and installing 10.04 to the whole drive, as you suggested. ~g~

But I'll have learned something, and, for me, it's all about the journey.

---

### Post by stardustdk on 2010-04-25
Well we all learn something down the road ;).

Have a nice trip :).

Best regards

---

### Post by nss0000 on 2010-04-25
> **stardustdk said:**
> The easy way to set up your harddrive: gparted.

It is GUI software.

In terminal: sudo aptitude install gparted.

In Synaptic: search for gparted and install it.

You will thereafter find GParted in System->Administration.

From that software, you can setup the harddrive to your needs.

Best regards


Though sporting a GUI, sad to say casual use of GPARTED is **far from obvious**. I tried using it to install a 2nd HDD ... in fact I succeeded tho entrapped by GPARTED I never knew how, when or what it was that caused the success. 

Just proves that casual use of crap_GUI produces ... crap.

---

### Post by stardustdk on 2010-04-25
That's new to me. Tried it several times, all times working as supposed! 

If you are afraid of GUI, why not use #parted# instead?

Best regards

---

