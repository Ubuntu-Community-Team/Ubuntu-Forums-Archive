---
title: "This partition should be marked for use as a &quot;Reserved BIOS boot area&quot;"
date: 2017-01-13
forum: Installation &amp; Upgrades
---

### Post by CodeHead on 2017-01-13
Hello,

I'm getting the "This partition should be marked for use as a "Reserved BIOS boot boot area" and should be at least 1MB in size." error. I was following a video on YouTube that instructed me to make a partition before starting the Ubuntu installation. Should I ignore it & proceed? If not, what should I do?

Thanks!

Codehead

---

### Post by ubfan1 on 2017-01-13
If you're doing a legacy install to a gpt partitioned disk, you will need that small partition with the "grub-bios" flag to hold the main part of the bootloader.  On an MSDOS partitioned disk, that part is tucked in at the beginning, right after the first boot-block, and before the first partition start.  It might also be a good idea for future use in UEFI mode to add another 300M partition for eventual use as an EFI partition.  Much easier to plan a little for the future  than to move partitions around which hold your operating system.

---

### Post by ajgreeny on 2017-01-13
Don't ignore the warning.

Make sure you know what the reason is for the error and I suspect ubfan1 has got it right.

Give us more information and we can help you to sort it out in a much more certain manner. 
Is the disk GPT partitioned?
If you're not sure show us the output of command ```
sudo parted -l
```

---

### Post by CodeHead on 2017-01-14
Ok.

Btw, my PC is running Windows 10.

I think I will just convert this Alienware Aurora R5 into a Linux box. Can I just abort this dual boot installation & reverse what I have done?

Also, in the past, Linux has been accused of destroying graphics cards, etc. Is that still an issue?

---

### Post by oldfred on 2017-01-14
> Also, in the past, Linux has been accused of destroying graphics cards, etc. Is that still an issue? 				

Never heard of this?

Although I have had a video card blow out all its capacitors nVidia 7600GT multiple years ago. But I had to find in a Windows hardware forum that the capacitors were the issue. Still use nVidia though, if I have a separate video card, but newest systems just use the Intel video as I do not game.

---

### Post by CodeHead on 2017-01-14
Ok, thanks!

The clean installation went fine & I'm now free of Windows!

Thanks, everyone!

---

