---
title: "Updating kernel failed : no space in /boot partition"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Circomel on 2009-11-25
Hi, 

I've just tried to update my kernel from the 2.6.31.14 to the 2.6.31.15 using the updating manager but it failed due to lack of space in my /boot partition.
I have made a separate /boot partition of 32MB because I have installed 3 different Linux distributions and thought it was a good idea to have a dedicated partition for grub and the kernel of my main distribution (Ubuntu karmic), but now I realize it complicates my life for nothing... :(

So, I tried to "make" some space and moved the initrd.img-2.6.31-14-generic archive elsewhere.

My questions are :

- Let's say I want to keep the possibility to boot with the 2.6.31-14 kernel, **do I actually need to keep the initrd.img-2.6.31-14-generic?** 
Isn't it use just to install the kernel?

- **How do I reinstall the 2.6.31.15 kernel properly?**
When it tried to install it, there were 3 packages. I can't remember the names, so I tried to figure it out and used synaptic to reinstall "linux-image-generic" and "linux-image-2.6.31-15-generic" but I got a big error message to do with the /var/cache/apt/archives...

Now, I am a bit anxious about restarting my computer 'cause I am not sure it's going to boot properly with half kernels installed. :roll:

I would appreciate very much if anyone took some time to advise me.

---

### Post by fancypiper on 2009-11-25
> - Let's say I want to keep the possibility to boot with the 2.6.31-14 kernel, do I actually need to keep the initrd.img-2.6.31-14-generic?
Isn't it use just to install the kernel?I think you need to keep it.

> but I got a big error message to do with the /var/cache/apt/archives...It helps to post the error messages.

[Getting the Best Help on Linux Forums](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

Are you out of room?  You can use synaptic and remove the cached deb files in the preferences.

If your latest kernel works OK, you can delete the ones you don't need, including all the other files that refer to the older kernels.

Then, you should be able to install the latest kernel with:

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove

---

### Post by phillw on 2009-11-25
> **Circomel said:**
> Hi, 

I've just tried to update my kernel from the 2.6.31.14 to the 2.6.31.15 using the updating manager but it failed due to lack of space in my /boot partition.
I have made a separate /boot partition of 32MB because I have installed 3 different Linux distributions and thought it was a good idea to have a dedicated partition for grub and the kernel of my main distribution (Ubuntu karmic), but now I realize it complicates my life for nothing... :(

So, I tried to "make" some space and moved the initrd.img-2.6.31-14-generic archive elsewhere.

My questions are :

- Let's say I want to keep the possibility to boot with the 2.6.31-14 kernel, **do I actually need to keep the initrd.img-2.6.31-14-generic?** 
Isn't it use just to install the kernel?

- **How do I reinstall the 2.6.31.15 kernel properly?**
When it tried to install it, there were 3 packages. I can't remember the names, so I tried to figure it out and used synaptic to reinstall "linux-image-generic" and "linux-image-2.6.31-15-generic" but I got a big error message to do with the /var/cache/apt/archives...

Now, I am a bit anxious about restarting my computer 'cause I am not sure it's going to boot properly with half kernels installed. :roll:

I would appreciate very much if anyone took some time to advise me.



TBH, I'm more concerned that your /boot is full.  can you post the output of ```
df
```

```
 sudo fdisk -l
``` also helps,
Phill.

---

### Post by Circomel on 2009-11-25
Thanks Fancypiper & Phillw for taking the time to answer.

> 

[quote]- Let's say I want to keep the possibility to boot with the 2.6.31-14 kernel, do I actually need to keep the initrd.img-2.6.31-14-generic?
Isn't it use just to install the kernel?                      I think you need to keep it.
Are you out of room?  You can use synaptic and remove the cached deb files in the preferences.
[/quote]It didn't help. I'm short of 4MB to move back the initrd.img-2.6.31-14-generic file to the /boot directory.
But in reality if I can be sure the 2.6.31-15 kernel is installed properly, I don't really need to keep the old one.

> [quote]but I got a big error message to do with the /var/cache/apt/archives...                      It helps to post the error messages.[/quote]Sorry about that. I didn't for 2 reasons :
- half of the error message is in French (my computer's default language), and I'm not sure to translate it accuratly, since words need to be quite specific
- I couldn't copy and past, but only took a sreenshot of those 20 lignes.

Here are the results of the df command :

```
Sys. de fich.           1K-blocs       Occupé Disponible Capacité Monté sur
/dev/sda2             12594596   6614112   5340696  56% /
udev                   1028472       300   1028172   1% /dev
none                   1028472       384   1028088   1% /dev/shm
none                   1028472       312   1028160   1% /var/run
none                   1028472         0   1028472   0% /var/lock
none                   1028472         0   1028472   0% /lib/init/rw
/dev/sda1                30075     23693      4778  84% /boot
/dev/sda5            115353540 101594176   7899660  93% /home

```And the fdisk -l :

```
Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0xba73d918

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1           4       32098+  83  Linux
/dev/sda2               5        1597    12795772+  83  Linux
/dev/sda3            1598        3202    12892162+  83  Linux
/dev/sda4            3203       19457   130568287+   5  Etendue
/dev/sda5            3203       17792   117194143+  83  Linux
/dev/sda6           17793       19264    11823808+  83  Linux
/dev/sda7           19265       19457     1550241   82  Linux swap / Solaris
```

(Sorry about the French titles)

Thanks again for your help.

---

### Post by inevitable7 on 2009-11-25
i also just updated my ubuntu using the update manager and now i can't load ubuntu

after i select ubuntu to load (choosing between windows and ubuntu) i get a page that says press TAB to get more commands and when i press it, i get a list of commands i can use

normally i get another window with two ubuntu load options (safe and regular) and two windows xp options

i'm guessing something is wrong with the kernel because when i use some of the commands, it says that i don't have a kernel

i have no idea where to start

---

### Post by Circomel on 2009-11-25
Hi Inevitable7,

You problem seems to be different than mine : if I couldn't update my kernel at the first place, it's because I have a separate partition for my /boot file and this partition is too small.

I think you'll have more chance to have an answer to your problem if you open an other thread.

Good luck ;)

---

### Post by oldfred on 2009-11-25
Here is another thread with the same issue.

You can move boot back to your main partition or you can increase the size of your /boot by a few mb. 

[http://ubuntuforums.org/showthread.php?t=834376](http://ubuntuforums.org/showthread.php?t=834376)

I have 4 operating system and went with a dedicated grub partition with old grub and chainbooted to each operating system. Of course when I installed Karmic it overwrote that and I am currently booting via Karmic's grub, but I will change it. My grub partition is about 114mb and I am using 38mb for grub and menus and because of the way I created it a few kernels.

---

### Post by Circomel on 2009-11-25
Thanks Oldfred for posting a link.

I had a look at the thread, but I didn't really want to move my boot file to the main partition (which I haven't marked as bootable anyway) and it also involved editing the grub menu.list which doesn't exist anymore with grub2.

Anyway, I decided to be bold and deleted the initrd.img-2.6.31-14-generic archiveas well as the initrd.img-2.6.31-15-generic one,
I reinstalled the 3 packages with "2.6.31-15" in their title, this time successfully : obviously it was just a space problem,
And restarted my computer, and it just worked fine :D. I could restarted with the 2.6.31-14 kernel** _or_** with the 2.6.31-15 kernel : even if I deleted the initr.img archives (7,5Mb each), I still had the kernels themselves and their config files (< 4Mb each)[B].
[/B]
In any case, thanks for having taken the time to look into my problem.

---

