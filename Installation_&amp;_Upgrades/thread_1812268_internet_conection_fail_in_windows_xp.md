---
title: "internet conection fail in windows xp"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by ciradu on 2011-07-26
After I've installed Ubuntu 11.04 in dual boot, I miss my Internet connection in Windows XP. I've reinstalled windows XP, but without success in this problem. 
Can this problem be solved somehow?
Thanks

---

### Post by tommpogg on 2011-07-26
Ubuntu shouldn't conflict with Windows xp in any way.
Is your PC a laptop? Are you using a wireless connection? Many laptops have a switch/button to activate wireless.

---

### Post by ciradu on 2011-07-26
No, it is a desktop. And the connection is wired. 
I read somewere else that it might be a problem with mbr, which can be fixed with the recovery console in windows. But not on a dual boot system.

---

### Post by tommpogg on 2011-07-26
I had a similar problem and I solved it by reinstalling my network driver.
You can download your driver form your PC producer home page by using Ubuntu.

---

### Post by ciradu on 2011-07-26
I did this, but still not work. I have the driver that came with my motherboard.
Thanks, anyway

---

### Post by Mark Phelps on 2011-07-28
It's generally NOT an MBR problem -- but I've run into a similar situation where the onboard network controller was configured in one OS, and retained that configuration when booted into the other OS.

Basically, 11.04 would NOT connect to the Internet, and when I rebooted into Win7, it would not, either.

I was able to solve the problem temporarily because the network software (RealTek) also came with a diagnostic app -- which allowed me to RESET the network, in Win7.

Eventually, the motherboard vendor came up with a driver update that fixed this.

If you can get the same kind of software from your motherboard vendor, you may be able to fix this.

---

### Post by ciradu on 2011-07-28
Thank you.
I have the same software for the network: RealTek. I didnt search the second application that came with it, but today, instantly, I could connect to the internet in Windows (XP). I didn't try yet in Ubuntu.

PS. It works on Ubuntu too. 
The problem was solved by stopping and deconecting and unplugging the system. Then must boot windows first, from the grub. If enter first in Ubuntu and then, using restart switch to windows, it wont work.

So, I consider the problem solved

---

