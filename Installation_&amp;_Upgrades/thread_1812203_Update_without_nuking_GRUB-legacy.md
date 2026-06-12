---
title: "Update without nuking GRUB-legacy?"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2011-07-26
Anybody know how to do this? I've seen somewhere something about 'os-prober', and I guess this is one step in my task here?







(let me save some board space here, I hope...
Q; Why are you using GRUB-legacy?
Y: Yes, I are using GRUB-legacy. 'Nuff said on that :wink: )

---

### Post by uRock on 2011-07-26
Do you plan to run an upgrade or a clean install? Which version of ubuntu are you installing?

I would think that you could install the newer version of Ubuntu, then install grub legacy once the install is complete.

---

### Post by Moozillaaa on 2011-07-26
Hi uRock...

It's a fresh install of 10.04 LTS - about 2 months; putting off initial update for this very reason, with multi-boot, chainloaded GRUB**S**/house of cards ...

---

### Post by dino99 on 2011-07-26
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by haresear on 2011-07-26
So I assume you have grub legacy currently installed, and you are concerned that running update will replace it with grub2?

I am using grub legacy with one of my 11.04 installs (after an update hosed grub2), and have gone thru several subsequent updates (not recently, tho) and that hasn't happened so far. I locked the grub legacy package(s) in synaptic to try and prevent update from messing with it. I can't say for sure that will work always work, but so far it has for me.

---

### Post by dino99 on 2011-07-26
its up-to-you but the future never stop

---

### Post by uRock on 2011-07-26
> **haresear said:**
> So I assume you have grub legacy currently installed, and you are concerned that running update will replace it with grub2?

I am using grub legacy with one of my 11.04 installs (after an update hosed grub2), and have gone thru several subsequent updates (not recently, tho) and that hasn't happened so far. I locked the grub legacy package(s) in synaptic to try and prevent update from messing with it. I can't say for sure that will work always work, but so far it has for me.

10.04 was the first LTS to have grub2, so after installing it will try to upgrade grub during regular updates. 

If you installed 10.04 and told it to install grub within the home, instead of the MBR, then after it upgrades to grub2, your system will use grub legacy, then hand off to grub after you select to boot 10.04.

---

### Post by haresear on 2011-07-26
Well, in my case it seemed like the simplest solution to avoid the problem where update forgets where grub2 is originally installed and reinstalls to the wrong mbr.

The larger issue for me is that when I have a half-dozen OS installs, each one really really wants to install its bootloader into the mbr. Grub-legacy is a little more forgiving, and makes it easier to keep the peace. I still use grub2 for my main OS (10.04).

---

### Post by Moozillaaa on 2011-07-26
> **dino99 said:**
> here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? ,  will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)
I think I don't want to install anything, or change any partitions (I KNOW I don't, really); is there any useful info here that applies to me?


> **haresear said:**
> So I assume you have grub legacy currently  installed, and you are concerned that running update will replace it  with grub2?

I am using grub legacy with one of my 11.04 installs (after an update  hosed grub2), and have gone thru several subsequent updates (not  recently, tho) and that hasn't happened so far. I locked the grub legacy  package(s) in synaptic to try and prevent update from messing with it. I  can't say for sure that will work always work, but so far it has for  me.
I'm glad for ya', but I'm hoping there's a way to make sure that this Windows-like behavior stays in WIndows environments.


> **uRock said:**
> 10.04 was the first LTS to have grub2, so after  installing it will try to upgrade grub during regular updates.  So can GRUB2 updates be prevented during updates?

>  If you installed 10.04 and told it to install grub within the home  Yes. 


>  ... , then after it upgrades to grub2, your system will  use grub legacy, then hand off to grub [COLOR=Red][2 ???][/COLOR] after you select to boot  10.04. How do we not allow GRUB2 to install?

Does it have a relation to the os-prober function? How is this done?

---

### Post by uRock on 2011-07-26
> **Moozillaaa said:**
> I think I don't want to install anything; is there any useful info here that applies to me?



I'm glad for ya', but I'm hoping there's a way to make sure that this Windows-like behavior stays in WIndows environments.


 So can GRUB2 updates be prevented during updates?

 Yes. 


 How do we not allow GRUB2 to install?

Does it have a relation to the os-prober function? How is this done?
You should be able to untick the updates within update manager when you run updates, but that is going to get old. I have seen some threads in the past asking how to blacklist certain updates. Here is a set of links to other threads on that subject, but I have no experience in doing that.

I know I have installed 11.04 as a dual boot and it installed its bootloader within its own partition, then I had to restart my 10.04 and run grub-update to make the primary grub see the new install. If your grub is handled by one of the other installs, then this should be possible for you to do, then you'll have to run the OS which controls the default bootloader and add 10.04 to it.

I can't make any promises, since I haven't dealt with grub legacy in a long while.

---

### Post by haresear on 2011-07-26
> **Moozillaaa said:**
> 
Does it have a relation to the os-prober function? How is this done?
The os-prober script just looks for other OS installs when the (grub2) command "update-grub" is run to generate a new grub2 configuration file (i.e. /boot/grub/grub.cfg) assuming grub2 is installed. I don't see how it would affect whether the update manager tries to update grub2 (or grub-legacy) to a new version. If you are using grub-legacy, the os-prober script should never be run anyway, since you don't have grub2 installed and don't even have a grub2 configuration file. Logically, if you only have grub-legacy installed, then the update manager shouldn't try to update/change it to grub2, but I admit logic doesn't always prevail in software design. That is why I've locked the grub-legacy packages. If you find a guaranteed way to do what you want, please report back. Generally I don't like the idea of an OS update process messing with the MBR, so if there is a better way to prevent that, I'm interested. Good luck.

---

### Post by Moozillaaa on 2011-07-31
Anybody?

Where's Herman?

---

### Post by oldfred on 2011-08-01
Herman's here:
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

The os-prober is only part of grub2. The rudimentary prober that was part of grub legacy only found XP and sometime would not find that. We almost always had to help users add boot stanzas to menu.lst.

You can uninstall grub legacy & grub2 and then just reinstall grub legacy & grub common.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Uninstall grub2
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)
Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

But I prefer grub2 now. Most of the bugs for most users are worked out and we much better understand how it works.

---

