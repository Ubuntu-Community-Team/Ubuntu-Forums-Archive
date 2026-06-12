---
title: "Install help"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by natman on 2008-04-24
I have a dual boot set up and am doing a fresh install of Kubuntu 8.04, so i chosse manual, and get the following list

ntfs
ext3
swap
free

I delete all but the ntfs partitions and am left wit one big free partition, what do i do next format it all as ext3 or some swap, could someone please tell me exactly what i need to do next to install Kubuntu 804 and keep windows.

Thanks

---

### Post by Pumalite on 2008-04-24
In that 'free space', make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
Then press 'Forward'

---

### Post by natman on 2008-04-24
Thank you, but i only ever remember doing two partitons, does the third for home make it safer, but will it cap my home directory size?

---

### Post by Pumalite on 2008-04-24
Having a /home partition is good because you can keep it in case of a reinstall.

---

### Post by natman on 2008-04-24
Okay, sorry about all the question, trying to learn also. I make 3 NEW partitons
1 ext3 mount point /
2 swat mount /swap
3 home mount /home

and the total size of 1+2+3 = Total size of "free space"

And with the separate home partition, does it just work as normal in term of accessing it, is there mounting unmounting needed to work with inside Kubuntu, or will i not even notice the difference?

---

### Post by Partyboi2 on 2008-04-24
You shouldn't have any problems with having home on a seperate partition. Your system will behave like it normally does except that your /home folder is now a seperate partition, so that if you have to reinstall you will not loose what is on that partition as its not part of the / partition.

---

