---
title: "Hp Pavilion dv6 problems"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by PersonInNeed on 2013-02-19
Hello, I have been trying to install Ubuntu on my Hp Pavilion dv6 for a few days now, and now my patience has run out.

 I currently have 2 USB flash drives plugged in, 1 with the install, and one for extra space if needed. I have installed Ubuntu on this machine 4 times now (Uninstall and reinstall), but after it supposedly finishes installing it says "Computer must restart to go to the next install page" or something of that nature. After that I get a black screen and it's been siting like that for 20-30-ish minutes now. 

That scenario happened every single time I installed and it's frustrating the hell out of me. 

If anyone can help me with this it'd be greatly appreciated. 

Thanks,
PersonInNeed

---

### Post by dino99 on 2013-02-20
i suppose HP having installing its own crappy partition (maybe its hidden)
so load a partition tool (like gparted) from a livecd/liveusb, and glance at it.
save what you think that could be usefull, then format that HP partition.

Then ubuntu installation might be easier.
[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

if you still get some issue, maybe you need to use some boot option
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Mark Phelps on 2013-02-20
Are you trying to install Ubuntu dual-boot with Win7 -- so you can use both? Or are you trying the Replace Win7 with Ubuntu?

It makes a big difference.

---

### Post by SeijiSensei on 2013-02-20
Unless you have manually repartitioned this machine, it is impossible to install Ubuntu in a dual-boot arrangement because HP partitions its disks with the maximum four primary partitions all in use.  Worse, they place the large Windows partition third, so it's not easy to free up enough space to install Linux alongside.

There really isn't any way to do this effectively that doesn't include reinstalling Windows.  I posted the steps I took to install Linux on a dv6t [here]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5"), but they might be pretty daunting if you're a Linux novice.  Search these forums for "hp dv6" and you should see some other suggestions as well.  You might start with [this thread](http://ubuntuforums.org/showthread.php?t=2079034).

---

