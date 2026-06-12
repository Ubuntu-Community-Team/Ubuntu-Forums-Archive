---
title: "cant load ubuntu/grub loading error 17"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by mugatea on 2008-02-22
ok, I got a ubuntu DVD a week ago and installed it.  Dead easy to do with no probs except some broken packages.  I did this in a partitioned drive, so I could have xp just incase i didnt like ubuntu or found it limiting.  

Well I was very happy and I installed it on my uncles computer, he loves it and cant understand why everyone doesnt have it.  Installing on his computer was easy and they werent even any broken packages.

I decided to get rid of xp and reinstall Ubuntu on the full harddrive, so thats what I did yesterday.  It installed fine but around 11 packages were broke, but very easy to fix.  I began moving all my songs and docs and stuff over to ubuntu, downloaded apps inc wine and set up itunes to work too.  Itunes goes very slow and crashed, it wouldnt close so I just reset the computer from the power icon and when it restarted I got this message...

[I]Grub loading stage 1.5.

Grub loading, please wait

Error 17[/I]

And then nothing, nothing happened, so i reset it and the same message appeared, Ubuntu failed to load.  I didnt know what to do so I reinstalled Ubunutu again and after it installed and asked me to remove the DVD it restarted and showed the same error message.  Today I reinstalled it again and the same problem.

I'm currently using the DVD live session to get online.

I need your help.

Ps I scanned the disk for errors from  the Ubuntu dvd menu and it is fine.

Jamie

---

### Post by Pumalite on 2008-02-22
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by dstew on 2008-02-22
The error you have means that the partitions have changed since the grub boot loader was installed. To fix it, you have to re-install grub. Boot a Live CD, open a terminal and enter```
grub
```That will get you the grub command line, with the grub> prompt. At the grub prompt, enter```
find /boot/grub/menu.lst
```Whatever answer you get (hopefully you will just get one!) use as the argument for the root command. For example, if it returns (hd0,1) the root command would be```
root (hd0,1)
```Next, setup grub into the MBR of the hard disk and quit```
setup (hd0)
quit
```Close the live CD session and boot. You should get the grub menu now. If you get errors when you choose menu items, then we will have to edit /boot/grub/menu.lst to make the final repairs.

---

