---
title: "Installation &amp; partitons"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by gman2004 on 2006-02-25
I have two hardrives. On one I have install WinXP Pro.
The other hd (250GB)has been partioned to three (equal), two of the partitions have data and on the third I want to install Ubutu. Don't ask me why, but the first and last partions are the ones with data. 
I did started installing Ubuntu but when it got to partitioning I aborted.
I located the empty partition manualy, I created the free space and I tryed the guided installation. What scares me, is the 175GB of swap file(!) that want's to create. 
Any advice?

---

### Post by shams2 on 2006-02-25
i didn't understand what do you mean, any how select the custom partition, create swap partition double of your ram or as you wish and the rest for /.

---

### Post by gman2004 on 2006-02-25
How do I create the swap partition, Guided method creates a 175 GB swap partition.

---

### Post by Coelocanth on 2006-02-25
How much RAM do you have? Are you sure it's saying 175 *GB* and not 175 *MB*?

---

### Post by drachir on 2006-02-26
When you are installing ubuntu and you get to the partition section you have full control of the size of partition you are creating. When you create a new partition manually it defaults to the size of the hdd you are using. I am using a 80 GB on my laptop. When you select manual configuration select the free space, then select the size you want. Again it will default to the size of your hdd. Backspace the default and use 512 MB or what ever youwant for your swap. Then change the type to SWAP. Whe you create the next partition for the install it will default to the remaining size of free space.Mine was 80GB - 512MB. around about 79.48GB Partition the remaining free space as you choose.

---

### Post by aysiu on 2006-02-26
Take a look at this:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You don't have to follow all the steps, but it has screenshots and walks you through the partition table process.

---

### Post by gman2004 on 2006-02-26
I partition the hd with gparted and after starting installing basic system I got the message "The debootstrap program exited with an error (return value 1)".
Any idea?

---

