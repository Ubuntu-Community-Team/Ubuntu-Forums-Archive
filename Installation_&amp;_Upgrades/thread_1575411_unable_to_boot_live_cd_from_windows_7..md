---
title: "unable to boot live cd from windows 7."
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by newbemac on 2010-09-15
Hi to all.
I down loaded a copy for 10.4 two days ago as well as a copy of mint 9
and burned two cd's.
Upon attempting to boot the live cd's (either one), I get the purple screen in 10.4, select the first option to run from the cd and press enter then I get 24 lines for numbers and letters on a blackscreen. 
The last line reads  
[ 0.600467] ]<c0104087>] kernal_thread_kelper+0x7/0x10
the machine freezes.
(toshiba Satellite L-505D) I have attached a photo of the screen.  In MInt 9
I get the save screen.
Thanks.
PS I did a check SUM and mem test on both CD's and did a completly new down load and fresh CD.. still the same.***  windows boots fine  checked the windows directory and Ubuntu is there

up date*****  is down loaded the WUBI installer..... rebooted... same thing happened.
I would like to be able to duel boot.
thanks

---

### Post by andrewthomas on 2010-09-16
Try this thread.  May have to add acpi=off or noacpi to the kernel line at boot.

[http://ubuntuforums.org/showpost.php?p=9391988&postcount=10](http://ubuntuforums.org/showpost.php?p=9391988&postcount=10)

[http://ubuntuforums.org/showthread.php?t=1415525&highlight=acpi](http://ubuntuforums.org/showthread.php?t=1415525&highlight=acpi)

---

### Post by newbemac on 2010-09-19
thanks for the help.  that did the trick. however once the disk installed and rebooted i selected the first option and i still get the screen described it by first post and 10.4 will not load.

---

### Post by newbemac on 2010-09-20
hi again,
day 3.   ubuntu 10.4 is installed on my hd. but i cannot boot to it.  and if i use the disk that will only boot by using f6 and placing an "x" next to acpi=off.
i have found linux located on my hd using terminal, at /dev/sda5    ext 4   89.37 gb
/dev/sda6   linux swap 3.84 gb. it appers grup is not loading.  windows 7 boots fine.
when I type sudo grub in terminal it is not found.   I'm lost and confused.

---

### Post by andrewthomas on 2010-09-23
Next time that you boot, press e then use your right arrow key to move to the end of the linux line and add noacpi then ctrl-x (I think, there are instructions on the bottom of the screen) to boot.

If that works then 
```

gksu gedit /etc/default/grub 
```

and add change  
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noacpi"
```

---

