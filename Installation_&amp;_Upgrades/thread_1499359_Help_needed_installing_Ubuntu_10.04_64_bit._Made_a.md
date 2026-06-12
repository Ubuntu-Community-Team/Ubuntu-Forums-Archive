---
title: "Help needed installing Ubuntu 10.04 64 bit. Made a mess trying already!"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by adamsiddhi on 2010-06-01
Hi,

I have written about my experience installing Ubuntu 10.04 over here
[[COLOR="Indigo"]**http://superuser.com/questions/147854/problem-installing-ubuntu-10-04-64-bit-side-by-side-with-vista-by-using-a-bootabl**[/COLOR]]("http://superuser.com/questions/147854/problem-installing-ubuntu-10-04-64-bit-side-by-side-with-vista-by-using-a-bootabl")

If you have read it all you can see that I have truly made a mess of things. What I need to know now is how to find out how to delete the 2 bad Ubuntu partitions I made to my hard drive. Also I need to know how to SAFELY install Ubuntu 10.04 64 bit. 

I hope you can help as I am in a dire state.

Thanks,
Adam

---

### Post by jetgraphics on 2010-06-01
What chipset is in your machine?

I had a major problem with installing 10.04 on my machine.
Problem: after install, and reboot, screen goes black. Monitors show "no  signal" warning.

CPU: Phenom 9600
MB: ASROCK A780GMH/128M (AMD 780G chipset)
RAM: 4 GB DDR2-800
Video Adapter: ATI (AMD) Radeon HD 2600 XT

---

### Post by adamsiddhi on 2010-06-01
CPU: Intel Core 2 Duo T6400
RAM: 4gig SDRAM
Video: Intel GMA 4500MHD Dynamic Video 
MB: 320 GB - Serial ATA-150 

Hope that helps. Not sure how hardware really effects installs. I will post my updates here. 

I popped into IRC channel #ubuntu and got some help. 2 users suggested that I use 'gparted' software to delete my 2 bad ubuntu partitions and to reinstall Ubuntu 10.04 with out choosing to import my account settings from Vista. Like I said in my Super User post, the installer stalled at 83% trying to import my Vista account settings.

---

### Post by roubman on 2010-06-01
tried bootit?

---

### Post by adamsiddhi on 2010-06-02
> **roubman said:**
> tried bootit?
From what I know Bootit NG is free for 30 days. I dont want to go down the pay route if I have not yet tried gparted.

---

### Post by BergmanW on 2010-06-03
L.S.

here is what I have successfully done to de a ne (freh) install of Ubuntu 10.4 on a dual boot system (W7 and Ubuntu)

1. Start Windows (in your case Vista)
2. go to system -> configuration manager -> system manager -> Disk management

remove (**not format**)  the Ubuntu partitions (probably 2) so that it will become **1 unused space.**

3. Restart the system end boot from the USB drive

4. When you get the selection where to put Ubuntu, select "the largest unused space"

check if it selected the correct drive and partition.

5. Then let it continue to download and install. 

In my case, it did recognize that there was Windows on it en created a correct boot sector.

Though I used a dutch version and W7

---

### Post by darkod on 2010-06-03
> **BergmanW said:**
> L.S.

here is what I have successfully done to de a ne (freh) install of Ubuntu 10.4 on a dual boot system (W7 and Ubuntu)

1. Start Windows (in your case Vista)
2. go to system -> configuration manager -> system manager -> Disk management

remove (**not format**)  the Ubuntu partitions (probably 2) so that it will become **1 unused space.**

3. Restart the system end boot from the USB drive

4. When you get the selection where to put Ubuntu, select "the largest unused space"

check if it selected the correct drive and partition.

5. Then let it continue to download and install. 

In my case, it did recognize that there was Windows on it en created a correct boot sector.

Though I used a dutch version and W7

+1

If you already have "bad" ubuntu that you just want to replace, this is the best way. Just delete the partitions, leave the space as unallocated, and use Use Largest Available Free space in the installer. Job done.

---

### Post by adamsiddhi on 2010-06-03
Today I was searching for a way to fix that bad Ubuntu install I had. I eventually was able to delete it to create a chunk of unallocated space. Then I extended my C partition and took up all that unallocated space. So I am basically where I started. I will see how it goes. 

Thanks for the replies.

---

