---
title: "New to Ubuntu and Linux - Trouble with installation due to Intel RST"
date: 2020-11-10
forum: Installation &amp; Upgrades
---

### Post by germaninhungary on 2020-11-10
Hi, as the title says, I am completely new to both Ubuntu and Linux as a whole. I decided to try out using Ubuntu on my HP laptop. However, I am not able to install it due to RST. If I understand correctly, I should go to BIOS > Advanced Settings and the switch SATA operation mode from RST to AHCI.

But the real problem is this: HP doesn't allow access to Advanced Settings in BIOS on it's consumer-grade laptops. 

What should I do?





Side Note: I also tried installing Pop_OS! on the same laptop and it worked without any problems.

---

### Post by TheFu on 2020-11-10
Keep using Pop?

If you have at least 4G of RAM and a Core2 Duo CPU or faster, use Virtualbox under some other OS to gain that beginner knowledge of Linux. There must be 1000 how-to examples on youtube and in blogs with the settings.

If you check these forums, seems that HP hardware always needs some extra help to work. If it isn't the BIOS then it is their EFI implementation.  Always something.

---

### Post by germaninhungary on 2020-11-10
> use Virtualbox under some other OS to gain that beginner knowledge of Linux.

I don't really need the laptop rn, I don't travel much these days because of covid, so I can just use my desktop. So I figured I would put the laptop to some use.

> Keep using Pop? 

I can live with that. But I wonder why it had no issues during instalation when Ubuntu had. It is based on Ubuntu after all, right?

Well at least I know not to buy HP hardware.

---

### Post by tea for one on 2020-11-10
> **germaninhungary said:**
> But the real problem is this: HP doesn't allow access to Advanced Settings in BIOS on it's consumer-grade laptops. 

What should I do?

That sounds unusual and contradicts EU acceptable practice for consumer devices.

Is this an enterprise machine, where certain facilities have been removed and/or secured?

---

### Post by germaninhungary on 2020-11-10
No, I bought it myself to use for schoolwork, but thanks to covid I can just use my desktop for that. 

Multiple threads on HP support forums are saying the same thing: [https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Accessing-advanced-BIOS-setup/m-p/7498769/highlight/true#M179267](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Accessing-advanced-BIOS-setup/m-p/7498769/highlight/true#M179267)

---

### Post by tea for one on 2020-11-10
Perhaps try HP Support or their User Forums.

Some UEFI/BIOS iterations require a Supervisor/Administrator Password to access Advanced Settings.

I would be surprised if you couldn't find a solution.

---

### Post by germaninhungary on 2020-11-10
That's where I found out about it.

[https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Access-BIOS-UEFI-Advanced-Settings-Tab/m-p/7596788/highlight/true#M183858](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Access-BIOS-UEFI-Advanced-Settings-Tab/m-p/7596788/highlight/true#M183858)
[https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Accessing-advanced-BIOS-setup/m-p/7498769/highlight/true#M179267](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Accessing-advanced-BIOS-setup/m-p/7498769/highlight/true#M179267)
[https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/How-do-I-get-to-the-advanced-settings-in-the-BIOS/m-p/6848574/highlight/true#M149919](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/How-do-I-get-to-the-advanced-settings-in-the-BIOS/m-p/6848574/highlight/true#M149919)

---

### Post by TheFu on 2020-11-10
dumb question - did you already search for "ubuntu install hp {insert model}"?
I'm sure you have. Often the settings needed for any model wll be listed. by someone who fought the battle already.

We would have done that search but you didn't say which model.

---

### Post by germaninhungary on 2020-11-10
It's HP14-cf1000nc and I didn't find anything the first time I googled it, but now I found a similiar thread about a different model, which made me suspect switchable graphics are the problem.

[https://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/install-linux-on-my-hp-laptop/m-p/7645347/highlight/true#M591791](https://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/install-linux-on-my-hp-laptop/m-p/7645347/highlight/true#M591791)

It would make sense, as the post mentions PopOs solving the problem by default and PopOs works flawlessly on the laptop.

---

### Post by SeijiSensei on 2020-11-10
I have an older HP laptop with switchable graphics. I disabled the Intel chip in the BIOS so the machine always uses the AMD device.

---

### Post by germaninhungary on 2020-11-10
> I disabled the Intel chip in the BIOS so the machine always uses the AMD device.

Honestly, PopOS works great for me so far, so I think will just keep on using it. Still, I would love to know how to do this. Trying to find an answer on HP support forum is a pain in the *ss, since they **really** don't want you to change **anything**.

---

### Post by oldfred on 2020-11-10
Do you have the latest UEFI from HP.
These said with an Omen that UEFI update then worked, where before it did not.

 HP OMEN 15-dh0 UEFI update
[https://ubuntuforums.org/showthread.php?t=2448563](https://ubuntuforums.org/showthread.php?t=2448563)
HP OMEN 15-ce0xx
[https://ubuntuforums.org/showthread.php?t=2407145](https://ubuntuforums.org/showthread.php?t=2407145) & 
[http://martinsosic.com/linux/2015/03/01/arch-linux-on-hp-omen.html](http://martinsosic.com/linux/2015/03/01/arch-linux-on-hp-omen.html) &
[https://jeanbruenn.info/2018/04/01/omen-hp-with-linux/](https://jeanbruenn.info/2018/04/01/omen-hp-with-linux/)
HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work

---

### Post by germaninhungary on 2020-11-11
Ah, but the thing is I don't even get error messages like those people. Installation simply stops when it detects Intel RST, which I have no way to change in BIOS settings, and doesn't let me countinue. 

But I will try to follow the instructions in the thread you linked later today.

---

### Post by germaninhungary on 2020-11-12
After several days of searching on the internet, the answer I got from everywhere is that it is simply impossible to access the Advanced tab in consumer grade HP laptops without modifying the BIOS (and I don't want to risk ruining my laptop with that).

I will mark this as solved, since using PopOS technically solves my problem. Thanks to everybody who tried to help me.

---

### Post by slickymaster on 2020-11-12
*Thread moved to **Installation & Upgrades**.*

---

