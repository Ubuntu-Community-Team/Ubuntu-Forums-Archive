---
title: "Imaging using clonezilla, stuck at GRUB"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by sdwinder on 2010-09-15
Hi everyone. I am trying to image a bunch of machines with a xubuntu image that I used clonezilla to make. The imaging works fine, but when I attempt to reboot the new system, it will not boot up the xubuntu image, instead it just gets to the GRUB prompt and stays there, I am not sure how to fix this, or if posssibly a picked an incorrect option on clonezilla. For anyone wondering, I did use advanced more in clonezilla, but I left all the default options as is. 

The file system is ext4 (xubuntu 9.10) so clonezilla was my best option at the time. 


Also on a side note, is there any way for clonezilla to clone a drive to a simple NAS thats sitting on the network? (no server or any ftp running on it, we simply access it by entering the ip address in windows explorer.

On a side note, I used LS under grub and got a few different things

I got (hd0) (hd0,5) and hd(0,1) i tried root(XXX) on all of them, the first two i got "unknown file system" and the last one i got file system is ext2. Not sure what to do next.



Some backstory. I originally used fsarchiver to take an image of a xubuntu 9.10 machine and used it to image a bunch of other computers. The problem with this is that it only images whats on the filesystem, If i take a blank hard drive, format it to ext4 and attempt to install the image on it, it wont work. So I needed something that will image a hard drive without already having xubuntu installed on it. I chose clonezilla because its the only good one i could find that could support ext 4. The image MUST be of used space only, I cannot make a raw image of the entire drive, I have nowhere to store it. So, I figured imaging would be simple, unfortunately I have gone through hell to find a single program that will actually do it. Clonezilla is as close as I have managed to get.

---

