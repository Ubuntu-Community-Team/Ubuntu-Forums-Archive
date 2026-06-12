---
title: "How do I Dual Boot XP with Linux Mint?"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by hayz on 2008-07-26
Hello there,

Let me head straight to the issue:

I just installed Linux Mint on my HP Dv5215us Laptop (AMD)and I will like to Proceed further to Install both Windows OS on the 50GB+ Partition I have left.

k, I av a 100GB HDD. . There is a 48GB partition i made for my DATA (like you know i am not touching that)

Now, i installed Linux Mint on the Remaining 50GB+ (By selecting Continuous Largest Space during Installation)

So now i will like to install Windows on the same partition i installed Linux mint, it's not that i don't know how to do the partitioning nd install the Windows. .  Its just dat I think i mite get thing screwed bcos of my present DATA partition. .

I will like Good & Seasoned members of this Forum to put me thru.

Thanks. .

*As time goes i will post Here likely problems i encounter on the Linux Mint distro.

Thanks.

---

### Post by pmlxuser on 2008-07-26
Use something like Gparted to creat a partition on the current partition; Use a live cd so that the current parttion should not be mounted.
After creating aprtition for your windows OS (NTFS), proced to install windows. Howevr windows is very selfish it will write it self in the boot partition not allowing other OS to be seen. Hence after installing Win XP you will need to Reinstall is it Grub or what ever Boot manager you are using...

---

### Post by hayz on 2008-07-26
> **pmlxuser said:**
> Use something like Gparted to creat a partition on the current partition; Use a live cd so that the current parttion should not be mounted.
After creating partition for your windows OS (NTFS), proced to install windows. Howevr windows is very selfish it will write it self in the boot partition not allowing other OS to be seen. Hence after installing Win XP you will need to Reinstall is it Grub or what ever Boot manager you are using...

k, i will use d Linux Mint Live CD i av to Create a partiton for the WindowsXp i want to install.

:Good:

> **pmlxuser said:**
> 
Howevr windows is very selfish it will write it self in the boot partition not allowing other OS to be seen.

That is one of my concerns, . . nd i dnt want that to occur. . I want the default Linux mint BootManager that appears @ start up to remain there.


> **pmlxuser said:**
> Hence after installing Win XP you will need to Reinstall is it Grub or what ever Boot manager you are using...

I don't understand you suggestion @ this point, pls come out clearer.
How do i do a Grub re-install so dat Windows don't take over the Whole thing?

I don't use any Boot Manager, Am sure the OS's can handle that

---

### Post by stevoo on 2008-07-26
you will create a partition that you want for it to be on the 48gb.
Lets say 20gb for windows.
That 20gb will be dedicated for windows.


The OS can act in two ways. Either by erasing the boot start and writing it own and not displaying the Linux one just the windows, which you will have to edit later on. 
OR it will simply add its self on.

Simply if the boot manager changes, youll have to change it your self. 
It is up to windows now, depending on what it will do.

---

### Post by hayz on 2008-07-26
So, you guys want a Outcome after am done installing Windows on a Created Partition?

You want to know if Windows will take over the Booting and not show a Linux Option or Linux will still Retain its BootManager. .

However the case mayb, Hope u will put me thru the boot editing then!

Thanks.

---

### Post by hayz on 2008-07-26
On a 2nd thought, i won't be able to do a Windows install on that Partition bcos i knw for Sure Windows will Override the Linux nd it won't show @ Start-up!

k, Lets say i read alot of Tutorials online about Re-installing the Linux Grub after a Widows on Linux Dual Boot. . But i must confess I am sceared on all the Codes am seeing* bcos several times i type in the Terminal exactly wat i see in tutorials but the Pc always come up with one thing Or the other that i barely understand :arrgh:

Is it Me or The Whole Linux thing?!

Pls, see below a sap of my Partition Table, mayb some1 can take me frm there . .

Thanks.

---

### Post by SuperSonic4 on 2008-07-26
I found this site which will hopefully work for you:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

It appears you need only steps 4 and 5 though.

---

### Post by hayz on 2008-07-26
> **SuperSonic4 said:**
> I found this site which will hopefully work for you:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

It appears you need only steps 4 and 5 though.

I have been recommended to that link via a Reply i got on the LinuxMint Forums.

But it got to a stage it didnt Help @ All . .

P.S: Can some1 actually spend some time to put me thru all this One on One?

Will appreciate that Thanks.

---

