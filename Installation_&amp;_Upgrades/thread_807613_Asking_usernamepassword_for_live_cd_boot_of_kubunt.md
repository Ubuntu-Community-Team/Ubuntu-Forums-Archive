---
title: "Asking username/password for live cd boot of kubuntu 8.04"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by venkatat on 2008-05-26
Hi,

I have downloaded Kubuntu 8.04 ( KDE 4.04 remix version of type 64 bit) and burned the image to disk. When i boot from live cd or selecting option 'test kubuntu ...without changing the your system)  option , the system is booting up and asking for username/password.

As i didn't install it yet, why it is asking for username ? is there any default username/password ? I checked the md5checksum it is different and when i checked the cd for errors from Kubuntu boot menu, it has reported 1 file damaged .But it hasn't reported what is the file damaged. For download again it will take 1 days for me because of slow internet connection.

Please help me about username issue first if u can..thanks in advance....

---

### Post by amingv on 2008-05-26
Maybe try username=kubuntu, password=[nothing].
I think it's around that, though burning a new cd might be the best fix.

---

### Post by zvacet on 2008-05-26
> For download again it will take 1 days for me because of slow internet connection.

If you still have iso on your HDD download same iso with torrent and point download to the folder where your iso is.Torrent will just check your iso for corrupted files and replace them with good ones.After that do md5sum again and burn iso on lower possible speed.Check disc integrity and if that goes well go for install.

---

### Post by venkatat on 2008-05-26
Thanks Guys for response...

I have downloaded the iso by direct download by using download manager Multiget. I still have index file for the download. Is there any way to get corrupted file only like bit torrent..

---

### Post by Shardok on 2008-07-14
It seems I am having the same issue. However, this is with a CD that I ordered from shipit... Any ideas what I could try? I've tryed admin, kubuntu, no user... none of them worked with any of the passes I thought of (admin, kubuntu, no pass)

I currently have a working version of Ubuntu on my main computer and have never had any issues, but couldn't find a spare CD of it to install on another computer I needed to hook up for testing...

---

### Post by florb75 on 2008-07-24
> **amingv said:**
> Maybe try username=kubuntu, password=[nothing].
I think it's around that, though burning a new cd might be the best fix.

I just had this problem too, i reconfigured my display rez and had to log out and restart X, and then i couldn't log in again.

I finally figured out that the username is "ubuntu" and the password is blank... that worked for me.

---

### Post by pwhitted on 2008-10-13
I had similar experience. I used the same Ubuntu Desktop Edition 8.0.4 CD that I used to build my laptop in a WinXP laptop, and was able to get Ubuntu to launch from the live CD. Tried my XP Pro desktop, same thing. No prompt for username/password, straight into Ubuntu. I tried a couple PCs of my friend - one Dell, one HP - and both of them prompted for username/password. I tried "root" with no password, root/root, "ubuntu" with no password, and ubuntu/ubuntu, and none of those worked. I tried booting multiple times, and had the same experience each time.

---

