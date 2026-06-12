---
title: "Ubuntu on 32GB SDHC SLC"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by nocturnal1 on 2010-09-22
I have a small laptop that came pre-loaded with Windows 7. It's an HP dm3-1030US.
I would like to run Ubuntu 10.04 on it. It's a small laptop with a 13.3" screen and no CD/DVD so there's no room for a second HDD and I don't want to dual boot  "Too many issues" and I don't have the Windows disk in case anything gets messed up.
I have run Ubuntu from a Supertalent 16GB SLC thumb drive but ran out of room after a few updates. Does anyone have experience using a 32GB SDHC SLC for Ubuntu ?
I'am looking at this one:
[http://www.amazon.com/OEM-Memory-Secure-Digital-Capacity/dp/B001PED7HS](http://www.amazon.com/OEM-Memory-Secure-Digital-Capacity/dp/B001PED7HS)

Thanks

---

### Post by libssd on 2010-09-22
Unless you are storing a lot of user data on the SDHC card or USB flash drive, I'm surprised that you ran out of room with 16gb. I'm generally able to keep an 8gb SDHC card at ~50% of capacity. After using Ubuntu for over a year, I only have about 5.5 gb on my 32 gb SSD:

```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             30278424   5407480  23332860  19% /
```

Periodically run Ubuntu Tweak's Package Cleaner to remove old package caches and kernels -- it's amazing how much space it can recover. If you have more than three kernels, you may want to consider removing old kernel packages.

Assuming your laptop has a 2.5" SATA drive that is easy to get to, you might also consider a 32gb SSD, which has a real controller, and will perform way faster than a memory card at about the same cost. 

For example:  [http://www.amazon.com/OCZ-Technology-2-5-Inch-Solid-OCZSSD2-1ONX32/dp/B003BPBUQO/ref=sr_1_4?s=STORE&ie=UTF8&qid=1285200902&sr=1-4](http://www.amazon.com/OCZ-Technology-2-5-Inch-Solid-OCZSSD2-1ONX32/dp/B003BPBUQO/ref=sr_1_4?s=STORE&ie=UTF8&qid=1285200902&sr=1-4)

I ran some benchmarks recently using Disk Utility:

[LIST]
[*]**32gb OCZ Vertex SSD:** read-only throughput 140mb/sec; access time 0.25 millisecond.
[*]**8gb Transcend class 6 SDHC:**  read-only throughput 15mb/sec; access time 1.1 millisecond.
[/LIST]
You can pick up an external 2.5" SATA enclosure with USB interface for around $10.

---

### Post by nocturnal1 on 2010-09-22
That SSD drive you mentioned isn't SLC it's MLC and from everything I've read MLC's aren't recommend for OS drives. 
Perhaps I did have multiple kernels. I was just learning Ubuntu when I ran out of room.
I got rid of all games, Openoffice ect. I just had GTK+ and Glade3.
I'am not familiar with "Ubuntu Tweak's Package Cleaner" but I've found the site now.

---

### Post by libssd on 2010-09-22
True, but I suspect that even an MLC SSD is still going to be far faster than an SLC memory card, if it has a decent controller -- which the card does not. If the virtual cylinders are aligned to the erase block size (typically 512kb), I don't think MLC/SLC matters much, and the Ubuntu 10.04 installer aligns automatically during the formatting stage.

Good article here: [http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux](http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux)

With the Vertex SSD, I'm seeing boot times ~20 seconds; shutdown ~4 seconds; open most applications ~2 seconds. This is on an Acer netbook with a puny Atom N270 running at 1.6gHz clock speed, and a SATA I bus.

---

### Post by libssd on 2010-09-22
> **nocturnal1 said:**
> Perhaps I did have multiple kernels. I was just learning Ubuntu when I ran out of room.
I got rid of all games, Openoffice ect. I just had GTK+ and Glade3.
Then I really don't understand why you ran out of room. I have installed the full Ubuntu 10.04 32 bit desktop, with all updates applied, and the full set of applications, including OO3.2, help files, additional utilities, plus about 500 images, and a bunch of text and PDF files (including several books), and I'm using only about 5.2gb of space. On a a 16gb device, you should have *at least* 10gb free. Is it possible that you have installed Ubuntu more than once? This isn't hard to do if you don't use the manual partitioning option during installation.

---

### Post by nocturnal1 on 2010-10-17
Ok I did a fresh install to my USB stick so I don't have multiple copies of Ubuntbu but after trying to install Eclipse I'am getting the message that the system is running low on space. Gparted shows the thumb drive on /dev/sde1 with 14.93GiB and 13.25GiB unused. How do I correct this to use all the space?

---

### Post by libssd on 2010-10-19
> **nocturnal1 said:**
> Ok I did a fresh install to my USB stick so I don't have multiple copies of Ubuntbu but after trying to install Eclipse I'am getting the message that the system is running low on space. Gparted shows the thumb drive on /dev/sde1 with 14.93GiB and 13.25GiB unused. How do I correct this to use all the space?
That's only a little over 50% used, so I don't understand why you would be getting a low on space warning.

How did you install Eclipse? From the Eclipse downloads web page, it appears that none of the modules is bigger than 250 mb, which is certainly not huge. As an experiment, I just installed the base Eclipse package through the Ubuntu Software Center; it took forever, but here are before/after disk space figures.

**Before**:
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              29G  5.8G   22G  21% /
```

**After**:
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              29G  6.1G   22G  23% /
```

---

### Post by nocturnal1 on 2011-01-17
Well the Supertalent 16GB SLC thumb drive was** _JUNK_ DO NOT BUY!** (STP16GSLRD)
This was the most poorly made flash drive. The base material for the actual connections was made of plastic _**NOT**_ ceramic like most brands and the body was metal but so thin it felt like it would crush just holding it. It broke after about 2 months.
Now running Ubuntu from my Seagate Goflex 500GB external USB 2.0 HDD. But I have to use both cables comming from the cradle. Needless to say it's not very portable. I'm now looking for a 16 - 32GB SLC thumb drive replacement. Any recommendations?.

I've also been thinking about replacing my laptop with something with a larger 15.6" screen a faster core i3 CPU and a USB 3.0 slot.

Is the AData S102 SLC or MLC ?

---

### Post by nocturnal1 on 2011-01-18
Well I just got an email back from ADATA, their S102 is MLC. 
Anyone know of a 16 - 32GB with SLC?

---

### Post by libssd on 2011-01-18
> **nocturnal1 said:**
> Well I just got an email back from ADATA, their S102 is MLC. 
Anyone know of a 16 - 32GB with SLC?
You are wasting your time with worrying about MLC vs SLC. Even an MLC will likely outlive the rest of the hardware it's in. Last week, Micro Center had the OCZ Vertex 32gb SSD on sale for $49.95.

---

