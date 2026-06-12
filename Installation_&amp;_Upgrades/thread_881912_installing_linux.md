---
title: "installing linux"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by mgarcia9921 on 2008-08-06
i just bought a notebook and i bean trying to install ubuntu. i try a live cd and also wubi and not luck .. when i use the cd it takes me to choose the language and then i select to install ubuntu
then the ubuntu logo appears and then after a moment the screen goes dark and then it says that the temperature is about 60 c some times 79 and then it shutdown.. can anyone help me finding the problem.... thanks
well my notebook is hp pavillion tx 2000 (table pc) it has 4gb memory 200gb hd ,64bits, ati graphics ,amd

---

### Post by overdrank on 2008-08-06
> **mgarcia9921 said:**
> i just bought a notebook and i bean trying to install ubuntu. i try a live cd and also wubi and not luck .. when i use the cd it takes me to choose the language and then i select to install ubuntu
then the ubuntu logo appears and then after a moment the screen goes dark and then it says that the temperature is about 60 c some times 79 and then it shutdown.. can anyone help me finding the problem.... thanks

Hi and welcome, could you give us some system specs? Like graphics, memory.

---

### Post by werries on 2008-08-06
is your fan not turning on?
could this be an acpi problem?

---

### Post by mgarcia9921 on 2008-08-06
well my notebook is hp pavillion tx 2000 (table pc) it has 4gb memory 200gb hd ,64bits, ati graphics ,amd

---

### Post by overdrank on 2008-08-07
> **mgarcia9921 said:**
> well my notebook is hp pavillion tx 2000 (table pc) it has 4gb memory 200gb hd ,64bits, ati graphics ,amd

Hi and I have seen some with that model have issue. You may search the forums for solutions but I will give a few to start
have you check the cd for errors. Then you may want to do a checksum on the iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
You may also when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash this will allow you to see any errors.

---

### Post by uxe1 on 2008-09-09
i have th same machine same problem. 
:/ 
any thing in specific i can offer about the hardware?
same problem with both x and k versions as well as fedora and even damnsmall.

---

### Post by technotitclan on 2008-09-09
first: is it actualy a notebook, or is it a desktop pc? those are 2 very different types of computers. second: if it is a desktop then try taking off the side panel and start up the machine and try to install ubuntu. keep an eye on the cpu fan. if it stops at any point ore drasticly slows down that could be your problem. although, you did say it was new. with that being the case i recomend you just take the whole sys back and ask for a complete replacement, not a part replacement, the whole computer. 9 times out of 10 if 1 part in a new sys needs to be replaced then one by one everything is going to need replacing. also, try the cd's on other computers. and can you operate the live cd w/o installing? or does it do the same thing?

---

### Post by uxe1 on 2008-09-09
its a laptop. the install disk works on my other system, and Ive tried quite a few disks by now.(same prob live install, and alternate cd) id totally consider trying to take it in to be serviced, except i got it from staples. so 1 they know next to nothing, and 2 i think they'd say installing new OS voids the warranty. also what would i say to them?

any other ideas, like is there a way to get it to ignore the temp warning while it installs, and am i melting my processor the rest of the time im using it?

---

### Post by technotitclan on 2008-09-09
tell them it cuts out durring "heavy usage" also i belive os has nothing to do with warranty. most warrentys don't cover software. example-most companies will tell you your out of luck if you call them with a virus problem while in warenty because: software isn't covered. also call hp directly, they should have a ship in service

---

### Post by Pumalite on 2008-09-09
This is a link worth reading for you:
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by uxe1 on 2008-09-11
ya none of those are the same.
tried installing in a virtual machine. it just hung as soon as i chose install, maybe a symptom of the same problem?
also left it off for 2 hours (just in case it really was just too hot) same thing, over heating 69degrease shutting dwn.
i dont under stand what im t select after hitting f6 but all those tend to just hang as well.

stupid hp
:mad:

---

### Post by zohaib on 2008-09-11
that problem happened to my friend and he told me that the processor fan was not running that's why i was getting that problem now my computer is OK.,

so that can be a hardware problem.

---

### Post by uxe1 on 2008-09-13
ok so phoned HP, and after an hour and a half of him being loged on to my machine, ha asked "what is this you-bun-tow thing" and i explained that was the linux distro that was telling me that my puter was over heating, so after a few more minets of humming and hawing he responds that this "utorrent is a secrity risk and the heat may be comming from it ACCESSING THE INTERNET WITH OUT ME KNOWING" so he deleated it and said it should runn cooler now.:confused: so i took the computer back and traded it in on another unit. and guess what SAME FREAKING PROBLEM!!!
but at least i got to laugh at the stupid hp guy. 

so to recap, its not a BIOS update, nor fauly hardware.
and i am officaly out of things to try. any new ideas from you guys?

---

### Post by Pumalite on 2008-09-13
You can try your luck with some boot parameters. Use the most common first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
To be tried one at the time or in different combinations.

---

### Post by uxe1 on 2008-10-09
ive just slid in the xubuntu bata of 8.10. and the live disk booted up fine!!! could we maybe call this issue solved?

---

