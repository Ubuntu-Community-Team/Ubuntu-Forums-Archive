---
title: "Ubuntu + XP Fresh Installs"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by dethredic on 2007-11-30
I just upgraded my Hard drive, and I would like to install XP and Ubuntu. I would to have windows as the default boot choice and Ubuntu as the second.

I have installed both these operations systems before using the disks partitioner, but have never done it to my satisfaction. I normally install windows first, then Ubuntu second. When I do this, Ubuntu always turns into the default boot.

Also, is there an easy way to change which one is the default boot?

Finally, what is the easiest way to delete an Ubuntu install?

---

### Post by Pumalite on 2007-11-30
Get Gparted Live CD and format your whole hard drive ntfs. Install XP. Boot Gparted again and resize your XP partition, then install Ubuntu. If Windows doesn't show up, it can be fixed easily.

---

### Post by dethredic on 2007-11-30
Ok thanks.

---

### Post by dethredic on 2007-12-02
Well I have decided that I want Ubuntu as my first boot, and Windows as my second. I will assume the path of logic, and reverse the order of Ubuntu and XP.

My only question now is, for the partition part of the Ubuntu setup, should I choose the first option (As if Ubuntu is the only OS) or one of the other ones?

(This step)

[IMG]http://img503.imageshack.us/img503/802/ubuntuinstallthumbnailah2.jpg[/IMG]

---

### Post by Pumalite on 2007-12-02
Are you installing before Windows?

---

### Post by dethredic on 2007-12-02
Yes, I will install Ubuntu First, then windows after.

I would like ubuntu to be the primary boot.

---

### Post by Pumalite on 2007-12-02
Don't do that. Follow my instructions and you will have Ubuntu as your primary boot. BTW, going Manual gives more control of your installation.

---

### Post by dethredic on 2007-12-02
So the instructions from your first post?

---

### Post by Pumalite on 2007-12-02
# 2

---

### Post by dethredic on 2007-12-02
well your first post, so yes #2.

I will post if I have any problems.

Thanks a lot for your help so far

---

### Post by dethredic on 2007-12-02
Ok, the windows CD and Gparted went well.

For Ubuntu partition area, I clicked Manual, and now I see my windows partition and my free space.

What mount point should I use?
What "type" (format) should I use?

Should I make the "free space in case I don't have enough physical memory" partition, and if so, how big should it be and how can I go about doing it (and should it have the same mount point and format of the main partition)?

I have 2 gigs 6400 Ram (800mhz OC to 1000) so pretty fast.

---

### Post by Pumalite on 2007-12-02
This a good scheme:
10 GB for  '/'
2x Ram up to 1 GB for /swap
The rest for /home

---

### Post by dethredic on 2007-12-02
Ok, so I should make 4 partitions: ???

10 GB for /root
10 GB for mount point '/'
1 GB for /Swap
The rest for /home

Also, what do I format these as ext3?

---

### Post by merlinus on 2007-12-02
/ and /root are the same.  You only need one.  Select mountpoint as either / or /root, depending upon the options in the menu.

ext3 is fine.

---

### Post by dethredic on 2007-12-02
ok, thatnks for clearing that up.

Umm, there is no /swap on my list, should I just type it in?

Here is what I have, does it look alright?

[IMG]http://img253.imageshack.us/img253/1680/screenshotyk2.png[/IMG]

---

### Post by merlinus on 2007-12-02
From the graphic, /dev/sda3 looks like /swap to me.  The others look fine as well.

---

### Post by dethredic on 2007-12-02
ok, well I typed in the /swap, because it didn't appear on the list.

---

### Post by dethredic on 2007-12-02
ok , when I press forward it gives me the message that I don't have not selected any partitions to use as swap space, I assume it must be wrong, any typing in /swap didn't work.

---

### Post by merlinus on 2007-12-02
There definitely should be a swap option in the dropdown menu when you select and choose to edit the partition.  Did you try right-clicking on the partition?

---

### Post by dethredic on 2007-12-02
Yes, I go right click -> edit

Then my choices are:

/
/boot
/home
/tmp
/usr
/var
/svr
/opt
/user/local


I would take a screen shot, but I can't take one when I have the arrow thing pressed to show the options.

---

### Post by merlinus on 2007-12-02
You might look at this tutorial:

[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

---

### Post by dethredic on 2007-12-02
well, after looking at the images in the tutorial.

I had the type as ext3 and the location as /swap, where as the type should be swap. I found it, and it worked. Thanks a lot!!

---

### Post by merlinus on 2007-12-02
Excellent news!

Have fun, and post back with any issues.

---

### Post by dethredic on 2007-12-03
ok, everything seems to be working fine, but just a couple questions:

How can I lower the countdown time?
How can I remove all the other partition options? (like backup and memtest and such)?

---

### Post by Pumalite on 2007-12-03
Bad idea to remove memtest or Recovery. I don't know what you mean by backup. If you mean other kernels; don't do it either. You never know when and update will go south and you will need a different kernel to boot.

---

### Post by dethredic on 2007-12-03
ok, you have a good point.

how about lowering the time before it auto chooses?

---

### Post by merlinus on 2007-12-03
gksudo gedit /boot/grub/menu.lst

Look for this line near the top:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

And change timeout to whatever you like.  Best not less than 3 so you have time to manually choose.

---

