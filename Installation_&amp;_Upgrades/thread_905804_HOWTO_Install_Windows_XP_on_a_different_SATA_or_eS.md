---
title: "HOWTO: Install Windows XP on a different SATA or eSATA drive"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by Emblem Parade on 2008-08-30
Sometimes we Ubuntu users would like to have Windows XP handy, if only to play some cutting-edge games that don't, for now, work on WINE.

One way to add Windows is to partition your hard drive. But, with prices dropping on hard drives, and the availability of eSATA ports on laptops, having Windows on an entirely separate, dedicated hard drive can be a better alternative. It keeps your Ubuntu and Windows installations clean and separate. For laptops, eSATA means that your external drive is just as fast as (with the potential to be even faster than) your internal drive.

I wrote this HOWTO for my recently purchased Pangolin Performance laptop from [system76]("http://system76.com/"), but it can be easily adapted to other laptops, or even desktops.

First, to avoid the chicken-and-egg problem, make sure you have all your Windows drivers ready and accessible, especially your networking (LAN or WiFi) drivers. Once you have Windows connected to the internet, you would be able to download all the rest of your drivers. An easy way is to put them on a USB key drive, or burn them on a CD.

For my Pangolin, I got my Windows drivers [here]("http://knowledge76.com/index.php/Panp4"). Getting Windows drivers for mobile video adapters can actually be pretty difficult! (Those who claim that Ubuntu is harder to install than Windows don't know what they're talking about.) For my NVIDIA video, I used the "enhanced" drivers at [LaptopVideo2Go]("http://www.laptopvideo2go.com/"). Also, the high-definition audio drivers from [Realtek]("http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3") worked for me.

Next, if you're installing Windows XP, make sure your installation CD is of at least Service Pack 2. Otherwise, the installer will not recognize SATA drives! One way around this is to have SATA drivers handy and make the Windows XP installer use them. Another way around is to ["slipstream"]("http://www.winsupersite.com/showcase/windowsxp_sp2_slipstream.asp") the service pack into your installation CD.

Before booting the installer, you should get into your computer's BIOS configuration and change the boot order, making sure that your Windows hard drive is before your Ubuntu hard drive. The reason is that the Windows installer insists on installing the MBR (boot loader) on the first hard drive, and you definitely don't want to soil your Ubuntu installation with it. There's no reason to: Ubuntu's GRUB loader can boot a Windows MBR even if it's on another drive. We'll get into that later.

Once you do that, boot into the Windows installation CD and try your best to enjoy the process. Just make sure you don't do any changes to the partitions of your Ubuntu hard drive!

Once Windows is installed, go back to your BIOS configuration and change back to having your Ubuntu drive come before your Windows drive. Boot into Ubuntu.

We will now configure GRUB so it can boot Windows.

Edit your GRUB configuration file:

```
sudo gedit /boot/grub/menu.lst
```

And add something like this at the bottom of the file:

```
title		Windows XP
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
makeactive
chainloader	+1
```

The "root" definition may vary per your machine. The first digit is the number of the Windows hard disk -- it should follow the boot order as configured in your BIOS. So, hd0 should be your Ubuntu drive. The digit after the comma as it the partition number. If you just installed Windows as one partition on the entire drive, it should be 0.

The two "map" definitions are important. The tell GRUB to swap the BIOS order of the drives before booting, so hd1 effectively becomes hd0 and vice versa. This allows the Windows boot loader to believe that it is in the first drive, as it requires.

That's it! Rebooting should allow you to select your operating system in GRUB, and your Ubuntu drive is absolutely devoid of Windows.

---

### Post by vgrisham on 2010-03-17
Thanks for this how-to. I realize this thread is pretty old, but it's new to me. 

I have a Pangolin (PanP4N) and I'm trying to set up what you've described in this how-to. My question is, I don't see the esata drive listed as a boot option in the bios. Where did you adjust it's boot priority over the internal drive?  Is it the same as an external usb drive in the bios?

---

