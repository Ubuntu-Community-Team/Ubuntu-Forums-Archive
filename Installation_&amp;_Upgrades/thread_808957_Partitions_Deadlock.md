---
title: "Partitions Deadlock"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by suby-luby on 2008-05-27
Hi All,

I have a dual boot system: Vista/Ubuntu. I am trying to decrease the size of my Vista and increase the size of my Ubuntu, here is the current partitions listing (in order):

Vista Recovery: 6 G
Vista: 100 G
Swap: 4 G
Ubnuntu /: 40G

I resized my vista using GParted Live CD and now I have Vista at 60 G, which left me with 40 G of free space. I want to add this to my Ubuntu. However, because I have a total of four partitions, I am not able to create a partition. I now that there is something called Extended (logical) partition, but for that, it seems I have to delete one of the four current partitions, which I would like to avoid.

Any help is really appreciated.

Thank you all

---

### Post by dstew on 2008-05-27
Yes, you will have to delete one of your current partitions in order to create an extended partition. The easiest thing would be to delete the swap partition, and create a large extended partition. The re-create your swap partition as a logical partition inside the extended partition. You will probably have to re-configure your swap usage in Ubuntu after you do this, using mkswap and swapon commands.

But, can't you just increase the size of your current Ubuntu root partition? Isn't that what you wanted to do? You might need to move your swap partition farther toward the front of the drive to make room for your Ubuntu partition to expand.

---

### Post by suby-luby on 2008-05-27
> **dstew said:**
> Yes, you will have to delete one of your current partitions in order to create an extended partition. The easiest thing would be to delete the swap partition, and create a large extended partition. The re-create your swap partition as a logical partition inside the extended partition. You will probably have to re-configure your swap usage in Ubuntu after you do this, using mkswap and swapon commands.

But, can't you just increase the size of your current Ubuntu root partition? Isn't that what you wanted to do? You might need to move your swap partition farther toward the front of the drive to make room for your Ubuntu partition to expand.

Thank you for your help DStew. I deleted my swap, increased the size of my / and created a swap again, here is the new listing:
1. Vista Recovery: 6G
2. Vista: 60G
3. Swap: 4G
4. /: 80G.

I created the swap using the GParted live CD but is my Ubuntu aware of it, how do I check that? I do not think swapon/off or mkswap are the answer as I did create a swap, I just want to make my Ubuntu aware of it (if its not).

Again, thank you so much

---

### Post by dstew on 2008-05-27
If the swap partition name changes, Ubuntu will not be aware of it. You can see if Ubuntu is using swap by ```
cat /proc/meminfo
```It should show swap usage at the top.

If swap is not being used, you can set it up easily. First, do```
sudo fdisk -l
```to see what the name of your swap partition is. Then, do```
sudo mkswap /dev/sda3
```or whatever the name of your swap partition is. Then, turn swapping on with```
sudo swapon /dev/sda3
```Now check /proc/meminfo again to see if swap is working. If so, edit the file /etc/fstab to make the swap partition start at boot time. If you already have a swap line in there, just change it to the correct new swap partition name. If there isn't a swap line, add one. An fstab swap line should look like this:```
/dev/sda3       none swap sw 0 0
```Again, substitute the correct swap device name for /dev/sda3 if yours is different.

---

