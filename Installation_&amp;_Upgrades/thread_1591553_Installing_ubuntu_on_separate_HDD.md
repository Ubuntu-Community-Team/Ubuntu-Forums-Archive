---
title: "Installing ubuntu on separate HDD"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by ivanlj on 2010-10-09
Hello everyone! 

Tomorrow will be my first installation of Ubuntu and Linux in general, decided to finally give it a shot, and join the ranks :)  Hence, I've got one question to begin with (probably about two million later on, but all in due time :)  ).

I have now one HDD, which is my primary, with Windows on it. I was thinking about installing Ubuntu on a second HDD which I will put in tomorrow. Both of them are SATA. Now, I was wondering this:

Is it smarter to just unplug the HDD with Windows on while I play with the other HDD and put Ubuntu on it, and if I do that, is there a way to, after everything is done, at some point, have poth plugged in and be asked which system I actualy want to boot up? Or, do I keep them both plugged in, just insert Ubuntu installation, and set it up? Or will I be forever condemned to play in bios with boot priorities? Or..... something other. 

I hope this wasn't too confusing and that my question got through. In any case, thank you, and hope to be on the forums much in the future :)

---

### Post by sikander3786 on 2010-10-09
Hi and Welcome to the forums. :popcorn:

> Tomorrow will be my first installation of Ubuntu and Linux in general, decided to finally give it a shot, and join the ranks

Good Luck!

> Is it smarter to just unplug the HDD with Windows on while I play with the other HDD and put Ubuntu on it, and if I do that, is there a way to, after everything is done, at some point, have poth plugged in and be asked which system I actualy want to boot up?

If you unplug the HDD with Windows, and install Ubuntu on your second HDD, you'll need to switch First Boot Device from Bios Menu every time you need to boot the other OS.

You can install Ubuntu with just one HDD plugged in and then later on add the Windows HDD and just run

```
sudo update-grub
```

It will pick up your Windows and show it in the Grub menu every time you boot. Make sure your Ubuntu HDD is the first boot device in Bios.

However the recommended method, in my opinion is to leave both the HDD's plugged in and then at step 8 of the Installer, just before you click Install, click Advanced and select the HDD you want to install the boot loader to. You can install it to either of them. You can also leave it upto the installer. It'll do better as it will install Grub to your Ubuntu HDD.

I have to leave in a hurry. Wait for some other replies if I made some mistakes. I'll join you later.


**[COLOR="Red"]EDIT:[/COLOR]** While installing Maverick Meerkat RC a few days back, I noticed there was no 'Advanced' button in the installer, hence no choice to choose the target of bootloader. It is present in Lucid and all previous releases. Can somebody tell how it works in Meerkat?

---

### Post by ivanlj on 2010-10-09
> **sikander3786 said:**
> 
However the recommended method, in my opinion is to leave both the HDD's plugged in and then at step 8 of the Installer, just before you click Install, click Advanced and select the HDD you want to install the boot loader to. You can install it to either of them. You can also leave it upto the installer. It'll do better as it will install Grub to your Ubuntu HDD.

I have to leave in a hurry. Wait for some other replies if I made some mistakes. I'll join you later.


**[COLOR="Red"]EDIT:[/COLOR]** While installing Maverick Meerkat RC a few days back, I noticed there was no 'Advanced' button in the installer, hence no choice to choose the target of bootloader. It is present in Lucid and all previous releases. Can somebody tell how it works in Meerkat?


Thank you for the prompt answer. But tell me just one more thing: If I put the boot loader to the Ubuntu HDD, does that mean I have to set that one as primary in BIOS?

Also, I read here in a few places, and a few friends told me that I will have to make a partition for the swap file. How much shoul I set it to? If it's any use, I have 4Gb of ram.

---

### Post by drs305 on 2010-10-09
If you install Ubuntu on the second hard drive, you should put Grub on that drive as well (if you have an option). Then you want to tell the BIOS to boot your Ubuntu partition first.

Once Ubuntu is installed, when you update the bootloader (GRUB 2) with "sudo update-grub" it will find your Windows OS and add it to the Grub menu and you will be all set.

Now, if it's convenient and you are the nervous type, you can also unplug your Windows drive first and install Ubuntu. That way there isn't a chance you will overwrite Windows, and the Windows bootloader won't be overwritten. Grub will definitely be installed on your Ubuntu parition, and once Ubuntu is running (you may still have to instruct the BIOS to boot the Ubuntu drive first) you can add your Windows drive and tell Grub to go find it and add it to the menu.

As far as swap goes, 2GB is about the largest I'd make it. Opinions vary, but that's more or less in the ballpark of the consensus I think.

Welcome to Ubuntu!

---

### Post by oldfred on 2010-10-09
I installed the RC of Maverick, but I used the advanced install as I have the partitions already set up. The first time I missed it (or was it the beta?) but the advance button now seemed to be a full width combo box that let you choose where to install grub. Not sure if it is there on the other install choices.

---

### Post by ivanlj on 2010-10-10
Thank you for all the answers. Since apparently I'll have to "update"Grub anyhow after the Ubuntu is installed, I reckon I'll go for the "nervous twitchy" option, and unplug the Windows HDD for starters :P

One more quick quick question, sort of off-topic from the subject.... and yes, I know that the answer is far from simple, but....  x64 or x86 version? I do have x64 version of windows installed and working without troubles for the stuff I need it, so I was going for the same with Ubuntu. Any tips on that one?

---

### Post by sikander3786 on 2010-10-10
> x64 or x86 version?

Well, different opinions on this topic. You can run both 32-bit or 64-bit OS on 64-bit machine but you can't run 64-bit OS on 32-bit machine.

I have been running 32-bit on 64-bit machines without any problems. Many people say that you get some troubles that way (drivers sometimes etc), but I didn't. Also, what you hear so often on these forums, flash problems on 64-bit, honestly, I never got that problem a single time.

So, it is upto you, whatever you decide. If your machine is 64-bit capable, I'll recommend you to install x64. It won't boost up the system that much, but surely it will be a bit faster.

As far as RAM > 3GB is concerned, 64-bit will support it natively, while under 32-bit, you'll need to install the PAE-Kernel. So RAM size is not an issue anymore.

Now, you've got the choice. In my opinion, go for the 64-bit.

Good Luck!

Happy Ubuntu-ing!

---

