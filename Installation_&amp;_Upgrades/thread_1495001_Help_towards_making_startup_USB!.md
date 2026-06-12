---
title: "Help towards making startup USB!"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by gagea on 2010-05-27
I am going to make startup usb disk for ubuntu  10.04. So, I want to buy a memory stick. What is the best capacity for this job? I am usually install a lot of programs on my computer.   I have also another question about the 4GB capacity that the computer ask at the beginning of making startup usb. This 4GB bacome full so quickly. What is possible solution for this?  Thanks a lot.

---

### Post by NUboon2Age on 2010-05-27
I did okay with Ubuntu on 4GB pen drive and (Ubuntu-based) Peppermint OS on a 2GB,  but I was only treating them as a kind of occasional-use or emergency use thing. I've heard pen drives have a limited number of read/writes so I would be hesitant to see it as a permanent solution. I hear SD cards have a longer write/read lifespan that pen drives, so that might work better.

---

### Post by kansasnoob on 2010-05-27
> **gagea said:**
> I am going to make startup usb disk for ubuntu  10.04. So, I want to buy a memory stick. What is the best capacity for this job? I am usually install a lot of programs on my computer.   I have also another question about the 4GB capacity that the computer ask at the beginning of making startup usb. This 4GB bacome full so quickly. What is possible solution for this?  Thanks a lot.

Well, 2GB is the most efficient if you plan to use it all as a live environment.

If you use anything larger than that I'd do some partitioning:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Alternate%20partition%20layout](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Alternate%20partition%20layout)

The whole doc:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I'm sad because I can't get Portable Linux to work in Lucid :(

---

### Post by Herman on 2010-05-27
> I am going to make startup usb disk for ubuntu  10.04. So, I want to buy  a memory stick. What is the best capacity for this job? I am usually  install a lot of programs on my computer.   I have also another question  about the 4GB capacity that the computer ask at the beginning of making  startup usb. This 4GB bacome full so quickly. What is possible solution  for this?  Thanks a lot.The best capacity for the job will be the largest you can afford.
They're available in larger capacities than they used to be, and they're also getting more affordable. I saw some 16GB memory sticks on special in a store not long ago and they were a well known brand. I already have two older flash memory sticks from the same manufacturer and I know they will last for a long time and the have acceptable read and write speeds. I have installed and run Ubuntu in them both many times and used them quite a lot, and they're both getting old now and still good, but not the capacity I want. I bought eight new 16GB USB flash memory sticks for $59.95 au each. (Since I don't get the chance to travel to a city very often I decided to make the most of the opportunity).

In my country a case of beer is about $60.00 now, at least out here in the 'outback', (translate as 'woods' if you're Canadian or American), where I live. 
If I spent my $60 on a case of beer it would be gone in a few hours if I had a few friends around.
A 16 GB USB flash memory drive will probably last for years and years with the full (standard) Ubuntu installation in it, so I think that's a better investment. 

It doesn't greatly concern me if the flash memory ever wears out. By the time it wears out, I will have had my money's worth out of it. Most flash memory sticks nowadays have a built in flash memory controller chip which feature various grades of wear leveling so if you have chosen a decent brand it will probably last for many years no matter how hard you use it. Larger capacity flash drives would tend to last disproportionally longer because if you leave more free space in the drive there will be more empty erase blocks available for the wear leveling algorythm to rotate the disk writes to.

I use 'USB Startup Disk Creator', (available from the 'System' menu in all recent versions of Ubuntu) for making 'startup disks' for installing Ubuntu, especially in computers with no optical drive.
That's all 'persistent' type of installs are good for.

Actually, the full Ubuntu installation makes a better boot loader disk than the 'startup disk', because the full Ubuntu installation features GRUB2. That means if there's an unbootable computer I can usually get it going by bootiing my USB Ubuntu, updating grub.cfg, and rebooting. I don't know why they chose the name 'startup disc' for the persistent type of USB installation featuring the Ubuntu installer in it. It's virtually useless as a boot loader disk. 

My advice is to buy the largest USB flash memory stick I can afford,  and install the full Ubuntu installation in it. :)

---

### Post by SuperR00t on 2010-05-27
The smallest flash drive I've been able to get Ubuntu on was 1GB. If you're short on money, 4GB should be fine. But if you want a TON of programs, something bigger couldn't hurt either.

---

