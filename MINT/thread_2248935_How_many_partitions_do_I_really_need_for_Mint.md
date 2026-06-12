---
title: "How many partitions do I really need for Mint?"
date: 2014-10-18
forum: MINT
---

### Post by J Tinsby on 2014-10-18
I see so many other partitions that people use for Mint that I don't have or didn't create for Ubuntu. Such as /usr ... /boot..../var...etc. I only have 3 for Ubuntu root.../home ...../swap and I'm told with enough RAM, ( I have 6GB) I may not even need a /swap file. I ask because I tried a Mint Qiana Live CD and liked the interface better than Unity. A lot of things that worked right away in Ubuntu didn't work, like my printer and scanner. Ubuntu goes on standby and awakens with no trouble, Mint didn't do that either!

Love that GUI in Mint but I hesitate to move away from Ubuntu.

I will be moving to an SSD and want to keep the read / write cycles to a minimum, seems like all those partitions in Mint won't help me achieve that goal.

Thanks to all, I always get the **best** information from this group that's why I am here and not somewhere else asking these questions.

---

### Post by TheFu on 2014-10-18
How many partitions?  The answer depends on what you want to accomplish.
Minimally, 2.  / and a swap.
Nominally, 3.  /, /home, and a swap.
If you add LVM, then 3.   /boot, swap, and the rest for LVM to manage. It also manages swap.
If you use encryption ... at least 3.  /boot cannot be encrypted, swap needs to be encrypted too and /.

Of course, there are many other methods.

To have swap or not?  That depends on the workload for the system. For desktops, I think having swap is highly, highly needed.  Desktops tent to get used more and more with many more programs open than a server.  I have some servers with extremely well-known workloads - no swap at all. I've set the RAM for them to be exactly what is necessary.

If you hibernate, swap needs to be a tiny bit larger than RAM.

On a normal desktop with 4+G of RAM (no hibernation), then a 2-3G of swap should be fine. The goal of swap is to let the user "feel" the system slow down when RAM runs out.

On a RAM constrained system, like a netbook or chromebook, a larger swap may be desired.  My netbook has 2G of RAM and I'd initially setup 2G of swap. Unfortunately, the system would crash about once a month ... it has an SSD, so swap didn't slow enough for me to "feel" it.  Made swap 4G a few weeks ago - no crashes so far.  This netbook is basically an email/browser box for me ... so it is 100% mozilla's fault for sucking too much RAM. ;)  It isn't like there were more than 50 tabs open - geeze.

---

### Post by buzzingrobot on 2014-10-18
Remember, a standard default set of directories is required:  /, bin, usr, etc, var, home, etc.  

if only a / partition and a swap partition exist, then all those required direcories will be created within the / partition.

If additional partitions are created, one or more of those directories can be mapped to partitions.  E.g., you can create a partition you intend to use for /var, and map that directory to it. /var remains in the same place in the directory tree, but it resides on its own partition.

---

### Post by J Tinsby on 2014-10-18
> **buzzingrobot said:**
> Remember, a standard default set of directories is required:  /, bin, usr, etc, var, home, etc.  

if only a / partition and a swap partition exist, then all those required direcories will be created within the / partition.

If additional partitions are created, one or more of those directories can be mapped to partitions.  E.g., you can create a partition you intend to use for /var, and map that directory to it. /var remains in the same place in the directory tree, but it resides on its own partition.


Thanks for that information now that makes me ask another question.

If my Grub is located on the /root partition why do my restored images fail to boot? The image is made with Acronis 2014 which supports ext 2,3,4 journaling. Makes me wonder why it seems to go wrong when I try and boot Ubuntu.
Since I am imaging all the Ubuntu partitions /root swap and /home, you'd think Grub would go along with it and work fine, yet it doesn't. :( Sure I can use the Boot Rescue CD and that puts Grub everywhere including the MBR where I don't want it. It makes it boot but not the way I'd prefer to have it. Hopefully the transition to the SSD, which will be a clean install of everything, will solve that niggling problem. :)

Regards,

J T

---

### Post by mips on 2014-10-19
> **J Tinsby said:**
> 
If my Grub is located on the /root partition why do my restored images fail to boot? The image is made with Acronis 2014 which supports ext 2,3,4 journaling. Makes me wonder why it seems to go wrong when I try and boot Ubuntu.
**Since I am imaging all the Ubuntu partitions** /root swap and /home, you'd think Grub would go along with it and work fine, yet it doesn't. 

No, if you are imaging the partitions and not the entire disk your MBR will not be backed up.

You can always use 'dd' to backup & restore the MBR 

[http://www.cyberciti.biz/faq/howto-copy-mbr/](http://www.cyberciti.biz/faq/howto-copy-mbr/)
[http://www.techpository.com/?page_id=123](http://www.techpository.com/?page_id=123)
[https://wiki.archlinux.org/index.php/Master_Boot_Record](https://wiki.archlinux.org/index.php/Master_Boot_Record)

---

### Post by J Tinsby on 2014-10-19
RE: the dd command: That's all new to me, I never knew that existed until you told me.

I should have said I am imaging the whole disc including the MBR which clearly shows in Acronis. The system is triple boot of XPired, 7, and Ubuntu.

Should I start a new topic or continue here? I need to explain a bit more but don't want to get too far off topic.

Thanks

---

### Post by TheFu on 2014-10-19
> **J Tinsby said:**
> RE: the dd command: That's all new to me, I never knew that existed until you told me.

I should have said I am imaging the whole disc including the MBR which clearly shows in Acronis. The system is triple boot of XPired, 7, and Ubuntu.

Should I start a new topic or continue here? I need to explain a bit more but don't want to get too far off topic.

Thanks

Most beginner texts on Linux will provide a list of commands and a short description of their purpose.  Get the free PDF for a great book here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  BTW - if you learn the UNIX/Linux CLI, that knowledge will last indefinitely. If you learn the GUI, it changes ever 2-3 years because marketing has trained us that "new" is better. ;(
dd is just 1 of those been-around-forever tools. There are newer versions with some better error handling that might be better to use like ddrescue. For the MBR, it shouldn't matter, but for cloning any HDD the chances of a bad sector preventing a complete mirror is higher.

Anyway - get that book, spend an hour skimming it. Then you'll have the knowledge of where to look later for specific commands.  Of course any Linux book is out of date by the time they hit the printers, but for CLI stuff, it doesn't change nearly as quickly.

---

### Post by buzzingrobot on 2014-10-19
Be careful with dd. Essentially, it copies a batch of bytes from here to there. For example, a bootable ISO image to a USB stick.  Or an entire partition to another drive.

dd assumes it's pointed at the right place. If you tell it, by mistake, for example, to overwrite that ISO image to your backup external drive with a gig's worth of precious files, it will happily do that. 

Try to identify the actual issue you're having with those images before taking random shots with dd.You should look into what an MBR is, and how Grub and Acronis deal with it,

---

### Post by TheFu on 2014-10-19
> **buzzingrobot said:**
> Be careful with dd. Essentially, it copies a batch of bytes from here to there.

That is the UNIX philosophy.  "I told you want I want - now DO IT! Don't ask for confirmation, just do it."

Expect that from every CLI tool and most GUI tools on Linux.

---

