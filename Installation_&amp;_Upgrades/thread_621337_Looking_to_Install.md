---
title: "Looking to Install"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by Casket on 2007-11-23
I bought a computer back in September, that sadly came with Vista installed. After getting annoyed enough at Vista I decided to switch back to XP. After a while though I am getting bored with it and have decided to install Ubuntu as a dual boot.

Just a couple of questions though. 

1. Drivers, normal Linux drivers will work with Ubuntu? The main drivers I am looking for is nVidia, Realtek, AMD64. Any of these have specific problems?

2. Programs like AIM, MSN, mIRC? Do they have Linux counterparts? Or something I can use instead?

3. Games, I play WoW, COD4, and random others. Will I have a problem installing them? Do I need special instals for them?

4. Music, I have a lot, a lot, a lot of music. What kind of formats are suported? What are some popular music players?

Thanks in advance for all your help!


-Casket

---

### Post by GavinZac on 2007-11-23
> **Casket said:**
> I bought a computer back in September, that sadly came with Vista installed. After getting annoyed enough at Vista I decided to switch back to XP. After a while though I am getting bored with it and have decided to install Ubuntu as a dual boot.

Just a couple of questions though. 

1. Drivers, normal Linux drivers will work with Ubuntu? The main drivers I am looking for is nVidia, Realtek, AMD64. Any of these have specific problems? they are usually independant of the distro and run inside the linux kernel.

> 2. Programs like AIM, MSN, mIRC? Do they have Linux counterparts? Or something I can use instead? the default IM program in Ubuntu, Pidgin, lets you connect to all of those, at the same time, and use them as if they were one program :)

> 3. Games, I play WoW, COD4, and random others. Will I have a problem installing them? Do I need special instals for them?WoW works. I dont know about CoD4. For best answers, see [www.winehq.com](www.winehq.com) :)

> 4. Music, I have a lot, a lot, a lot of music. What kind of formats are suported? What are some popular music players?all formats will be supported if you install their codecs. My favourite player is Exaile :) other popular ones are RhythmBox (default) and amarok (like xaile, but for KDE desktop.)

---

### Post by jken146 on 2007-11-23
> **Casket said:**
> 
1. Drivers, normal Linux drivers will work with Ubuntu? The main drivers I am looking for is nVidia, Realtek, AMD64. Any of these have specific problems?

The proprietary nVidia driver can be enabled with the Restricted Drives Manager after installing Ubuntu.  You may want to install the 64-bit version of Ubuntu instead of the i386 one.

> **Casket said:**
> 
2. Programs like AIM, MSN, mIRC? Do they have Linux counterparts? Or something I can use instead?

Pidgin is the IM client that is installed by default.  As far as I know it supports the 3 that you mentioned.

> **Casket said:**
> 
3. Games, I play WoW, COD4, and random others. Will I have a problem installing them? Do I need special instals for them?

Some windows games will work under wine.  Check out [www.winehq.com](www.winehq.com) for full details.   There is also Cedega, a non-cost-free windows emulator designed for games. There are also some Linux games in the Ubuntu repositories.

> **Casket said:**
> 
4. Music, I have a lot, a lot, a lot of music. What kind of formats are suported? What are some popular music players?

Only free formats are supported out-of-the-box.  However, proprietary formats can be used if the appropriate codecs are installed.  This is very easy to do (in many cases the player searches for and installs them for you).  You may want to install the ubuntu-restricted-extras package that takes care of most things like this.
Rhythmbox is the music player installed by default.  It is quite feature-rich and I find it to be very good indeed, much better than anything I've come across for Windows.  Many people will probably recommend you Amarok.  There are quite a few others too - just install them and have a play around!

---

### Post by Casket on 2007-11-23
Thanks for the help so far!

Another question, is since all my files are already on my computer, and I am going to be dual booting, do I have to copy the files all over again, or will one location suffice for both OSes?

---

