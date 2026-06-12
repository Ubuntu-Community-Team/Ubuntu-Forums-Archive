---
title: "Root File System Undefined"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by VinnyLC on 2010-08-08
I would like to start off by saying this: I am very new to Linux, and this is my first time installing it, therefor I am having some very newb-like issues. Please bear with me.
I am currently at step five of the installation process of Ubuntu, and I clicked on the partition which I have set aside to install Ubuntu onto, but when I proceed by hitting forward, I get the following error message:

"[I]No root file system is defined.

Please correct this from the partitioning menu.[/I]"

My question to the community is, how would I correct that? How do I turn my 20GB partition into the root file system? All help is greatly appreciated.
Thanks,
Vinny

P.S. I searched the forum for this issue, and being that it sounds so simple, yet I found nothing about it being previously asked, I feel sort of dumb....

---

### Post by oldos2er on 2010-08-08
If I'm not mistaken, right-click on the partition and choose "/" for root.

---

### Post by VinnyLC on 2010-08-08
When I right clicked the partition I got three options: *change, delete, revert*, but no / :(
I have taken a screenshot of what I see when I go through this process. I will attach it; hopefully you'll be able to help me out then.
Thank you for the swift reply, though.

---

### Post by Rubi1200 on 2010-08-08
Hi,
You set aside 20GB for Ubuntu; sda5 in the screenshot. Correct?

Then do this:

Try again and this time when it gives the message right-click on sda5 and choose Add.

Then, select Ext4 as the filesystem under Use as and under Mount point select /

Ubuntu will then create a root partition and a swap partition on the 20GB partition. All your "home" files will also be there.

Then you can continue the installation.

One word of advice: when it comes to the bootloader; use the defaults and don't change anything. The bootloader needs to be installed to the MBR.

Good luck!

---

### Post by VinnyLC on 2010-08-08
[INDENT]I Gave that a try, but it didn't work because after right clicking it, I didn't see add so I clicked Change instead. Choosing* Ext4 Journaling File System* didn't work, but there was an option called *Ext2 File System*, should I choose that one instead?
Also, when I chose the sda5, it causes *Add* to become unclickable.
I'm having a bad feeling I misinterpreted something, I'm sorry :(
**Edit: I did. Give me a second and I'm going to go back through this and try it again. Oopsies.**
 Ok, it worked. But I apparently have not added any swap space. Should I assign a 1GB partition for that?

[/INDENT]

---

### Post by Rubi1200 on 2010-08-08
> **VinnyLC said:**
> Ok, it worked. But I apparently have not added any swap space. Should I assign a 1GB partition for that?
No, Ubuntu should automatically create a swap partition on the 20GB partition. But if that won't work then yes create a swap partition.

---

### Post by VinnyLC on 2010-08-08
I got this pop-up(linked below) that states I either need to assign one myself or else I don't get one, haha. Oh jeeze, good ol' brainless Vinny is back I suppose. I must be missing something. Anyway:


Oh and, I have to say this.... I am reeeeally grateful for your time, and quite frankly, patience. I love this community already ;)

---

### Post by Rubi1200 on 2010-08-08
> **VinnyLC said:**
> I got this pop-up(linked below) that states I either need to assign one myself or else I don't get one, haha. Oh jeeze, good ol' brainless Vinny is back I suppose. I must be missing something. Anyway:


Oh and, I have to say this.... I am reeeeally grateful for your time, and quite frankly, patience. I love this community already ;)
First of all, there is no dumb question here. And you are not > brainless

Ok, this is going to be a pain, but we have to do it. Go back again and then resize the 20GB partition so that you have enough space for Ubuntu. I recommend 18 GB. Then with the space left, 1-2 GB depending on your needs, create the swap partition. Go through the same procedure as above for preparing the 2 partitions.

I am here to help for at least the next hour (then I need to sleep a bit haha).

---

### Post by VinnyLC on 2010-08-08
How do I change the partition's volume through Ubuntu? Or am I going to need to hop over to Vista(I hope not, I got Ubuntu for a reason :P)
Please, please forget I asked that. I figured it out. It was right in front of my face. *sigh*

---

### Post by Rubi1200 on 2010-08-08
> **VinnyLC said:**
> How do I change the partition's volume through Ubuntu? Or am I going to need to hop over to Vista(I hope not, I got Ubuntu for a reason :P)
Since you are using the Ubuntu CD (I assume?), you can resize the partition using GParted, which is installed by default on the LiveCD. 

Go to System > Administration > GParted. Make sure all partitions are unmounted, meaning there are no locked key icons next to them. Then right-click on the 20GB partition and choose Resize. Do what you have to do and then Apply. You will then have 2 parttions; one for the root filesystem and one for swap. No need to format them at this stage unless you want to.

When you are done, start the installer again and move forward to where we were not so long ago.

Edit: just saw your edit; no problem (some of this I am working on from memory because I have not installed anything for some time).

---

### Post by VinnyLC on 2010-08-08
Whoa! It worked. You have no idea how appreciative I am right now :P
That website is right when they say Linux isn't Windows, I can tell by the patience you gave in the support. Thanks, you really helped me out.
Vinny

---

### Post by Rubi1200 on 2010-08-08
> **VinnyLC said:**
> Whoa! It worked. You have no idea how appreciative I am right now :P
That website is right when they say Linux isn't Windows, I can tell by the patience you gave in the support. Thanks, you really helped me out.
Vinny
You are more than welcome :)

So, you have Ubuntu installed and everything works fine?

Also, no problems with booting into Windows again?

If, yes: welcome to Ubuntu as well as dual-booting.

Please mark this thread as Solved using the Thread Tools near the top of the page. This way, others can also benefit from your experiences.

Feel free to come back and ask as many questions as you want; there is no such thing as a dumb question here.

---

### Post by libssd on 2010-08-08
Re-install Ubuntu from the beginning. When the installer gets to the partitioning phase, choose Manual. For the partition filesystem type, choose ext4. Then **TYPE** a slash character / in the area where it says "Mount point". Also click on the Format box. A picture is worth a thousand words:

---

### Post by VinnyLC on 2010-08-08
> **Rubi1200 said:**
> You are more than welcome :)

So, you have Ubuntu installed and everything works fine?

Also, no problems with booting into Windows again?

If, yes: welcome to Ubuntu as well as dual-booting.

Please mark this thread as Solved using the Thread Tools near the top of the page. This way, others can also benefit from your experiences.

Feel free to come back and ask as many questions as you want; there is no such thing as a dumb question here.

Erm, I've yet to try that. It hasn't finished installing yet, and I'm kind of afraid to try to boot into Windows again in case it doesn't work.... Guess I'm going to have to.

---

### Post by Rubi1200 on 2010-08-08
> **VinnyLC said:**
> Erm, I've yet to try that. It hasn't finished installing yet, and I'm kind of afraid to try to boot into Windows again in case it doesn't work.... Guess I'm going to have to.
Don't worry; let Ubuntu finish installing and then boot into it and after that into Windows. There shouldn't be any issues.

---

### Post by VinnyLC on 2010-08-08
Thank you, all is well. I can use both Operating Systems normally :D
Solved.

---

### Post by Rubi1200 on 2010-08-08
Excellent!!!

:)

---

### Post by VinnyLC on 2010-08-08
> **Rubi1200 said:**
> Excellent!!!

:)
Definitely, and I don't think I would have been able to do it without your help. ;)

---

