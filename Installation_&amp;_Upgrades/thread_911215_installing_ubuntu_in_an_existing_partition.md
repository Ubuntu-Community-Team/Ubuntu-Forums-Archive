---
title: "installing ubuntu in an existing partition"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by mekejt on 2008-09-05
Hello everybody,
I have a problem and I am seeking help. I have a machine where there is are some partitions with different OSes:
sda1=ubuntu
sda2=debian
sda3=swap
sda4=extended
sda5=NTFS
sda6=/pub

What I want to do is to install ubuntu in sda2 which means to replace debian by ubuntu without harming the other partitions which they hold important data, I have a ubuntu LiveCD.

If anyone knows how to deal with this or has anu link, just let me know.
thank you in advance.
best regards,

---

### Post by az on 2008-09-05
Just boot the installer and when you get to the partitioning step, pick "manual" and set sda2 as your "/".  It will ask if you want to format it; yes, you do.  Don't forget to set a swap.

That's it.

Ubuntu will scan the other partitions and should pick up all your other OSes and add them to Grub.

---

### Post by mikewhatever on 2008-09-05
At the partitioning stage, select the manual option. The installer will not know you want Ubuntu on sda2 and swap on sda3, right click on each of these select edit, and choose / and ext3 for sda2, and swap for sda3. Proceed with the installation as usual.

---

### Post by joaquinx on 2008-09-05
I have a Dell laptop with 2gb of ram. The hard drive has five partitions: a 71mb Healthy EISA configuration partition, a 10gb Recovery NTFS Primary, 48gb Vista Primary boot NTFS, 14gb xx Logical NTFS, and a 2.50gb Healthy Primary. I would like to install Unbuntu on the xx 14gb drive. The question is: do I need other partitions for the OS and swap areas? Can I install the OS and user area in the 14gb partition and use the 2.5gb for the swap? I really don't use the 10gb recovery, but vista does, could I use that drive for the OS and swap partitions?

---

### Post by mikewhatever on 2008-09-05
You can happily use the 14 GB logical partition for both swap and Ubuntu.
1 GB is more then enough for swap in your case. Just be careful not to delete something you need. What's on the 2.5 BG partition, by the way?

---

### Post by joaquinx on 2008-09-05
The 2.5gb partition is a Dell diagnostics partition that boots up in XP. In reading the instructions for a dual boot at this site, they speak of three partitions: OS, user, and swap. Do I need three partitions or can I install them on one partition - the 14gb one? I want to keep the Vista one for now since it contains a bunch of software and files, also the Dell diagnostics one. The recovery one could go as well as the 2.5gb "Healthy".

---

### Post by mikewhatever on 2008-09-05
> **joaquinx said:**
> The 2.5gb partition is a Dell diagnostics partition that boots up in XP. In reading the instructions for a dual boot at this site, they speak of three partitions: OS, user, and swap. Do I need three partitions or can I install them on one partition - the 14gb one? I want to keep the Vista one for now since it contains a bunch of software and files, also the Dell diagnostics one. The recovery one could go as well as the 2.5gb "Healthy".

It's a popular setup to have /, /home and swap, but you can also have it as / and swap only. [Read more on partitions.]("http://psychocats.net/ubuntu/partitioning") I would simply delete the 14 gb one, create a new extended partition, and then create / and swap as logical partitions for Ubuntu.

---

### Post by joaquinx on 2008-09-07
I have a 48gb Vista partition setting between a 10gb and a 14gb ntfs partitions. Using the Vista Disk Management screen, I am unable to change these partition into something that Ubuntu would use. Since Disk Management sometimes works and sometimes doesn't, I can not extent the Vista partition into the 14gb one. In trying to install Ubuntu with the manual option with the 10gb as the / and the 14gb as the /home, it asks for a swap area. I decided to opt out of the swap area and then Ubuntu fails. (I really need to write down the exact error). 
I was guided to a page that discussed partitioning, but none of the examples seem to fit my configuration. I tried to use Diskpart, but really don't know what the partitions should look like.
I guess that the bottom line is: What should the two partitions' be? I have a background in computer programming, but partitioning drives is something that I am not experienced in. I'll get back with the error message from Ubuntu.

---

### Post by joaquinx on 2008-09-07
I used the 10gb partition for the / and the 14gb for the /home and skipped the swap. The GRUB boot failed to install. And I couldn't get it to recognize the Linksys router. Back to stage one.

---

