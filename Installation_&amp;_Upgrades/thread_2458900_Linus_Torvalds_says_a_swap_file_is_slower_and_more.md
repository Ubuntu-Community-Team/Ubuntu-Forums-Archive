---
title: "Linus Torvalds says a swap file is slower and more problematic than a swap partition"
date: 2021-03-06
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2021-03-06
According to [recent news]("https://arstechnica.com/gadgets/2021/03/psa-linux-folks-stay-away-from-the-5-12-rc1-kernel/"), Linus Torvalds warns against using a swap file, saying that you should use swap partition instead.
> And, as far as I know, all the normal distributions set things up with swap partitions, not files, because honestly, swapfiles tend to be slower and have various other complexity issues.
He says that a swap file not only is slower, but also has the potential to cause problems.

Does this mean that Ubuntu's policy of using a swap file instead of a swap partition is a mistake? Would it be a good idea for me to remove my swap file and replace it with a swap partition? Or is it a bit of scaremongering?

---

### Post by mikewhatever on 2021-03-06
It's an opinion expressed from his standpoint. Obviously, there are arguments for and against both.
Here are some answers and opinions:
[https://askubuntu.com/questions/904372/swap-partition-vs-swap-file](https://askubuntu.com/questions/904372/swap-partition-vs-swap-file)
[https://serverfault.com/questions/25653/swap-partition-vs-file-for-performance](https://serverfault.com/questions/25653/swap-partition-vs-file-for-performance)

---

### Post by GhX6GZMB on 2021-03-06
Whether it's faster or not I can't say, but if you need Hibernate (I do, I only use laptops), you'll need to keep the swap partition.

---

### Post by ubfan1 on 2021-03-06
Kernel  5.12 rc1 was recalled because of potential swap-file mismanagement overwriting the root.  ;^(

---

### Post by DuckHook on 2021-03-06
I tend to give Linus' opinions more weight than most.

Even before his comments, I've never trusted swap files. I always have mine on its own separate partition. It's not a matter of performance; I don't like having a swap file mucking about on the same partition as my root. It just doesn't feel right/secure.

---

### Post by kansasnoob on 2021-03-06
I can attest to a swap partition providing "more speed" on low RAM systems that use a SSD. I maintain several Latitude 2110's that max out at 2GB RAM and they're frustratingly slow even with a swap partition on a standard hard drive but with a SSD and a swap partition they're considerably less frustrating. Just to satisfy my own curiosity I tried a fresh install of 20.04 running GNOME Flashback w/metacity letting the installer do it's thing with the SSD, which of course creates a swap file, and I was back to frustratingly slow so I went back to using a separate swap partition and the improvement was very noticeable. I think on anything with 4GB or more of RAM the difference would be negligible.

Please don't rush out and buy one of these old netbooks though! No matter what they're a real kludge and the money is much better spent on a slightly more powerful 12" to 14" laptop of the same vintage!

---

### Post by hk42 on 2021-03-07
A swap partition has the great advantage that it can be shared among several Linux installations.
Even some Live USB dongle or DVD are clever enough to use it.
It is also a good idea to locate it at the end of a Windows C: partition so that when W10 
complains that there is not enough room for updating you destroy it and extend the  C: one.

---

### Post by TheFu on 2021-03-07
I'm firmly in the swap partition/LV group.
Distros haven't used swapfiles very long and there are clearly failure modes that exist.  
Unix has decades of using swap partitions. The solutuion has been well proven.

**New** is the **enemy** of *stable*.  Every generation has to re-re-relearn this fact.

---

### Post by C.S.Cameron on 2021-03-07
> **ml9104 said:**
> Whether it's faster or not I can't say, but if you need Hibernate (I do, I only use laptops), you'll need to keep the swap partition.

Hibernation works with Swapfiles but you need to provide a **resume_offset**. See:
[https://askubuntu.com/questions/1247133/how-to-handle-full-install-usb-and-swap-space/1247151#1247151](https://askubuntu.com/questions/1247133/how-to-handle-full-install-usb-and-swap-space/1247151#1247151)

A Full install USB drive with a swap partition will also try to use the computers swap partition which can confuse things if the computer is in hibernation.

---

### Post by DuckHook on 2021-03-08
> **C.S.Cameron said:**
> …A Full install USB drive with a swap partition will also try to use the computers swap partition which can confuse things if the computer is in hibernation.
Hibernation is a risky function at the best of times. Pros who know what they are doing can usually spot its pitfalls, but so many newbies have been burned that I recommend against it on general principles.

---

### Post by ajgreeny on 2021-03-08
Going back several years here, but in the days when I used hibernation it 5ook almost as long to get back to the working desktop as a cold boot so I quickly gave up hibernating and moved to suspend only.

Admittedly I have a very reliable mains power system here so suspend risks are very unlikely and on a laptop just about negligible.

---

### Post by TheFu on 2021-03-08
I've never used hibernation.

I use standby on laptops that don't leave a building and when physical control cannot be lost.  

My laptops are always encrypted, so for encryption to be useful, the system must be completely powered down.  Not in standby. Not hibernated.  Walking between college buildings is too much risk for standby if you've gone to the effort to encrypt the storage.  The one time you don't completely shutdown is the time when it will be stolen or some accident will happen requiring a detour to the health center and then I'd forget to shutdown the system.  Just not worth it.

---

### Post by GhX6GZMB on 2021-03-08
> **ajgreeny said:**
>  it 5ook almost as long to get back to the working desktop as a cold boot

It actually takes a bit longer that a cold boot.

It's all a question of working environment. I have no big need for security á la TheFu, but often have many programs/documents open and need to reloacte quickly. Slamming the lid closed, moving to the new location, and just restoring from hibernate is the optimum solution for me. Suspend is not really an option, as several hours can go by.

Each has her/his own needs.

---

### Post by TheFu on 2021-03-08
> **ml9104 said:**
> It actually takes a bit longer that a cold boot.

It's all a question of working environment. I have no big need for security á la TheFu, but often have many programs/documents open and need to reloacte quickly. Slamming the lid closed, moving to the new location, and just restoring from hibernate is the optimum solution for me. Suspend is not really an option, as several hours can go by.

Each has her/his own needs.

Suspend barely touches the battery on my laptops.  Basically, everything is shutdown except the RAM and 1 LED on the left side.  My 8th gen Core i5 laptop routinely works disconnected for 10 hrs, so in suspend, it would last ... perhaps 10 days?  I really don't know.    Had a 2015 Core i3 laptop that was similar.  The battery lasted forever.  

Of course, this depends on the workloads, temperature, CPU, and battery age. I'd always thought AMD laptop CPUs weren't as power efficient, but thought that changed about 2-3 yrs ago.

---

### Post by VMC on 2021-03-08
I've never loaded enough programs to warrant either/or, but I've always used swap partition.

---

### Post by GhX6GZMB on 2021-03-08
> **TheFu said:**
> Suspend barely touches the battery on my laptops.  Basically, everything is shutdown except the RAM and 1 LED on the left side.  My 8th gen Core i5 laptop routinely works disconnected for 10 hrs, so in suspend, it would last ... perhaps 10 days?  I really don't know.    Had a 2015 Core i3 laptop that was similar.  The battery lasted forever.  

Of course, this depends on the workloads, temperature, CPU, and battery age. I'd always thought AMD laptop CPUs weren't as power efficient, but thought that changed about 2-3 yrs ago.

Well, we can't all own state-of-the-art machines. My hours sometimes turn into days, so just suspending is not an option.

---

