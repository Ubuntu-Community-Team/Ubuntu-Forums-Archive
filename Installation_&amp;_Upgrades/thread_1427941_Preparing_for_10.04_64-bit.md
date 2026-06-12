---
title: "Preparing for 10.04 64-bit"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by leeds_shrew on 2010-03-12
I first installed 9.04 32-bit and relatively smoothly upgraded to 9.10, however this was my first experience with Ubuntu.

Now a fully fledged convert, and as someone who hardly EVER uses his Vista install anymore I am looking to go 64-bit for 10.04 not because I know there to be any huge advantages for me but because I feel like I might as well as not having a 64-bit processor.  I am panicking a bit though because I haven't tried a clean install upgrade before.  Can I check the steps with them what know what they're doing please?

1) I go back into Vista and tidy up all the files with a defrag and things - I haven't been in there for a good 3 months but before then hopped in from time to time.  Is it worth me altering the size of Vista's partition at this point as I use it so little? If so: **how?**

2) I download the .iso of 10.04 and burn a lovely CD

3) I back up anything I'm remotely bothered about

4) I pop the CD in and boot and all sorts of exciting stuff happens? (This is where it's a step into the unknown for me) Does it completely wipe all my previous Ubuntu installs? Can I alter the size of my partitions?

To recap: Can someone 1) Tell me how to alter the size of my Vista partition from Vista (if I need to or if it's worth it) and 2) Give me (or point me in the direction of) a reassuring step by step guide to a clean install of Ubuntu overwriting a previous install?

Thanks,
G

---

### Post by bruno9779 on 2010-03-12
There are a number of things you can do, but lets go with order.

1. Resize Windows partitions with windows software.
    I have managed before with a linux tool, but the chances aren't very high.

2. You could also make a live usb (if your mobo supports usb-boot).
    It is up to you

3. Back up and overwrite is definitely the fastest and safest course of action in this case.

4. Here you have a few options, I advise you to have / and /home on different partitions. This will make so much easier to back-up in the future (/home and only /home contains personal data and conf). Then a linux-swap, the size or twice the size of your RAM and you are good to go.

I am looking for a good guide, I'll post back

---

### Post by bruno9779 on 2010-03-12
Backing up your system:

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

About /home:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sdpiowa on 2010-03-12
You should (though I haven't done it) be able to alter the partition size from the Live Disk.  That would let you change Vista's size before installing Ubuntu.  Also, you will probably need to overwrite your previous Ubuntu installation, as you are going from 32-bit to 64-bit.

---

### Post by coffeecat on 2010-03-12
> **leeds_shrew said:**
> Can someone 1) Tell me how to alter the size of my Vista partition from Vista (if I need to or if it's worth it)

You don't need 3rd party partitioning software in Vista (or Windows 7).

Click on start menu button > Right-click on "Computer" > Manage

In the Computer Management window, highlight 'disk management'. Right-click on your C: partition and choose 'shrink'.

**Or**: Control Panel classic View > Administrative Tools > Computer Management, and then as above.

If you find Vista won't let you shrink by much, that's down to the limitations of the inbuilt defragger. In which case this link might help:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

You can shrink the Vista C: partition with Gparted (I've done it) but very much at your own risk. For some this has caused Vista to become unbootable, but not all. I got away with it. Vista merely had a grumble when I first booted it after shrinking it with Gparted and insisted on chkdsk-ing itself before proceeding. There's more about this in that link although it's not a "definitely" as they say. Ymmv, but you have been warned. If you do get an unbootable Vista, you can repair it with the Vista DVD (if you have a Microsoft disc - OEM disc images won't do) or you can download a Vista recovery disc ISO here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by leeds_shrew on 2010-03-14
Thanks for your excellent replies - sorry I haven't responded sooner - I've been away a couple of days.

Creating different partitions for / and /home.  Is that something which I can do as I'm installing from the CD or do I have to be clever to do it?  My problem is, that as a long time Windows user I don't actually know how to do anything for myself other than what I've learnt by installing and running Ubuntu!

Is it just as easy to clean install Ubuntu over a previous version as it was to install it in the first place? I guess that's my real question!

---

### Post by efflandt on 2010-03-14
I'd listen to coffeecat.  Vista and Win7 have their own administration utility to shrink their partitions.  But for XP or older, even ntfs over 5 years ago, I have never had any problems shrinking partitions with Linux tools.

But I did learn that with XP when you temporarily disable virtual memory, you do have to reboot before defragging for virtual memory is freed up.  5 years ago I could only free up 24 GB of a 200 GB drive.  But recently I figured out that I could have freed up over 150 GB by doing it right.  But I only freed up enough for (2) 32 GB Linux partitions (to try 32 and 64-bit) and swap.  I used a gparted live CD, but gparted is also on Ubuntu install CDs.

From there it is up to you if you want to set up specific partitions, or take your chances with automatic use of freed up (unallocated) space.

---

### Post by phillw on 2010-03-14
> **leeds_shrew said:**
> Creating different partitions for / and /home.  

Is it just as easy to clean install Ubuntu over a previous version as it was to install it in the first place? I guess that's my real question!

Once you have used ubuntu for a while, you'll realise having a seperate /home is a really good idea. It just makes life sooooo much less complicated !!

You can then do a 'clean' installation of Ubuntu, without touching any of your own personal stuff -- That's an I win and I win again situation :)

the pyschocats HowTo is excellent and the only one we recommend. (It's written by one of the mods, so we have to say that - lol -- No, seriously, it is well written, it works & he has a thread on here for if you get stuck / have any questions).

As you upgraded from 9.04 to 9.10, a couple of things to note.

you will be running grub-legacy ( we're now on grub2. you can move from grub legacy to grub2 with these instructions --> [https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)  )

You will most likely be running on ext3, you can move over to ext4 this way --> [http://forum.phillw.net/viewtopic.php?f=4&t=8](http://forum.phillw.net/viewtopic.php?f=4&t=8)


Now, if you're doing a clean install it will install Grub2 so there is no need to convert.

If you're going to make a /home partition (and I strongly suggest you do) then if you make it in ext4 format, when you copy over your existing /home to it, it will do the conversion for you. That would only be needed if you already had made a /home partition using ext3 and wanted to upgrade it to ext4.

Regards,

Phill.

---

### Post by leeds_shrew on 2010-03-15
Brain overload occurring... Basically it looks complicated, but once following the tutorials and things I should be alright!

So now looking to do three major things:

1) Reduce the size of my Windows partition as I have limited use for it (woohoo!) - I'll pop off and try to do this in Vista shortly - will let you guys know my success or otherwise.
2) Create a separate /home partition (although most of my personal stuff is on an external drive - seems sensible for downloads etc.)
3) Clean install 10.04 64-bit (when it's released) which is a move from my current 32-bit install.

There's a couple of things I want to check before I move on with steps 2 and 3:

a) My current swap partition (is it a partition? - I just followed standard procedure) doesn't seem to be adequate - what is adequate and how do I make it so? Is it just giving Ubuntu a bit more space as I'm installing it? I read something about it being the same size as your RAM? Correct? How do I check how much RAM I have within Ubuntu - I didn't build my computer and can't remember things like that!

b) Creating a /home partition via a live CD seems complicated. Can I do it whilst I'm doing the install of 10.04 instead?

Thanks all!

---

### Post by phillw on 2010-03-15
> **leeds_shrew said:**
> Brain overload occurring... Basically it looks complicated, but once following the tutorials and things I should be alright!

So now looking to do three major things:

1) Reduce the size of my Windows partition as I have limited use for it (woohoo!) - I'll pop off and try to do this in Vista shortly - will let you guys know my success or otherwise.
2) Create a separate /home partition (although most of my personal stuff is on an external drive - seems sensible for downloads etc.)
3) Clean install 10.04 64-bit (when it's released) which is a move from my current 32-bit install.

There's a couple of things I want to check before I move on with steps 2 and 3:

a) My current swap partition (is it a partition? - I just followed standard procedure) doesn't seem to be adequate - what is adequate and how do I make it so? Is it just giving Ubuntu a bit more space as I'm installing it? I read something about it being the same size as your RAM? Correct? How do I check how much RAM I have within Ubuntu - I didn't build my computer and can't remember things like that!

