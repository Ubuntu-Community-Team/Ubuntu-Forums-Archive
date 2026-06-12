---
title: "Partitioning"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by almayfie on 2012-04-22
I am currently running Windows 7 and would like to install Ubuntu as a second operating system. 

I get a bit confused by all the partitions and not really sure what I need.

I would like to use enough of my disk to run Ubuntu smoothly, but not more than I need.

I read so many different things about the swap partition. My initial thought is that 12GB of RAM, I wouldn't need to have 2 times my RAM for a swap partition.

Any help on the number of partitions and their sizes would be greatly appreciated.

My system is as follows:

CPU -  Intel Core i7 930  2.8Ghz
Ram- 12 GB
HDD - 2TB
OS- Windows 7 64 bit

---

### Post by strask on 2012-04-22
Overall, the amount of disk space you need is going to be whatever space your data (documents, music, pictures, etc.) takes up plus a bit for the OS... I think the installer requests that you have a minimum of around 5gb. I've seen people say that they have only 15gb or even less and get by without troubles, but personally I want to leave room for lots of additional software and expect the OS to get bigger with upgrades and stuff, so I made my / partition 50gb plus enough space for my data.

As for swap, with 12gb of ram you will rarely touch it so it doesn't much matter. The only important consideration that I am aware of is that if you plan to use the hibernate feature, you need a swap partition at least as big as your physical ram, plus a buffer in case something was already in swap when you activated hibernate. So in your case maybe 14-18gb. But if you don't plan to use hibernate, you can get away with a small or nonexistent swap partition (you can always add swap later as a file in the file system, but that's no good for hibernate).

So my advice... 20-50gb for the OS, 14gb for swap partition if using hibernate, plus room for your data.

---

### Post by darkod on 2012-04-22
Just to add to the above, if you don't need to use a ton of large programs in ubuntu, and if you don't plan to keep large files (videos, photos, etc) inside it, you can have / as small as 15GB and it will work fine. Ubuntu programs take a lot less space than in windows, so 15GB fits a lot.

For swap you can use 2GB for example, only if you don't hibernate as said above. For hibernate it needs to be at least as big as the RAM.

---

### Post by oldfred on 2012-04-22
I also suggest another partition formated NTFS for shared data. You can easily read from the Windows NTFS system partition but should not write into it normally. Windows often does not like to much going on in its system that it has not controlled. A shared partition then can be read/write from both systems.

I also suggest a smaller swap and if storing most of your data in data or shared paritions, not in the Ubuntu system partition, then the system partition does not have to be large.

Are you booting with BIOS or newer UEFI and gpt partitioning? Most new i7 systems may have UEFI mode as one way to boot, although most Windows 7  systems seem to be configured with the older BIOS/MBR configuration. All new UEFI system seem to have a BIOS boot mode.

Maybe best to post this from Ubuntu liveCD or USB flash terminal to see current partition layout.

sudo parted /dev/sda unit s print

---

