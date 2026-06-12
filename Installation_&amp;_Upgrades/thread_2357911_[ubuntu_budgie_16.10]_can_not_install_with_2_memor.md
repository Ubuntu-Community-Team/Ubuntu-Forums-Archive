---
title: "[ubuntu budgie 16.10] can not install with 2 memory cards"
date: 2017-04-07
forum: Installation &amp; Upgrades
---

### Post by barry1984 on 2017-04-07
Hello Everyone! My problem is that my laptop will restart again and again at the beginning of installation process. I can only see the following menu. No matter what item I select, computer only restart and display the menu again.

[COLOR=#ff0000]Default
Help
install ubuntu budgie remix.....
....

[/COLOR]Then I remove one memory car from my laptop. Magically everything is OK. I install the OS successfully. And ubuntu budgie can start successfully as well. But the story is not ended.

I insert the memory card, then similar problem happen.  ubuntu budgie can not start successfully. I can only see the following start menu. If I select item "ubuntu" or "Advanced options for ubuntu", computer only restart and display the menu again. But if I select item "Windows 7...", it can start successfully.

What is the problem?

My laptop is Sumsung R458 with 2 memory card. The capacity of each memory card is 2G.

[COLOR=#ff0000]Ubuntu
Advanced options for ubuntu
Windows 7 (loader) (on /dev/sda1)[/COLOR]

---

### Post by RobGoss on 2017-04-07
Hello and welcome to the forums, Strange issue, does everything work ok in Windows when you run it?

Have you tried switching the memory sticks? not sure why you would have to but it's just a thought

---

### Post by barry1984 on 2017-04-07
Hello!

1) Windows works well.
2) Yes, I have tried to switching the memory sticks, but it can not start neither.

---

### Post by barry1984 on 2017-04-07
Maybe it's the problem of Ubuntu budgie 16.10. So I try to install Ubuntu 16.04.2 on my laptop. But the problem is the same. I can not install Ubuntu on my laptop with 2 memory cards.

---

### Post by davidmohammed on 2017-04-07
I had similar strange issues which I tracked down to a failing memory dimm - eventually tracked it down by running a memtest and it highlighted errors in the ram chips.  Had to replace the chip and all was well.

---

### Post by Impavidus on 2017-04-07
Sounds like broken hardware. In the grub menu (maybe hidden behind advanced options), there may be a memory test. Maybe you can run that.

Windows manages memory in a completely different way than Linux. There may be a range of bad memory addresses that Windows simply never attempts to use.

---

### Post by barry1984 on 2017-04-07
1) I also doubt that it's the problem of memory card. So I make a memtest86+ USB and run it to check if the memory is broken. But memtest86+ says that no error is found.

2) I also replace each of two memory cards with the third memory card which has the capacity 1 GB. It works well in the two cases in which my laptop has 3 GB memory. So I think the two memory cards are not broken.

---

### Post by barry1984 on 2017-04-07
> **Impavidus said:**
> Sounds like broken hardware. In the grub menu (maybe hidden behind advanced options), there may be a memory test. Maybe you can run that.

Windows manages memory in a completely different way than Linux. There may be a range of bad memory addresses that Windows simply never attempts to use.

1) I have tried the advanced options. No memtest item is listed. If I select recovery mode in advanced options, I can see some message in my screen. But after 2 or 3 seconds, my laptop restart.


2) When I try to install Ubuntu budgie 16.10, the item "Memory test" is listed in the menu. If I select memory test,  I can see some message in my screen. But after 2 or 3 seconds, my laptop restart.


3) When I try to install Ubuntu 16.04, the item "Memory test" is also listed in the menu. If I select memory test,  it says memory is OK and then return back to the start menu. In this case my laptop does restart.

---

