---
title: "migrating from old to new machine"
date: 2020-01-14
forum: Installation &amp; Upgrades
---

### Post by oldsoundguy on 2020-01-14
Well, comes a time when upgrading is the only answer, but I am at a loss as to how to do it!
I picked up a new box with lots of disk space, lots of memory, and a 4 core processor (64 bit)
The old box is just that, OLD .. 
New box is 64 bit and SATA only ... where the old box was 32 bit and had both IDE & Sata, but the drive is IDE I want to move 32 bit Ubuntu 16.04 to the new machine and then update to 18.04. (64 bit)

I really could uses a step by step....... do I need to try using a stick (i have a couple of 16gb units)? ... 
Or, can I just run a cable?...
Or, can I use my home network?...

Will I need special software?

Not been under the hood in Linux for a LONG time, so, please be kind and treat me like a newbie (lol)

AND THANKS!!

---

### Post by CelticWarrior on 2020-01-14
You can't upgrade from 32 to 64-bit. You need a new installation.

Simply backup your personal files from the old to an external media or cloud service and then transfer to the new after installing the OS.

---

### Post by oldsoundguy on 2020-01-14
THANK YOU!!   Nice and quick!  (not sure as to what are the "personal files".  Guess I will get the 18.4 now and get that part done.)

---

### Post by SeijiSensei on 2020-01-14
Anything under /home should constitute "personal" files.

If you want to have the same software on the next machine as the old, you can use the command
```

cd ~
sudo dpkg --get-selections > package.list

```
That will create a file called "package.list" in your home directory.  After installing a new Ubuntu version on the new machine, you can use this file to recreate your installation:
```
sudo dpkg  --set-selections < package.list
```

Put the file on a USB thumbdrive or equivalent so you can use it on the new machine.

---

### Post by mörgæs on 2020-01-14
With new gear 18.04 is not always a good option. Hardware support is better in 19.10.

You might be lucky that 18.04 works but the safe bet is 19.10.

---

### Post by oldsoundguy on 2020-01-14
Thanks for the hardware tips as well ...  I am an oldefart and retired over 25 years ago.  So, I do spend a lot of time on my computers. I have the new(er) box up and running and updated with 18.04 and later this week will set up the stick and see how that goes.  

Again, thanks people.

---

