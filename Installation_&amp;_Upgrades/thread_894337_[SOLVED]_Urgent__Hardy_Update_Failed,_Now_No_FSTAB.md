---
title: "[SOLVED] Urgent:  Hardy Update Failed, Now No FSTAB"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by robelliott2125 on 2008-08-19
As the title says...

Due to a prob with my Innotek Virtualbox yesterday, I decided to fully upgrade from Gutsy to Hardy, given the amount of time to which the ubuntu community would have had to sort out my drivers and other probs which I had when I first upgraded.

Anyway, last night, the upgrade failed with 15 minutes to go, became fully unresponsive, and as a typical Winblows user, I switched off the PC, thinking "I'll sort it in the morn".

I've come downstairs this morning, to finish what I started, and now, when booting, it reports there is no /home drive for me.
I thought this wasn't going to be an issue, since I have recently managed to use a backed up fstab.

But when trying to ```
rm /etc/fstab
``` and then ```
mv /etc/fstab.bak /etc/fstab
``` it failed, informing me of there not being any file called that.

Booting onto a live disk, and looking for the fstab.bak or even the fstab~ came up with nothing.

Now, I have luckily got a subscription to a solved thread, where I'd commented out my /home folder before, and managed to solve it (obviously), to which there is a copy of my fstab.

Is there any way, to mount the drive with RW, and write the fstab back in, while using live?

Its either this, or I simply fully reinstall, which will annoy me, as you guys have been great sorting the rest of my probs out.

I hope someone can help soon...

---

### Post by sameerds on 2008-08-19
> **robelliott2125 said:**
> 
Is there any way, to mount the drive with RW, and write the fstab back in, while using live?

Yes. When running from the live CD, all your hard discs partitions should be visible somewhere. I don't remember if they are mounted automatically, but you should see them if you poke around a bit. Mounting hard disc partitions like this from the live CD is supposed to be easy, so you probably won't have to do much. Just identify the correct partition for your root (/), and then you can create fstab inside it.

---

### Post by robelliott2125 on 2008-08-19
> **sameerds said:**
> Yes. When running from the live CD, all your hard discs partitions should be visible somewhere. I don't remember if they are mounted automatically, but you should see them if you poke around a bit. Mounting hard disc partitions like this from the live CD is supposed to be easy, so you probably won't have to do much. Just identify the correct partition for your root (/), and then you can create fstab inside it.

I'm able to find the partition, however when mounting, it mounts as RO, not RW.

Because I'm a complete n00b, I wouldn't know how to type out a command to get it to mount as rw.

---

### Post by robelliott2125 on 2008-08-19
Anyone?

---

### Post by robelliott2125 on 2008-08-19
I really don't want to be reinstalling guys...

I know someone will be able to say how to do this...

---

### Post by coffeecat on 2008-08-19
> **robelliott2125 said:**
> I'm able to find the partition, however when mounting, it mounts as RO, not RW.

How are you attempting to mount? In the live environment, if you double-click on the icon for your root partition in Places > Computer it should mount read/write. If that's what you're doing and it's mounting read only, it sounds as though there may be more damage than just a missing fstab - perhaps the journal is corrupted.

This is how you do it from the terminal in the live environment, assuming your root partition is sda6 - adjust appropriately if not.

```
sudo mkdir /media/UbuntuHD
```.. to make the mountpoint. Use any name you want - UbuntuHD is what popped into my head first. Then...

```
sudo mount /dev/sda6 /media/UbuntuHD
```That should mount read/write by default.

---

### Post by robelliott2125 on 2008-08-19
> **coffeecat said:**
> How are you attempting to mount? In the live environment, if you double-click on the icon for your root partition in Places > Computer it should mount read/write. If that's what you're doing and it's mounting read only, it sounds as though there may be more damage than just a missing fstab - perhaps the journal is corrupted.

This is how you do it from the terminal in the live environment, assuming your root partition is sda6 - adjust appropriately if not.

```
sudo mkdir /media/UbuntuHD
```.. to make the mountpoint. Use any name you want - UbuntuHD is what popped into my head first. Then...

```
sudo mount /dev/sda6 /media/UbuntuHD
```That should mount read/write by default.

When double clicking whenever i'm in Live, it doesn't mount as RW, just RO for some reason, and thats been when i've tried doing other things...

I'll try your suggestions now, so thank you.

Is there anything I could do without the commands?

I'm just hoping that the install didn't mess up anything further.

---

### Post by robelliott2125 on 2008-08-19
One question coffeecat, I'm just wondering, how would I find out what drive is for my install partition?

Because, when I set up my pc, I had /swap then / and then /home

I was completely new / am still completely new to linux, so as far as I was concerned, that was enough, especially to keep /home.

---

### Post by robelliott2125 on 2008-08-19
Just to add to the above...

```

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntuHD
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/ubuntuHD
mount: special device /dev/sda6 does not exist
ubuntu@ubuntu:~$ 

```

So needing to know if I can find out what sda is /

If the above makes sense?

---

### Post by coffeecat on 2008-08-19
> **robelliott2125 said:**
> One question coffeecat, I'm just wondering, how would I find out what drive is for my install partition?

I think you mean 'which partition is my root one?'. :wink: It's Microsoft that confuses everyone by referring to partitions as drives. 

Boot up with the live CD and do one of two things. Do both if you want. :p

**The Graphical Way**

Go to System > Administration > Partition Editor and have a look there. It should be clear which is your root partition - it should be ext3 format - unless you've got a very complicated partition structure. If you're unsure, and if you can connect to the internet from the live CD, just post a screenshot and someone will help you.

**The Geek's Way**

Open a terminal and:

```
sudo fdisk -l
```That's a lower-case L, not one. Post the output if you can't work out which is your root partition.

---

### Post by coffeecat on 2008-08-19
> **robelliott2125 said:**
> Just to add to the above...

```

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntuHD
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /media/ubuntuHD
mount: special device /dev/sda6 does not exist
ubuntu@ubuntu:~$ 

```So needing to know if I can find out what sda is /

If the above makes sense?

The answer should be in my previous post - I was typing it when you posted again. I was guessing when I said sda6, because it's a possible when you are dual-booting with Windows. If you have only Ubuntu on that machine, then most likely the root partition is sda1. Whatever - The partition editor or fdisk should be able to tell you.

---

### Post by robelliott2125 on 2008-08-19
Thanks coffeecat, should have thought of that.  :P

Going to try again.

---

### Post by dmizer on 2008-08-19
You have no fstab at all?

Are you sure that this was not the problem? [http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679)

---

### Post by robelliott2125 on 2008-08-19
I've decided to reinstall my OS...

Hardy is going directly onto the system.

Shame I've lost everything like my SMB share with a prog which I can't remember now, which allowed me to share music from my windows pc to this pc with Amarok, and I think i've lost all my bookmarks with Firefox, not to mention my original Samba setup...

This is why I didn't want to just reinstall...

Damnit.

---

### Post by dmizer on 2008-08-19
You said you had a separate /home partition.  I believe your firefox bookmarks are located in your /home partition.

/home/username/.mozilla/firefox/<crazyleters>.default/bookmarks.html

For a new samba setup, see the first link in my sig.

---

### Post by robelliott2125 on 2008-08-19
> **dmizer said:**
> You said you had a separate /home partition.  I believe your firefox bookmarks are located in your /home partition.

/home/username/.mozilla/firefox/<crazyleters>.default/bookmarks.html

For a new samba setup, see the first link in my sig.

I'd finished the installation, but no other drives...

So i'm reinstalling now, hopefully my tinkering will have worked...

---

