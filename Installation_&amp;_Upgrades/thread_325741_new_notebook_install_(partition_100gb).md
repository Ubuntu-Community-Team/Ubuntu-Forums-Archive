---
title: "new notebook install (partition 100gb)"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by Lowfront on 2006-12-26
Alright just got my x60, ya I'm high on life right now.

First things first the clean install.  Planning on just doing xp and ubuntu because I really don't give a crap about vista.


So I was thinking

got 100 gigs

going to be using mostly Ubuntu but want xp just in case.

So what do you think

xp 5gb
ubuntu 5 gb

and then what....

thanks a lot

---

### Post by meng on 2006-12-26
You'll want a swap partition, perhaps 1 GB, although it's arguable how much you need it.
Then you'll want a separate partition for /home (data) which can be recognized by both Windows and Ubuntu (format to ext3, install fs-driver on Windows, [www.fs-driver.org](www.fs-driver.org))

Perhaps instead of allocating all remaining space to /home you could leave 10GB free, just in case you want to fool around with other distros/OSes in future.

Having said all of that, GParted (best on live cd) will allow you to make changes to your partition table later if you decide you didn't make the wisest choices in terms of size.

---

### Post by Lowfront on 2006-12-26
so regardless of how big or small the home drive is windows will recognize it?

Do you think 5 gigs for windows is fine, considering I'm not going to be using it really at all.

also should I try out 64 bit or just stick with the 32?  I'm sill new to linux and am kind of afraid of a very hard setup.  But would really love to get 64 bit going.  I don't care about flash and such so that doesn't matter to me.

---

### Post by meng on 2006-12-26
Windows should recognize the /home partition (you can stop thinking of it as a "drive") so long as you install fs-driver. Note that some have advised not to install fs-driver because it may be easier for Windows viruses to cause havoc with your data if windows recognizes the partition. However, I just choose to be more careful with Window.

I think 5GB for Windows is fine. I'd still recommend 32-bit install, but you could experiment with 64-bit on another partition!

---

### Post by Lowfront on 2006-12-26
ok so on gpart how should this look then

5gb ntfs primary          windows
5gb fat 32 primary       ubuntu

extended 90gb
79gb ext 3               home
1gb                     linux swap 
10gb fat32           other os

---

### Post by bulldog on 2006-12-26
> **Lowfront said:**
> ok so on gpart how should this look then

10gb ntfs primary          windows just in case you don't like ubuntu.
10gb ext3 primary       ubuntu for the root / 5gb should be sufficient but if you want to install applications you could run out of space very soon.

extended 90gb
40gb ext 3            /home
39gb ext 3           /data always handy to keep important data aside of everything. 
1gb                     linux swap 
10gb fat32           other os

I have modified your list a little,but you're free to do as you want of course.

---

### Post by Lowfront on 2006-12-26
10 gigs for both os's.  I really don't think I'll need to much.  On xp I'll have next to nothing on there.  

And on Ubuntu I really haven't found any programs I need besides whats on there accept for gtkpod.


I don't know I'm limited on space so would really like to make the most of it.   But I guess I should go the better safe then sorry route.

---

### Post by bulldog on 2006-12-26
If you gonna use ubuntu on a daily bases ,you'll install software for sure.
If you made a 5gb / root partition you'll end up without space,you can repair this but if you're not into it,it could be a pain to do.

You haven't any experience with ubuntu or Linux?
How you gonna know on forehand, you gonna like it?
It's really different from windows.

But it's your computer and hard disk,so you can do what ever you want to do,just giving some advice to think about.:D

---

### Post by Lowfront on 2006-12-26
Ive been using for a month now and love it

---

### Post by bulldog on 2006-12-26
> **Lowfront said:**
> Ive been using for a month now and love it

Yes but can you trouble shoot if things go wrong?
That's why it's comfortable to have a windows install waiting for you.

You can learn a lot in one month,but using it on a daily bases is some what different.

But I won't argue,if you think 5gb is enough,well make it so.:D 
After all you gonna use this box and should know what to do.

---