### Post by Danikar on 2007-11-23
> **Casket said:**
> I bought a computer back in September, that sadly came with Vista installed. After getting annoyed enough at Vista I decided to switch back to XP. After a while though I am getting bored with it and have decided to install Ubuntu as a dual boot.

Just a couple of questions though. 

1. Drivers, normal Linux drivers will work with Ubuntu? The main drivers I am looking for is nVidia, Realtek, AMD64. Any of these have specific problems?

2. Programs like AIM, MSN, mIRC? Do they have Linux counterparts? Or something I can use instead?

3. Games, I play WoW, COD4, and random others. Will I have a problem installing them? Do I need special instals for them?

4. Music, I have a lot, a lot, a lot of music. What kind of formats are suported? What are some popular music players?

Thanks in advance for all your help!


-Casket

For Drivers the main one you have to worry about is Nvidia.  And u can use Envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") to install those.

Pidgn is a good instant messenger program, works with IRC also, though there are many alternatives for IRC avaliable.

There are ways to play games on ubuntu, wine and cedega for example, but honestly if gaming is a huge deal to you, I would just stick to windows.  If you are dual booting you should be fine though.

There are tons of open source music players, so you will have no problem finding somthing you like.

> **Casket said:**
> Thanks for the help so far!

Another question, is since all my files are already on my computer, and I am going to be dual booting, do I have to copy the files all over again, or will one location suffice for both OSes?

I think Ubuntu now comes with NTFS-3G which will allow you to read your Linux partition, however if you plan on running windows applications through wine or cedega I would suggest installing a copy on your Linux Partition because they run better that way.

---

### Post by Casket on 2007-11-23
Yeah, I was talking more about like my Music/Videos/Pictures.

---

### Post by Danikar on 2007-11-23
Yeah videos/pictures you can leave on your NTFS partition.

Just install NTFS-3G if it isn't installed already, and mount your NTFS partition.

---

### Post by Casket on 2007-11-23
Sweet. Thanks for all the help. Just gotta wait for the DL to finish.

---

### Post by Casket on 2007-11-23
So,the live CD finished up DLing, I burned the image to a disc, and VOILA. I am on the live cd right now posting to you! Woot.

So, now I want to install. I opened up the install guide and got ready to go! Up to step three everything was all good to go. Then came the part where I had to choose which partition to use. In the guide, it said that I could make another partition but when I went to actually do it, all I could do was erase my entire HD and start from scratch.

Any ideas on how I can actually make a partition with out formatting the drive?

---

### Post by GavinZac on 2007-11-23
> **Casket said:**
> So,the live CD finished up DLing, I burned the image to a disc, and VOILA. I am on the live cd right now posting to you! Woot.

So, now I want to install. I opened up the install guide and got ready to go! Up to step three everything was all good to go. Then came the part where I had to choose which partition to use. In the guide, it said that I could make another partition but when I went to actually do it, all I could do was erase my entire HD and start from scratch.

Any ideas on how I can actually make a partition with out formatting the drive?
you need to shrink the windows partition. are you using vista or xp?

---

### Post by Casket on 2007-11-23
Im using XP.

---

### Post by Casket on 2007-11-23
Anyone else able to lend a hand?

---

### Post by GavinZac on 2007-11-23
> **Casket said:**
> Anyone else able to lend a hand?

i havent done this with XP im afraid. research shrinking an XP partition. that will give you the free space you need to create an ext3 partition

---

### Post by Casket on 2007-11-23
After I learn how to shrink, what can I do to actually make the partition?

---

### Post by GavinZac on 2007-11-23
> **Casket said:**
> After I learn how to shrink, what can I do to actually make the partition?

once you have free space, attempting to install ubuntu will now give you the option of using the largest available free space, rather than just wiping the disk :)

---

### Post by Casket on 2007-11-23
Okay. I need to leave for awhile but, when I get back i will defintly check that out.

Thanks for all your help!

---

