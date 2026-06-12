---
title: "Saving my personal files to format and reinstall ubuntu"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by nezurian on 2009-11-26
Hello!

I am kind of newbie and I have been using ubuntu for 5-6 months. 

While I was using Windows (now I hate it), I was seperating my HDD to 2 partitions like 10 gb and 30 gb (my HDD is 40gb). So I was installing the windows to C: drive, and was using the D: drive for my personal files. When the windows was down, or needed to reinstall, I was simply formatting c: drive where windows is installed, and I was able to save my personal files like my music, documents and pictures etc.

I wonder how to do this in ubuntu. Can I install ubuntu like 10 gb partition, and take the /home folder to another partition of 30gb? Let's say, it can be done; can I choose where to install ubuntu? so that I will have a fresh install but my home folder is untouched.

If it's not possible, another way is to target my /home folder to my external HDD. So that my /home will be directed to for example /media/wdpassport/sadasd . Is it possible?

And the last one: Can I create partitions while I am using Ubuntu (like partition magic), and move my /home folder?

Thank you :)

---

### Post by jjcv on 2009-11-26
Yes you can create a separate /home as you want to do, and keep this over multiple installs.  I do this myself.

When you setup your system and get to the point of creating partitions you need to go into the advanced (or custom) options.   Basically you need to create 3 partitions

/            [your main filesystem]   ie /dev/sda1
/home        [For your personal files] ie /dev/sda2
swap         [For swap space]  ie  /dev/sda3

The first time you do this you will need to fomat all the partions.  But next time you only format "/" and not /home

Remember what partition /home is on so you can select this when you need to.

Always backup before you fiddle with partitions.

---

### Post by nezurian on 2009-11-27
Whow, that's really cool. 

But I don't understand why should I create a swap? What do I use it for?

---

