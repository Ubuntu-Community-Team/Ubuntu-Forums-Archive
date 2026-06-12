---
title: "Ubuntu 9.10 updated Linux. Can't boot now."
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by DanInKtown on 2009-12-08
I used wubi to install Ubuntu dual booted with Windows XP. I've been successfully using Ubuntu 9.10 (and earlier).   

Ubuntu suggested that I update to linux-image-2.6.31-16-generic (from ~-15). 

I allowed the update. Then I attempted to reboot. 

Now when I select Ubuntu from the initial dual-boot screen, instead of the multiple choices of kernels (including Ubuntu 9.10, kernel 2.6.31-15-generic), I get a screen that says: 

[B][I]GNU GRUB version 1.97~beta4 

[ Minimal Bash-like line editing is supported. For first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ] 

sh:grub>[/I] [/B]

When I hit TAB I get: 

[B][I]Possible commands are: 

[ badram boot cat chainloader configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod parser.rescue parser.sh reader.normal reader.rescue reboot rnmod root save_env search set sleep source terminal_input.console terminal_output.console test unset[/I] [/B]

What should I do now?

---

### Post by darkod on 2009-12-08
Read post number #10 here how to solve it:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

Be careful in the XP instructions there is typing error in the third command, instead of 26.31 should be 2.6.31.
Depending on which partition you installed wubi, you might need to change /dev/sda1 to /dev/sda2, /dev/sda3 etc. First, second, third partition on the drive.

---

### Post by connectkevin on 2010-01-16
> **DanInKtown said:**
> I used wubi to install Ubuntu dual booted with Windows XP. I've been successfully using Ubuntu 9.10 (and earlier).   

Ubuntu suggested that I update to linux-image-2.6.31-16-generic (from ~-15). 

I allowed the update. Then I attempted to reboot. 

Now when I select Ubuntu from the initial dual-boot screen, instead of the multiple choices of kernels (including Ubuntu 9.10, kernel 2.6.31-15-generic), I get a screen that says: 

[B][I]GNU GRUB version 1.97~beta4 

[ Minimal Bash-like line editing is supported. For first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ] 

sh:grub>[/I] [/B]

When I hit TAB I get: 

[B][I]Possible commands are: 

[ badram boot cat chainloader configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod parser.rescue parser.sh reader.normal reader.rescue reboot rnmod root save_env search set sleep source terminal_input.console terminal_output.console test unset[/I] [/B]

What should I do now?
Hi Friend, just few minutes back i have updated the karmic, and i have come across the same problem, my computer got dual booting, i have installed ubuntu inside vista. Good news is that my problem got fixed, its very simple and easy thing which can be fixed in seconds. 
Download the file from the link given to your windows desktop, [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) 
replace it with the old file in your C: (drive)(as i have installed my windowsVista on C: drive), and reboot the computer and select your linux version and keep rocking, it works perfect like before.:popcorn:

---

### Post by balente84 on 2010-01-19
THis really works!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Thank you thank you thank you!!!

---

### Post by connectkevin on 2010-01-27
> **balente84 said:**
> THis really works!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Thank you thank you thank you!!!

You are welcome, One more bucket of Popcorn for you:popcorn:

---

### Post by Leppie on 2010-01-27
> **balente84 said:**
> THis really works!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Thank you thank you thank you!!!
which option worked for you?

---

### Post by darkod on 2010-01-27
> **Leppie said:**
> which option worked for you?

Replacing wubildr with a new version coz the original has a bug. Link here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Very interesting helping in cases like this, they say "I have dual boot" and go figure out that wubi was installed and not full ubuntu. Not my definition of dual boot. :)

---

### Post by Leppie on 2010-01-27
> **darkod said:**
> Replacing wubildr with a new version coz the original has a bug. Link here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Very interesting helping in cases like this, they say "I have dual boot" and go figure out that wubi was installed and not full ubuntu. Not my definition of dual boot. :)
i know, that's why i was asking... i personally try to stay out of wubi business, also because it gives the user the power to mess up ubuntu from within windows... not such a good idea...

users seem to get lazier all the time, but at the same time they're getting more demanding on the help provided. are we supposed to be psychics or something? and then leaving clear instructions for others, too much to ask for?

---

### Post by billcecil on 2010-02-05
> **connectkevin said:**
> Hi Friend, just few minutes back i have updated the karmic, and i have come across the same problem, my computer got dual booting, i have installed ubuntu inside vista. Good news is that my problem got fixed, its very simple and easy thing which can be fixed in seconds. 
Download the file from the link given to your windows desktop, [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) 
replace it with the old file in your C: (drive)(as i have installed my windowsVista on C: drive), and reboot the computer and select your linux version and keep rocking, it works perfect like before.:popcorn:

I tried this and it didn't work. ubuntu 9.10 is unstable at best on my machine. I've reinstalled it 3 times in 2 weeks. What is going on?

---

### Post by billcecil on 2010-03-04
Thanks Connectkevin, the patch worked. I was getting tired of reinstalling ubuntu every week.

---

