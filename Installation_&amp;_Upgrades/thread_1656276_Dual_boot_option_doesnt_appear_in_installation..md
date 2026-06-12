---
title: "Dual boot option doesnt appear in installation."
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by Myfathersheart on 2010-12-30
I have a MSI a6000 Laptop (that has given me a lot of problems installing Ubuntu.

I finally had to run Ubuntu from a CD in nomodeset

Then when I go to install Ubuntu the only options it gives (regarding my harddrive) are to format my whole hardrive or do the partitioning.  I have seen screenshots though where there is a third option on the same page to install ubuntu alongside a prior OS and dual boot.

Does anyone know why the "install alongside a prior OS (dual boot)" option doesn't show up?

---

### Post by foxmulder881 on 2010-12-30
What operating system is currently installed?

And is this on the same hdd as your current installed operating system?

---

### Post by Myfathersheart on 2010-12-31
I was running windows7 but I accidently changed one of my computers premade partitions to a linux swap partitio.

Now my laptop will not recognize windows 7. It says "no operating system installed" I tried recovery and that didn't work.

---

### Post by Quackers on 2010-12-31
So Ubuntu is booting?
If it is please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by gelos1010 on 2010-12-31
Quakers, I've had better luck with previous versions of Ubuntu.  This is my experience with Ubuntu 10.10.  I've initally installed it within Windows XP SP3, and it worked fine, I was able to browse the web, with out any issues.  
 
Upon restarting the computer, it presented the option to boot into either Ubuntu or Windows.  That may be a better choice for you.
 
Once it had installed operated successfully in a Windows environment, i decided to install it directly on to the HDD.  And installing directly on to the HDD was not successful.  It may be my system, so I'm in the process of building a new system this week and install it directly on to a new HDD.
 
Well gentlemen, this is my first post, any typos, in grammar or expression, may be an enigma of your imagination.

---

### Post by Myfathersheart on 2010-12-31
> **Quackers said:**
> So Ubuntu is booting?
If it is please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)





No ubuntu is not booting from grub or a CD

---

