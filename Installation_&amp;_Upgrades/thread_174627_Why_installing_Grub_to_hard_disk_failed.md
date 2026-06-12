---
title: "Why installing Grub to hard disk failed?"
date: 2006-05-12
forum: Installation &amp; Upgrades
---

### Post by MichaelLi on 2006-05-12
Recently, I choose to install DapperDrake beta2 to my computer by using ISO file on my hard disk. Following the instruction on the Internet, I boot my computer and enter the installing process. Everything goes well except that the Grub can not be installed to the hard disk. I have tried several times, but all failed. Now the grub previously installed on the disk has been corrupted, and I can not boot into my system. I just have an CD of Ubuntu 5.10. Can I use this CD to fix the problem without reinstallation? Why installing grub in the last stage of installation failed? 
    Any advice is appreciated.
    Thank you.

---

### Post by louis_nichols on 2006-05-12
I don't know why it failed, but yes, you can install it to disk from the install CD. Instructions [here]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")

---

### Post by MichaelLi on 2006-05-15
[QUOTE=louis_nichols]I don't know why it failed, but yes, you can install it to disk from the install CD. Instructions [here]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")[/QUOTE]

Thanks for the reply. But solution provided by the instruction does not work for me. I just have an ubuntu 5.10 install CD. Now I failed to install the ubuntu 6.04 beta2 from hard disk. The grub is not installed. It failed to write to the disk.  Using the 5.10 install CD and enterring the rescue mode, I can finally get a command prompt. But the command "grub-install" is not found. After all, I am not recovering grub after install Windows. I don't have anything related to grub installed originally. Now, what should I do?

---

### Post by codejunkie on 2006-05-15
[quote=MichaelLi]Thanks for the reply. But solution provided by the instruction does not work for me. I just have an ubuntu 5.10 install CD. Now I failed to install the ubuntu 6.04 beta2 from hard disk. The grub is not installed. It failed to write to the disk.  Using the 5.10 install CD and enterring the rescue mode, I can finally get a command prompt. But the command "grub-install" is not found. After all, I am not recovering grub after install Windows. I don't have the grub installed originally. Now, what should I do?[/quote] type ```
sudo grub
``` in the terminal if grub is installed it will display a screen like this 
```

    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>
```type **quit** to exit the grub screen, if you don't see the grub screen run ```
sudo apt-get install grub
```and then run
```
sudo grub-install /dev/hda
```again

---

### Post by MichaelLi on 2006-05-15
[QUOTE=codejunkie]...
if you don't see the grub screen run ```
sudo apt-get install grub
```and then run
```
sudo grub-install /dev/hda
```again[/QUOTE]

I have tried the command you gave and configured the network properly, but it said:

[b]Package grub is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: package grub has no installation candidate.[/b]

---

### Post by Sef on 2006-05-15
What file system did you use?

---

### Post by mad_jack on 2006-05-17
[QUOTE=MichaelLi]Recently, I choose to install DapperDrake beta2 to my computer by using ISO file on my hard disk. Following the instruction on the Internet, I boot my computer and enter the installing process. Everything goes well except that the Grub can not be installed to the hard disk. I have tried several times, but all failed. Now the grub previously installed on the disk has been corrupted, and I can not boot into my system. I just have an CD of Ubuntu 5.10. Can I use this CD to fix the problem without reinstallation? Why installing grub in the last stage of installation failed? 
    Any advice is appreciated.
    Thank you.[/QUOTE]

I had exactly the same problem on 2 different machines in the last week. I suspect there is a problem with grub-install writing to / (root) partitions over a certain size, as another machine I installed dual boot with WinXP previously installed went fine. The latter had approx. 40Gb / partition; the previous 2 were clean installs on 80Gb and 100Gb drives with just swap set aside and everything else allocated to the root partition. It may be to do with drive geometry, but I haven't had time to look into it.

My simple solution is to create a seperate /boot partition (mine was 1Gb out of a 100Gb drive) - it installs fine then.

Hope this helps.

---

