---
title: "Update manager on 1st March 2013 broke Ubuntu 10.04 on my PC"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2013-03-01
Update Manager started on my PC on 1st March stating Software updates are available for this computer.
As is my normal practice I clicked Install updates and let it run to completion. This took a longish time.
On rebooting Ubuntu, many lines appeared on a black screen and my computer hung with the Caps Lock and Scroll Lock indicator lights flashing.
Fortunately I had taken an Acronis True image backup of the hard drive earlier on 1st March 2013 and I was able to restore the Ubuntu root partition.
This successfully restored the root partition and Ubuntu (kernel 2.6.32-45-generic) booted OK.
Looking at the details of the (I think the same) Update Manager Software updates that caused the problem I see is shows a Download size 107.5 MB and 44 selected.
There is an update to kernel 2.6.32-45-generic in the list shown by Update manager and many updates for libqt4.
This is the first time I have had an Ubuntu update problem and this potentially disastrous failure for me since I started using delightful Ubuntu as my regular and vital operating system with an install of Ubuntu 8.04 in 2008.

I attach 5 files of screenshots of the list of Software updates. There is one more to attach (see my next post in this thread).

---

### Post by welshmike on 2013-03-01
Attached is the sixth and final screenshot.

---

### Post by satyamM on 2013-03-02
Even I am having problems with the yesterday's update. Now whenever I  open "System Settings" its window pops out on the screen and it doesn't  close thereafter whenever I try to do. Plus more irritating is **its  window remains at the top of all other windows of different application  which I have opened**. Everytime I have to restart the laptop to work  normally. Your problem is more weird. Update manager doesn't fail to this  extent I suppose. Some mod/admin will be coming to help you & me.

---

### Post by welshmike on 2013-03-02
Having slept on it perhaps the problem was as a result of me cancelling the large update because it was taking a long time.
Hmm! Self inflicted User error? :oops:

---

### Post by welshmike on 2013-03-03
Updates linux-headers-2.6-32-45 , linux-headers-2.6-32-45-generic and linux-image-2.6-32-45-generic broke my system.
After recovering from getting my ubuntu system broken by the recent update I did the update for all the items except the above.
Then later I did the updates for the above and guess what? My system was blown away as stated in my first post in this thread.
Oh dear! I do not know what is going on but I have lost my 5 years of confidence in Ubuntu updates.
My system is now recovered after my true image restore of my ubuntu root partition but I now need to block the aforesaid updates. How sad...

---

### Post by prodigy_ on 2013-03-03
> **welshmike said:**
> linux-headers-2.6-32-45 , linux-headers-2.6-32-45-generic and linux-image-2.6-32-45-generic
That's kernel and kernel headers. Sometimes kernel updates can indeed break things. If you have any proprietary drivers installed you could try removing them before updating kernel. Or you can stick with the old kernel if everything works.

---

### Post by welshmike on 2013-03-04
> Originally Posted by welshmike
linux-headers-2.6-32-45 , linux-headers-2.6-32-45-generic and linux-image-2.6-32-45-generic 

> **prodigy_ said:**
> That's kernel and kernel headers. Sometimes kernel updates can indeed break things. If you have any proprietary drivers installed you could try removing them before updating kernel. Or you can stick with the old kernel if everything works.

The only drivers I recollect having installed were for my HP Deskjet D1660 printer, my Canon iP2600 printer and my Musktek BearPaw 1200CS scanner.

However I note
> mike@notebook:~$ uname -r
2.6.32-45-generic
mike@notebook:~$ 

that I am running with the same kernel version that Update Manager wants to update.

I'm confused !!!

---

### Post by Paddy Landau on 2013-03-04
> **welshmike said:**
> … I am running with the same kernel version that Update Manager wants to update.
I'm confused!
It is not upgrading the kernel; merely updating.

Unless someone else has a better idea, my suggestion is to not update the kernel until a newer version is released for your system. You don't say what you are using, but looking at your signature I imagine that you are using 10.04?

---

### Post by welshmike on 2013-03-04
> **Paddy Landau said:**
> It is not upgrading the kernel; merely updating.

Unless someone else has a better idea, my suggestion is to not update the kernel until a newer version is released for your system. You don't say what you are using, but looking at your signature I imagine that you are using 10.04?

Yes I'm running with 10.04 which of course goes end of life in April.
I liked the idea of 12.04 Unity but found it slow and a little buggy so I prefer not to go to Unity.
[Here]("http://ubuntuforums.org/showthread.php?t=2121852") in the Ubuntu forums I wrote about trying Lubuntu 12.04 on my old laptop and quite liked it.
So after 5 happy years starting with Ubuntu 8.04 LTS as my main operating system it looks like it will be Lubuntu 12.04 for me next month.

---

### Post by Paddy Landau on 2013-03-04
> **welshmike said:**
> I liked the idea of 12.04 Unity but found it slow and a little buggy
Ubuntu 12.04 LTS has improved dramatically recently; you may want to try the latest release, 12.04.2 LTS (available from the [download page]("http://www.ubuntu.com/download/desktop")).

However, if you have low-end hardware, you'll find Ubuntu somewhat slow. It needs 1Gb RAM, but I recommend at least 2Gb, preferably more.

Try [Xubuntu]("http://xubuntu.org/") (using the XFCE desktop); system requirements are somewhere between Ubuntu and Lubuntu. It's more customisable than Lubuntu, I believe.

[Lubuntu]("http://lubuntu.net/") (using the LXDE desktop) is best for low-end hardware; it has saved several ex-Windows machines I've handled that would have otherwise gone to recycling. The only problem with Lubuntu is that there isn't (yet) an LTS version; although, I hope, the regular distribution upgrades should work.

Both Xubuntu and Lubuntu are good, reliable systems.

---

### Post by welshmike on 2013-03-04
Thanks for the reminder about Xubuntu. I did try it a while ago (on my old Toshiba notebook - 1.5GiB RAM). I'll try it out again there and see if it meets my needs. If so I'll install it on this msi CR620 notebook that has 2GiB RAM.
Would an extra 2GiB RAM (making it 4GiB) make much difference to performance I wonder?

[I]I understand what you wrote about Windows. This notebook is dual boot XP and Ubuntu. I groan when I have to use XP for an application, Atomic Mail Sender, that [AMIPP]("http://www.amipp.org.uk/"), where I run a [forum]("http://www.amipp.org.uk/phorum5/index.html"), bought for me to send out a bulk email to some thousands of members registered in a MS Works database.
I also have a minimal XP in saved system status running as a guest under VirtualBox that I use for my weekly shopping list that is a small MS Works database. I've not found an application that runs on Ubuntu that is as suitable.[/I]

---

### Post by Paddy Landau on 2013-03-04
> **welshmike said:**
> Would an extra 2GiB RAM (making it 4GiB) make much difference to performance I wonder?
With Ubuntu, I believe so, yes. With Xubuntu and Lubuntu, probably not unless you use RAM-intensive applications such as video editing.

> **welshmike said:**
> I also have a minimal XP … as a guest under VirtualBox [with] a small MS Works database.
I don't know Works. Does Libre Office's Base not do the trick?

---

### Post by welshmike on 2013-03-04
> **Paddy Landau said:**
> 
I don't know Works. Does Libre Office's Base not do the trick?
Possibly. I'll need to learn how to use it.

---

### Post by MainframeGuy on 2013-03-18
or there is unity 2d which does not need half as much resource

---

