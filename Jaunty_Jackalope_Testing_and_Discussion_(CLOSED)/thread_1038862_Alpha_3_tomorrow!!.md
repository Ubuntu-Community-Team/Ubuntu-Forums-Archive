---
title: "Alpha 3 tomorrow!!"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-14
If I am right, alpha 3 comes out tomorow! (I am in florida, it is 1/14 now)

Any idea about when is should be available?

---

### Post by ShirishAg75 on 2009-01-14
one of the ways would be to point a browser to [http://cdimage.ubuntu.com/releases/9.04/](http://cdimage.ubuntu.com/releases/9.04/)

Sometime tomorrow it would state a directory named alpha-3 there

Another way is to keep on coming to this forum, there should be an announcement of the same on the forum as well. 

Another way is to subscribe to [EMAIL="ubuntu-devel-announce@lists.ubuntu.com"]ubuntu-devel-announce@lists.ubuntu.com[/EMAIL] 

[http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

It would also give an announcement release. 

Either or all of these options should work.

---

### Post by LordVeovis on 2009-01-14
Thanks

---

### Post by Gina on 2009-01-14
Well let's hope it's installable!  Alpha 2 wasn't, nor have the daily builds on some machines, such as AMD64.  I'm using Alpha 1 updated.  Recent builds have ext4 format available and provide an easy way to try ext4 for cases where the install ***does*** work.  It's ironic for me that it works on a ten year old desktop but not on my six month old AMD64 nachine.

---

### Post by talkingwires on 2009-01-14
> **Gina said:**
> It's ironic for me that it works on a ten year old desktop but not on my six month old AMD64 nachine.Hell, it's ironic that it works on newer machines, [but not my six year-old laptop]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34155"). Here's my latest comment on the [Launchpad report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34155"):> @Launchpad Janitor: Good to know that top men are working on this. TOP MEN. Oh, wait, you're just a robot and the developers have pretty much ignored this bug for three years now. On a related note, I now have two of these machines (Military surplus), and the second one came with Windows 2000 installed. I booted it up and closed the lid. A tear ran down my cheek when I opened the lid and watched a ten year-old OS resume from suspend.I know I'm being snarky, but three years and *no progress* from the developers? Really? I'm tempted to put Win98SE on there and see if it works, too. Just for kicks. Maybe we can see how far back we can go? DOS 6.22 didn't have laptop support, but I'd bet that it supports a Dell C640 as well as Ubuntu. Older versions Osx86 reportedly run on the machine, too. It's kinda sad that an OS that was never made to run on the hardware works better than Ubuntu. Here's a comment I made on Launchpad one year ago:> Oh, and I just noticed that this bug just celebrated its second birthday. I added ACPI to the affected packages as a birthday present, and invited the Kernel ACPI team to come to the party.

---

### Post by LordVeovis on 2009-01-14
> **Gina said:**
> Well let's hope it's installable!  Alpha 2 wasn't, nor have the daily builds on some machines, such as AMD64.  I'm using Alpha 1 updated.  Recent builds have ext4 format available and provide an easy way to try ext4 for cases where the install ***does*** work.  It's ironic for me that it works on a ten year old desktop but not on my six month old AMD64 machine.

I hope they fix the 64 bit install I am debating btrfs or ext4 install on my 64 bit system.  Question though, does btrfs have built in encryption? or will I need to do that on my own / can I do that on my own and still install with btrfs?

---

### Post by Slug71 on 2009-01-14
> **LordVeovis said:**
> I hope they fix the 64 bit install I am debating btrfs or ext4 install on my 64 bit system.  Question though, does btrfs have built in encryption? or will I need to do that on my own / can I do that on my own and still install with btrfs?

Btrfs isnt in Jaunty yet.

---

### Post by LordVeovis on 2009-01-14
No, but it's in the kernel, should I not be able partition before install and then install to that partition?

---

### Post by amano on 2009-01-14
It is NOT in the kernel. Jaunty has the recent 2.6.28 kernel and Btrfs was just merged to the upcoming 2.6.29 kernel. Nobody knows if the Ubuntu devs will switch to this kernel for Jaunty or stay with 2.6.28.x ):P

And btrfs is considered absolutely experimental at its current state and was just merged to faciliiate easier and faster development. In conlusion even the final 2.6.29 will not "support" that feature, nor will do any distribution with its stock kernel. The feature will be disabled before compiling and you would need a custom kernel to be compiled on your own anyway.

---

### Post by LordVeovis on 2009-01-14
> **amano said:**
> It is NOT in the kernel. Jaunty has the recent 2.6.28 kernel and Btrfs was just merged to the upcoming 2.6.29 kernel. Nobody knows if the Ubuntu devs will switch to this kernel for Jaunty or stay with 2.6.28.x ):P

And btrfs is considered absolutely experimental at its current state and was just merged to initiate faster development. Thus even the final 2.6.29 will not "support" that feature, nor will do any distribution with its stock kernel. Thus the feature will be disabled before compiling and you would need custom kernels anyway.

I know btrfs is still in development.  It will also need testers.  I don't plan on making this a main pc, I have many here.  Some ppl use the vanila kernels here so I know I *should* be able to as well then.

---

### Post by the_slain_man on 2009-01-15
When today can we expect the release of the iso?

---

### Post by Gina on 2009-01-15
I guess the answer will be same as every time - it'll be ready when it's ready :lolflag:

---

### Post by andrewabc on 2009-01-15
> **the_slain_man said:**
> When today can we expect the release of the iso?

As usual, don't bother waiting every moment for it. If you are living near Eastern USA, it will probably be out by Friday morning.
They have a tendency to release them very late in the release day.

---

