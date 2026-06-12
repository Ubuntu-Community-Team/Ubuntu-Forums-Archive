---
title: "boot isue after installing ubuntu on multi boot system"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by jitster71 on 2011-08-04
Hi all I am new to Linux and thought i would give it a go finally. 
My System - Asrock ion 330HT - with 2 x 500 Gb internal and 1 external 320Gb on Esata. I have a multi boot system with the first HDD partitioned as: 1-WinXP, 2-Win7, 3-Win7, 4-empty 44Gb, 5-partition for Linux 10Gb. I have used EasyBCD to bring back the Win Xp boot option. 

After Installing Ubuntu 11.04 from cd i was unable to see a boot option. I used EasyBCD to insert a boot option for ubuntu but it does not load and I get a grub prompt. Not sure how to proceed from here. Also which file system would be the best to use for ubuntu?

---

### Post by oldfred on 2011-08-04
Welcome to the forums.

I do not use EasyBCD and like grub2 as  a boot loader. But there are a few that use Win7 and seem to like EasyBCD.

To see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Windows moves its boot files to the active partition (boot flag) for every additional install. Do not plan on deleting the first windows without resolving which boot files belong in which partition. 
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

