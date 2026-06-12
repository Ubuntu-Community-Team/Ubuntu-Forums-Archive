---
title: "partition and install questions"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by Cariboukayak on 2009-11-28
I want to install 8.10 on my hard drive, Compaq Presario C501, 2 G Ram, 120 G HD. I've been playing with it for some time as live USB, and although I'm still confused it seems to work on my system (though modem is still a problem) and I think its time to try an install. The USB is too slow. 

So, I have 15 G of unallocated space already on my computer, and want to do a dual-boot with XP (I guess). I have Windows xp on drive C (25 G) storage on E (80 G, 40 free) and the 15 G unallocated space. I dont want it to sound like I know what I'm doing; I know very little. I have read the install instructions but still have questions.

Can I just tell it to install to that 15 G space? Do I have to format it or will Ubunto do that for me? I also have EASEUS partition manager, that is what I set up the partitions with when I installed the HD last spring. I dont know if I will need it but just thought I'd mention it as I found it quite easy to use and can use it again if I have to. 

I'm also wondering how to create the swap file I read about in the install instructions-is that going to be straightforward (ie is Ubunto going to ask me if/how i want to do that?) 

Lastly, how can I get my wireless working once it is installed, without havig a wired connection? I was able to get it working on USB because I found an ethernet connection O could use, but I dont have that available right now. 

Anything else I need to know? I'd like to install this today if I can....Thanks!

---

### Post by darkod on 2009-11-28
Since you have unpartitioned space you can just tell the installer to use that. I think the option was called something like Use Largest Continuos Free Space. In that case it will create one bigger / partition and the swap partition by itself, no need to worry about it. It will format automatically so no need to worry about that too.

The wi-fi might be a problem, if it didn't work on LiveCD probably it will not have the drivers to work by itself. One option might be to put the driver you have on usb stick and use it later. You said you installed it yourself, still got it?

Any particular reason you want 8.10? 9.10 might have your wi-fi driver for example.

---

### Post by phillw on 2009-11-28
> **darkod said:**
> Since you have unpartitioned space you can just tell the installer to use that. I think the option was called something like Use Largest Continuos Free Space. In that case it will create one bigger / partition and the swap partition by itself, no need to worry about it. It will format automatically so no need to worry about that too.

The wi-fi might be a problem, if it didn't work on LiveCD probably it will not have the drivers to work by itself. One option might be to put the driver you have on usb stick and use it later. You said you installed it yourself, still got it?

Any particular reason you want 8.10? 9.10 might have your wi-fi driver for example.

Another neat tip is to do the install without the ethernet lead plugged in .... Don't ask me why ... but it worked for me & others ;-)

Regards,

phill.

---

### Post by Cariboukayak on 2009-11-28
No reason I cant use 9.10, but I figured I can always upgrade and I already have 8.10. 

Its my modem that has been difficult, my wireless worked fine once I activated it via ethernet. Modem questions will surely be coming after install.

I'm too dumb to know how to save the B43 wireless driver and install it separately. I do have it somewhere on my USB because it works...

I dont have ethernet n ow so its n ot a problem installling without it plugged in...but it never did me any good when booting from USB. I had to get on ethernet to activate wireless.  It seems like it should be able to install the driver since its there, working right now on the USB that I will install the OS from, but I have a feeling that wont happen.

---

### Post by darkod on 2009-11-28
Just to remind you that clean install of 9.10 would always be preferred then clean install of 8.10 and upgrading. Lots of issues can happen with the upgrade.
If you don't have fast internet or internet at all, maybe a friend can help you download the 9.10 version and put it on CD or bootable usb stick. It's free. And as I said, it might recognize your wi-fi and you don't have to worry about drivers then.

---

### Post by Cariboukayak on 2009-11-28
I'll try that. Downloading 9.10....

---

### Post by Cariboukayak on 2009-11-29
> **Cariboukayak said:**
> I'll try that. Downloading 9.10....


Wish I hadnt. It too me all day and then a 60 mile drive to get 9.10, and after all that I didnt bother to test it. I installed it to the 15G space no problem, but it not only does NOT have my wireless driver as far as I an tell) it doesnt even give me the option of activating the one that worked in 8.10, even when I'm connected t ethernet (which I have to drive a long way to get).  I tried to install 8.10 over it, but it asked questions about roots that I am too dumb to answer. So now I'm stuck again with no connectivity.

---

