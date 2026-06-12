---
title: "Ubuntu Hp Laptop booting problem CD stalls blank screen"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by Natealt on 2010-03-09
I wanted to post and explain what happened to me. My laptop is a HP Pavilion DV4-2170us.
I tried to install the Ubuntu Cd on my laptop and when I restarted my computer it did not read the Ubuntu cd. And just loaded up windows again like the CD wasn't there. So I inserted the cd when the computer was on and there was an option to download this little program that will help your computer boot off the live cd. That program made a little screen where i could select either windows or Ubuntu when restarting the computer. When I selected ubuntu the computer would start reading the CD then just stall with a blank screen. I figured out that the program would not work on my computer. I had to manually go into the Bios and select the computer to boot off CD in 1st choice.

To do this on my HP DV4 I had to press F10 on the first screen when booting up. Then it brought me to the Bios screen. Then I went to Boot options, scrolled down to Boot order.. pressed enter. Then scrolled down to "boot from cd/dvd drive" and pressed F6 to move it to position #1 in the boot order. Once I did this it booted off the CD just fine. But the 9.10 Karmic version will not boot on my laptop, I had to get the 9.04 version. I'm using the 64 bit version. There is somthing wrong with the 9.10 karmic live CD and hopefully they will fix it shortly.

It took me a very long time to figure this out, the moral of this problem is that your computer may freek out on you if you choose to download that program off the live cd to help your comp boot off the CD its best to just go into your bios and do it that way. It's not that hard to change the bios either.

---

