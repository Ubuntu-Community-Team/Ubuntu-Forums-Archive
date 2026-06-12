---
title: "Installing Ubuntu Correctly"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Alyis on 2010-05-23
I want to properly install Unbuntu on my multi boot pc. I would like to install to E partition which is currently ntfs. I have never installed Linux.
What drive should the boot loader go?
I can format E partition during install? 
Does it still need a swap file partition? If so, can that be made from E partition? How big?
I'd like to have a boot menu to choose Ubuntu or a choice that takes me to the windows boot loader. Would that boot loader get wiped if I did a fresh install of 7 to the I drive?
Also, what would be the proper way to upgrade Ubuntu? I see a lot of post where people are doing it wrong.
 
Here is my drives layout. Should install Ubuntu to my SSD J drive instead?
I tried the live CD. Seems to work well. I have a Asus Max Formula MB, Phenom II 6core, ATI 4870. MB has a built in Via sound card. Not sure if that was working.
Thx for any help!
[IMG]http://i908.photobucket.com/albums/ac282/alyis/2010-05-23_223609.jpg[/IMG]

---

### Post by darkod on 2010-05-24
If you can put it on the SSD, it would work really fast on it. At least that's what people have reported.

You can also install in place of E:.

Either way, I recommend using manual partitioning for total control. You can delete a partition using manual partitioning, and create root + swap partitions. Depending on your RAM size, swap is used sometimes, sometimes not.

Usually 2GB is enough for swap, unless you plan to hibernate regularly. In that case make it 1.5 x RAM. The rest of the space can go to root.

If you install in place of E: you will have to make the partitions logical. If you install on the SSD you can create 3rd and 4th primary partition but it's probably better to make them logical too, so you can still create one more primary later if needed.

PS. For multi disk systems it's important to check where grub2 will go. In the last screen in the installer, hit the Advanced button and make sure grub2 goes on the MBR of the same disk where ubuntu is installed, like /dev/sda, /dev/sdb, /dev/sdc, etc. It shouldn't contain a number.

---