b) Creating a /home partition via a live CD seems complicated. Can I do it whilst I'm doing the install of 10.04 instead?

Thanks all!

a) Swap = RAM is a good guide. System --> Administration --> System Monitor
Yes, your Swap area is a partition

b) To create a seperate /home during installation, head over to here --> [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Regards,

Phill.
Regards,

---

### Post by leeds_shrew on 2010-03-16
Woohoo! Thanks! I'm excited about all this now, although having difficulty persuading Windows it can shink my C:/ by any more than 7mb despite having 48gb free space! Probably not the forum for that though. :D

---

### Post by coffeecat on 2010-03-16
> **leeds_shrew said:**
>  having difficulty persuading Windows it can shink my C:/ by any more than 7mb despite having 48gb free space!

Yup. That's about par for the course with the Vista resize utility. Have a look at the links I gave in my earlier post. There's probably all the information you need there without having to go to a Windows forum.

---

### Post by leeds_shrew on 2010-03-19
Wahooooooo!!! Now it's REALLY taking off (to an extent where I may need to create a new thread)! I managed to persuade Vista that it could shrink my partition by more than 7mb but got a new error when I tried to shrink it - "Access Denied" (From who?! By who?!)

Cue new solutions. I downloaded a partitioner and told it to chop off a great whack of that partition and merge then unallocated spaces. All goes smoothly until the reboot when I am greeted with the (familiar if you search through the forums) message of "Grub Loading stage1.5. Grub loading, please wait... Error 17"

Yum! Can't get into anything! So I go to a new plan - use my wife's mac and download the ISO for 9.10 64 bit using a torrent client. MD5 and everything good and I confidently pop it into my computer and try to boot from it to be confronted with (you guessed it: Error 17)

Now my computer is a Dell so I don't have a Vista disk which seems to be the next thing to try, but I've come to terms with getting rid of Vista anyway so I really can't be bothered to spend the next 6 hours downloading the ISO from the location mentioned above.

Is this the only way to make my computer do anything apart from display this screen again?

I've got a back up of all my important files and I'm happy to get rid of Vista. Can I get around grub to boot from the Ubuntu CD?

Thanks again,

G

---

