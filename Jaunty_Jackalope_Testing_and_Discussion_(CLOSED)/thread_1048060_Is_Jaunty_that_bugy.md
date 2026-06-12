---
title: "Is Jaunty that bugy?"
date: 2009-01-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sroland81 on 2009-01-23
Hi all, i'm running Intrepid 32bit on Compaq Presario F700, AMD Athlon X2, 2GB ram, nVidia... etc. i feel like i want to write "sudo update-manager -d" and click on new distribution available... should i do that? is Jaunty that much buggy like it was Intrepid alpha5 or 6? i really want a faster boot time... and overall performance... is the performance increased some? is there some list of things that are already fixed for most common hardware or notebook users?

thanks,

Santiago.-

---

### Post by Archmage on 2009-01-23
For gods sake. It is an ALPHA! It may screw your system, delete all files, set your PC on fire, rape your dog and kindnap your daughter, wife and sister!

There are bugs, security risks, crashes and so on. Don't use it as your productivy system.

---

### Post by SlowJet on 2009-01-23
> **sroland81 said:**
> Hi all, i'm running Intrepid 32bit on Compaq Presario F700, AMD Athlon X2, 2GB ram, nVidia... etc. i feel like i want to write "sudo update-manager -d" and click on new distribution available... should i do that? is Jaunty that much buggy like it was Intrepid alpha5 or 6? i really want a faster boot time... and overall performance... is the performance increased some? is there some list of things that are already fixed for most common hardware or notebook users?

thanks,

Santiago.-

You could try A3 in Virtual-box 2.1.0 (or the latest 2.1.2)
I run all the Ub's on that as they come and go.
It's a lot of fun, self contained and does harm the orginal system.
[www.virtualbox.org](www.virtualbox.org)

SJ

P.S. You can boot the iso from th harddisk as it can pretend to be your CD.

---

### Post by ronacc on 2009-01-23
the reason to run jaunty right now is to FIND bugs and report them , not to gain any improvements that it may bring . If you have to ask the question you probably shouldn't run juanty until after release .On any given day it can do anything from run flawlesly to fail to boot at all .

---

### Post by Archmage on 2009-01-23
> **ronacc said:**
> On any given day it can do anything from run flawlesly to fail to boot at all .

Don't forget to mention that some people are reporting problems with ext4 and there whole data seems to be lost. No one should use this as their productive system.

---

### Post by ronacc on 2009-01-23
you had already warned of some pretty dire consequences in your first post :p but yes. heres the thread for reference.
[http://ubuntuforums.org/showthread.php?t=1040199](http://ubuntuforums.org/showthread.php?t=1040199)

---

### Post by inportb on 2009-01-23
> **sroland81 said:**
> is Jaunty that much buggy like it was Intrepid alpha5 or 6?

Um... that should go without saying. Though... I haven't experienced any major headaches running this thing.

---

### Post by sroland81 on 2009-01-25
I thaught about running Jautny on a vBox but i wanted to see how respond to my particular hardware. Intrepid Ibex has been the best ubuntu distro ever, i never caused major problems and i had it installed since alpha 4 or 5 and it was not so bugy, i asked this because i read that Jaunty is supposed to be a "bug fixing" distro, and has some interesting things like implementing ext4 file system instead of ext3 and a reduced boot up time about ~30%, i also read about installing Grub2 and migrating ext3 to ext4 in my actual Intrepid, but i would have to compile again the kernel and i don't like the idea. Has anybody did this?

---

### Post by Slug71 on 2009-01-25
> **sroland81 said:**
> I thaught about running Jautny on a vBox but i wanted to see how respond to my particular hardware. Intrepid Ibex has been the best ubuntu distro ever, i never caused major problems and i had it installed since alpha 4 or 5 and it was not so bugy, i asked this because i read that Jaunty is supposed to be a "bug fixing" distro, and has some interesting things like implementing ext4 file system instead of ext3 and a reduced boot up time about ~30%, i also read about installing Grub2 and migrating ext3 to ext4 in my actual Intrepid, but i would have to compile again the kernel and i don't like the idea. Has anybody did this?

Yes Jaunty is a bug fixing and boot performance Version.
Grub2 is not going to be in Jaunty.
Ext3 will still be default in Jaunty. Ext4 as an option.

---

### Post by sroland81 on 2009-01-26
but i read that ext4 file system is only supported by grub2 boot loader, is that right? may be i read wrong.

---

### Post by Gina on 2009-01-26
No, there's a patch for GRUB which is automatically used when you install Jaunty and specify ext4 - so it works.  I have two ccomputers using ext4 and the standard (legacy) grub.  Installation when ahead with no problems.

---

### Post by Slug71 on 2009-01-26
Yep, Grub Legacy has been patched to boot ext4.

---

### Post by sroland81 on 2009-01-27
is there some thread there explaining the patch process for the grub in order to boot with ext4 fs? if this feature (ext4 fs) is the most remarkable in the Jaunty and reduces boot time that much, i would be very interested on implement it in my Intrepid, what is your advice?

---

### Post by Archmage on 2009-01-27
> **sroland81 said:**
> is there some thread there explaining the patch process for the grub in order to boot with ext4 fs? if this feature (ext4 fs) is the most remarkable in the Jaunty and reduces boot time that much, i would be very interested on implement it in my Intrepid, what is your advice?

Since you would need a new kernel and the new version, I would advice to wait till April and than upgrade to Jaunty.

---

### Post by Slug71 on 2009-01-27
> **sroland81 said:**
> is there some thread there explaining the patch process for the grub in order to boot with ext4 fs? if this feature (ext4 fs) is the most remarkable in the Jaunty and reduces boot time that much, i would be very interested on implement it in my Intrepid, what is your advice?

Firstly, This is JAUNTY Testing and Discussion. Intrepid questions need to be asked else where.
There is no thread here describing how to patch it as it was patched upstream. So if you downloaded Jaunty today, grub is patched.

---

### Post by MrKlean on 2009-01-27
I put the A3 on my regular puter that I use every day LOL!! I know.. everything was backed up with remastersys... and it's running fine ; )  I have hit no problems..YET !!  I backup before I install updates....just in case.. thot you might wanna know!
Laterzzzz

---

