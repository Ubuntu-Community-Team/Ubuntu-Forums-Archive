---
title: "misinterpretation or ubuntu installation wizard super cokroach?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by andres.ordonez on 2011-01-06
Hi, thanks for reading, I was trying to install ubuntu-10.10 side by side with a windows-7 partition in my aunt's laptop. I've done it before 3 or 4 times (one of those in the same laptop) without problems so I was kinda (over) confident and did no backup (damn! mistake 1).

This is what I remember:

First I shrank the windows partition leaving ~100GB free. Then I made a bootable usb with "startup disk creator" (in my laptop's ubuntu 10.10) and, as the other times, booted from it (in my aunt's laptop), checked that the wireless worked and proceeded to install from the desktop "install" icon. When asked for how to partition the disk I chose to do it manually (as I've always done) and when I got to the keyboard layout part I tried to change the layout from Spain to USA (I chose Spanish at the beginning of the installation, but the computer was bought in USA), when looking for the USA layout I first changed it to United Kingdom and then when tried to change to USA I couldn't do it, the pointer was "busy" and the forward button was greyed out, everything else worked fine but I could not proceed with the installation even after 10-15mins during which I read here (at ubuntuforums) that it may be due to a disk error. 

There was no way to cancel the installation which was stucked at the keyboard layout part saying "ready when you are" or something like that, so I did "sudo shutdown -h now" and then checked that windows was still there, after that restarted again and did "check the disc for errors" when booting from the usb, no errors, checked the memory too with the same result and finally tried to install again from the window with nice graphics where it says "Try Ubuntu" "Install Ubuntu" or something similar.

This time I decided to choose the English language at the beginning, so I wouldn't have to change the keyboard layout and possibly prevent the previous problem. However, this time I decided to don't make a manual partition and have faith in the installation wizard (damn I'm a freaking science man I DON'T HAVE FAITH, what's wrong with me?!! mistake 2) so I chose "install ubuntu alongside another OS" and then an image of the ~100GB free partition appeared split in half with ubuntu at one side (~50GB) and something else in the other side (~50GB), and a little message below that saying the other partitions where hidden. I figured that since I freed 100GB I should give ubuntu those 100GB and dispose of that which was occupying the other 50GB, so I did, a few minutes later the installation was complete and I restarted the laptop only to find that there was no grub menu at the beginning and that ubuntu was booting, when it finished booting my fears where confirmed when I found nothing in /media and the windows partition was gone, ubuntu fills the entire disk. 


Now, I have two questions:

1. What did I do wrong (besides not doing a backup)? (Something tells me that I misinterpreted the installation wizard)

2. Is there any way to recover the data that was in the windows partition? (I don't have any hope, but given the circumstances I have to ask)

Thanks again.

PS:
If you see anything wrong with my English please let me know

---

