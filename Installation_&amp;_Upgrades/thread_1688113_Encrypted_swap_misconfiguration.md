---
title: "Encrypted swap misconfiguration"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by jaykubun on 2011-02-15
Hello fellow (k)ubuntu users!

I am not sure if I choose the right forum for my question, but here is rthe problem: I configured an encrypted swap during the installation process of my kubuntu maverick using the manual install CD. I do not use LVM. This worked fine but I made the mistake of assigning a password to the encrypted swap. I would like to change this in favor for a random key. I tried to change /etc/crypttab in the following way:

old /etc/crypttab looked like this: 
```

sda7_crypt UUID=23df4831-fb6d-4183-8d28-dd46664bcfbe none luks,swap
```

new:
```

sda7_crypt UUID=23df4831-fb6d-4183-8d28-dd46664bcfbe /dev/urandom swap
```

Now the system still asks for a password for sda7_crypt at startup, but does not even recognize the old password. This is not a big issue, but it is annoying. When the system is up I can do swapoff and swapon without problems and no password is needed. 

Question: What do i have to change in order to have random encrypted swap already during boot time?

Thanks all!

---

### Post by wojox on 2011-02-15
What does this tell us:

```
cat /proc/swaps
```

---

### Post by jaykubun on 2011-02-15
Ok - I will post the results of "cat /proc/swaps" this afternoon (Eurpean time) when I am at my PC again.

---

### Post by jaykubun on 2011-02-15
Hello again!

So here it is directly after boot:

```
cat /proc/swaps
 Filename                                Type            Size    Used    Priority
 /dev/dm-1                               partition       5890044 0       -1
```

then I do "sudo swapoff -a" and get

```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
```

and finally after "sudo swapon -a"

```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       5890044 0       -1
```

I am still getting asked for a pw at boot time.

---

### Post by jaykubun on 2011-02-16
Nobody knows how I can change to random keys at boot time?

---

### Post by jaykubun on 2011-02-22
Solved the problem by typing this into my shell:

```
sudo dpkg-reconfigure linux-image-2.6.35-25-generic
```

now it works

---

