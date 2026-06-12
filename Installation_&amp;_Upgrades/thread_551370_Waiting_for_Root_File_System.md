---
title: "Waiting for Root File System"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by Uncle Che on 2007-09-15
I am posting this to help others who might in the same situation I found myself in.

**I use Xubuntu 6.06.1**

Today I did an apt-get update on my system for the first time since it was installed. It's never had internet access over than dialup and now that my laptop is dead, I use it full time. So the update went fine but then when it came time to reboot, it stuck on waiting for root file system. 

After a several minute wait, it booted into a debian shell which was of no use whatsoever except to tell me that /dev/sda3 couldn't be found. 

I booted into Windows and found no help here on the forums(that's why I am posting this!) so I decided to roll up my sleeves and start again. 

I booted again into the Xubuntu and let it go all the way to debian shell. I then typed:

```
ls /dev
```

That gave me the hard drives on the system. Guess what? No sdas, just hdas. I wrote down all of the hda numbers, hda1, hd2, etc. 

Next, I turned off the computer and rebooted and at the grub menu I hit e to edit. Then I edited this line: (Highlight then line then hit e to edit it again)
```

kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
```

to
```

kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
```

I figured I might as well go for the most obvious at first. So I hit b for boot.

Lo and behold it booted up no problems.......to my shouts, huh, who's your daddy, who's your daddy?

:guitar:

Once booted in, I opened a terminal and typed:
```

sudo gedit /boot/brub/menu.lst
```

You need to edit the file as above so that it doesn't keep repeating the error every time you boot. 

Now, all is working well. My thought is the update of the kernel had something to do with it, maybe some sort of bug, but it might have just been isolated to me. Anyways, it's fixed and if you run across this problem, you can now fix yourself.

---

