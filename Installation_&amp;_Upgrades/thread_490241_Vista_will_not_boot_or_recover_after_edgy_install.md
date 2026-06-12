---
title: "Vista will not boot or recover after edgy install"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by Aryxa on 2007-07-02
Hi guys,

I installed edgy 6.10 on the new HP media center, which has vista home premium. I partition the drive and put edgy on it. Ever since installation, I cannot boot into vista, or recover it using the recovery disks. Since the install, Vista appears in the boot menu. Although when it loads I get the green bars.. then nothing.. 20-30 minutes later. Same thing happens with the recovery discs. I even tried to recover using XP discs and it gave me errors.

Is there anyway to get vista back? I have read for the past 3 hours ad I could not find any solution - apart from it must be that grub wiped over the new vista boot loaders. That means nothing to me. 

Has anyone dual booted ubuntu with vista and had this problem and actually got vista back? 

TIA
fae

---

### Post by LaRoza on 2007-07-02
Bad news, you used an old version of Ubuntu, I doubt that Vista will work.

If you have the recovery disks, use them.

(For the recovery disks, boot from the first one if there is more than one.)

If you used the latest Ubuntu, this wouldn't have happened.

---

### Post by Aryxa on 2007-07-02
> **LaRoza said:**
> Bad news, you used an old version of Ubuntu, I doubt that Vista will work.

If you have the recovery disks, use them.

(For the recovery disks, boot from the first one if there is more than one.)

If you used the latest Ubuntu, this wouldn't have happened.

Hi, as I said in my first post. The recovery discs didn't work. 
I don't care what I lose on the computer, I just want linux off and any windows back on.

---

### Post by LaRoza on 2007-07-02
Please answer this questions:

1. How many recovery disks are there, and are they numbered?

2. What error messages to you receive?

3. What is your computer's brand? (HP,Compaq, Dell, etc)

4. Why do you want to get rid of Linux?

Assuming the recovery disks are not damaged they should work.

---

### Post by voided3 on 2007-07-02
Hello, boot into the Ubuntu live CD and use the program GParted to completely erase all partitions on your hard drive, then do a full reinstall of Vista, followed by a clean install of Feisty 7.04. It'll take some time, but you'll end up with a very versatile system if you keep both OSes. Good luck!

---

### Post by Aryxa on 2007-07-02
1: 2 discs, I made them myself inside vista on good quality discs.
2: errors mesages is windows didn't shut down properly and must restart.. it's in a blue screen (this is using the xp recovery discs) the vista discs don't load like vista either.
3: brand is HP Media Center m8095a
4: I want to get rid of linux because I have a 4 day old computer that cannot boot into windows after I installed edgy. (plus the husband is a 100% windows user and I am getting the silent treatment right now LOL)

I didn't think twice about installing it, I do it on my XP computer and wasn't ready to try the latest feisty. I had no idea vista was going poop itself.

So, can I somehow wipe it all and start again? Maybe try installing feisty down the track, differently. 

I just want it back :(

---

### Post by LaRoza on 2007-07-02
> **Aryxa said:**
> 1: 2 discs, I made them myself inside vista on good quality discs.
2: errors mesages is windows didn't shut down properly and must restart.. it's in a blue screen (this is using the xp recovery discs) the vista discs don't load like vista either.
3: brand is HP Media Center m8095a
4: I want to get rid of linux because I have a 4 day old computer that cannot boot into windows after I installed edgy. (plus the husband is a 100% windows user and I am getting the silent treatment right now LOL)

I didn't think twice about installing it, I do it on my XP computer and wasn't ready to try the latest feisty. I had no idea vista was going poop itself.

So, can I somehow wipe it all and start again? Maybe try installing feisty down the track, differently. 

I just want it back :(

1. Vista ruined the recovery disks I made, Vista has extreme trouble burning disk, I ruined many disks with Vista, a lot of people have this problem. (Good quality disks, bad quality OS)  If the disks do work, when you boot from the first one, you will get an HP message. Recovery takes a long time, 1.25 hours for XP, I don't know how long for Vista.

2. Vista's error message is likely wrong

3. Good, I know HP.

4. Is your husband a 100% Vista user? Vista is NOT a good OS, so unless something doesn't work (hardware) in Linux, I suggest you keep it.

If the recovery disks don't work, you will likely have to buy Vista, $150. Great, huh? Tell that to your husband, show him Feisty, maybe show him Beryl. Tell him it is free.

If he needs an explanation, tell him it is a file system change in Vista, specifically, Microsoft changed NTFS5 and it is now incompatible with the partition editor that Ubuntu Edgy used.

---

### Post by Aryxa on 2007-07-02
Bump!

Has anyone else come across this issue? Is there a way to wipe the lot clean to start again? 


>  Hello, boot into the Ubuntu live CD and use the program GParted to completely erase all partitions on your hard drive, then do a full reinstall of Vista, followed by a clean install of Feisty 7.04. It'll take some time, but you'll end up with a very versatile system if you keep both OSes. Good luck

Which live CD would this be? Could you please link me so I can download it. 
Thanks

---

### Post by Alex&amp;Linux on 2007-07-03
Hey
I had an issue like this when I first tried setting up a dual boot.
If youre looking to start fresh, just insert your Vista disk, and clean install using entire disk.
You can use the built in disk partitioning tool in Vista to push back a volume of your NTFS to allow for Ubuntu to "install on largest contigious space"
Simple as that!

Youll have a pretty versatile system after setting this up!

---

### Post by LaRoza on 2007-07-03
> **Aryxa said:**
> Bump!

Has anyone else come across this issue? Is there a way to wipe the lot clean to start again? 




Which live CD would this be? Could you please link me so I can download it. 
Thanks

It is in my sig.

---

### Post by MacMan on 2007-07-05
Ciao,
I haven't tried this solution myself (haven't even tried to install Linux on my Vista laptop yet...:-) ) but I was browsing this forum in search for tips on how to install Feisty on a laptop with Vista and I found this thread:
[http://ubuntuforums.org/showthread.php?t=398122&highlight=install+vista](http://ubuntuforums.org/showthread.php?t=398122&highlight=install+vista)

I wonder if the solution proposed in the post would fix the damage?

I hope this helps.
Ciao.

---

