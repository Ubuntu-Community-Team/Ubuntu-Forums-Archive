---
title: "Can't boot into windows 7 after installing Ubuntu 11.04"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by sixpix on 2011-06-22
i just installed Ubuntu 11.04 and i was enjoying it, but when i wanted to boot into windows 7 my computer just restarts by itself. I really don't know much about Ubuntu so please help.

---

### Post by blackbird34 on 2011-06-22
I had that. I think sudo update-grub does the trick, see [COLOR=Blue][this wiki page (click here)]("https://help.ubuntu.com/community/Grub2")[/COLOR]
:popcorn:

---

### Post by sixpix on 2011-06-22
I already tried that and it still doesn't work.:(

---

### Post by jramshu on 2011-06-22
Hold the shift key while booting to get the grub menu, see if windows is showing up. If it is then you will have to put a delay in grub so you can select which OS to boot to.

EDIT: If not run this in terminal to see if 7 is being recognized

```
sudo os-prober
```

You'll get an output similar to this:
```
jimmy@jimmy-HP:~$ sudo os-prober
[sudo] password for jimmy: 
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda2:Windows Vista (loader):Windows1:chain

```

---

### Post by sixpix on 2011-06-22
Windows is shown in the GRUB menu but still when i select it and try to boot the pc just restarts itself.

---

### Post by sanderd17 on 2011-06-22
That sounds like a corrupt windows installation. When shrinking your partition, there is probably one file corrupted that windows needs to boot.

You will have to backup all your data and run the windows repair disk.

---

### Post by sixpix on 2011-06-22
And how can i backup my windows files from Ubuntu?

---

### Post by sanderd17 on 2011-06-22
you can just access the windows drives via the ubuntu file manager.

---

### Post by Marcelo Ruiz on 2011-06-22
You could apply the repair disk without making the backup (if you don't have very important data), it is quite safe actually. Windows places some files at a specific location in the hard drive, and if you shrink/move the partition and you affect the location of those files you have the problem. The files are actually there, so the repair disk just corrects the information about the new location.
You might need to re install grub after that.
Note we are talking about the windows 7 repair disk. Be careful not to use the image you created to restore the hard drive to its original state. If you don't have the repair disk (that was my case: my notebook didn't come with it), you can google and get a torrent to download the ISO file for the distribution you have (32 or 64 bits) and burn the CD. 
In case you install ubuntu in a dual boot computer again, I would suggest you to first prepare the partitions as you would like them to be, then boot windows 7 to see if it work. If it doesn't, use the repair CD to fix it (it takes literally 2 seconds). Then install ubuntu.
I hope this helps.

---

